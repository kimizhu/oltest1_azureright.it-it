---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# Supporto di Microsoft Azure Rights Management da parte delle applicazioni
In questo argomento sono contenute informazioni che descrivono il modo in cui le applicazioni dell'utente finale, ad esempio le applicazioni Office quali Word, Excel, PowerPoint e Outlook, e i servizi, ad esempio Exchange e SharePoint, possono usare Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] per proteggere i dati dell'organizzazione.

-   [Applicazione RMS sharing per piattaforme Windows e mobili](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Applicazioni Office: Word, Excel, PowerPoint, Outlook](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Exchange Online ed Exchange Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online e SharePoint Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [File server che eseguono Windows Server e usano la funzionalità Infrastruttura di classificazione file](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [Altre applicazioni che supportano le API RMS](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> Per verificare le applicazioni e le versioni che [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) supporta, vedere [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

In alcuni casi, la protezione delle informazioni viene applicata automaticamente in base ai criteri configurati dall'utente, ad esempio nel caso di raccolte SharePoint, file classificati e regole di trasporto di Exchange. In altri casi, gli utenti devono applicare in modo autonomo la protezione delle informazioni selezionando un modello oppure opzioni specifiche, ad esempio nel caso in cui condividono un file tramite e-mail o proteggono un file in locale limitandone l'accesso o l'uso a utenti selezionati oppure a utenti esterni all'organizzazione.

I modelli semplificano agli utenti e agli amministratori che configurano i criteri l'applicazione del livello corretto di protezione e la limitazione dell'accesso a persone all'interno dell'organizzazione. Sebbene in [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] siano disponibili due modelli predefiniti, sarà possibile creare modelli personalizzati per ridurre i tempi qualora sia necessario specificare opzioni singole. Per altre informazioni, vedere [Configurazione di modelli personalizzati per Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

Nei casi in cui gli utenti debbano applicare in modo autonomo la protezione delle informazioni, assicurarsi di fornire loro istruzioni e linee guida sulle modalità e sul momento in cui eseguire l'operazione. Le istruzioni devono essere specifiche per l'applicazione e le versioni usate e per le modalità di uso, mentre le linee guida relative al momento e alle modalità di applicazione della protezione delle informazioni devono essere appropriate per l'azienda. Per altre informazioni, vedere [Consentire agli utenti di proteggere i file mediante Azure Rights Management](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md).

Per altre informazioni sulle modalità di configurazione di queste applicazioni per Azure RMS, vedere [Configurazione di applicazioni per Rights Management di Windows Azure](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

> [!TIP]
> Per esempi e schermate delle applicazioni che usano Azure RMS, vedere la sezione [Azure RMS in azione: Cosa vedono gli amministratori e gli utenti](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) dell'argomento [Informazioni su Microsoft Azure Rights Management](../Topic/What_is_Azure_Rights_Management_.md).

## <a name="BKMK_SharingAppIntro"></a>Applicazione RMS sharing per piattaforme Windows e mobili
L'applicazione RMS sharing è un'applicazione scaricabile gratuita, necessaria per supportare Office 2010, ma consigliata anche per computer Windows e Mac e dispositivi mobili. L'applicazione è particolarmente vantaggiosa perché consente di applicare la protezione generica ad applicazioni e file senza supporto nativo per [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], il che significa che è possibile proteggere tutti i file. Per altre informazioni sui diversi livelli di protezione, vedere la sezione [Livelli di protezione nativa e generica](http://technet.microsoft.com/library/dn339003.aspx) della [Guida dell'amministratore dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339003.aspx).

Quando gli utenti proteggono i file usando l'applicazione RMS sharing, possono anche tenere traccia dei documenti protetti e, se necessario, revocarne l'accesso. A tale scopo, usare il [sito di rilevamento del documento](http://go.microsoft.com/fwlink/?LinkId=529562).

Per computer Windows, l'applicazione RMS sharing si integra in modo semplice con le applicazioni giù usate dagli utenti, contribuendo anche a migliorarle:

-   Viene installato un componente aggiuntivo di Office per Word, Excel, PowerPoint e Outlook. In questo modo gli utenti possono usare un pulsante **Condividi file protetto** sulla barra multifunzione che consente di visualizzare una semplice finestra di dialogo in cui sono disponibili le impostazioni usate più di frequente per proteggere i file da inviare tramite e-mail. Questo pulsante consente anche un rapido accesso al sito di rilevamento del documento.

-   È disponibile una nuova opzione di scelta rapida in Esplora file che consente agli utenti di applicare l'opzione **Proteggi sul posto** e di visualizzare una semplice finestra di dialogo in cui sono disponibili le impostazioni usate più di frequente per proteggere file archiviati su un disco.

-   Viene installato un visualizzatore per aprire i file protetti con [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. richiamato automaticamente quando non è installata alcuna applicazione in grado di aprire il file protetto.

-   È prevista una configurazione back-end per Office 2010 che consente alle versioni di Word, Excel, PowerPoint e Outlook di questa suite di integrarsi in modo semplice con [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Sebbene sia possibile scaricare l'applicazione di condivisione RMS per Windows e installarla in un singolo computer tramite la [pagina di Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), è supportata anche una distribuzione aziendale per l'installazione invisibile all'utente e la configurazione personalizzata. Per altre informazioni, vedere le risorse seguenti:

-   [Guida dell'amministratore dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339003.aspx)

-   [Guida dell'utente dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339006.aspx)

L'applicazione RMS sharing per dispositivi mobili supporta i dispositivi di questo tipo usati più di frequente, ad esempio iPad e iPhone nonché dispositivi Android, Windows Phone e Windows RT. Gli utenti possono scaricare questa app dallo Store pertinente cui è possibile accedere dai collegamenti presenti nella [pagina di Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).

## <a name="BKMK_OfficeAppsIntro"></a>Applicazioni Office: Word, Excel, PowerPoint, Outlook
Queste applicazioni supportano Rights Management a livello nativo usando Information Rights Management (IRM) e consentono agli utenti di applicare la protezione a un documento salvato oppure a un messaggio e-mail da inviare tramite l'applicazione di modelli o la scelta di impostazioni con un elevato livello di personalizzazione per limitare l'accesso, i diritti e l'uso. Gli utenti possono ad esempio configurare un file in modo che possano accedervi solo le persone appartenenti all'organizzazione o per controllare se il file può essere modificato, per impostarne l'accesso in sola lettura o per impedirne la stampa. Per file soggetti a vincoli temporali, è possibile configurare un'ora di scadenza (direttamente oppure applicando un modello) per stabilire il momento in cui non è più possibile accedere al file. Per Outlook, gli utenti possono anche scegliere l'opzione **Non inoltrare** per impedire la perdita di dati.

### <a name="BKMK_ExchangeIntro"></a>Exchange Online ed Exchange Server
Quando si usa Exchange Online oppure Exchange Server, è possibile usare l'integrazione IRM (Information Rights Management) che fornisce soluzioni di protezione delle informazioni aggiuntive:

-   **Exchange ActiveSync IRM** per proteggere dispositivi mobili e usare messaggi di posta elettronica protetti.

-   Supporto RMS per **Outlook Web App**, implementato in modo analogo al client Outlook, in modo che gli utenti possano proteggere i messaggi di posta elettronica tramite modelli o tramite la specifica di singole opzioni e che possano leggere e usare i messaggi di posta elettronica ricevuti in modo protetto.

-   **Regole di protezione** per client Outlook che un amministratore configura per applicare automaticamente modelli RMS ai messaggi di posta elettronica per destinatari specifici. Quando ad esempio vengono inviati messaggi e-mail interni all'ufficio legale dell'organizzazione, è possibile configurare tali messaggi in modo che possano essere letti solo dai membri dell'ufficio e che non possano essere inoltrati. Prima di inviare il messaggio e-mail gli utenti vedono la regola di protezione applicata e, per impostazione predefinita, possono rimuoverla se ritengono non sia necessaria. I messaggi e-mail vengono crittografati prima dell'invio. Per altre informazioni, vedere [Regole di protezione di Outlook](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) e [Creare una regola di protezione di Outlook](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) nella libreria di Exchange.

-   **Regole di trasporto** che un amministratore configura per applicare automaticamente modelli RMS a messaggi di posta elettronica in base a determinate proprietà, ad esempio mittente, destinatario, oggetto del messaggio e contenuto. Tali regole sono concettualmente analoghe alle regole di protezione, ma non consentono agli utenti di rimuovere la protezione, possono essere applicate a Outlook Web Access e a messaggi e-mail inviati da dispositivi mobili e non crittografano i messaggi e-mail prima che vengano inviati dal client. Per altre informazioni, vedere [Creare una regola di protezione del trasporto](http://technet.microsoft.com/library/dd302432.aspx) nella libreria di Exchange.

-   **Criteri di prevenzione della perdita dei dati** che contengono set di condizioni per filtrare i messaggi di posta elettronica e intraprendere azioni per prevenire la perdita di dati nel caso di informazioni riservate o sensibili, ad esempio quelle personali o correlate alla carta di credito. Quando si rilevano dati sensibili, è possibile usare i suggerimenti relativi ai criteri per avvertire gli utenti che potrebbe essere necessario applicare la protezione in base alle informazioni presenti nel messaggio e-mail. Per altre informazioni, vedere [Prevenzione della perdita di dati](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) nella libreria di Exchange.

-   **Crittografia dei messaggi di Office 365** che usa regole di trasporto per inviare messaggi di posta elettronica crittografati a persone all'esterno dell'organizzazione e che comporta la lettura del messaggio in un browser con un'interfaccia analoga a Outlook Web App. Nei messaggi e-mail crittografati della società è possibile personalizzare il testo della dichiarazione di non responsabilità e dell'intestazione nonché aggiungere il logo della società. Per altre informazioni, vedere [Crittografia messaggi di Office 365](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx) nel sito Web di Office.

Se si usa Exchange Server, è possibile usare le funzionalità di protezione delle informazioni con [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] grazie alla distribuzione del connettore RMS, che opera come un relè tra i server locali e il servizio cloud RMS. Per altre informazioni, vedere [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

### <a name="BKMK_SharePointIntro"></a>SharePoint Online e SharePoint Server
Quando si usa SharePoint Online o SharePoint Server, è possibile usare l'integrazione IRM (Information Rights Management) che consente agli amministratori di proteggere elenchi o raccolte, in modo che quando un utente estrae un documento il file venga protetto per consentirne la visualizzazione e l'uso solo alle persone autorizzate in base ai criteri di protezione delle informazioni specificati. Il file ad esempio potrebbe essere di sola lettura, potrebbe esserne stata disabilitata la copia del testo oppure potrebbe esserne stato impedito il salvataggio di una copia locale e la stampa.

La protezione delle informazioni per elenchi e raccolte viene sempre applicata da un amministratore e mai da un utente finale e viene applicata a livello di elenco o di raccolta per tutti i documenti contenuti anziché sui file singoli.  Se si usa SharePoint Online, gli utenti possono anche applicare IRM alla raccolta OneDrive for Business.

È necessario inoltre che il servizio IRM sia abilitato per SharePoint. Specificare quindi il servizio Information Rights Management per una libreria. Nel caso di SharePoint Online e OneDrive for Business, gli utenti possono specificare anche Information Rights Management per la raccolta OneDrive for Business. SharePoint non usa i modelli di criteri di diritti, anche se è possibile selezionare alcune impostazioni di configurazione di SharePoint, molto simili alle impostazioni che possono essere specificate nei modelli.

Se si usa SharePoint Server, è possibile usare le funzionalità di protezione delle informazioni con [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] grazie alla distribuzione del connettore RMS, che opera come un relè tra i server locali e il servizio cloud RMS. Per altre informazioni, vedere [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!NOTE]
> Attualmente, ci sono alcune limitazioni quando si usa IRM con SharePoint:
> 
> -   Non è possibile usare i modelli predefiniti o personalizzati gestiti nel portale di Azure classico.
> -   I file con un'estensione di file PPDF per i file PDF protetti non sono supportati. I file con un'estensione di file PDF e che sono protetti a livello nativo da RMS sono supportati quando si usa un programma per leggere i file PDF che supporta RMS a livello nativo.
> -   Dal momento che Office nei dispositivi mobili non supporta ancora RMS, questi dispositivi devono usare un browser per visualizzare i file protetti con RMS e quelli che sono di sola lettura.

Azure RMS applica le restrizioni d'uso e la crittografia dei dati per i documenti quando questi vengono scaricati da SharePoint e non quando il documento viene creato inizialmente in SharePoint o caricato nella raccolta. Per informazioni su come vengono protetti i documenti di essere scaricati, vedere [Crittografia dei dati in OneDrive for Business e SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) nella documentazione di SharePoint.

Per altre informazioni sull'uso di Azure RMS con SharePoint, vedere il post seguente del blog di Office: [Novità di Information Rights Management in SharePoint e SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>File server che eseguono Windows Server e usano la funzionalità Infrastruttura di classificazione file
Quando si configura Windows Server per usare Infrastruttura di classificazione file, questa funzionalità di Gestione risorse file server può analizzare i file locali per stabilire se contengono dati sensibili I file che soddisfano questi criteri vengono contrassegnati con proprietà di classificazione definite da un amministratore. A questo punto possono essere eseguite azioni automatiche, a seconda della classificazione, ad esempio l'applicazione della protezione delle informazioni usando [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] e la distribuzione del connettore Rights Management (noto anche come connettore RMS). I file di Office vengono automaticamente protetti da Azure RMS.

Per proteggere tutti i tipi di file, non si userà il connettore RMS, ma si deve invece eseguire uno script di Windows PowerShell, usando i cmdlet dello [strumento di protezione di RMS](https://www.microsoft.com/en-us/download/details.aspx?id=47256).

I criteri di classificazione sono completamente configurabili ed estendibili e consentono in tal modo di impedire la perdita potenziale di dati da parte di utenti autorizzati o meno. Tali criteri consentono inoltre di ridurre il rischio di perdita di dati da parte di amministratori di rete perché è possibile configurarli in modo che agli amministratori non venga richiesto l'accesso ai file.

Per istruzioni su come usare lo script di Windows PowerShell per tutti i tipi di file, vedere [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

Per istruzioni su come usare lo script PowerShell di Windows per tutti i tipi di file, vedere [Protezione RMS con l'infrastruttura di classificazione file &#40;FCI, File Classification Infrastructure&#41; per Windows Server](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md).

## <a name="BKMK_APIAppsIntro"></a>Altre applicazioni che supportano le API RMS
Con RMS SDK, gli sviluppatori interni di un'azienda possono scrivere applicazioni line-of-business per supportare [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] in modalità nativa. Le modalità di integrazione della protezione delle informazioni con queste applicazioni dipende dal modo in cui queste ultime sono state scritte. L'integrazione potrebbe ad esempio essere applicata automaticamente con un intervento minimo dell'utente oppure, per un'esperienza più personalizzata, agli utenti potrebbe essere richiesto di configurare impostazioni specifiche per applicare la protezione delle informazioni ai file. Per altre informazioni sull'SDK, vedere la pagina relativa a [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx).

In modo analogo, molti fornitori di software offrono soluzioni di protezione delle informazioni, applicazioni note anche come prodotti ERM (Enterprise Rights Management). Un esempio comune è quello di un lettore di file in formato PDF che supporta [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] per piattaforme specifiche. È possibile usare la tabella nella sezione [Funzionalità del dispositivo client](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) dell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) per identificare le applicazioni che supportano RMS (applicazioni abilitate per RMS) e quindi usare una ricerca Web per acquistare o scaricare l'applicazione.

> [!TIP]
> Per applicazioni rilasciate di recente, controllare i canali della community RMS elencati in [Informazioni e supporto per Rights Management di Windows Azure](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## Vedere anche
[Introduzione a Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

