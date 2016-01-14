---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# Migrazione da AD&#160;RMS ad Azure Rights Management
Usare il set di istruzioni seguente per la migrazione della distribuzione di Active Directory Rights Management Services (AD RMS) ad Azure Rights Management (Azure RMS). Dopo la migrazione gli utenti avranno comunque accesso ai documenti e ai messaggi di posta elettronica che l'organizzazione ha protetto con AD RMS, nonché al nuovo contenuto che verrà protetto con Azure RMS.

Se non si è certi che questa migrazione di AD RMS sia adatta alla propria organizzazione

-   Per un'introduzione ad Azure RMS, ai problemi che può risolvere, a opinioni di amministratori e utenti e al relativo funzionamento, vedere [Informazioni su Microsoft Azure Rights Management](../Topic/What_is_Azure_Rights_Management_.md)

-   Per un confronto tra Azure RMS e AD RMS, vedere [Confronto tra Rights Management di Microsoft Azure e AD RMS](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md).

## Prerequisiti per la migrazione da AD RMS ad Azure RMS
Prima di iniziare il processo di migrazione ad Azure RMS, verificare che i prerequisiti seguenti siano soddisfatti e accertarsi di avere compreso le possibili limitazioni.

|Requisito|Altre informazioni|
|-------------|----------------------|
|Distribuzione di RMS supportata|Tutte le versioni di AD RMS, da Windows Server 2008 a Windows Server 2012 R2, supportano la migrazione ad Azure RMS:<br /><br />-   Windows Server 2008 (x86 o x64)<br />-   Windows Server 2008 R2 (x64)<br />-   Windows Server 2012 (x64)<br />-   Windows Server 2012 R2 (x64) **Note:** Se si esegue Windows RMS in Windows Server 2003, questa versione del sistema operativo non sarà più supportata nel corso del 2015. È possibile eseguire la migrazione di questa versione di RMS ad Azure RMS, ma questo processo è supportato solo se lo è il sistema operativo. Come soluzione alternativa è possibile importare il dominio di pubblicazione trusted in una versione di AD RMS supportata e quindi reimportarlo senza l'opzione di compatibilità RMS 1.0. Per altre informazioni sui domini di pubblicazione trusted, vedere [Dominio di pubblicazione trusted](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)<br />Sono supportate tutte le topologie di AD RMS valide:<br /><br />-   Singola foresta, singolo cluster RMS<br />-   Singola foresta, più cluster RMS di sola gestione delle licenze<br />-   Più foreste, più cluster RMS **Note:** Per impostazione predefinita, la migrazione di più cluster RMS viene eseguita a un singolo tenant di Azure RMS. Per usare diversi tenant di RMS, è necessario considerarli come diverse migrazioni. Non è possibile importare una chiave da un cluster RMS in più tenant di Azure RMS.|
|Tutti i requisiti per l'esecuzione di Azure RMS, incluso un tenant di Azure RMS (non attivato)|Vedere [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Anche se è necessario avere un tenant di Azure RMS per poter eseguire la migrazione da AD RMS, è consigliabile non attivare il servizio Rights Management prima della migrazione. Questo passaggio è incluso nel processo di migrazione dopo l'esportazione delle chiavi e dei modelli da AD RMS e la relativa importazione in Azure RMS. Tuttavia, se Azure RMS è già attivato, è ugualmente possibile eseguire la migrazione da AD RMS.|
|Preparazione per Azure RMS:<br /><br />-   Sincronizzazione della directory tra la directory locale e Azure Active Directory<br />-   Gruppi abilitati alla posta elettronica in Azure Active Directory|Vedere [Preparazione per Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).|
|Se è stata usata la funzionalità Information Rights Management (IRM) di Exchange Server (ad esempio le regole di trasporto e Outlook Web Access) o SharePoint Server con AD RMS:<br /><br />-   Pianificare un breve intervallo di tempo durante il quale IRM non sarà disponibile in questi server|Si potrà continuare a usare IRM in questi server con Azure RMS dopo la migrazione. Uno dei passaggi della migrazione consiste tuttavia nel disattivare temporaneamente il servizio IRM, installare e configurare un connettore, riconfigurare i server e quindi riabilitare IRM.<br /><br />Questa è la sola interruzione del servizio durante il processo di migrazione.|
Limitazioni:

-   Anche se il processo di migrazione supporta la migrazione della chiave del certificato SLC da un modulo di protezione hardware per Azure RMS, Exchange Online non supporta attualmente questa configurazione. Se si vuole la funzionalità IRM completa con Exchange Online dopo la migrazione ad Azure RMS, la chiave del tenant di Azure RMS deve essere [gestita da Microsoft](http://technet.microsoft.com/library/dn440580.aspx). In alternativa, è possibile eseguire IRM con la funzionalità ridotta in Exchange Online quando il tenant di Azure RMS è gestito dall'utente (BYOK). Per altre informazioni sull'uso di Exchange Online con Azure RMS, vedere [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration) in queste istruzioni.

-   Se si usano software e client non supportati con Azure RMS, non riusciranno a proteggere o usare il contenuto protetto da Azure RMS. Verificare la sezione relativa ad applicazioni e client supportati nell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

-   Se si importa la chiave locale in Azure RMS come archiviata (non si imposta il dominio di pubblicazione trusted come attivo durante il processo di importazione) e si esegue la migrazione degli utenti in batch per una migrazione graduale, il nuovo contenuto protetto dagli utenti di cui è stata eseguita la migrazione non sarà accessibile agli utenti che rimangono in AD RMS. In questo scenario, quando possibile, eseguire la migrazione degli utenti in tempi brevi e in batch logici, in modo che, quelli che collaborano tra loro, vengano sottoposti a migrazione insieme.

    Questa limitazione non viene applicata quando si imposta il dominio di pubblicazione trusted come attivo durante il processo di importazione, perché tutti gli utenti proteggeranno il contenuto usando la stessa chiave. Si consiglia questa configurazione perché consente di eseguire la migrazione di tutti gli utenti in modo indipendente e con gradualità.

-   Se si collabora con partner esterni, ad esempio tramite domini utente trusted o la federazione, anche questi dovranno eseguire la migrazione ad Azure RMS contemporaneamente a quando viene eseguita dall'utente o quanto prima possibile. Per continuare ad accedere ai contenuti precedentemente protetti dall'organizzazione con AD RMS, i partner dovranno apportare modifiche di configurazione al client simili a quelle apportate dall'utente, descritte in questo documento.

    A causa delle differenze di configurazione tra l'utente e i partner, le istruzioni precise per questa riconfigurazione non rientrano nell'ambito di questo documento. Per informazioni, contattare il Servizio Supporto Tecnico Clienti Microsoft.

## Procedura per la migrazione da AD RMS ad Azure RMS

|Passaggio della migrazione|Altre informazioni|
|------------------------------|----------------------|
|**1. Scaricare Azure RMS Management Administration Tool**|Per istruzioni, vedere [Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration).|
|**2. Esportare i dati di configurazione da AD RMS e importarli in Azure RMS**|Esportare i dati di configurazione (chiavi, modelli, URL) da AD RMS in un file XML e quindi caricare il file in Azure RMS usando il cmdlet Import-AadrmTpd di Windows PowerShell. Potrebbero essere necessari altri passaggi, a seconda della configurazione della chiave di AD RMS<br /><br />-   Migrazione da una chiave protetta tramite software a un'altra: da chiavi basate su password gestite a livello centrale in AD RMS a chiave del tenant di Azure RMS gestita da Microsoft. Questo è il percorso di migrazione più semplice e non richiede altri passaggi.<br />-   Migrazione da una chiave HSM protetta a un'altra: da chiavi archiviate da un modulo di protezione hardware per AD RMS a chiave del tenant di Azure RMS gestita dal cliente (scenario "bring your own key" o BYOK). È necessario eseguire altri passaggi per trasferire la chiave dal modulo di protezione hardware Thales locale al modulo di protezione hardware di Azure RMS.<br />-   Migrazione da una chiave tramite software a una chiave HSM protetta: chiavi basate su password gestite a livello centrale in AD RMS a chiave del tenant di Azure RMS gestita dal cliente (scenario "bring your own key" o BYOK). È necessaria la configurazione più estesa, perché è innanzitutto necessario estrarre la chiave software e importarla in un modulo di protezione hardware locale e quindi eseguire i passaggi aggiuntivi per trasferire la chiave dal modulo di protezione hardware Thales locale al modulo di protezione hardware di Azure RMS.<br /><br />Per istruzioni, vedere [Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration).|
|**3. Attivare il tenant di RMS**|Se possibile, eseguire questo passaggio dopo il processo di importazione, non prima.<br /><br />Per altre informazioni e istruzioni, vedere [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).|
|**4. Configurare i modelli importati**|Quando si importano i modelli di criteri per i diritti di utilizzo, il relativo stato viene archiviato. Se si vuole che gli utenti possano visualizzarli e usarli, è necessario modificare lo stato del modello in Pubblicato nel portale di Azure classico.<br /><br />Per istruzioni, vedere [Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration).|
|**5. Riconfigurare i client per l'uso di Azure RMS**|Per usare il servizio Azure RMS invece del servizio AD RMS, è necessario riconfigurare i computer Windows esistenti. Questo passaggio si applica ai computer dell'organizzazione e ai computer di organizzazioni partner, nel caso si sia collaborato con esse durante l'esecuzione di AD RMS.<br /><br />Inoltre, se per supportare dispositivi mobili, quali telefoni e iPad iOS, telefoni e tablet Android, Windows Phone e computer Mac, sono state distribuite le [estensioni per dispositivo mobile](http://technet.microsoft.com/library/dn673574.aspx), sarà necessario rimuovere i record SRV in DNS che reindirizzavano questi client all'uso di AD RMS.<br /><br />Per istruzioni, vedere [Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration).|
|**6. Configurare l'integrazione IRM con Exchange Online**|Questo passaggio è obbligatorio per usare Exchange Online con Azure RMS.<br /><br />Per istruzioni, vedere [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration).|
|**7. Distribuire il connettore RMS**|Questo passaggio è obbligatorio se si vuole usare uno dei servizi locali seguenti con Azure RMS:<br /><br />-   Exchange Server (ad esempio, le regole di trasporto e Outlook Web Access)<br />-   SharePoint Server<br />-   Windows Server con la funzionalità Infrastruttura di classificazione file<br /><br />Per istruzioni, vedere [Passaggio 7: Rimuovere le autorizzazioni di AD RMS](#BKMK_Step7Migration).|
|**8. Rimuovere le autorizzazioni di AD RMS**|Dopo aver verificato che tutti i client usano Azure RMS e non accedono più ai server AD RMS, sarà possibile rimuovere le autorizzazioni per la distribuzione di AD RMS.<br /><br />Per istruzioni, vedere [Passaggio 8: Reimpostare la chiave del tenant di Azure RMS.](#BKMK_Step8Migration).|
|**9. Reimpostare la chiave del tenant di Azure RMS**|Questo passaggio è obbligatorio se prima della migrazione non era in esecuzione la Modalità crittografia 2. È facoltativo, ma consigliato, per tutte le migrazioni allo scopo di salvaguardare la sicurezza della chiave del tenant di Azure RMS.<br /><br />Per istruzioni, vedere [Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>Passaggio 1: Scaricare Azure Rights Management Administration Tool
Passare all'Area download Microsoft e [scaricare Azure Rights Management Administration Tool](http://go.microsoft.com/fwlink/?LinkId=257721), contenente il modulo di amministrazione di Azure RMS per Windows PowerShell.

### <a name="BKMK_Step2Migration"></a>Passaggio 2: Esportare i dati di configurazione da AD RMS e importarli in Azure RMS
Questo passaggio è un processo costituito da due parti:

1.  Esportare i dati di configurazione da AD RMS esportando i domini di pubblicazione trusted in un file XML. Questo processo è identico per tutte le migrazioni.

2.  Importare i dati di configurazione in Azure RMS. Per questo passaggio esistono diversi processi, a seconda della configurazione della distribuzione corrente di AD RMS e della topologia preferita per la chiave del tenant di Azure RMS.

#### Esportare i dati di configurazione da AD RMS.
Eseguire le operazioni seguenti in tutti i cluster AD RMS, per tutti i domini di pubblicazione trusted con contenuto protetto per l'organizzazione. Non è necessario eseguire questa procedura nei cluster usati per la sola gestione delle licenze.

> [!NOTE]
> Se si usa Windows Server 2003 Rights Management, invece di queste istruzioni seguire la procedura [Esportare il certificato concessore di licenze server, il dominio utente trusted, il dominio di pubblicazione trusted e la chiave privata RMS](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) nell'argomento [Migrazione da Windows RMS ad AD RMS in un'infrastruttura diversa](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx).

###### Per esportare i dati di configurazione (informazioni su domini di pubblicazione trusted)

1.  Accedere al cluster AD RMS come utente con autorizzazioni di amministratore di AD RMS.

2.  Dalla console di gestione di AD RMS (**Active Directory Rights Management Services**), espandere il nome del cluster AD RMS, espandere **Criteri di attendibilità** e quindi fare clic su**Domini di pubblicazione trusted**.

3.  Nel riquadro dei risultati selezionare il dominio di pubblicazione trusted e quindi nel riquadro Azioni fare clic su **Esporta dominio di pubblicazione Trusted**.

4.  Nella finestra di dialogo **Esporta dominio di pubblicazione trusted**:

    -   Fare clic su **Salva con nome** e salvare in un percorso e con un nome file a propria scelta. Assicurarsi di specificare **.xml** come estensione di file, perché non viene aggiunta automaticamente.

    -   Specificare e confermare una password complessa. Prendere nota della password, perché sarà necessaria in seguito per l'importazione dei dati di configurazione in Azure RMS.

    -   Non selezionare la casella di controllo per salvare il file di dominio trusted in RMS versione 1.0.

Dopo l'esportazione di tutti i domini di pubblicazione trusted, sarà possibile avviare la procedura di importazione dei dati in Azure RMS.

#### Importare i dati di configurazione in Azure RMS
Le procedure esatte per questo passaggio dipendono dalla configurazione della distribuzione corrente di AD RMS e dalla topologia preferita per la chiave del tenant di Azure RMS.

La distribuzione corrente di AD RMS userà una delle seguenti configurazioni per la chiave del certificato concessore di licenze server (SLC):

-   Password di protezione nel database AD RMS. Questa è la configurazione predefinita.

-   Protezione tramite un modulo di protezione hardware Thales.

-   Modulo di protezione hardware tramite un modulo di protezione hardware di un fornitore diverso da Thales.

-   Protezione con password tramite un provider del servizio di crittografia esterno.

> [!NOTE]
> Per altre informazioni sull'uso di moduli di protezione hardware con AD RMS, vedere [Uso di AD RMS con moduli di protezione hardware](http://technet.microsoft.com/library/jj651024.aspx).

Per la topologia di chiave del tenant di Azure RMS esistono due opzioni: la chiave del tenant viene gestita da Microsoft (**gestione di Microsoft**) oppure dall'utente (**gestione del cliente**). Quando la chiave del tenant di Azure RMS è gestita dall'utente, viene a volte definita BYOK ("bring your own key") e richiede un modulo di protezione hardware di Thales. Per altre informazioni, vedere la sezione [Scegliere la topologia di chiave del tenant: gestione di Microsoft (impostazione predefinita) o BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

> [!IMPORTANT]
> Exchange Online non è attualmente compatibile con la modalità BYOK di Azure RMS.  Se si vuole usare la modalità BYOK dopo la migrazione e si prevede di usare Exchange Online, verificare come questa configurazione riduce la funzionalità IRM per Exchange Online. Rivedere le informazioni nella sezione [Prezzi e restrizioni della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) per poter scegliere la migliore topologia di chiave del tenant di Azure RMS per la migrazione.

Usare la tabella seguente per identificare la procedura da eseguire per la migrazione. Le combinazioni non elencate non sono supportate.

|Distribuzione di AD RMS corrente|Topologia di chiave del tenant di Azure RMS scelta|Istruzioni relative alla migrazione|
|------------------------------------|------------------------------------------------------|---------------------------------------|
|Password di protezione nel database AD RMS|Gestione di Microsoft|Vedere la procedura **Migrazione da chiave protetta tramite software a un'altra** dopo questa tabella.<br /><br />Questo è il percorso di migrazione più semplice e richiede solo il trasferimento dei dati di configurazione in Azure RMS.|
|Modulo di protezione hardware tramite un modulo di protezione hardware nShield di Thales|Gestione del cliente (scenario BYOK)|Vedere la procedura **Migrazione da chiave HSM protetta a un'altra** dopo questa tabella.<br /><br />Sono necessari il set di strumenti BYOK e due procedure per trasferire la chiave dal modulo di protezione hardware locale ai moduli di protezione hardware di Azure RMS e quindi trasferire i dati di configurazione in Azure RMS.|
|Password di protezione nel database AD RMS|Gestione del cliente (scenario BYOK)|Vedere la procedura **Migrazione da una chiave protetta tramite software a una chiave HSM protetta** dopo questa tabella.<br /><br />Sono necessari il set di strumenti BYOK e tre procedure, prima di tutto per estrarre la chiave software e importarla nel modulo di protezione hardware locale, quindi trasferire la chiave dal modulo di protezione hardware locale ai moduli di protezione hardware di Azure RMS e infine trasferire i dati di configurazione in Azure RMS.|
|Modulo di protezione hardware tramite un modulo di protezione hardware di un fornitore diverso da Thales.|Gestione del cliente (scenario BYOK)|Contattare il fornitore del modulo di protezione hardware per istruzioni sul trasferimento della chiave da questo modulo di protezione hardware a un modulo di protezione hardware nShield di Thales. Seguire le istruzioni per la procedura **Migrazione da chiave HSM protetta a un'altra** dopo questa tabella.|
|Protezione con password tramite un provider del servizio di crittografia esterno|Gestione del cliente (scenario BYOK)|Contattare il fornitore del provider del servizio di crittografia per istruzioni sul trasferimento della chiave a un modulo di protezione hardware nShield di Thales. Seguire le istruzioni per la procedura **Migrazione da chiave HSM protetta a un'altra** dopo questa tabella.|
Prima di iniziare queste procedure, assicurarsi che sia possibile accedere ai file con estensione XML creati in precedenza durante l'esportazione dei domini di pubblicazione trusted. Ad esempio, è possibile salvarli su una chiavetta USB che può essere spostata dal server AD RMS alla workstation connessa a Internet.

> [!NOTE]
> Indipendentemente dalla modalità di archiviazione di questi file, per proteggerli attenersi alle procedure consigliate per la sicurezza, poiché tali dati includono la chiave privata.

##### Migrazione da una chiave protetta tramite software a un'altra
Usare questa procedura per importare la configurazione di AD RMS in Azure RMS. La chiave del tenant di Azure RMS verrà gestita da Microsoft.

###### Per importare i dati di configurazione in Azure RMS

1.  In una workstation connessa a Internet scaricare e installare il modulo Windows PowerShell per Azure RMS (versione minima 2.1.0.0), che include il cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx).

    > [!TIP]
    > Se il modulo è stato scaricato e installato in precedenza, verificarne il numero di versione eseguendo il comando seguente: `(Get-Module aadrm -ListAvailable).Version`

    Per le istruzioni di installazione, vedere [Installazione di Windows PowerShell per Microsoft Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

2.  Avviare Windows PowerShell con l'opzione **Esegui come amministratore** e usare il cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) per connettersi al servizio Azure RMS:

    ```
    Connect-AadrmService
    ```
    Quando viene richiesto, immettere le credenziali dell'amministratore del tenant [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. In genere, viene usato un account amministratore globale per Azure Active Directory o Office 365.

3.  Usare il cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) per caricare il file del primo dominio di pubblicazione trusted esportato (file con estensione xml) usando il seguente comando: Se si hanno più file XML, perché avevi più domini di pubblicazione trusted, scegliere il file che contiene il dominio di pubblicazione trusted esportato che si desidera utilizzare in Azure RMS per proteggere il contenuto dopo la migrazione. Utilizzare il seguente comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    ad esempio **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Quando richiesto, immettere la password specificata in precedenza e confermare che si desidera eseguire questa azione.

4.  Al termine del comando, ripetere il passaggio 3 per ogni restante file XML creato esportando il tuo domini di pubblicazione trusted. Per questi file impostare invece **-Active** su **false** quando si esegue il comando di importazione. ad esempio **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Usare il cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) per disconnettersi dal servizio Azure RMS:

    ```
    Disconnect-AadrmService
    ```

È ora possibile andare al [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Migrazione da una chiave HSM protetta a un'altra
Questa procedura in due parti consente di importare la chiave HSM e la configurazione di AD RMS in Azure RMS. La chiave del tenant di Azure RMS verrà gestita dall'utente (BYOK).

Innanzitutto è necessario creare il pacchetto e la chiave HSM in modo che sia pronta da trasferire in Azure RMS e quindi importarla con i dati di configurazione.

###### Parte 1: Il pacchetto della chiave HSM è quindi pronto per essere trasferito ad Azure RMS

1.  Attenersi alla procedura riportata nella sezione [Implementazione della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), usando la procedura **Generare e trasferire la propria chiave del tenant tramite Internet** con l'eccezione seguente:

    -   Non seguire la procedura per **generare la chiave del tenant**, perché ne esiste già una equivalente nella distribuzione di AD RMS. È necessario identificare la chiave usata dal server AD RMS dall'installazione di Thales e usare questa chiave durante la migrazione. I file di chiave crittografati di Thales sono in genere denominati **key_(keyAppName)_(keyIdentifier)** in locale nel server.

    -   Non seguire la procedura per **Trasferire la chiave tenant ad Azure RMS**, che utilizza il comando Add-AadrmKey.  Al contrario, la chiave HSM preparata verrà trasferita quando si caricherà il dominio di pubblicazione attendibile esportato, utilizzando il comando Import-AadrmTpd.

2.  Nella workstation connessa a Internet, nella sessione PowerShell di Windows, riconnettersi al servizio Azure RMS.

Ora che la chiave HSM è stata preparata per Azure RMS, si è pronti per importare i file di chiave HSM e dati di configurazione di AD RMS.

###### Parte 2: Importare i dati di configurazione e la chiave HSM ad Azure RMS

1.  Ancora sulla workstation connettersi a Internet e nella sessione di Windows PowerShell, caricare il primo file di dominio (. Xml) attendibile esportato editrice. Se si hanno più un file XML, perché avevi più domini di pubblicazione trusted, scegliere il file che contiene il dominio di pubblicazione trusted esportato che corrisponde alla chiave di HSM che si desidera utilizzare in Azure RMS per proteggere il contenuto dopo la migrazione. Utilizzare il seguente comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    ad esempio **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Quando richiesto, immettere la password specificata in precedenza e confermare che si desidera eseguire questa azione.

2.  Al termine del comando, ripetere il passaggio 1 per ogni restante file XML creato esportando il tuo domini di pubblicazione trusted. Per questi file impostare invece **-Active** su **false** quando si esegue il comando di importazione.  ad esempio **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Usare il cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) per disconnettersi dal servizio Azure RMS:

    ```
    Disconnect-AadrmService
    ```

È ora possibile andare al [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

##### Migrazione da una chiave tramite software a una chiave HSM protetta
Questa procedura in tre parti consente di importare la configurazione di AD RMS in Azure RMS. La chiave del tenant di Azure RMS verrà gestita dall'utente (BYOK).

È innanzitutto necessario estrarre la chiave del certificato concessore di licenze server (SLC) dai dati di configurazione e trasferire la chiave in un modulo di protezione hardware locale di Thales, quindi creare il pacchetto e trasferire la chiave del proprio modulo di protezione hardware in Azure RMS e infine importare i dati di configurazione.

###### Parte 1: Estrarre il certificato concessore di licenze server (SLC) dai dati di configurazione e importare la chiave nel modulo di protezione hardware locale

1.  Attenersi alla procedura riportata nella sezione [Implementazione della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Generare e trasferire la propria chiave del tenant tramite Internet**: **Preparare la workstation connessa a Internet**

    -   **Generare e trasferire la propria chiave del tenant tramite Internet**: **Preparare la workstation disconnessa**

    Non attenersi a questa procedura per generare la chiave del tenant, perché è già disponibile una chiave equivalente nel file di dati di configurazione (con estensione XML) esportati. Si eseguirà invece un comando per estrarre la chiave dal file e importarla nel modulo di protezione hardware locale.

2.  Nella workstation disconnessa eseguire il comando seguente:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Ad esempio, per America del Nord: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Informazioni aggiuntive:

    -   Il parametro ImportRmsCentrallyManagedKey indica che l'operazione consiste nell'importazione della chiave del certificato concessore di licenze server.

    -   Se non si specifica la password nel comando, verrà richiesto di farlo.

    -   Il parametro KeyIdentifier riguarda un nome descrittivo della chiave che crea il nome del file di chiave. È necessario usare solo caratteri ASCII minuscoli.

    -   Il parametro ExchangeKeyPackage indica un pacchetto di chiavi per lo scambio delle chiavi specifico dell'area geografica, il cui nome inizia con BYOK-KEK-pkg-.

    -   Il parametro NewSecurityWorldPackage indica un pacchetto di sicurezza di livello universale specifico dell'area geografica, il cui nome inizia con BYOK-SecurityWorld-pkg-.

    Questo comando produce quanto segue:

    -   File di chiave del modulo di protezione hardware: %NFAST_KMDATA%\local\key_mscapi_&lt;KeyID&gt;

    -   File di dati di configurazione di RMS con il certificato concessore di licenze server (SLC) rimosso: %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml

3.  Se è disponibile più di un file di dati di configurazione di RMS, ripetere il passaggio 2 per il file restanti.

Dopo l'estrazione del certificato concessore di licenze server (SLC) in modo da avere una chiave basata sul modulo di protezione hardware, è possibile creare il pacchetto e trasferirlo in Azure RMS.

###### Parte 2: Creare il pacchetto e trasferire la chiave del modulo di protezione hardware in Azure RMS

1.  Attenersi alla procedura riportata nella sezione [Implementazione della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md):

    -   **Generare e trasferire la propria chiave del tenant tramite Internet**: **Preparare la chiave del tenant per il trasferimento**

    -   **Generare e trasferire la propria chiave del tenant tramite Internet**: **Trasferire la chiave del tenant ad Azure RMS**

Dopo avere trasferito la chiave del modulo di protezione hardware in Azure RMS, è possibile importare i dati di configurazione di AD RMS, che contengono solo un puntatore alla chiave del tenant appena trasferita.

###### Parte 3: Importare i dati di configurazione in Azure RMS

1.  Sempre nella workstation connessa a Internet e nella sessione di Windows PowerShell, copiare i file di configurazione di RMS con il certificato concessore di licenze server (SLC) rimosso (dalla workstation disconnessa, %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml)

2.  Caricare il primo file. Se si hanno più un file XML, perché avevi più domini di pubblicazione trusted, scegliere il file che contiene il dominio di pubblicazione trusted esportato che corrisponde alla chiave di HSM che si desidera utilizzare in Azure RMS per proteggere il contenuto dopo la migrazione. Utilizzare il seguente comando:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    ad esempio **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Quando richiesto, immettere la password specificata in precedenza e confermare che si desidera eseguire questa azione.

3.  Al termine del comando, ripetere il passaggio 2 per ogni restante file XML creato esportando il tuo domini di pubblicazione trusted. Per questi file impostare invece **-Active** su **false** quando si esegue il comando di importazione. ad esempio **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Usare il cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) per disconnettersi dal servizio Azure RMS:

    ```
    Disconnect-AadrmService
    ```

È ora possibile andare al [Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>Passaggio 3. Attivare il tenant di RMS
Le istruzioni per questo passaggio sono descritte in dettaglio nell'argomento [Attivazione di Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

> [!TIP]
> Se si ha una sottoscrizione a Office 365, è possibile attivare Azure RMS dall'interfaccia di amministrazione di Office 365 o nel portale di Azure classico. È consigliabile usare il portale di Azure classico perché verrà usato per completare il passaggio successivo.

**Cosa accade se il tenant di Azure RMS è già attivato?** Se il servizio Azure RMS è già attivato per l'organizzazione, gli utenti potrebbero avere già usato Azure RMS per proteggere il contenuto con una chiave del tenant generata automaticamente (e con i modelli predefiniti) invece che con le chiavi (e i modelli) esistenti da AD RMS. È improbabile che ciò accada su computer ben gestiti nella Intranet, perché verranno automaticamente configurati per l'infrastruttura AD RMS. Può però verificarsi su computer di un gruppo di lavoro o su computer che non si connettono spesso alla Intranet. Dal momento che sfortunatamente è anche difficile identificare questi computer, si consiglia di non attivare il servizio prima di importare i dati di configurazione da AD RMS.

Se il tenant di Azure RMS è già attivato ed è possibile identificare questi computer, assicurarsi di eseguire lo script CleanUpRMS_RUN_Elevated.cmd su questi computer, come descritto nel passaggio 5. L'esecuzione dello script li obbliga a reinizializzare l'ambiente utente e quindi a scaricare la chiave del tenant aggiornata e i modelli importati.

### <a name="BKMK_Step4Migration"></a>Passaggio 4. Configurare i modelli importati
Poiché i modelli importati hanno uno stato predefinito **Archiviato**, è necessario impostare questo stato su **Pubblicato** se si vuole consentire agli utenti di usarli con Azure RMS.

Inoltre, se i modelli in AD RMS usavano il gruppo **ANYONE**, questo gruppo viene rimosso automaticamente quando si importano i modelli in Azure RMS. È necessario aggiungere manualmente il gruppo o gli utenti equivalenti e gli stessi diritti ai modelli importati. Il gruppo equivalente per Azure RMS è denominato **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com**. Ad esempio, questo gruppo potrebbe essere simile al seguente per Contoso: **AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**.

Se non si è certi che i modelli AD RMS includano il gruppo ANYONE, espandere la sezione [PowerShell script to identify AD RMS templates that include the ANYONE group](#BKMK_ScriptForANYONE) in questo passaggio per copiare e usare lo script di PowerShell di esempio per identificare questi modelli. Per altre informazioni sull'uso di Windows PowerShell con AD RMS, vedere l'articolo relativo all'[uso di Windows PowerShell per amministrare AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

È possibile vedere il gruppo creato automaticamente dell'organizzazione copiando uno dei modelli di criteri per i diritti predefiniti nel portale di Azure classico e quindi identificando il **NOME UTENTE** nella pagina **DIRITTI**. Non è tuttavia possibile usare il portale di Azure classico per aggiungere questo gruppo a un modello creato manualmente o importato. È invece necessario usare una delle opzioni di Azure RMS PowerShell seguenti:

-   Usare il cmdlet di PowerShell [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) per definire il gruppo "AllStaff" e i diritti come un oggetto di definizione dei diritti ed eseguire di nuovo questo comando per ognuno degli altri gruppi o utenti a cui sono già stati concessi diritti nel modello originale, in aggiunta al gruppo ANYONE. Aggiungere quindi tutti questi oggetti di definizione dei diritti ai modelli con il cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx).

-   Usare il cmdlet [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) per esportare il modello in un file con estensione XML che è possibile modificare per aggiungere il gruppo "AllStaff" e i diritti ai gruppi e ai diritti esistenti. Usare quindi il cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) per importare di nuovo le modifiche in Azure RMS.

> [!NOTE]
> Questo gruppo equivalente "AllStaff" non corrisponde esattamente al gruppo ANYONE in RMS:  Il gruppo "AllStaff" include tutti gli utenti nel tenant di Azure, mentre il gruppo ANYONE comprende tutti gli utenti autenticati, che potrebbero essere esterni all'organizzazione.
> 
> A causa di questa differenza tra i due gruppi, potrebbe essere necessario aggiungere anche gli utenti esterni in aggiunta al gruppo "AllStaff". Gli indirizzi email esterni per i gruppi attualmente non sono supportati.

I modelli importati da AD RMS hanno lo stesso aspetto e comportamento dei modelli personalizzati che è possibile creare nel portale di Azure classico. Per modificare i modelli importati pubblicandoli in modo che gli utenti possano visualizzarli e selezionarli dalle applicazioni o per apportarvi altre modifiche, vedere [Configurazione di modelli personalizzati per Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

> [!TIP]
> Per un'esperienza più coerente per gli utenti durante il processo di migrazione, non apportare modifiche ai modelli importati oltre a queste due. Non pubblicare i due modelli predefiniti forniti con Azure RMS, né creare nuovi modelli in questa fase. Attendere invece il completamento del processo di migrazione e la rimozione delle autorizzazioni dei server AD RMS.

#### <a name="BKMK_ScriptForANYONE"></a>Esempio di script di Windows PowerShell per identificare modelli AD RMS che includono il gruppo ANYONE
Questa sezione include lo script di esempio per facilitare l'identificazione dei modelli AD RMS per i quali è definito un gruppo ANYONE, come descritto nella sezione precedente.

*&#42;&#42;Dichiarazione di non responsabilità&#42;&#42;: Questo script di esempio non è supportato in alcun programma o servizio di supporto standard Microsoft. Questo script di esempio viene fornito "nello stato in stato in cui si trova" senza garanzia di alcun tipo.*

```
import-module adrmsadmin New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force $ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate foreach($Template in $ListofTemplates) { $templateID=$Template.id $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright $templateName=$Template.DefaultDisplayName if ($rights.usergroupname -eq "anyone") { $templateName = $Template.defaultdisplayname write-host "Template " -NoNewline write-host -NoNewline $templateName -ForegroundColor Red write-host " contains rights for " -NoNewline write-host ANYONE  -ForegroundColor Red } } Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>Passaggio 5. Riconfigurare i client per l'uso di Azure RMS
Per i client Windows:

1.  [Scaricare gli script di migrazione](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Questi script reimpostano la configurazione nei computer Windows in modo che usino il servizio Azure RMS anziché AD RMS.

2.  Seguire le istruzioni nello script di reindirizzamento (Redirect_OnPrem.cmd) per modificare lo script in modo che faccia riferimento al nuovo tenant di Azure RMS.

3.  Nei computer Windows eseguire questi script con privilegi elevati nel contesto dell'utente.

Per i client di dispositivi mobili e i computer Mac:

-   Rimuovere i record SRV in DNS creati al momento della distribuzione dell'[estensione per dispositivo mobile di AD RMS](http://technet.microsoft.com/library/dn673574.aspx).

#### Modifiche apportate dagli script di migrazione
Questa sezione illustra le modifiche apportate dagli script di migrazione. È possibile usare queste informazioni solo a scopo di riferimento o per la risoluzione dei problemi oppure se si preferisce apportare queste modifiche manualmente.

CleanUpRMS_RUN_Elevated.cmd:

-   Eliminare il contenuto delle cartelle %userprofile%\AppData\Local\Microsoft\DRM e %userprofile%\AppData\Local\Microsoft\MSIPC, incluse eventuali sottocartelle e i file con nomi di file lunghi.

-   Eliminare il contenuto delle chiavi del Registro di sistema seguenti:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Eliminare i valori del Registro di sistema seguenti:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Creare i valori del Registro di sistema seguenti per ogni URL fornito come parametro in ognuno dei percorsi seguenti:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Ogni voce include un valore **https://OldRMSserverURL/_wmcs/licensing**con i dati nel formato seguente: **https://&lt;YourTenantURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt;URLdelTenant&gt;* ha il formato seguente: **{GUID}.rms.[Region].aadrm.com**.
    > 
    > Ad esempio:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > È possibile individuare questo valore identificando il valore **RightsManagementServiceId** quando si esegue il cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) per Azure RMS.

### <a name="BKMK_Step6Migration"></a>Passaggio 6. Configurare l'iterazione IRM per Exchange Online
Se in precedenza si è importato il dominio di pubblicazione trusted da AD RMS a Exchange Online, è necessario rimuovere questo dominio per evitare conflitti di modelli e criteri dopo la migrazione in Azure RMS. A tale scopo, usare il cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) da Exchange Online.

Se si è scelta una topologia di chiave del tenant di Azure RMS **gestita da Microsoft**:

-   Vedere la sezione [Exchange Online: configurazione di IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline) nell'argomento [Configurazione di applicazioni per Rights Management di Windows Azure](../Topic/Configuring_Applications_for_Azure_Rights_Management.md). Questa sezione include i normali comandi da eseguire per connettersi al servizio Exchange Online, importa la chiave del tenant da Azure RMS e abilita la funzionalità di IRM per Exchange Online. Dopo aver completato questi passaggi, si avrà la funzionalità RMS completa con Exchange Online.

Se si è scelta una topologia di chiave del tenant di Azure RMS **gestita dal cliente (BYOK)**:

-   La funzionalità di RMS con Exchange Online risulterà ridotta, come descritto nella sezione [Prezzi e restrizioni della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

### <a name="BKMK_Step7Migration"></a>Passaggio 7. Distribuire il connettore RMS
Se è stata usata la funzionalità Information Rights Management (IRM) di Exchange Server o di SharePoint Server con AD RMS, è innanzitutto necessario disabilitare IRM su questi server e rimuovere la configurazione di AD RMS. Distribuire quindi il connettore Rights Management (RMS), che funziona come interfaccia di comunicazione (inoltro) tra i server locali e Azure RMS.

Infine, per questo passaggio, se in Azure RMS sono stati importati più domini di pubblicazione trusted usati per proteggere i messaggi di posta elettronica, è necessario modificare manualmente il Registro di sistema nei computer che eseguono Exchange Server per reindirizzare tutti gli URL dei domini di pubblicazione trusted al connettore RMS.

> [!NOTE]
> Prima di iniziare, verificare le versioni dei server locali supportate dal connettore RMS nel paragrafo relativo ai server locali che supportano Azure RMS nella sezione [Applicazioni che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) dell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

##### Disabilitare IRM nei computer che eseguono Exchange Server e rimuovere la configurazione di AD RMS

1.  In ogni computer che esegue Exchange Server trovare la cartella seguente ed eliminare tutte le voci che contiene: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  In uno dei computer che eseguono Exchange Server usare il cmdlet [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) di Exchange per disabilitare prima di tutto le funzionalità IRM per i messaggi inviati a destinatari interni:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Usare quindi lo stesso cmdlet per disabilitare le funzionalità IRM per i messaggi inviati a destinatari esterni:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Si userà poi lo stesso cmdlet per disabilitare IRM in Microsoft Office Outlook Web App e in Microsoft Exchange ActiveSync:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Infine, usare lo stesso cmdlet per cancellare tutti i certificati memorizzati nella cache:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  A questo punto, in ogni computer che esegue Exchange Server reimpostare IIS, accedendo ad esempio a un prompt dei comandi come amministratore e digitando **iisreset**.

##### Disabilitare IRM nei computer che eseguono SharePoint Server e rimuovere la configurazione di AD RMS

1.  Assicurarsi che non ci siano documenti estratti da librerie protetti da RMS. In tal caso, non saranno più accessibili alla fine di questa procedura.

2.  Nel sito Web di Amministrazione centrale SharePoint, nella sezione **Avvio veloce** fare clic su **Sicurezza**.

3.  Nella pagina **Sicurezza**, nella sezione **Criteri informazioni** fare clic su **Configura Information Rights Management**.

4.  Nella pagina **Information Rights Management**, nella sezione **Information Rights Management** selezionare **Non utilizzare IRM in questo server**, quindi fare clic su **OK**.

5.  In ognuno dei computer che eseguono SharePoint Server eliminare il contenuto della cartella \ProgramData\Microsoft\MSIPC\Server\*&lt;SID dell'account che esegue SharePoint Server&gt;*.

##### Installare e configurare il connettore RMS

-   Usare le istruzioni disponibili nell'argomento [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

##### Solo per Exchange e più domini di pubblicazione trusted: Modificare il Registro di sistema

-   In ogni computer che esegue Exchange Server aggiungere manualmente le chiavi del Registro di sistema seguenti per ogni dominio di pubblicazione trusted aggiuntivo importato, per reindirizzare gli URL dei domini di pubblicazione trusted al connettore RMS. Queste voci del Registro di sistema sono specifiche per la migrazione e non vengono aggiunte dallo strumento di configurazione server per il connettore Microsoft RMS.

    Quando si apportano queste modifiche al Registro di sistema, attenersi alle istruzioni seguenti:

    -   Sostituire *ConnectorFQDN* con il nome definito per il connettore in DNS, ad esempio **rmsconnector.contoso.com**.

    -   Usare il prefisso HTTP o HTTPS per l'URL del connettore, a seconda che sia stato configurato per comunicare con i server locali usando HTTP o HTTPS.

    **Per Exchange 2013:**

    |Percorso del Registro di sistema|Tipo|Valore|Dati|
    |------------------------------------|--------|----------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Intranet Licensing URL&gt;/_wmcs/licensing|Uno dei seguenti, in base all'uso del protocollo HTTP o HTTPS per le comunicazioni dal server di Exchange al connettore RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Extranet Licensing URL&gt;/_wmcs/licensing|Uno dei seguenti, in base all'uso del protocollo HTTP o HTTPS per le comunicazioni dal server di Exchange al connettore RMS:<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/licensing|
    **Per Exchange Server 2010:**

    |Percorso del Registro di sistema|Tipo|Valore|Dati|
    |------------------------------------|--------|----------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Intranet Licensing URL&gt;/_wmcs/licensing|Uno dei seguenti, in base all'uso del protocollo HTTP o HTTPS per le comunicazioni dal server di Exchange al connettore RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS Extranet Licensing URL&gt;/_wmcs/licensing|Uno dei seguenti, in base all'uso del protocollo HTTP o HTTPS per le comunicazioni dal server di Exchange al connettore RMS:<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|

Dopo aver completato queste procedure, è opportuno leggere la sezione **Passaggi successivi** nell'argomento [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_Step8Migration"></a>Passaggio 8. Rimuovere le autorizzazioni di AD RMS
Facoltativa: rimuovere il punto di connessione del servizio da Active Directory per impedire ai computer di individuare l'infrastruttura Rights Management locale. Questo passaggio è facoltativo a causa del reindirizzamento configurato nel Registro di sistema, ad esempio eseguendo lo script di migrazione. Per rimuovere il punto di connessione del servizio, usare lo strumento AD SCP Register da [Rights Management Services Administration Toolkit](http://www.microsoft.com/download/details.aspx?id=1479).

Monitorare l'attività dei server AD RMS, ad esempio controllando le [richieste nel report di integrità del sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx) o la [tabella ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) oppure [controllando l'accesso utente ai contenuti protetti](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Dopo aver verificato che i client RMS non comunicano più con questi server e che usano Azure RMS, è possibile rimuovere il ruolo del server AD RMS da questi server. Se si usano server dedicati, per precauzione è possibile scegliere di arrestare innanzitutto i server per un certo intervallo di tempo per verificare che non vengano segnalati problemi che potrebbero richiederne il riavvio, in modo da garantire la continuità del servizio mentre si esaminano i motivi per cui i client non usano Azure RMS.

Dopo la rimozione delle autorizzazioni dei server AD RMS, è possibile cogliere l'opportunità per esaminare i modelli nel portale di Azure classico e consolidarli in modo che gli utenti ne abbiano meno da scegliere oppure riconfigurarli o eventualmente aggiungerne di nuovi. Potrebbe anche essere il momento opportuno per pubblicare i modelli predefiniti. Per altre informazioni, vedere [Configurazione di modelli personalizzati per Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

### <a name="BKMK_Step9Migration"></a>Passaggio 9. Reimpostare la chiave del tenant di Azure RMS
Questo passaggio è obbligatorio al termine della migrazione se per la distribuzione di AD RMS è stata usata la Modalità crittografia 1 di RMS. La reimpostazione della chiave crea infatti una nuova chiave del tenant che usa la Modalità crittografia 2 di RMS. L'uso di Azure RMS con la Modalità crittografia 1 è supportato solo durante il processo di migrazione.

Questo passaggio è facoltativo ma consigliato al termine della migrazione, anche se è stata usata la Modalità crittografia 2 di RMS, perché consente di proteggere la chiave del tenant di Azure RMS da possibili violazioni della sicurezza della chiave di AD RMS. Quando si reimposta la chiave del tenant di Azure RMS (un'operazione detta anche "rolling della chiave"), viene creata una nuova chiave e la chiave originale viene archiviata. Poiché tuttavia il passaggio da una chiave all'altra non avviene immediatamente, ma nell'arco di alcune settimane, evitare di attendere che si sospetti una violazione della chiave originale, ma reimpostare la chiave del tenant di RMS non appena la migrazione è completata.

Per reimpostare la chiave del tenant di Azure RMS:

-   Se la chiave del tenant di RMS è gestita da Microsoft: Contattare il Servizio Supporto Tecnico Clienti Microsoft e dimostrare di essere l'amministratore del tenant di RMS.

-   Se la chiave del tenant di RMS è gestita dall'utente (BYOK): Ripetere la procedura BYOK per generare e creare una nuova chiave tramite Internet o di persona.

Per altre informazioni sulla gestione della chiave del tenant di RMS, vedere [Operazioni relative alla chiave del tenant di Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

