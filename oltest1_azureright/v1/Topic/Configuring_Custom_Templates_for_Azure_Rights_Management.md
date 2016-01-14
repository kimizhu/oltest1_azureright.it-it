---
description: na
keywords: na
title: Configuring Custom Templates for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
---
# Configurazione di modelli personalizzati per Azure Rights Management
Dopo l'attivazione di Azure Rights Management (Azure RMS), gli utenti sono automaticamente in grado di usare due modelli predefiniti che facilitano l'applicazione di criteri ai file riservati allo scopo di limitare l'accesso alle sole persone autorizzate all'interno dell'organizzazione. Questi due modelli prevedono le seguenti restrizioni relativamente ai criteri per i diritti d'uso:

-   Visualizzazione di sola lettura per il contenuto protetto

    -   Nome visualizzato: **&lt;nome organizzazione&gt; - Solo visione riservata**

    -   Autorizzazione specifica: Visualizza contenuto

-   Autorizzazioni di lettura o modifica per il contenuto protetto

    -   Nome visualizzato: **&lt;nome organizzazione&gt; - Riservato**

    -   Autorizzazioni specifiche: Visualizza contenuto, Salva file, Modifica contenuto, Visualizza diritti assegnati, Consenti macro, Inoltra, Rispondi, Rispondi a tutti

Inoltre, l’[applicazione di condivisione RMS](http://technet.microsoft.com/library/dn339006.aspx) consente agli utenti di definire un proprio set di autorizzazioni. Per il client di Outlook e Outlook Web Access, gli utenti possono anche selezionare l'opzione **Non inoltrare** per i messaggi di posta elettronica.

Per molte organizzazioni, i modelli predefiniti potrebbero essere sufficienti. È tuttavia possibile creare modelli personalizzati di criteri per i diritti d'uso, se lo si desidera. È possibile decidere di creare un modello personalizzato per diversi motivi, tra cui i seguenti:

-   Si desidera disporre di un modello per concedere diritti a un sottoinsieme di utenti anziché a tutti gli utenti dell'organizzazione.

-   Si desidera che solo un subset di utenti sia in grado di visualizzare e selezionare un modello (modello di reparto) dalle applicazioni, anziché tutti gli utenti dell'organizzazione.

-   Si desidera definire un diritto personalizzato per un modello, ad esempio la visualizzazione e la modifica, ma non la copia e la stampa.

-   Si desidera configurare in un modello opzioni aggiuntive quali una data di scadenza e la possibilità di accedere al contenuto senza una connessione Internet.

Per consentire agli utenti di selezionare un modello personalizzato contenente impostazioni come queste, è necessario prima crearlo, configurarlo e quindi pubblicarlo.

Per configurare e usare più agevolmente i modelli personalizzati, fare riferimento alle seguenti sezioni:

-   [Come creare, configurare e pubblicare un modello personalizzato](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToConfigureCustomTemplates)

-   [Come copiare un modello](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)

-   [Come rimuovere (archiviare) modelli](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToArchiveTemplates)

-   [Aggiornamento dei modelli per gli utenti](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)

-   [Riferimenti Windows PowerShell](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_PowerShellTemplates)

## <a name="BKMK_HowToConfigureCustomTemplates"></a>Come creare, configurare e pubblicare un modello personalizzato
Il portale di Azure classico consente di creare e gestire modelli personalizzati. È possibile eseguire questa operazione direttamente nel portale di Azure classico oppure accedendo all'interfaccia di amministrazione di Office 365 e scegliendo le **funzionalità avanzate** di Rights Management, che a loro volta reindirizzano al portale di Azure classico.

Per creare, configurare e pubblicare modelli personalizzati per Rights Management, seguire queste procedure.

#### Per creare un modello personalizzato

1.  Seguire una di queste due procedure in base al tipo accesso scelto, dall'interfaccia di amministrazione di Office 365 o dal portale di Azure classico:

    -   Dall’[interfaccia di amministrazione di Office 365](https://portal.office.com/):

        1.  Nel riquadro a sinistra, fare clic su **impostazioni servizio**.

        2.  Nella pagina **impostazioni servizio** fare clic su **rights management**.

        3.  Nella sezione **Proteggere le informazioni** fare clic su **Gestione**.

        4.  Nella sezione **rights management** fare clic su **funzionalità avanzate**.

            > [!NOTE]
            > Se Rights Management non è stato attivato, fare prima clic su **attiva** e confermare l'azione. Per altre informazioni, vedere [Attivazione di Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).
            > 
            > Se l'opzione **funzionalità avanzate** non è mai stata selezionata prima, dopo aver attivato Rights Management seguire le istruzioni visualizzate per ottenere una sottoscrizione di Azure gratuita necessaria per accedere al portale di Azure classico.

            Facendo clic su **funzionalità avanzate** viene caricato il portale di Azure classico, in cui è possibile gestire il servizio **RIGHTS MANAGEMENT** relativo ad Azure Active Directory dell'organizzazione.

    -   Dal [portale di Azure classico](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  Nel riquadro sinistro fare clic su **ACTIVE DIRECTORY**.

        2.  Nella pagina **active directory** fare clic su **RIGHTS MANAGEMENT**.

        3.  Selezionare la directory da gestire per Rights Management.

        4.  Se Rights Management non è stato ancora attivato, fare clic su **ATTIVA** e confermare l'azione.

            > [!NOTE]
            > Per altre informazioni, vedere [Attivazione di Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

2.  Creare un nuovo modello:

    -   Nella pagina di avvio rapido **Introduzione a Rights Management** del portale di Azure classico fare clic su **Creare un nuovo modello di criteri di diritti**.

        Se questa pagina non viene visualizzata immediatamente dopo aver seguito le istruzioni per Office 365, è possibile usare le istruzioni di navigazione precedenti relative al portale di Azure classico.

3.  Nella pagina **Aggiungi un nuovo modello di criteri di diritti** selezionare la lingua in cui si intende specificare il nome e la descrizione del modello che saranno visibili agli utenti (più avanti si potranno aggiungere altre lingue). Digitare quindi un nome univoco e una descrizione e fare clic sul pulsante Completa.

Nella pagina di avvio rapido **Introduzione a Rights Management** fare clic su **Gestire i modelli di criteri di diritti**. Il modello appena creato sarà visualizzato nell'elenco dei modelli con lo stato **Archiviato**. A questo punto il modello è stato creato, ma non è configurato e non è visibile agli utenti.

#### Per configurare e pubblicare un modello personalizzato

1.  Selezionare il modello appena creato nella pagina **MODELLI** del portale di Azure classico.

2.  Nella pagina di avvio rapido **Il modello è stato aggiunto** fare clic su **Introduzione** nel passaggio 1, **Configurare diritti di utenti e gruppi**, quindi fare clic su **PER INIZIARE** o **AGGIUNGI** e infine selezionare gli utenti e i gruppi che avranno i diritti per usare il contenuto protetto tramite il nuovo modello.

    > [!NOTE]
    > Gli utenti o i gruppi selezionati devono disporre di un indirizzo di posta elettronica. Questa condizione si verifica quasi sempre in un ambiente di produzione, ma in un ambiente di test semplice può essere necessario aggiungere gli indirizzi di posta elettronica agli account utente o ai gruppi.

    Come procedura consigliata, usare gruppi anziché utenti singoli perché la gestione dei modelli risulterà più agevole. Se si dispone di Active Directory locale e si esegue la sincronizzazione in Azure AD, è possibile utilizzare i gruppi abilitati alla posta che sono gruppi di protezione o gruppi di distribuzione. Se tuttavia si desidera concedere diritti a tutti gli utenti dell'organizzazione, la procedura più efficiente consiste nel copiare uno dei modelli predefiniti piuttosto che specificare più gruppi. Per altre informazioni, vedere la sezione [Come copiare un modello](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates) di questo argomento.

    > [!TIP]
    > È quindi possibile aggiungere al modello utenti esterni all'organizzazione usando il [modulo Windows PowerShell per Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx) e usando uno dei metodi seguenti:
    > 
    > -   **Usare un oggetto di definizione dei diritti per aggiornare un modello**:    specificare gli indirizzi di posta elettronica esterni e i relativi diritti in un oggetto di definizione dei diritti, che verrà quindi usato per aggiornare il modello. È possibile specificare l'oggetto di definizione dei diritti usando il cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) per creare una variabile e quindi fornire questa variabile al parametro -RightsDefinition con il cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) per modificare un modello esistente. Tuttavia, se si stanno aggiungendo questi utenti a un modello esistente, sarà necessario definire anche gli oggetti di definizione dei diritti per i gruppi esistenti nei modelli e non solo i nuovi utenti esterni.
    > -   **Esportare, modificare e importare il modello aggiornato**: usare il cmdlet [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) per esportare il modello in un file che sia possibile modificare in modo da aggiungere gli indirizzi di posta elettronica esterni degli utenti e i relativi diritti rispetto a gruppi e diritti esistenti. Usare quindi il cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) per importare di nuovo le modifiche in Azure RMS.

3.  Fare clic sul pulsante Avanti, quindi assegnare agli utenti e ai gruppi selezionati uno dei diritti elencati.

    Per altre informazioni su ogni diritto (e per i diritti personalizzati), usare la descrizione visualizzata. Informazioni più dettagliate sono inoltre disponibili anche in [Configurazione dei diritti di utilizzo per Azure Rights Management](../Topic/Configuring_Usage_Rights_for_Azure_Rights_Management.md). Tuttavia, le applicazioni che supportano RMS possono implementare questi diritti in modo diverso. Consultare la relativa documentazione ed eseguire test personalizzati con le applicazioni usate dagli utenti per controllare il comportamento prima di distribuire il modello per gli utenti. Per fare in modo che il modello sia visibile solo agli amministratori per eseguirne il test, rendere questo modello un modello di reparto (passaggio 6).

4.  Se si seleziona **Personalizzato**, fare clic sul pulsante Avanti e quindi selezionare i diritti personalizzati.

    Benché sia possibile usare qualsiasi combinazione dei singoli diritti disponibili, in alcune applicazioni determinati diritti possono dipendere da altri diritti. In questo caso, i diritti dipendenti vengono selezionati automaticamente.

    > [!TIP]
    > Valutare l'opportunità di aggiungere il diritto **Copia ed estrai contenuto** e concedere questo diritto al personale o agli amministratori selezionati in altri ruoli responsabili del recupero di informazioni. Gli utenti con questo diritto possono rimuovere, se necessario, la protezione da file e messaggi di posta elettronica che verranno protetti mediante questo modello. La possibilità di rimuovere la protezione a livello del modello consente un controllo più accurato rispetto all'uso della funzionalità dell'utente con privilegi avanzati.

5.  Fare clic sul pulsante Completa.

6.  Se si vuole che il modello sia visibile solo a un subset di utenti quando viene visualizzato un elenco di modelli nelle applicazioni, fare clic su **AMBITO** per configurare questo modello come modello di reparto e fare clic su **PER INIZIARE**. In caso contrario, andare al passaggio 9.

    Altre informazioni sui modelli di reparto: per impostazione predefinita, tutti gli utenti nella directory di Azure visualizzano tutti i modelli pubblicati e possono quindi selezionarli dalle applicazioni quando vogliono proteggere il contenuto. Se si vuole consentire solo ad alcuni utenti specifici di visualizzare alcuni dei modelli pubblicati, è necessario definire l'ambito dei modelli per tali utenti. Quindi, solo tali utenti potranno selezionare questi modelli. Gli altri utenti che non sono stati specificati non potranno visualizzare i modelli e pertanto non potranno selezionarli. Questa tecnica semplifica la scelta del modello corretto da parte degli utenti, soprattutto quando si creano modelli che sono progettati per essere usati da gruppi o reparti specifici. Gli utenti visualizzeranno solo i modelli che sono stati progettati per loro.

    Ad esempio, si è creato un modello per il reparto Risorse umane che applica l'autorizzazione di sola lettura ai membri del reparto Finanze. Affinché solo i membri del reparto Risorse umane possano applicare questo modello quando usano l'applicazione di condivisione Rights Management, assegnare l'ambito del modello al gruppo abilitato alla posta elettronica denominato HumanResources. Quindi, solo i membri di questo gruppo potranno visualizzare e applicare questo modello.

7.  Nella pagina **VISIBILITÀ DEL MODELLO** selezionare gli utenti e i gruppi che potranno vedere e selezionare il modello nelle applicazioni che supportano RMS. Come indicato in precedenza, è consigliabile usare i gruppi anziché gli utenti e i gruppi o gli utenti selezionati dovranno avere un indirizzo di posta elettronica.

8.  Fare clic sul pulsante Avanti e stabilire se è necessario configurare la compatibilità delle applicazioni per il modello di reparto. Per configurarla, fare clic su **COMPATIBILITÀ DELL'APPLICAZIONE**, selezionare la casella di controllo e scegliere **Completa**.

    Per quale motivo potrebbe essere necessario configurare la compatibilità delle applicazioni? Non tutte le applicazioni possono supportare i modelli di reparto. A tale scopo, per poter scaricare i modelli, è necessario eseguire prima l'autenticazione dell'applicazione con il servizio RMS. Se il processo di autenticazione non viene eseguito, per impostazione predefinita non viene scaricato alcun modello di reparto. È possibile eseguire l'override di questo comportamento specificando che tutti i modelli di reparto devono essere scaricati, configurando la compatibilità dell’applicazione e selezionando la casella di controllo **Mostra questo modello a tutti gli utenti quando le applicazioni non supportano l'identità utente**.

    Ad esempio, se non si configura la compatibilità delle applicazioni per il modello di reparto nell'esempio delle Risorse umane, solo gli utenti del reparto Risorse umane visualizzeranno il modello di reparto quando useranno l'applicazione RMS sharing, ma nessun utente visualizzerà il modello di reparto quando userà Outlook Web Access (OWA) da Exchange Server 2013 poiché OWA di Exchange ed Exchange ActiveSync non supportano i modelli di reparto. Se si esegue l'override di questo comportamento predefinito configurando la compatibilità delle applicazioni, solo gli utenti del reparto Risorse umane visualizzeranno il modello di reparto quando useranno l'applicazione RMS sharing, ma tutti gli utenti visualizzeranno il modello di reparto quando useranno Outlook Web Access (OWA). Se gli utenti usano OWA o Exchange ActiveSync da Exchange Online, i modelli di reparto saranno visibili a tutti gli utenti o a nessun utente, a seconda dello stato del modello (archivio o pubblicato) in Exchange Online.

    Office 2016 supporta in modo nativo i modelli di reparto, così come fa anche Office 2013 con gli ultimi aggiornamenti di Office ([KB 3054853](https://support.microsoft.com/kb/3054853)).

    > [!NOTE]
    > Se si dispone di applicazioni che ancora non supportano in modo nativo i modelli di reparto, è possibile usare uno script personalizzato per il download dei modelli RMS o altri strumenti per distribuire questi modelli nella cartella locale del client RMS. In queste applicazioni quindi i modelli di reparto potranno essere visualizzati correttamente solo dagli utenti e i gruppi selezionati per l'ambito del modello:
    > 
    > -   Per Office 2010, la cartella client è **%localappdata%\Microsoft\DRM\Templates**.
    > -   Da un computer client in cui sono stati scaricati tutti i modelli, è possibile copiare e incollare i file modello in altri computer.
    > 
    > È possibile [scaricare lo script personalizzato dei modelli RMS dal sito Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=524506). Se viene visualizzato un errore quando si fa clic su questo collegamento, probabilmente non è ancora stata eseguita la registrazione in Microsoft Connect.   Per eseguire la registrazione:
    > 
    > 1.  Andare al [sito Microsoft Connect](http://www.connect.microsoft.com) e accedere con il proprio account Microsoft.
    > 2.  Fare clic su **Directory** e selezionare la categoria **Visualizza prodotti Connect che attualmente non accettano commenti**.
    > 3.  Eseguire la ricerca di **Rights Management Services** e, in corrispondenza del programma **Microsoft RMS Enterprise Features**, fare clic su **Aggiungi**.

9. Fare clic su **CONFIGURA** e aggiungere le altre lingue usate dagli utenti, nonché il nome e la descrizione del modello in tali lingue. Quando sono presenti utenti multilingue, è importante aggiungere ogni lingua usata e specificare un nome e una descrizione in tale lingua. In tal modo, gli utenti vedranno il nome e la descrizione del modello nella stessa lingua del sistema operativo client di cui dispongono e questo garantisce la piena comprensione dei criteri applicati a un documento o a un messaggio di posta elettronica. In caso di mancata corrispondenza con il sistema operativo client, il nome e la descrizione verranno visualizzati nella lingua definita al momento della creazione del modello.

    Verificare quindi se si desideri apportare modifiche alle impostazioni riportate di seguito.

    |Impostazione|Altre informazioni|
    |----------------|----------------------|
    |**scadenza contenuto**|Definire una data o un numero di giorni in cui i file protetti tramite il modello non devono essere aperti. È possibile specificare una data o un numero di giorni a partire dal momento in cui la protezione viene applicata al file.<br /><br />Quando si specifica una data, diventa effettiva alla mezzanotte del fuso orario corrente.|
    |**accesso offline**|Usare questa impostazione per far fronte agli eventuali requisiti di sicurezza previsti e, allo stesso tempo, all'esigenza degli utenti di poter aprire i file protetti quando non dispongono di una connessione Internet.<br /><br />Se si specifica che il contenuto non è disponibile senza una connessione Internet o che è disponibile solo per un determinato numero di giorni, al raggiungimento di tale soglia, gli utenti dovranno eseguire di nuovo l'autenticazione e l'accesso verrà registrato. In questo caso, se le credenziali non sono memorizzate nella cache, verrà chiesto agli utenti di eseguire l'accesso prima di poter aprire il file.<br /><br />Oltre alla riesecuzione dell'autenticazione, verrà nuovamente valutata l'appartenenza degli utenti ai criteri e ai gruppi. Questo significa che gli utenti potrebbero avere risultati di accesso diversi per lo stesso file se dall'ultimo accesso si sono verificati cambiamenti relativi all'appartenenza ai criteri o ai gruppi.|

10. Quando si è convinti che il modello sia configurato in modo appropriato per gli utenti, fare clic su **PUBBLICA** per renderlo visibile agli utenti e quindi su **SALVA**.

11. Fare clic sul pulsante Indietro nel portale classico per tornare alla pagina **MODELLI** in cui lo stato aggiornato del modello è ora impostato su **Pubblicato**.

Per apportare modifiche al modello, selezionarlo e quindi eseguire di nuovo i passaggi di avvio rapido. In alternativa, procedere in uno dei seguenti modi:

-   Per aggiungere altri utenti e gruppi e definirne i diritti, Fare clic su **DIRITTI** e quindi su **AGGIUNGI**.

-   Per rimuovere utenti o gruppi selezionati precedentemente, fare clic su **DIRITTI**, selezionare l'utente o il gruppo dall'elenco e quindi fare clic su **ELIMINA**.

-   Per modificare gli utenti che possono visualizzare i modelli da selezionare dalle applicazioni, fare clic su **AMBITO**, quindi fare clic su **AGGIUNGI** o su **ELIMINA** o su **COMPATIBILITÀ DELL'APPLICAZIONE**.

-   Per nascondere il modello a tutti gli utenti, fare clic su **CONFIGURA**, **ARCHIVIA** e **SALVA**.

-   Per apportare altre modifiche di configurazione, fare clic su **CONFIGURA**, apportare le modifiche e fare clic su **SALVA**.

> [!WARNING]
> Quando si apportano modifiche a un modello salvato in precedenza, le modifiche non saranno visibili ai client finché i modelli non vengono aggiornati nei computer. Per altre informazioni, vedere la sezione [Aggiornamento dei modelli per gli utenti](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates) di questo argomento.

## <a name="BKMK_HowToCopyTemplates"></a>Come copiare un modello
Per creare un nuovo modello con le impostazioni molto simili a quelle di un modello già esistente, selezionare il modello originale nella pagina **MODELLI**, fare clic su **COPIA**, specificare un nome univoco e apportare le modifiche desiderate.

> [!IMPORTANT]
> Quando si copia un modello, viene copiato anche lo stato **Pubblicato** o **Archiviato**. Se pertanto si copia un modello pubblicato, lo stato immediato del nuovo modello sarà Pubblicato, a meno che non si decida di modificarlo.

È possibile copiare sia i modelli personalizzati sia quelli predefiniti. Come procedura consigliata, copiare uno dei modelli predefiniti invece di creare un nuovo modello personalizzato se si desidera che il modello conceda diritti a tutti gli utenti dell'organizzazione. Questo metodo non comporta la necessità di creare o selezionare più gruppi per specificare tutti gli utenti. In questo scenario, tuttavia, assicurarsi di specificare un nuovo nome e una descrizione per il modello copiato per le lingue aggiuntive.

## <a name="BKMK_HowToArchiveTemplates"></a>Come rimuovere (archiviare) modelli
Non è possibile eliminare i modelli predefiniti, ma è possibile archiviarli in modo da renderli invisibili agli utenti.

Analogamente, se un modello personalizzato è stato pubblicato ma non si desidera più renderlo visibile agli utenti, è possibile modificarlo e scegliere **ARCHIVIA** e **SALVA** nella pagina **CONFIGURA**. In alternativa, è possibile selezionarlo nella pagina **MODELLI** e scegliere **ARCHIVIA**.

Poiché non è possibile modificare i modelli predefiniti, per archiviarli è necessario usare l'opzione **ARCHIVIA** nella pagina **MODELLI**. Non è possibile archiviare l'opzione **Non inoltrare** di Outlook.

#### Per rimuovere un modello predefinito

-   Nella pagina **MODELLI** selezionare il modello predefinito e fare clic su **ARCHIVIA**.

Lo stato passa da **Pubblicato** ad **Archiviato**. Se si cambia idea, selezionare il modello e fare clic su**PUBBLICA**.

## <a name="BKMK_RefreshingTemplates"></a>Aggiornamento dei modelli per gli utenti
Quando si usa Azure RMS, i modelli vengono scaricati automaticamente nei computer client, in modo che gli utenti possano selezionarli dalle rispettive applicazioni. Potrebbe tuttavia essere necessario effettuare alcuni passaggi aggiuntivi se si apportano modifiche ai modelli:

|Applicazione o servizio|Modalità di aggiornamento dei modelli dopo le modifiche|
|---------------------------|-----------------------------------------------------------|
|Exchange Online|È necessaria la configurazione manuale per aggiornare i modelli.<br /><br />Per la procedura di configurazione, espandere la sezione seguente, [Solo Exchange Online: come configurare Exchange per il download dei modelli personalizzati modificati](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_ExchangeOnlineTemplatesUpdate).|
|Office 365|I modelli vengono aggiornati automaticamente e non sono necessari altri passaggi.|
|Office 2016 e Office 2013:<br /><br />Applicazione RMS sharing per Windows|I modelli vengono aggiornati automaticamente in base a una pianificazione:<br /><br />-   Per le versioni più recenti di Office: L'intervallo di aggiornamento predefinito è ogni 7 giorni.<br />-   Per l’applicazione di RMS sharing per Windows: A partire dalla versione 1.0.1784.0, l'intervallo di aggiornamento predefinito è ogni giorno. Le versioni precedenti prevedono un intervallo di aggiornamento predefinito di 7 giorni.<br /><br />Per forzare un aggiornamento prima di questa pianificazione, espandere la sezione seguente, [Office 2016, Office 2013 e applicazione di RMS sharing per Windows: come forzare un aggiornamento per un modello personalizzato modificato](#BKMK_Office2013ForceUpdate).|
|Office 2010|I modelli vengono aggiornati quando gli utenti eseguono l'accesso.<br /><br />Per forzare l'esecuzione di un aggiornamento, chiedere o imporre agli utenti di disconnettersi e rieseguire l'accesso. In alternativa, vedere la sezione seguente, [Solo Office 2010: come forzare un aggiornamento per un modello personalizzato modificato](#BKMK_Office2010ForceUpdate).|
Per i dispositivi mobili che usano l'applicazione di RMS sharing, i modelli vengono scaricati automaticamente (e aggiornati se necessario) senza che siano richieste attività di configurazione aggiuntive.

### <a name="BKMK_ExchangeOnlineTemplatesUpdate"></a>Solo Exchange Online: come configurare Exchange per il download dei modelli personalizzati modificati
Se Information Rights Management (IRM) è stato già configurato per Exchange Online, i modelli personalizzati non verranno scaricati per gli utenti finché non si apportano le modifiche illustrate di seguito mediante Windows PowerShell in Exchange Online.

> [!NOTE]
> Per altre informazioni su come usare Windows PowerShell in Exchange Online, vedere [Uso di PowerShell con Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

È necessario eseguire questa procedura ogni volta che si modifica un modello.

##### Per aggiornare i modelli per Exchange Online

1.  Utilizzando Windows PowerShell in Exchange Online, connettersi al servizio:

    1.  Fornire il nome utente di Office 365 e la password:

        ```
        $Cred = Get-Credential
        ```

    2.  Connettersi al servizio Exchange Online eseguendo i due comandi seguenti:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Usare il cmdlet [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) per reimportare il dominio di pubblicazione trusted da Azure RMS:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Ad esempio, se il nome del dominio di pubblicazione trusted è **RMS Online - 1** (nome tipico per molte organizzazioni), immettere quanto segue: **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > Per verificare il nome del dominio di pubblicazione trusted, è possibile usare il cmdlet [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx).

3.  Per verificare che i modelli siano stati importati correttamente, attendere alcuni minuti, quindi eseguire il cmdlet [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) e impostare Type su All. Ad esempio:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > È utile conservare una copia dell'output affinché sia possibile copiare facilmente i nomi di modello o GUID se si archivia un modello in un secondo momento.

4.  Per ogni modello importato da rendere disponibile in Outlook Web App è necessario usare il cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) e impostare il Tipo su Distribuito:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Poiché Outlook Web Access memorizza nella cache l'interfaccia utente per 24 ore, gli utenti potrebbero non vedere il nuovo modello per un intervallo di tempo che può raggiungere un giorno.

Inoltre, se si archivia un modello (personalizzato o predefinito) e si usa Exchange Online con Office 365, gli utenti continueranno a vedere i modelli archiviati se si avvalgono di Outlook Web App o di dispositivi mobili che usano il protocollo Exchange ActiveSync.

Per impedire agli utenti di visualizzare questi modelli, connettersi al servizio mediante Windows PowerShell in Exchange Online, quindi usare il cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) eseguendo il seguente comando:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### <a name="BKMK_Office2013ForceUpdate"></a>Office 2016, Office 2013 e applicazione di RMS sharing per Windows: come forzare un aggiornamento per un modello personalizzato modificato
Modificando il Registro di sistema nei computer che eseguono Office 2016, Office 2013 o l’applicazione di condivisione Rights Management (RMS) per Windows, è possibile modificare la pianificazione automatica in modo che i modelli modificati vengano aggiornati nei computer più frequentemente rispetto al relativo valore predefinito. È inoltre possibile forzare un aggiornamento immediato eliminando i dati esistenti in un valore del Registro di sistema.

> [!WARNING]
> L'uso inappropriato dell'editor del Registro di sistema può causare seri problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che sia possibile risolvere i problemi derivanti da un uso non corretto dell'editor del Registro di sistema. L'uso dell'editor del Registro di sistema è di sola responsabilità dell'utente.

##### Per modificare la pianificazione automatica

1.  Utilizzando un editor del Registro di sistema, creare e impostare uno dei seguenti valori del Registro di sistema:

    -   Per impostare una frequenza di aggiornamento in giorni (minimo di 1 giorno):  Creare un nuovo valore del Registro di sistema denominato **TemplateUpdateFrequency** e definire un valore intero per i dati, che specifica la frequenza in giorni per il download di tutte le modifiche a un modello scaricato. Utilizzare la seguente tabella per individuare il percorso del Registro di sistema per creare questo nuovo valore del registro.

        |Percorso del Registro di sistema|Tipo|Valore|
        |------------------------------------|--------|----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequency|

    -   Per impostare una frequenza di aggiornamento in secondi (minimo di 1 secondo):  Creare un nuovo valore del Registro di sistema denominato **TemplateUpdateFrequencyInSeconds** e definire un valore intero per i dati, che specifica la frequenza in secondi per il download di tutte le modifiche a un modello scaricato. Utilizzare la seguente tabella per individuare il percorso del Registro di sistema per creare questo nuovo valore del registro.

        |Percorso del Registro di sistema|Tipo|Valore|
        |------------------------------------|--------|----------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequencyInSeconds|

    Assicurarsi di creare e impostare uno di questi valori del Registro di sistema, non entrambi. Se sono presenti entrambi, **TemplateUpdateFrequency** viene ignorato.

2.  Se si desidera forzare un aggiornamento immediato dei modelli, passare alla procedura successiva. In caso contrario, riavviare ora le applicazioni di Office e le istanze di Esplora file.

##### Per forzare un aggiornamento immediato

1.  Utilizzando un editor del Registro di sistema, eliminare i dati per il valore **LastUpdatedTime**. Ad esempio, i dati possono visualizzare **2015-04-20T15:52**; eliminare 2015-04-20T15:52 in modo che non vengano visualizzati dati. Utilizzare la seguente tabella per individuare il percorso del Registro di sistema per eliminare questo nuovo valore del registro.

    |Percorso del Registro di sistema|Tipo|Valore|
    |------------------------------------|--------|----------|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\&lt;MicrosoftRMS_FQDN&gt;\Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > Nel percorso del Registro di sistema, *&lt;MicrosoftRMS_FQDN&gt;* fa riferimento all’FQDN del servizio Microsoft RMS. Se si desidera verificare questo valore:
    > 
    > 1.  Eseguire il cmdlet [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) per Azure RMS. Se ancora non è stato installato il modulo di Windows PowerShell per Azure RMS, vedere [Installazione di Windows PowerShell per Microsoft Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).
    > 2.  Nell'output identificare il valore **LicensingIntranetDistributionPointUrl**.
    > 
    >     Ad esempio: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Da questo valore rimuovere **https://** e **/_wmcs/licensing** da questa stringa. Il valore rimanente è l’FQDN del servizio Microsoft RMS. Nell'esempio, il valore dell'FQDN di Microsoft RMS è il seguente:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Eliminare la cartella seguente e tutti i file che contiene: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Riavviare le applicazioni di Office e le istanze di Esplora file.

### <a name="BKMK_Office2010ForceUpdate"></a>Solo Office 2010: come forzare un aggiornamento per un modello personalizzato modificato
Modificando il Registro di sistema nei computer che eseguono Office 2010, è possibile impostare un valore in modo che i modelli modificati vengano aggiornati nei computer senza attendere che gli utenti eseguano la disconnessione e si riconnettano. È inoltre possibile forzare un aggiornamento immediato eliminando i dati esistenti in un valore del Registro di sistema.

> [!WARNING]
> L'uso inappropriato dell'editor del Registro di sistema può causare seri problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che sia possibile risolvere i problemi derivanti da un uso non corretto dell'editor del Registro di sistema. L'uso dell'editor del Registro di sistema è di sola responsabilità dell'utente.

##### Per modificare la frequenza di aggiornamento

1.  Utilizzando un editor del Registro di sistema, creare un nuovo valore del registro denominato **UpdateFrequency** e definire un valore intero per i dati, che specifica la frequenza in giorni per il download di tutte le modifiche a un modello scaricato. Utilizzare la seguente tabella per individuare il percorso del Registro di sistema per creare questo nuovo valore del registro.

    |Percorso del Registro di sistema|Tipo|Valore|
    |------------------------------------|--------|----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_DWORD|UpdateFrequency|

2.  Se si desidera forzare un aggiornamento immediato dei modelli, passare alla procedura successiva. In caso contrario, riavviare le applicazioni di Office.

##### Per forzare un aggiornamento immediato

1.  Utilizzando un editor del Registro di sistema, eliminare i dati per il valore **LastUpdatedTime**. Ad esempio, i dati possono visualizzare **2015-04-20T15:52**; eliminare 2015-04-20T15:52 in modo che non vengano visualizzati dati. Utilizzare la seguente tabella per individuare il percorso del Registro di sistema per eliminare questo nuovo valore del registro.

    |Percorso del Registro di sistema|Tipo|Valore|
    |------------------------------------|--------|----------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  Eliminare la cartella seguente e tutti i file che contiene: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Riavviare le applicazioni di Office.

## <a name="BKMK_PowerShellTemplates"></a>Riferimenti Windows PowerShell
Tutte le operazioni che è possibile eseguire nel portale di Azure classico possono essere eseguite anche nella riga di comando tramite Windows PowerShell. È inoltre possibile esportare e importare modelli, affinché sia possibile copiarli tra tenant o eseguire modifiche in blocco di proprietà complesse nei modelli, ad esempio nomi e descrizioni in più lingue.

È anche possibile usare l'esportazione e l'importazione per eseguire il backup e il ripristino dei modelli personalizzati. Come procedura consigliata, eseguire regolarmente il backup dei modelli personalizzati, in modo da poter ripristinare facilmente una versione precedente se si apporta una modifica imprevista.

> [!IMPORTANT]
> Per utilizzare Windows PowerShell per creare e gestire i modelli di criteri dei diritti di Azure RMS, è necessario avere almeno la versione 2.0.0.0 del [modulo Windows PowerShell per Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Se il modulo Windows PowerShell è stato installato in precedenza, eseguire il seguente comando in una finestra di PowerShell per verificare il numero di versione: `(Get-Module aadrm -ListAvailable).Version`

Per le istruzioni di installazione, vedere [Installazione di Windows PowerShell per Microsoft Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

I cmdlet che supportano la creazione e la gestione di modelli sono i seguenti:

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## Passaggi successivi
Dopo aver configurato i modelli personalizzati per Azure Rights Management, usare [Guida di orientamento per la distribuzione di Microsoft Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) per verificare se può essere necessario eseguire operazioni di configurazione aggiuntive prima di distribuire [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] a utenti e amministratori. Se non si prevede di eseguire operazioni di configurazione aggiuntive, usare [Uso di Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) come guida operativa per una corretta distribuzione nell'organizzazione.

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

