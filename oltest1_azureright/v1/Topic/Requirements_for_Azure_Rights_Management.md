---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Requisiti per Azure Rights Management
Per distribuire Microsoft Azure Rights Management (Azure RMS) nell'organizzazione, assicurarsi di disporre dei prerequisiti seguenti. Se si dispone dei prerequisiti richiesti, si può usare la [Guida di orientamento per la distribuzione di Microsoft Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) per distribuire Rights Management nell'organizzazione.

|Requisito|Altre informazioni|
|-------------|----------------------|
|Sottoscrizione cloud per RMS|L'organizzazione deve avere una sottoscrizione cloud che supporti RMS.<br /><br />Per informazioni sulle licenze, vedere la sezione [Sottoscrizioni cloud che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) in questo argomento.|
|Directory di Azure AD|Per supportare l'autenticazione utente per RMS, l'organizzazione deve disporre di una directory di Azure AD. Inoltre, se si desidera usare gli account utente dalla directory locale (AD DS), è necessario anche configurare l'integrazione delle directory.<br /><br />Multi-Factor Authentication (MFA) è supportata con Azure RMS quando si dispone del software client richiesto e l'infrastruttura di supporto MFA è configurata correttamente.<br /><br />Per altre informazioni, vedere la sezione [Directory di Azure AD](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant) di questo argomento.|
|Dispositivi client|Gli utenti devono avere dispositivi client, quali computer o dispositivi mobili, che eseguono un sistema operativo che supporta RMS.<br /><br />Per altre informazioni, vedere la sezione [Dispositivi client che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) di questo argomento.|
|Applicazioni|Le applicazioni eseguite dagli utenti devono supportare RMS.<br /><br />Per altre informazioni, vedere la sezione [Applicazioni che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications) di questo argomento.|
|Infrastruttura in grado di supportare la connettività a Internet e ai servizi cloud dipendenti.|Se si ha un firewall o simili dispositivi di rete intermedi che devono essere configurati per consentire connessioni specifiche, vedere [URL e intervalli di indirizzi IP per Office 356](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />L'elenco degli URL e degli indirizzi IP riportato nella sezione dedicata a **identità e portale di Office 365** è valido per il portale di Office 365, le risorse di Azure Active Directory e Azure Rights Management. Usare le istruzioni in questo articolo per mantenersi aggiornati sulle modifiche apportate a queste informazioni tramite la sottoscrizione a un feed RSS.<br /><br />Oltre alle informazioni nell'articolo di Office, specifiche per Azure RMS:<br /><br />-   Non terminare la connessione TLS dal client al servizio, ad esempio per il controllo a livello di pacchetti. In questo modo viene interrotta l'associazione del certificato usata dai client RMS con le autorità di certificazione gestite da Microsoft per la protezione delle comunicazioni con Azure RMS.<br />-   Non usare una configurazione del proxy Web che esegue l'autenticazione per conto di un utente.|

Se si vuole usare RMS con server locali, sono supportati i prodotti seguenti:

-   Exchange Server

-   SharePoint Server

-   File server di Windows Server che supportano la funzionalità Infrastruttura di classificazione file

Per informazioni sui requisiti aggiuntivi di Azure RMS per questo scenario, vedere la sezione [Server locali che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers) di questo argomento.

> [!IMPORTANT]
> Lo scenario di distribuzione seguente non è supportato:
> 
> -   Esecuzione side-by-side di AD RMS e di Azure RMS nella stessa organizzazione, tranne che durante la migrazione, come illustrato in [Migrazione da AD RMS ad Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).
> 
> È disponibile un percorso di migrazione supportato [da AD RMS a Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx) e [da Azure RMS a AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Se si distribuisce Azure RMS e quindi si decide che non si vuole più usare questo servizio cloud, vedere [Rimozione delle autorizzazioni e disattivazione di Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Le sezioni seguenti forniscono altre informazioni sui requisiti di Azure RMS.

## <a name="BKMK_SupportedSubscriptions"></a>Sottoscrizioni cloud che supportano Azure RMS
Per usare Azure RMS, l'organizzazione deve avere almeno una delle seguenti sottoscrizioni con un numero sufficiente di licenze per utenti e servizi che proteggeranno i file e messaggi di posta elettronica. Se si dispone di un servizio che applicherà la protezione per gli utenti (proprietari dei file o messaggi di posta elettronica), gli utenti richiedono una di queste licenze. Per gli utenti che utilizzano solo (ad esempio, leggere e modificare) questi dati protetti non è necessaria una licenza.

-   Office 365

-   Azure Rights Management Premium (in precedenza Azure RMS Standalone)

-   Enterprise Mobility Suite

-   RMS per utenti singoli

Le sezioni seguenti forniscono altre informazioni e indicazioni sulle opzioni di iscrizione.

Per un confronto tra le licenze di Azure RMS disponibili per le sottoscrizioni a pagamento, vedere la pagina relativa al [confronto tra le offerte per Rights Management Services (RMS)](http://technet.microsoft.com/dn858608).

### Abbonamento a Office 365
[Versione di valutazione gratuita di 30 giorni: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

Questa sottoscrizione è concepita per le organizzazioni che desiderano usare i servizi online di Office e la relativa funzionalità Information Rights Management, che usa Azure RMS. Tuttavia, non tutte le sottoscrizioni Office 365 includono Azure RMS.

|Opzione gestione licenze|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Piano 1<br />SharePoint Piano 2|Exchange Online Piano 1<br />Exchange Online Piano 2|
|----------------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|------------------------------------------|----------------------------------------------------|
|Information Rights Management (IRM)|No|No|No|Sì|Sì|Sì|No|No|No|

### Sottoscrizione ad Azure Rights Management Premium
[Versione di valutazione gratuita di 30 giorni](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

Questa sottoscrizione era precedentemente nota come Azure RMS Standalone ed è concepita per le organizzazioni che vogliono usare Azure RMS ma non dispongono di una sottoscrizione che include Azure RMS. Ad esempio, se si dispone di una sottoscrizione per Office 365 Business Essentials o Office 365 Enterprise E1, queste sottoscrizioni non includono Azure RMS (vedere la tabella nella sezione precedente). L'uso di Azure RMS presuppone l'aggiornamento a una sottoscrizione di Azure Rights Management Premium (oppure l'acquisto di un altra sottoscrizione, ad esempio Office 365 Enterprise E4, che include Azure RMS).

Per altre informazioni, vedere [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management).

Questa sottoscrizione offre inoltre un periodo di valutazione gratuito per provare Azure RMS per 25 utenti. Se la sottoscrizione scade prima che ne venga acquistata una sostitutiva, vedere la seguente sezione "Cosa accade quando la sottoscrizione di valutazione scade?"

|Opzione gestione licenze|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Piano 1<br />SharePoint Piano 2|Exchange Online Piano 1<br />Exchange Online Piano 2|
|----------------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|------------------------------------------|----------------------------------------------------|
|Information Rights Management (IRM)|Sì|Sì <sup>1</sup>|Sì|Sì|Sì|Sì|Sì|Sì|Sì|
<sup>1</sup> Per Business Premium, esistono alcune restrizioni client: È possibile proteggere il contenuto e utilizzare contenuto protetto con RMS mediante Outlook Web App e l'app RMS sharing. È possibile utilizzare contenuto protetto con tutte le altre applicazioni Office, ad esempio Office Online e le applicazioni client per Office 365 Business Premium.

#### <a name="BKMK_TrialExpiryBehavior"></a>Cosa accade quando la sottoscrizione di valutazione scade?
Alla scadenza della sottoscrizione di valutazione, non sarà più possibile accedere al contenuto protetto tramite tale sottoscrizione per Azure RMS. Se a questo punto si acquista una sottoscrizione che supporta Azure RMS, l'accesso viene immediatamente ripristinato.

Tuttavia, se prima di ottenere la sottoscrizione di valutazione l'organizzazione usava Azure RMS con una sottoscrizione a RMS per utenti singoli, l'accesso al contenuto protetto in precedenza non viene perduto anche dopo la scadenza della sottoscrizione di valutazione.

### Sottoscrizione per Enterprise Mobility Suite
[Versione di valutazione gratuita di 30 giorni](http://go.microsoft.com/fwlink/?LinkId=615385)

Questa sottoscrizione è concepita per le organizzazioni che vogliono usare una combinazione di Azure Active Directory Premium, Windows Intune e Rights Management di Azure. Per altre informazioni , vedere la [panoramica su Microsoft Enterprise Mobility](http://go.microsoft.com/fwlink/?LinkId=615386).

|Opzione gestione licenze|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office 365 Enterprise E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint Piano 1<br />SharePoint Piano 2|Exchange Online Piano 1<br />Exchange Online Piano 2|
|----------------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|------------------------------------------|----------------------------------------------------|
|Information Rights Management (IRM)|Sì|Sì <sup>1</sup>|Sì|Sì|Sì|Sì|Sì|Sì|Sì|
<sup>1</sup> Per Business Premium, esistono alcune restrizioni client: È possibile proteggere il contenuto e utilizzare contenuto protetto con RMS mediante Outlook Web App e l'app RMS sharing. È possibile utilizzare contenuto protetto con tutte le altre applicazioni Office, ad esempio Office Online e le applicazioni client per Office 365 Business Premium.

### Sottoscrizione a RMS per utenti singoli
Questa sottoscrizione è concepita per gli utenti singoli di un'organizzazione in cui Azure RMS o AD RMS non è stato distribuito. Questa sottoscrizione consente agli utenti di visualizzare i contenuti protetti da un'organizzazione che usa Azure RMS e di proteggere i propri contenuti.

Per altre informazioni, vedere [RMS per utenti singoli e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## <a name="BKMK_AzureADTenant"></a>Directory di Azure AD
Per usare Azure RMS, è necessario disporre di una directory di Azure AD. L'account aziendale per questa directory consente di accedere al portale di Azure classico, in cui è possibile, ad esempio, configurare e gestire i modelli di Rights Management.

Se non si dispone di una sottoscrizione Azure aziendale, è possibile ottenerne una registrandosi per una versione di valutazione gratuita: Passare alla pagina di [introduzione a Azure](https://account.windowsazure.com/organization) e seguire le istruzioni.

Per altre informazioni, vedere le risorse seguenti contenute nella documentazione di Azure Active Directory:

-   [Che cos'è una directory di Azure AD?](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Associazione delle sottoscrizioni Azure ad Azure AD](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Se si desidera integrare la directory di Azure AD con le foreste di AD locali, vedere [Integrazione di directory](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8).

> [!NOTE]
> Se si hanno dispositivi mobili o computer Mac che eseguono l'autenticazione locale tramite AD FS o un provider di autenticazione equivalente:
> 
> -   È necessario usare AD FS nella versione server minima di **Windows Server 2012 R2** oppure un provider di autenticazione alternativo che supporti il protocollo OAuth 2.0.

### <a name="BKMK_MFA"></a>Multi-Factor Authentication (MFA) e Azure RMS
Per utilizzare Multi-Factor Authentication (MFA) con Azure RMS, è necessario almeno uno dei seguenti elementi:

-   Office 2013 (versione minima):

    -   Se si dispone di Office 2013, è necessario installare anche l’[aggiornamento del 9 giugno 2015 per Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). Per ulteriori informazioni su questo aggiornamento e su come l'autenticazione moderna porta Active Directory Authentication Library in Office 2013, vedere [Anteprima pubblica di autenticazione moderna di Office 2013 annunciata](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) sul blog di Office.

-   Applicazione di condivisione Rights Management per Windows:

    -   È necessario avere installato la versione minima 1.0.1908.0, che può essere confermata tramite Pannello di controllo, Programmi e funzionalità. Per ulteriori informazioni sull’applicazione di condivisione, vedere [Applicazione di condivisione Rights Management per Windows](../Topic/Rights_Management_Sharing_Application_for_Windows.md).

-   App di condivisione Rights Management per dispositivi mobili e computer Mac:

    -   Assicurarsi di avere la versione più recente installata. Il supporto di MFA è entrato nella versione di settembre 2015 dell’app di RMS sharing.

Quindi, configurare la soluzione MFA:

-   Per i tenant gestiti da Microsoft (si dispone di Azure Active Directory o Office 365):

    -   Configurare Azure MFA per forzare l'autenticazione a più fattori per gli utenti. Per istruzioni, vedere [Introduzione a Multi-Factor Authentication di Azure nel cloud](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/) nella documentazione di Azure.

        Per ulteriori informazioni su Azure MFA, vedere [Che cos'è Multi-Factor Authentication di Azure?](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)

-   Per i tenant federativi (si gestiscono i server in locale):

    -   Configurare i server federativi per Azure Active Directory o Office 365. Ad esempio, se si utilizza AD FS, vedere [Configurare ulteriori metodi di autenticazione per AD FS](https://technet.microsoft.com/library/dn758113.aspx) su TechNet.

        Per ulteriori informazioni su questo scenario, vedere [Lavorare con Office 365, programma identità ora semplificato](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) sul blog di Office.

## <a name="BKMK_SupportedDevices"></a>Dispositivi client che supportano Azure RMS
Le sezioni seguenti forniscono indicazioni utili a identificare i dispositivi che supportano Azure Rights Management e le funzionalità di RMS supportate.

-   [Computers](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [Dispositivi mobili](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [Funzionalità del dispositivo client](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>Computers
I sistemi operativi per computer seguenti supportano Azure Rights Management:

-   **Windows 7** (x86, x64)

-   **Windows 8** (x86, x64)

-   **Windows 8.1** (x86, x64)

-   **Windows 10** (x86, x64)

-   **Mac OS X**: la versione minima di Mac OS X è 10.8 (Mountain Lion)

### <a name="BKMK_RMSSupportedMobileDevices"></a>Dispositivi mobili
I sistemi operativi per dispositivi mobili seguenti supportano Rights Management di Azure:

-   **Windows Phone**: Windows Phone 8.1

-   **Telefoni e tablet Android**: la versione minima di Android è 4.0.3

-   **iPhone e iPad**: la versione minima di iOS è 7.0

-   **Tablet Windows RT**: Windows RT 8, Windows RT 8.1

### <a name="BKMK_ClientCapabilities"></a>Funzionalità del dispositivo client
Non tutti i dispositivi client supportano attualmente tutte le funzionalità RMS. Nella tabella seguente vengono indicate le applicazioni che supportano le funzionalità RMS e le eccezioni.

Se non diversamente indicato, le funzionalità supportate sono valide sia per Azure RMS che per AD RMS. Con il supporto AD RMS in iOS, Android, OS X e Windows Phone 8.1 è inoltre richiesta l'[estensione per dispositivi mobili Active Directory Rights Management Services](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341).

Informazioni sulle colonne della tabella:

-   **PDF protetto**: file caratterizzati dall'estensione ppdf e creati automaticamente quando si usa l'applicazione RMS sharing per condividere file di Office e file PDF tramite posta elettronica. L'applicazione RMS sharing include un lettore per i file PDF protetti. Se in precedenza sono stati creati file PDF protetti tramite Azure RMS o AD RMS, per continuare a leggere questi file su dispositivi Windows, iOS e Android, è possibile usare Foxit Reader e Nitro Pro.

-   **Posta elettronica:** i client di posta elettronica elencati possono proteggere il messaggio e-mail stesso, proteggendo quindi automaticamente eventuali file allegati. In questo scenario la funzionalità di anteprima del client può visualizzare il contenuto protetto (messaggio e allegato) ai destinatari autorizzati. Se tuttavia un messaggio di posta elettronica non è protetto ma l'allegato è protetto, la funzionalità di anteprima del client non potrà visualizzare l'allegato protetto ai destinatari autorizzati.

-   **Altri tipi di file**: file di testo e di immagine con estensioni quali txt, xml, jpg e jpeg. L'estensione cambia dopo che i file vengono protetti in modalità nativa da RMS e diventano di sola lettura. I file che non possono essere protetti in modalità nativa, dopo essere stati protetti in modo generico da RMS hanno un'estensione di tipo pfile. Per altre informazioni, vedere le sezioni [Livelli di protezione nativa e generica](https://technet.microsoft.com/library/dn339003.aspx) e [Tipi ed estensioni di file supportati](https://technet.microsoft.com/library/dn339003.aspx) della [Guida dell'amministratore dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx).

|**Sistema operativo dispositivo**|Word, Excel, PowerPoint|PDF protetto|Posta elettronica|Altri tipi di file|
|-------------------------------------|---------------------------|----------------|---------------------|----------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />App per dispositivi mobili Office (solo Azure RMS) <sup>1</sup><br /><br />Office Online <sup>2</sup>|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />App RMS sharing|Outlook 2010<br /><br />Outlook 2013<br /><br />Outlook Web App (OWA)<sup>3</sup><br /><br />Windows Mail<sup>4</sup>|Applicazione di condivisione RMS per Windows: Testo, immagini, pfile<br /><br />Siemens JT2Go: file JT (solo Windows 10)|
|**iOS**|Office per iPad e iPhone<sup>5</sup><br /><br />Office Online <sup>2</sup><br /><br />TITUS Docs|Foxit Reader<br /><br />App RMS sharing<sup>1</sup><br /><br />TITUS Docs|NitroDesk<sup>4</sup><br /><br />Outlook per iPad e iPhone<sup>4</sup><br /><br />OWA per iOS<sup>3</sup><br /><br />Secure Islands IQProtector<sup>1</sup><br /><br />TITUS Mail|App RMS sharing<sup>1</sup>: Testo, immagini, pfile<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online <sup>2</sup>|GigaTrust App for Android<br /><br />Foxit Reader<br /><br />App RMS sharing<sup>1</sup>|9Folders<sup>4</sup><br /><br />App GigaTrust per Android<sup>4</sup><br /><br />NitroDesk<sup>4</sup><br /><br />OWA per Android<sup>3</sup> <sup>6</sup><br /><br />Samsung Email (S3 e versioni successive)<sup>6</sup><br /><br />Secure Islands IQProtector<sup>1</sup><br /><br />Classificazione TITUS per dispositivi mobili|App RMS sharing<sup>1</sup>: Testo, immagini, pfile|
|**OS X**|Office 2011 (solo AD RMS)<br /><br />Office 2016 per Mac<br /><br />Office Online <sup>2</sup>|Foxit Reader<br /><br />App RMS sharing<sup>1</sup>|Outlook 2011 (solo AD RMS)<br /><br />Outlook 2016 per Mac<br /><br />Outlook per Mac|App RMS sharing<sup>1</sup>: Testo, immagini, pfile|
|**Windows RT**|Office 2013 RT<br /><br />Office Online <sup>2</sup>|Non supportato|Outlook 2013 RT<br /><br />App Mail per Windows<br /><br />Windows Mail<sup>4</sup>|Siemens JT2Go: file JT|
|**Windows Phone 8.1**|Office Mobile (solo AD RMS)|App RMS sharing<sup>1</sup>|Outlook Mobile<sup>4</sup>|App RMS sharing<sup>1</sup>: Testo, immagini, pfile|
|**Blackberry 10**|Non supportato|Non supportato|Posta elettronica BlackBerry<sup>4</sup>|Non supportato|
<sup>1</sup> Supporta la visualizzazione di contenuto protetto.

<sup>2</sup> Supporta la visualizzazione di contenuto protetto in SharePoint Online, OneDrive for Business e Outlook Web Access.

<sup>3</sup> Se un destinatario dispone di una cassetta postale di Exchange in locale e riceve un messaggio di posta elettronica protetto, il contenuto può essere aperto solo con un client di posta elettronica, come Outlook,  e non da Outlook Web Access.

<sup>4</sup> Usa Exchange ActiveSync IRM, che deve essere abilitato dall'amministratore di Exchange. Gli utenti possono visualizzare, rispondere e rispondere a tutti per messaggi di posta elettronica protetti, ma gli utenti non possono proteggere i nuovi messaggi di posta elettronica da sé.

Se un destinatario dispone di una cassetta postale di Exchange in locale e riceve un messaggio di posta elettronica protetto da un'altra organizzazione che usa Exchange, il contenuto può essere aperto solo con un client di posta elettronica, come Outlook,  e non con un dispositivo che usa Exchange Active Sync IRM.

<sup>5</sup> Supporta la visualizzazione e la modifica di documenti protetti. Per altre informazioni, vedere il post sul blog di Office: [Supporto per Azure Rights Management disponibile in Office per iPad e iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>6</sup> Per altre informazioni, vedere il post sul blog di Office relativo a: [OWA per Android ora disponibile su dispositivi specifici](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> Per altre informazioni sul supporto per RMS presto disponibile in Office per le diverse piattaforme, vedere il post seguente del blog di Office: [Office ovunque, crittografia ovunque](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>Applicazioni che supportano Azure RMS
Le applicazioni seguenti offrono supporto nativo per Azure RMS, che è perfettamente integrato in queste applicazioni grazie alle API RMS, usate per supportare le restrizioni d'utilizzo. Queste applicazioni sono anche note come "migliorate da RMS":

-   Le **applicazioni Microsoft Office** (Word, Excel, PowerPoint e Outlook) incluse nelle famiglie di prodotti seguenti possono proteggere il contenuto con Azure RMS:

    -   Office 365 ProPlus

    -   Office 365 Enterprise E3

    -   Office 365 Enterprise E4

    -   Office 365 Enterprise E5

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Altre edizioni di Office, ad eccezione di Microsoft Office 2007, possono utilizzare il contenuto protetto.

    > [!NOTE]
    > Azure RMS con Office Professional Plus 2010 oppure Office Professional 2010:
    > 
    > -   Richiede l'applicazione di condivisione Microsoft Rights Management per Windows
    > -   Non supportato in Windows 10

-   **Applicazione di condivisione Rights Management per Windows**

    Per altre informazioni sull'applicazione di condivisione Rights Management per Windows, vedere le risorse seguenti:

    -   [Guida dell'amministratore dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Guida dell'utente dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339006.aspx)

-   **Applicazione di condivisione Rights Management per piattaforme mobili**

    Per altre informazioni sull'applicazione di condivisione Rights Management per piattaforme mobili, vedere le risorse seguenti:

    -   Per scaricare l'applicazione desiderata, fare clic sul collegamento corrispondente nella pagina [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

    -   Se si gestiscono dispositivi mobili con Microsoft Intune, è possibile distribuire e configurare l'app su [dispositivi iOS e Android come app gestita da criteri](https://technet.microsoft.com/library/dn878026.aspx).

    -   [Domande frequenti sull'applicazione di condivisione Microsoft Rights Management per piattaforme mobili](http://technet.microsoft.com/dn451248)

-   **Altre applicazioni che supportano le API RMS**:

    -   Applicazioni line-of-business create internamente mediante RMS SDK

    -   Applicazioni di fornitori di software create mediante RMS SDK

    Per altre informazioni sull'SDK, vedere la pagina relativa a [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

> [!IMPORTANT]
> Le applicazioni seguenti non sono attualmente supportate da Azure RMS:
> 
> -   Microsoft Office per Mac 2011
> -   Microsoft OneDrive for Business per SharePoint Server 2013
> -   XPS Viewer
> 
> L'applicazione RMS sharing prevede inoltre le restrizioni seguenti:
> 
> -   Per computer Windows: la versione minima richiesta è Windows 7 Service Pack 1

Per altre informazioni sulle modalità di supporto di Azure RMS da parte di queste applicazioni, vedere [Supporto di Microsoft Azure Rights Management da parte delle applicazioni](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Per informazioni sulla configurazione di queste applicazioni, vedere [Configurazione di applicazioni per Rights Management di Windows Azure](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## <a name="BKMK_SupportedServers"></a>Server locali che supportano Azure RMS
I prodotti server locali seguenti sono supportati con Azure RMS quando si usa il connettore Azure RMS, che opera come interfaccia di comunicazione (inoltro) tra i server locali e Azure RMS. Questa configurazione richiede inoltre l'impostazione della sincronizzazione della directory tra le foreste Active Directory e Active Directory di Azure.

-   **Exchange Server**:

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **File server che eseguono Windows Server e usano la funzionalità Infrastruttura di classificazione file**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Poiché i file server che eseguono Windows Server 2008 R2 non includono un'azione predefinita per le attività di gestione file per l'applicazione della protezione RMS, non sarà possibile usare il connettore RMS per questo scenario. È tuttavia possibile usare Infrastruttura di classificazione file e Azure RMS in questi sistemi operativi se si configura un'attività personalizzata di gestione file per l'esecuzione di un file eseguibile o di uno script in grado di proteggere i file tramite Azure RMS. Ad esempio, uno script di Windows PowerShell che utilizza i [cmdlet di protezione RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > È inoltre possibile utilizzare questi cmdlet con server che eseguono versioni successive di Windows Server, con il vantaggio che questi cmdlet possono proteggere tutti i tipi di file. Il connettore RMS protegge solo i file di Office. Per istruzioni, vedere [Protezione RMS con l'infrastruttura di classificazione file &#40;FCI, File Classification Infrastructure&#41; per Windows Server](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

Il connettore RMS è supportato in Windows Server 2012 R2, Windows Server 2012 e Windows Server 2008 R2.

Per altre informazioni sulla configurazione del connettore RMS per questi server locali, vedere [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Vedere anche
[Introduzione a Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

