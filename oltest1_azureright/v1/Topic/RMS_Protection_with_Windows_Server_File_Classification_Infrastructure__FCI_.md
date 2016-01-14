---
description: na
keywords: na
title: RMS Protection with Windows Server File Classification Infrastructure (FCI)
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
---
# Protezione RMS con l&#39;infrastruttura di classificazione file (FCI, File Classification Infrastructure) per Windows Server
Usare questo articolo per ottenere istruzioni e uno script che consentono di usare il client Rights Management (RMS) con lo strumento di protezione RMS per configurare Gestione risorse file server e l'infrastruttura di classificazione file.

Queste soluzioni consentono di proteggere automaticamente tutti i file contenuti in una cartella di un file server che esegue Windows Server o proteggere automaticamente i file che soddisfano criteri specifici. File, ad esempio, che sono stati classificati come contenenti informazioni riservate o personali. Questa soluzione usa [Azure Rights Management](../Topic/Azure_Rights_Management.md) (Azure RMS) per proteggere i file, perciò è necessario che questa tecnologia sia distribuita nella propria organizzazione.

> [!NOTE]
> Nonostante Azure RMS includa un [connettore](https://technet.microsoft.com/library/dn375964.aspx) che supporta l'infrastruttura di classificazione file, questa soluzione supporta solo la protezione nativa, ad esempio, i file di Office.
> 
> Per supportare tutti i tipi di file con l'infrastruttura di classificazione file, è necessario usare il modulo di **protezione RMS** di Windows PowerShell, come descritto in questo articolo. I cmdlet di protezione RMS, come l'applicazione RMS sharing, supportano la protezione generica nonché quella nativa, per cui è possibile proteggere tutti i file. Per altre informazioni su questi livelli di protezione diversi, vedere la sezione [Livelli di protezione – nativo e generico](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) nell'argomento [Guida dell'amministratore dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md).

Le istruzioni qui di seguito sono per Windows Server 2012 R2 o Windows Server 2012. Se si eseguono altre versioni supportate di Windows, potrebbe essere necessario adattare alcuni di questi passaggi a causa delle differenze tra la versione del proprio sistema operativo e quello descritto in questo articolo.

## Prerequisiti per la protezione di Azure RMS con l'infrastruttura di classificazione file per Windows Server
Prerequisiti per queste istruzioni:

-   Su ogni file server su cui si esegue Gestione risorse file con l'infrastruttura di classificazione file:

    -   Gestione risorse file è stato installato come uno dei servizi ruolo per il ruolo Servizi file.

    -   È stata identificata una cartella locale che contiene file da proteggere con Rights Management. Ad esempio, C:\FileShare.

    -   È stato installato lo strumento di protezione RMS, inclusi i prerequisiti per lo strumento (ad esempio, il client RMS) e Azure RMS (ad esempio, l'account dell'entità servizio). Per altre informazioni, vedere [Cmdlet di protezione RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Se si vuole modificare il livello predefinito di protezione RMS (nativa o generica) per estensioni di file specifiche, si deve modificare il Registro di sistema come descritto nella pagina [Configurazione delle API dei file](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx).

    -   È disponibile una connessione Internet con le impostazioni del computer configurate, se necessario per un server proxy ad esempio `netsh winhttp import proxy source=ie`

-   I prerequisiti aggiuntivi sono stati configurati per la distribuzione di Azure Rights Management, come descritto in [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx). In particolare, sono disponibili i valori seguenti per connettersi ad Azure RMS usando un'entità servizio:

    -   BposTenantId

    -   AppPrincipalId

    -   Chiave simmetrica

-   Si sono sincronizzati gli account utente di Active Directory locali con Azure Active Directory o Office 365, compreso il loro indirizzo di posta elettronica. Ciò è necessario per tutti gli utenti a che potrebbero avere necessità di accedere ai file dopo che sono protetti da FCI e Azure RMS. Se si completa questo passaggio (ad esempio, in un ambiente di prova), gli utenti potrebbero essere bloccati ad accedere a questi file. Se sono necessarie ulteriori informazioni sulla configurazione di questo account, vedere [Preparazione per Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

-   È stato identificato il modello Rights Management da usare, che proteggerà i file. Assicurarsi di conoscere l'ID per questo modello usando il cmdlet [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx).

## Istruzioni per configurare l'infrastruttura di classificazione file di Gestione risorse file server per la protezione di Azure RMS
Per proteggere automaticamente tutti i file di una cartella usando uno script di Windows PowerShell come attività personalizzata, seguire queste istruzioni. Eseguire questa procedura secondo l'ordine seguente:

1.  Salvare uno script di Windows PowerShell

2.  Creare una proprietà di classificazione per Rights Management (RMS)

3.  Creare una regola di classificazione (Classifica per RMS)

4.  Configurare la pianificazione di classificazione

5.  Creare un'attività personalizzata di gestione file (Proteggi file con RMS)

6.  Testare la configurazione eseguendo manualmente la regola e l'attività

Al termine di queste istruzioni tutti i file della cartella selezionata saranno classificati con la proprietà personalizzata di RMS e saranno protetti da Rights Management. Per una configurazione più complessa che protegge in modo selettivo alcuni file e non altri, è possibile creare o usare una proprietà e una regola di classificazione diverse con un'attività di gestione file che protegge solo quei file.

#### Salvare uno script di Windows PowerShell

1.  Espandere la sezione [Script di Windows PowerShell per la protezione Azure RMS usando l'infrastruttura di classificazione file di Gestione risorse file server](#BKMK_RMSProtection_Script) in questo articolo e copiarne il contenuto. Incollare il contenuto dello script e il nome del file **RMS-Protect-FCI.ps1** nel proprio computer.

2.  Rivedere lo script e apportare le seguenti modifiche:

    -   Cercare la stringa seguente e sostituirla con il proprio AppPrincipalId usato con il cmdlet [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) per connettersi ad Azure RMS:

        ```
        <enter your AppPrincipalId here>
        ```
        Il seguente, ad esempio, è un tipico script:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)] [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Cercare la stringa seguente e sostituirla con la propria chiave simmetrica usata con il cmdlet [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) per connettersi ad Azure RMS:

        ```
        <enter your key here>
        ```
        Il seguente, ad esempio, è un tipico script:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Cercare la stringa seguente e sostituirla con il proprio BposTenantId (ID tenant) usato con il cmdlet [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) per connettersi ad Azure RMS:

        ```
        <enter your BposTenantId here>
        ```
        Il seguente, ad esempio, è un tipico script:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Se sul server è in esecuzione Windows Server 2012, potrebbe essere necessario caricare manualmente il modulo RMSProtection all'inizio dello script. Aggiungere il seguente comando o uno equivalente se la cartella "Programmi" è su un'unità diversa da C::

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  Firmare lo script. Se non si firma lo script (più sicuro), è necessario configurare Windows PowerShell sui server che lo eseguono. Eseguire, ad esempio, la sessione di Windows PowerShell con l'opzione **Esegui come amministratore** e digitare: **Set-ExecutionPolicy Unrestricted**. Questa configurazione, tuttavia, consente l'esecuzione di tutti gli script non firmati (meno sicuri).

    Per altre informazioni sulla firma degli script di Windows PowerShell, vedere [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) nella raccolta di documentazione di PowerShell.

4.  Salvare il file localmente su ogni file server che eseguirà Gestione risorse file con l'interfaccia di classificazione file. Salvare, ad esempio, il file in **C:\RMS-Protection**. Proteggere questo file usando le autorizzazioni NTFS in modo che utenti non autorizzati non possano modificarlo.

A questo punto si è pronti per iniziare la configurazione di Gestione risorse file server.

#### Creare una proprietà di classificazione per Rights Management (RMS)

-   In Gestione classificazioni di Gestione risorse file server creare una nuova proprietà locale:

    -   **Name**: Digitare **RMS**

    -   **Descrizione**:   Digitare **Protezione di Rights Management**

    -   **Tipo di proprietà**: Selezionare **Sì/No**

    -   **Valore**: Selezionare **Sì**

È ora possibile creare una regola di classificazione che usa questa proprietà.

#### Creare una regola di classificazione (Classifica per RMS)

-   Creare una nuova regola di classificazione:

    -   Fare clic sulla scheda **Generale**:

        -   **Name**: Digitare **Classifica per RMS**

        -   **Enabled**: Mantenere il valore predefinito,cioè quello selezionato in questa casella di controllo.

        -   **Descrizione**: Digitare **Classifica tutti i file nella cartella &lt;nome cartella&gt; per Rights Management**.

            Sostituire*&lt;nome cartella&gt;* con il nome della cartella scelta. Ad esempio, **Classifica tutti i file nella cartella C:\FileShare per Rights Management**

        -   **Ambito**: Aggiungere la cartella scelta. Ad esempio, **C:\FileShare**.

            Non selezionare le caselle di controllo.

    -   Nella scheda **Classificazione**:

    -   **Metodo di classificazione**: Selezionare **Utilità di classificazione cartelle**

    -   Nome **Proprietà**: Selezionare **RMS**

    -   **Valore** proprietà: Selezionare **Sì**

Nonostante sia possibile eseguire manualmente le regole di classificazione per le operazioni in corso, si vuole che questa regola venga eseguita in una pianificazione in modo tale che i nuovi file vengano classificati con la proprietà RMS.

#### Configurare la pianificazione di classificazione

-   Nella scheda **Classificazione automatica**:

    -   **Abilita pianificazione fissa**: Selezionare questa casella di controllo.

    -   Configurare la pianificazione per tutte le regole di classificazione da eseguire, che includono la nuova regola per classificare file con la proprietà RMS.

    -   **Consenti classificazione continua per i nuovi file**: Selezionare questa casella di controllo in modo che i nuovi file vengano classificati.

    -   Facoltativa: Apportare eventuali altre modifiche, come la configurazione di opzioni per report e notifiche.

Quando si è completata la configurazione per la classificazione, si è pronti per la configurazione di un'attività di gestione per applicare la protezione RMS ai file.

#### Creare un'attività personalizzata di gestione file (Proteggi file con RMS)

-   In **Attività di gestione file** creare una nuova attività di gestione file:

    -   Fare clic sulla scheda **Generale**:

        -   **Nome attività**: Digitare **Proteggi file con RMS**

        -   Mantenere selezionata la casella di controllo **Abilita**.

        -   **Descrizione**: Digitare **Proteggi i file in &lt;nome cartella&gt; con Rights Management e un modello usando uno script di Windows PowerShell.**

            Sostituire*&lt;nome cartella&gt;* con il nome della cartella scelta. Digitare, ad esempio, **Proteggi i file in C:\FileShare con Rights Management e un modello usando uno script di Windows PowerShell**

        -   **Ambito**: Selezionare la cartella scelta. Ad esempio, **C:\FileShare**.

            Non selezionare le caselle di controllo.

    -   Nella scheda **Azione**:

        -   **Type**: Selezionare **Personalizzata**

        -   **Eseguibile**: Specificare quanto segue:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Se Windows non è disponibile sull'unità C:, modificare questo percorso o selezionare questo file.

        -   **Argomento**: Specificare quanto segue, fornendo i propri valori per &lt;percorso&gt; e &lt;ID modello&gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Se, ad esempio, si copia lo script in C:\RMS-Protection e l'ID modello identificato dai prerequisiti è e6ee2481-26b9-45e5-b34a-f744eacd53b0, specificare quanto segue:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            In questo comando **[Percorso file di origine]** e **[Indirizzo posta elettronica proprietario file di origine]** sono entrambe variabili specifiche dell'infrastruttura di classificazione dei file, per cui digitarle nel comando qui sopra esattamente così come sono visualizzate. La prima viene usata dall'infrastruttura di classificazione file per specificare in modo automatico il file identificato della cartella e la seconda è per l'infrastruttura di classificazione file per richiamare automaticamente l'indirizzo di posta elettronica del proprietario del file identificato. Questo comando viene ripetuto per ogni file della cartella, che nel nostro esempio è ogni file della cartella C:\FileShare che inoltre ha RMS come proprietà di classificazione file.

            > [!NOTE]
            > Il parametro e valore  **-OwnerMail [Source File Owner Email]** garantisce che al proprietario originale del file viene concesso il diritto di proprietario Rights Management del file dopo che è stato protetto. Questo assicura che il proprietario del file originale ha tutti i diritti Rights Management per i propri file. Quando i file vengono creati da un utente di dominio, l'indirizzo di posta elettronica viene recuperato automaticamente da Active Directory utilizzando il nome dell'account utente nella proprietà Proprietario del file. Per effettuare questa operazione, il file server deve essere nello stesso dominio o dominio trusted dell’utente.
            > 
            > Quando possibile, assegnare i proprietari originali ai documenti protetti per assicurare che questi utenti continuino ad avere il pieno controllo dei file creati. Tuttavia, se si utilizza la variabile [Indirizzo posta elettronica proprietario file di origine] come sopra e un file non dispone di un utente di dominio definito come proprietario (ad esempio, un account locale è stato utilizzato per creare il file, quindi il proprietario visualizza SYSTEM), lo script non verrà eseguito.
            > 
            > Per i file che non hanno un utente di dominio come proprietario, è possibile copiare e salvare questi file come utente di dominio in modo da diventare il proprietario solo di questi file. In alternativa, se si dispone di autorizzazioni, è possibile modificare manualmente il proprietario.  O, in alternativa, è possibile fornire un indirizzo di posta elettronica specifico (come indirizzo personale o di gruppo per il reparto IT) anziché la variabile [Indirizzo posta elettronica proprietario file di origine], il che significa che tutti i file protetti con questo script utilizzeranno questo indirizzo di posta elettronica per definire il nuovo proprietario.

    -   **Esegui il comando come**: Selezionare **Sistema locale**

    -   Nella scheda **Condizione**:

        -   **Proprietà**: Selezionare **RMS**

        -   **Operatore**: Selezionare **Uguale**

        -   **Valore**: Selezionare **Sì**

    -   Nella scheda **Pianificazione**:

        -   **Esegui alle**: Configurare la pianificazione preferita.

            Attendere il completamento dello script. Nonostante questa soluzione protegga tutti i file della cartella, lo script viene eseguito una volta per file ogni volta. Nonostante questa operazione richieda più tempo della protezione di tutti i file contemporaneamente, che è supportata dallo strumento di protezione RMS, questa configurazione file per file per l'infrastruttura di classificazione file è molto più efficace. Ad esempio, i file protetti possono avere proprietari diversi (mantenere il proprietario originale) quando si usa la variabile [Indirizzo posta elettronica proprietario file di origine] e questa azione file per file sarà obbligatoria se si modifica in seguito la configurazione per proteggere in modo selettivo i file invece che tutti i file della cartella.

        -   **Esegui in modo continuo sui nuovi file**: Selezionare questa casella di controllo.

#### Testare la configurazione eseguendo manualmente la regola e l'attività

1.  Eseguire la regola di classificazione:

    1.  Fare clic su **Regole di classificazione** &gt; **Esegui classificazione con tutte le regole**

    2.  Fare clic su **Attendi il completamento della classificazione** e quindi fare clic su **OK**.

2.  Attendere la chiusura della finestra di dialogo **Esecuzione classificazione** e visualizzare i risultati del report visualizzato automaticamente. Verrà visualizzato **1** per il campo **Proprietà** e il numero di file della cartella. Confermare usando Esplora file e selezionando le proprietà dei file nella cartella selezionata. Nella scheda **Classificazione** verrà visualizzato **RMS** come nome proprietà e **Sì** per il **Valore**.

3.  Eseguire l'attività di gestione file:

    1.  Fare clic su **Attività di gestione file** &gt; **Proteggi file con RMS** &gt; **Esegui attività di gestione file**

    2.  Fare clic su **Attendi il completamento dell'attività** e quindi fare clic su **OK**.

4.  Attendere la chiusura della finestra di dialogo **Esecuzione attività di gestione file** e visualizzare i risultati del report visualizzato automaticamente. Verrà visualizzato il numero di file contenuti nella cartella selezionata nel campo **File**. Confermare che i file della cartella selezionata sono ora protetti da RMS. Se, ad esempio, la cartella selezionata è C:\FileShare, immettere i dati seguenti in una sessione di Windows PowerShell e confermare che non ci siano file con lo stato **Non protetto**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Alcuni suggerimenti per la risoluzione dei problemi:
    > 
    > -   Se viene visualizzato **0** nel report, invece del numero di file della cartella, questo valore indicherà che lo script non è stato eseguito. Prima di tutto, verificare lo script caricandolo in Windows PowerShell ISE per convalidare il contenuto dello script e cercare di eseguirlo per vedere se sono visualizzati errori. Senza specificare alcun argomento, lo script cercherà di connettersi ed eseguire l'autenticazione ad Azure RMS.
    > 
    >     -   Se lo script non riesce a connettersi ad Azure RMS, verificare i valori visualizzati per l'account dell'entità servizio, specificato nello script.  Per altre informazioni su come creare questo account dell'entità servizio, vedere il secondo prerequisito in [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)
    >     -   Se lo script non riesce a connettersi ad Azure RMS e la propria area di Azure è al di fuori dell'America del Nord, verificare di aver modificato correttamente il Registro di sistema per questa configurazione. A tale scopo eseguire direttamente Get-RMSTemplate da Windows PowerShell sul server. Per altre informazioni sulle modifiche del Registro di sistema, vedere il terzo prerequisito in [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx).
    > -   Se lo script da solo viene eseguito in Windows PowerShell ISE senza errori, cercare di eseguirlo come indicato da una sessione PowerShell, specificando il nome file da proteggere e senza il parametro -OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File <full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Se lo script viene eseguito correttamente in questa sessione di Windows PowerShell, verificare le voci relative a **Executive** e **Argomento** nell'azione per le attività di gestione file.  Se si è specificato  **-OwnerEmail [Indirizzo posta elettronica proprietario file di origine]**, provare a rimuovere questo parametro.
    > 
    >         Se l'attività di gestione dei file funziona correttamente senza  **- OwnerEmail [Indirizzo posta elettronica proprietario file di origine]** , verificare che i file non protetti abbiano un utente di dominio elencato come proprietario del file, piuttosto che **SYSTEM**.  Per effettuare questa operazione, utilizzare la scheda **Sicurezza** per le proprietà del file, quindi fare clic su **Avanzate**. Il valore **proprietario** valore viene visualizzato immediatamente dopo il **nome** del file. Inoltre, verificare che il file server si trova nello stesso dominio o in un dominio trusted per ricercare l'indirizzo di posta elettronica dell'utente dai servizi di dominio Active Directory.
    > -   Se si visualizza il numero corretto di file nel report, ma i file non sono protetti, provare a proteggerli manualmente usando il cmdlet [Protect-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) per vedere se sono visualizzati eventuali errori.

Dopo aver verificato che queste operazioni vengono eseguite correttamente, è possibile chiudere Gestione risorse file. I nuovi file saranno automaticamente protetti e tutti i file saranno nuovamente protetti quando si eseguono le pianificazioni. La riprotezione dei file assicura che eventuali modifiche al modello vengono applicate ai file.

### <a name="BKMK_RMSProtection_Script"></a>Script di Windows PowerShell per la protezione Azure RMS usando l'infrastruttura di classificazione file di Gestione risorse file server
Questa sezione contiene lo script di esempio per eseguire la copia e la modifica, come descritto nella sezione precedente.

*&#42;&#42;Declinazione di responsabilità&#42;&#42;: Questo script di esempio non è supportato in alcun programma o servizio di supporto standard Microsoft. Questo script di esempio viene fornito "nello stato in stato in cui si trova" senza garanzia di alcun tipo.*

```
<# .SYNOPSIS Helper script to protect all file types with Azure RMS and FCI. .DESCRIPTION Protect files with Azure RMS and Windows Server FCI, using an RMS template ID. #> param( [Parameter(Mandatory = $false)] [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })] [string]$File, [Parameter(Mandatory = $false)] [string]$TemplateID, [Parameter(Mandatory = $false)] [string]$OwnerMail, [Parameter(Mandatory = $false)] [string]$AppPrincipalId = "<enter your AppPrincipalId here>", [Parameter(Mandatory = $false)] [string]$SymmetricKey = "<enter your key here>", [Parameter(Mandatory = $false)] [string]$BposTenantId = "<enter your BposTenantId here>" ) # script information [String] $Script:Version = 'version 1.0' [String] $Script:Name = "RMS-Protect-FCI.ps1" #global working variables [switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running. #**Functions (general helper)*************************************** function Get-ScriptName(){ return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1) } #**Functions (script specific)************************************** function Check-Module{ param ([String]$Module = $(Throw "Module name not specified")) [bool]$isResult = $False #try to load the module if (get-module -list -name $Module) { import-module $Module if (get-module -name $Module ) { $isResult = $True } else { $isResult = $False } } else { $isResult = $False } return $isResult } function Protect-File ($ffile, $ftemplateId, $fownermail) { [bool] $returnValue = $false try { If ($OwnerMail -eq $null -or $OwnerMail -eq "") { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId") } else { $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId -OwnerEmail $fownermail $returnValue = $true Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail") } } catch { Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId") } return $returnValue } function Set-RMSConnection ($fappId, $fkey, $fbposId) { [bool] $returnValue = $false try { Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") $returnValue = $true } catch { Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId") } return $returnValue } #**Main Script (Script)********************************************* Write-Host ("-== " + $Script:Name + " " + $Version + " ==-") $Script:isScriptProcess = $True # Validate Azure RMS connection by checking the module and then connection if ($Script:isScriptProcess) { if (Check-Module -Module RMSProtection){ $Script:isScriptProcess = $True } else { Write-Host ("The RMSProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } if ($Script:isScriptProcess) { #Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" ) if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) { Write-Host ("Connected to Azure RMS") } else { Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black" $Script:isScriptProcess = $False } } #  Start working loop if ($Script:isScriptProcess) { if ( !(($File -eq $null) -or ($File -eq "")) ) { if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) { $Script:isScriptProcess = $False } } } # Closing if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"} write-host ("-== " + $Script:Name + " " + $Version + "  ==-") if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}
```

## Modifica delle istruzioni per proteggere i file in modo selettivo
Quando le istruzioni appena descritte risultano efficaci, è molto semplice modificarle per ottenere una configurazione più avanzata. Ad esempio, proteggere i file usando lo stesso script ma solo per i file che contengono informazioni personali e magari selezionare un modello che ha diritti più restrittivi.

A tale scopo, usare una delle proprietà di classificazione predefinite (ad esempio, **Informazioni personali**) o creare la propria nuova proprietà. Creare quindi una nuova regola che usi questa proprietà. Ad esempio, si potrebbe selezionare **Classificazione contenuto**, scegliere la proprietà **Informazioni personali** con un valore **Alto** e configurare la stringa o il modello di espressione che identifica il file da configurare per questa proprietà (ad esempio la stringa "**Data di nascita**").

A questo punto è sufficiente creare una nuova attività di gestione file che usa lo stesso script ma forse con un modello diverso e configurare la condizione per la proprietà di classificazione appena configurata. Ad esempio, invece della condizione configurata in precedenza (la proprietà **RMS**, **Uguale**, **Sì**), selezionare la proprietà **Informazioni personali** con il valore **Operatore** impostato su **Uguale** e il **ValoreAlto**.

