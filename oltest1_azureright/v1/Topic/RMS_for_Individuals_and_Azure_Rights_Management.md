---
description: na
keywords: na
title: RMS for Individuals and Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
---
# RMS per utenti singoli e Azure Rights Management
RMS per utenti singoli è una sottoscrizione gratuita self-service per gli utenti di un'organizzazione ai quali sono stati inviati file sensibili protetti da Microsoft Azure Rights Management (Azure RMS), ma che non possono essere autenticati perché il loro reparto IT non gestisce per loro un account di Azure. Ad esempio, il reparto IT non dispone di Office 365 o non utilizza i servizi di Azure.

Tali utenti possono iscriversi per ottenere un account aziendale o dell'istituto di istruzione gratuito da usare con Azure RMS e per scaricare e installare l'applicazione di condivisione Rights Management. Di conseguenza, questi utenti possono ora effettuare l’autenticazione per dimostrare di essere la persona a cui sono stati inviati i file protetti e quindi leggerli nel computer o su dispositivi mobili.

Grazie all'uso dell'applicazione di condivisione Rights Management su computer Windows, questi utenti possono inoltre proteggere i file localmente o inviarli tramite posta elettronica a persone all'interno o all'esterno dell'organizzazione. Se i destinatari del messaggio di posta elettronica inviato fanno parte di un'organizzazione che non gestisce gli account utente in Azure, possono iscriversi anch'essi per ottenere un account RMS per singoli utenti che consente di leggere l'allegato di posta elettronica protetto.

> [!IMPORTANT]
> Questa sottoscrizione gratuita assicura che le persone autorizzate possano sempre leggere i file protetti. Attualmente è anche possibile usare questa sottoscrizione gratuita per proteggere i documenti e creare nuovi messaggi di posta elettronica protetti. La capacità di creare nuovo contenuto protetto è però riservata solo all'uso della versione di valutazione e potrebbe essere rimossa in futuro. Per altre informazioni e per le eventuali modifiche relative all'uso di RMS per consentire a utenti singoli di proteggere i documenti, vedere le [Condizioni per l'Utilizzo del Servizio Microsoft Rights Management](https://portal.aadrm.com/Legal/Service).

Per altre informazioni su come proteggere i file tramite l'applicazione di condivisione Microsoft Rights Management gratuita, vedere la [guida dell'utente dell'applicazione di condivisione Microsoft Rights Management](http://technet.microsoft.com/library/dn339006.aspx).

RMS per utenti singoli è un esempio di un abbonamento self-service supportato da Azure Active Directory. Per ulteriori informazioni sul funzionamento, vedere [Che cos’è Self-Service Signup per Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/) nella documentazione di Microsoft Azure. Per ulteriori informazioni specifiche per RMS per utenti singoli, utilizzare le sezioni seguenti:

-   [Modalità di iscrizione per RMS per utenti singoli](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_SignUp)

    -   [Panoramica tecnica](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TechnicalOverview)

-   [Modalità di controllo da parte degli amministratori degli account creati per RMS per utenti singoli](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts)

-   [Come determinare se gli utenti hanno effettuato l'iscrizione per RMS per utenti singoli](#BKMK_Detect)

## <a name="BKMK_SignUp"></a>Modalità di iscrizione per RMS per utenti singoli
Per iscriversi per ottenere l'account gratuito, è necessario visitare la [pagina di Microsoft Rights Management](https://portal.aadrm.com/) e fornire il proprio indirizzo di posta elettronica aziendale. Il modo più comune con cui si verrà indirizzati a questa pagina per l'iscrizione è quando si riceve un messaggio di posta elettronica con un allegato protetto, che contiene istruzioni come per iscriversi. Si riceverà un messaggio di posta elettronica di risposta da Microsoft e sarà quindi possibile completare la procedura di iscrizione inserendo i dettagli per creare l'account. Quando si riceve una conferma tramite posta elettronica da Microsoft, questo messaggio di posta elettronica finale invia a una pagina in cui è possibile scaricare l'applicazione di condivisione per dispositivi diversi e un collegamento alla Guida dell'utente.

#### Per iscriversi per RMS per utenti singoli

1.  Utilizzando un computer Windows o Mac, passare alla [pagina di Microsoft Rights Management](https://portal.aadrm.com).

2.  Digitare l'indirizzo di posta elettronica usato come indirizzo aziendale, ad esempio **janetm@contoso.com** o **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > Gli account di posta elettronica personali non sono supportati, pertanto non immettere un account Microsoft (definito in precedenza account Microsoft Live ID) né un altro account personale privato fornito dal proprio provider Internet.

3.  Fare clic sul pulsante **Introduzione**.

    Microsoft utilizza l'indirizzo di posta elettronica per verificare se l'organizzazione dispone già di una [sottoscrizione pagata che include Azure RMS](https://technet.microsoft.com/library/dn655136.aspx). In tal caso, non è necessario RMS per utenti singoli quindi si verrà connessi immediatamente e l’iscrizione self-service per RMS per utenti singoli verrà annullata. Se non viene trovata una sottoscrizione a pagamento per Azure RMS, si procederà al passaggio successivo.

4.  Attendere un messaggio di posta elettronica di conferma proveniente da Microsoft e inviato all'indirizzo di posta indicato Sarà proveniente da Microsoft (DoNotReply@microsoft.com) e riporterà l'oggetto **Microsoft RMS**.

5.  Quando si riceve il messaggio di posta elettronica, fare clic sul collegamento presente nelle istruzioni per completare il processo di iscrizione.

6.  Il collegamento consente di accedere a una nuova pagina di **Microsoft Rights Management** in cui indicare i dettagli relativi al proprio account. Digitare il nome, il cognome, immettere e confermare una password di propria scelta, selezionare il paese (o il paese più vicino al proprio se non è elencato) nell'elenco a discesa e quindi fare clic su **Crea**.

7.  Attendere un altro messaggio di posta elettronica di Microsoft che conferma che l'account è pronto per essere usato.

8.  Quando si riceve il messaggio, fare clic sul collegamento per accedere e leggere le istruzioni per scaricare e installare l'applicazione di condivisione oppure fare clic sul collegamento relativo alla guida per leggere la guida dell'utente dell'applicazione di condivisione.

Dopo avere creato l'account, è possibile iniziare a proteggere i file e a leggere quelli protetti da altri utenti. Quando viene chiesto di accedere per proteggere i file o leggere quelli protetti, immettere l'indirizzo di posta elettronica e la password usati per creare l'account per RMS per utenti singoli.

### <a name="BKMK_TechnicalOverview"></a>Panoramica tecnica
RMS per utenti singoli usa un processo di iscrizione self-service impiegato anche da altri servizi che usano la tecnologia basata su Microsoft Cloud per autenticare gli utenti.

Questo è ciò che avviene in background quando un utente effettua l'iscrizione a RMS per utenti singoli e la sua organizzazione non dispone di un abbonamento a Office 365 o di una sottoscrizione di Azure e quindi non dispone di una directory in Azure per autenticare gli utenti:

1.  Quando il primo utente di un'organizzazione richiede una sottoscrizione di RMS per utenti singoli, il nome di dominio specificato nell'indirizzo di posta elettronica viene controllato per verificare se è già associato a un tenant Azure. Se non è presente alcun tenant esistente, viene creato automaticamente un nuovo tenant e una directory di Azure per l'organizzazione, che contiene un account per il primo utente. A differenza di una sottoscrizione di Azure a pagamento, questo primo account non è un amministratore globale, ma un utente standard. Il nuovo account usa l'indirizzo di posta elettronica e la password che l'utente ha specificato.

    > [!NOTE]
    > Alcuni nomi di dominio non possono essere usati per creare la directory e quindi neanche per RMS per utenti singoli. L'elenco dei nomi di dominio bloccati può essere visualizzato dal seguente file JavaScript Object Notation: [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json)

    Se viene trovato un tenant esistente, viene controllato per sapere se dispone già di una sottoscrizione per Azure RMS. Quando non viene trovata alcuna sottoscrizione, è possibile aggiungere la sottoscrizione gratuita a RMS per utenti singoli.

2.  L'organizzazione riceve gratuitamente la sottoscrizione di RMS per utenti singoli. Ora, questo utente può essere autenticato da Azure e può proteggere i file e leggere i file protetti da altri utenti tramite Azure Rights Management. Per proteggere i file e leggere i file protetti, l’utente deve disporre di un’applicazione abilitata per RMS, come l'[applicazione di condivisione Microsoft Rights Management gratuita](https://technet.microsoft.com/library/dn919648.aspx).

3.  Quando un secondo utente della stessa organizzazione richiede una sottoscrizione di RMS per utenti singoli, viene aggiunto un nuovo account utente alla directory di Azure creata in precedenza, usando la sottoscrizione di RMS per utenti singoli dell'organizzazione. Questo secondo utente può eseguire tutte le operazioni che può eseguire il primo (proteggere file e leggere file protetti), ma i due utenti possono ora collaborare più facilmente in modo sicuro perché sono in grado di applicare rapidamente modelli predefiniti ai file per limitare l'accesso agli account presenti nella directory di Azure dell'organizzazione.

4.  Gli utenti della stessa organizzazione che successivamente richiedono la sottoscrizione seguono lo stesso schema, ovvero l'aggiunta di account utente (quando nuovi utenti eseguono l'iscrizione) alla directory di Azure dell'organizzazione. Maggiore è il numero di account aggiunto alla directory, maggiore è il numero di utenti che possono collaborare in modo sicuro con colleghi e partner e in grado di impedire con semplicità a persone non autorizzate di leggere i file qualora non dispongano dell'accesso ai file stessi.

Questo processo non prevede costi aggiuntivi per l'organizzazione né attività da parte dei membri del reparto IT, sebbene questi ultimi possano scegliere di effettuare una delle operazioni seguenti:

-   **Gestire gli account e il processo di iscrizione**: gli amministratori IT possono diventare proprietari della directory e degli account creati automaticamente in Azure e quindi gestire gli account implementando le soluzioni di integrazione delle directory, ad esempio la sincronizzazione delle password e l'accesso Single Sign-On. In alternativa, possono impedire agli utenti di creare account o i iscriversi a RMS per utenti singoli.

    Per altre informazioni, vedere la sezione di seguito, [Modalità di controllo da parte degli amministratori degli account creati per RMS per utenti singoli](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts).

-   **Gestire Rights Management**: gli amministratori IT possono convertire la sottoscrizione di RMS per utenti singoli per l'organizzazione in una sottoscrizione a pagamento che include Azure Rights Management. In questo caso, la directory e gli account Azure esistenti vengono mantenuti per consentire una semplice transizione agli utenti esistenti che usavano RMS per utenti singoli. Tutti i file protetti in precedenza dagli utenti rimarranno protetti in base agli stessi criteri e le persone cui era stato concesso di usare i file saranno ancora in grado di usarli nello stesso modo.

    Quando si sceglie questo tipo di comportamento, l'organizzazione è in grado di integrare Rights Management nei propri flussi di lavoro, servizi e archivi dati. In questo scenario è inoltre possibile gestire Rights Management perché si dispone del controllo sulla chiave del tenant dell'organizzazione per Azure Rights Management. A questo punto è possibile eseguire le operazioni seguenti:

    -   Configurare Exchange e SharePoint per supportare Azure Rights Management, anche se le due applicazioni sono eseguite in locale. Exchange e SharePoint sono supportate in modalità nativa per i servizi online e tramite un connettore per i server locali. Per altre informazioni, vedere i seguenti articoli:

        -   Le sezioni Exchange Online e SharePoint Online per [Office 365: configurazione di client e servizi online](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365) nell'argomento [Configurazione di applicazioni per Rights Management di Windows Azure](../Topic/Configuring_Applications_for_Azure_Rights_Management.md)

        -   [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)

    -   Eseguire procedure di e-discovery sui dati di proprietà dell'azienda in modo che sia possibile, se richiesto, di decrittografare i file protetti tramite Rights Management. Per altre informazioni, vedere [Configurazione degli utenti con privilegi avanzati per Rights Management di Azure e servizi di individuazione o ripristino dei dati](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

    -   Registrare tutte le attività correlate all'uso di Rights Management nell'organizzazione. Questa operazione è estremamente utile perché consente non solo di monitorare i file protetti e gli utenti che vi hanno effettuato l'accesso, ma anche di identificare potenziali comportamenti sospetti di utenti non autorizzati che tentano di accedere a tali file. Per altre informazioni, vedere [Registrazione e analisi dell'uso di Rights Management di Windows Azure](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

    -   Fornire agli utenti la possibilità di tenere traccia e revocare i documenti protetti, se queste funzionalità sono supportate dalla [sottoscrizione Azure RMS](https://technet.microsoft.com/dn858608). Per ulteriori informazioni, vedere [Tenere traccia e revocare i file](https://technet.microsoft.com/library/dn986611.aspx) dalla [Guida dell'utente dell'applicazione di RMS sharing](https://technet.microsoft.com/library/dn339006.aspx).

    -   Implementare una soluzione BYOK in modo da generare la chiave del tenant per Azure Rights Management in locale in base ai propri criteri IT e di trasferirla in modo sicuro a Microsoft tramite un modulo di protezione hardware. Per altre informazioni, vedere [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

## <a name="BKMK_TakeControlofAccounts"></a>Modalità di controllo da parte degli amministratori degli account creati per RMS per utenti singoli
Se non si desidera convertire la sottoscrizione di RMS per utenti singoli dell'organizzazione in una sottoscrizione a pagamento, è comunque possibile controllare gli account utente nella directory di Azure creata per l'organizzazione nei modi seguenti:

-   Implementare soluzioni di integrazione delle directory per Azure Active Directory e per l'infrastruttura Servizi di dominio Active Directory. È possibile sincronizzare account e password in modo che gli utenti non debbano creare nuovi account per usare Rights Management e che i criteri associati alle password locali vengano applicati ai nuovi account utente di Azure. È inoltre possibile sincronizzare le password in modo che gli utenti non debbano ricordare una password diversa per usare Rights Management.

-   È possibile impedire agli utenti di eseguire l'iscrizione per usare Azure Rights Management con la sottoscrizione RMS per utenti singoli. Nella maggior parte dei casi, questa azione non è molto vantaggiosa perché gli utenti condivideranno file senza protezione (con potenziali rischi per la società) o useranno un altro meccanismo di protezione dei file, impedendo al personale del reparto IT di accedere ai dati. Se però si vuole impedire agli utenti di usare RMS per utenti singoli, effettuare una delle operazioni seguenti dopo aver acquisito la proprietà della directory dell'organizzazione in Azure:

    -   Impedire a tutti gli utenti di iscriversi alle sottoscrizioni self-service, incluso RMS per utenti singoli.  Attualmente, non è possibile impostare questo dal servizio; l'impostazione si applica a tutte le sottoscrizioni di Azure che utilizzano il processo self-service. A questo scopo, impostare il parametro **AllowAdHocSubscriptions** su false con il cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) del modulo Windows PowerShell per Azure Active Directory. ad esempio **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Impedire agli utenti di creare un nuovo account in Azure. In questo modo, solo gli utenti che dispongono già di un account in Azure potranno iscriversi alle sottoscrizioni self-service, incluso RMS per utenti singoli.  A questo scopo, impostare il parametro **AllowEmailVerifiedUsers** su false con il cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) del modulo Windows PowerShell per Azure Active Directory. ad esempio **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Sincronizzare 'infrastruttura Servizi di dominio Active Directory con Azure Active Directory. In questo modo si impedisce la creazione di nuovi account quando gli utenti si iscrivono a sottoscrizioni self-service come RMS per utenti singoli ed è possibile eliminare o disabilitare account creati in precedenza nella directory di Azure.

Per controllare gli account utente nella directory di Azure o impedire agli utenti di iscriversi a RMS per utenti singoli, è necessario disporre di una sottoscrizione di Azure ed essere proprietari della directory di Azure. Se non si dispone ancora di una sottoscrizione di Azure, è possibile ottenerne una senza alcun costo aggiuntivo. Se durante il processo self-service è stata creata automaticamente una directory, acquisire la proprietà del dominio usato per crearla. Se si dispone già di una directory in Azure, ma gli utenti hanno specificato un nuovo dominio in uso nell'organizzazione, unire il dominio alla directory esistente. Per ulteriori informazioni, vedere le istruzioni in [Cos’è Self-Service Signup per Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)

## <a name="BKMK_Detect"></a>Come determinare se gli utenti hanno effettuato l'iscrizione per RMS per utenti singoli
Per sapere se un utente si è iscritto per ottenere RMS per utenti singoli, un amministratore può usare uno o più tra i metodi seguenti:

-   Chiedere agli utenti in che modo proteggono i file riservati, in particolar modo quando collaborano con altre persone all'esterno dell'organizzazione.

-   Quando è disponibile una sottoscrizione di Azure per l'organizzazione, usare il cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) per verificare se **RIGHTSMANAGEMENT_ADHOC** viene restituito come una delle sottoscrizioni. Se restituito, si tratta di RMS per le singole sottoscrizioni concesse all'organizzazione, con un pool di unità attive disponibili per permettere agli utenti di usare il processo di iscrizione self-service.

-   Usare una soluzione di gestione di sistema, ad esempio System Center Configuration Manager, per tenere traccia del software installato e di quello in uso. L'applicazione di condivisione Microsoft Rights Management viene eseguita tramite il programma **ipviewer.exe** ed è possibile [scaricare e installare l'applicazione](http://go.microsoft.com/fwlink/?LinkId=303970) gratuitamente per identificare altre caratteristiche dell'applicazione che è possibile usare a scopo di inventario del software.

-   Prestare attenzione alle estensioni dei nomi di file creati nell'applicazione di condivisione Microsoft Rights Management. Le estensioni di file .pfile e .ppdf sono gli esempi più evidenti, ma esistono altri file la cui estensione viene modificata quando sono protetti in modalità nativa con Rights Management. Per altre informazioni, vedere la sezione [Tipi ed estensioni di file supportati](http://technet.microsoft.com/library/dn339003.aspx) nella [Guida dell'amministratore dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

## Vedere anche
[Introduzione a Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

