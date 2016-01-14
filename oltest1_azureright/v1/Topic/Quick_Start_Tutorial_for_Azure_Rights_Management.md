---
description: na
keywords: na
title: Quick Start Tutorial for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1db923bf-7d19-4fdd-a413-bfeb58af5e03
---
# Esercitazione di avvio rapido per Azure Rights Management
Usare questa esercitazione per provare rapidamente Microsoft Azure Rights Management (Azure RMS) per l'organizzazione. L'esercitazione è articolata in 5 passaggi, eseguibili in meno di 15 minuti. Verrà attivato il servizio, verrà inviato in modo sicuro tramite e-mail un documento riservato a un altro utente dell'organizzazione e infine sarà possibile rilevare quando il documento viene aperto. Quando viene inviato tramite posta elettronica, il documento riservato viene crittografato mentre è in transito e può essere letto solo dall'utente a cui è stato inviato usando le autorizzazioni impostate dal mittente.

![](../Image/AzRMS_QuickStartStepsAll.PNG)

Questa esercitazione è rivolta ai consulenti e agli amministratori IT e consente di valutare Azure Rights Management come soluzione di protezione delle informazioni per un'organizzazione. In un ambiente di produzione le istruzioni per attivare il servizio verrebbero eseguite da un amministratore, mentre quelle per inviare il documento verrebbero eseguite dagli utenti finali. In questa esercitazione sono inclusi entrambi i set di istruzioni, per illustrare lo scenario end-to-end di invio sicuro di un documento riservato a una persona di un'altra organizzazione. Se si verificano problemi per completare questa esercitazione, inviare un messaggio di posta elettronica a [AskIPTeam](mailto:askipteam@microsoft.com?subject=Having%20problems%20with%20the%20Quick%20Start%20tutorial), che fornisce il supporto necessario.

Per completare questa esercitazione, è necessario quanto segue:

-   Una sottoscrizione che supporta Azure Rights Management. Può trattarsi di una sottoscrizione a pagamento o di una sottoscrizione di valutazione. Se si desidera usare la funzionalità di rilevamento dei documenti, che è richiesta per il passaggio 5 di questa esercitazione, è necessario disporre di una sottoscrizione che supporti la tracciabilità dei documenti. Per ulteriori informazioni sulle opzioni di sottoscrizione e sui collegamenti alle versioni di valutazione gratuite, vedere la sezione [Sottoscrizioni cloud che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) dell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

    Suggerimento: Se è necessario richiedere una sottoscrizione, eseguire questa operazione in anticipo perché talvolta il processo può richiedere alcuni minuti.

-   Un account di amministratore per accedere all'interfaccia di amministrazione di Office 365 o al portale di Azure classico, in modo da poter attivare il servizio Rights Management. Questo account deve disporre inoltre di un indirizzo di posta elettronica e di un servizio di posta elettronica funzionante (ad esempio, Exchange Online o Exchange Server).

-   Un computer che esegue Windows (almeno Windows 7 SP1) e in cui è stato installato Office 2016 o Office 2013 oppure Office 2010.

A questo punto, procedere con l’esercitazione.

## Passaggio 1: Attivare il servizio Rights Management
![](../Image/AzRMS_QuickStartSteps1.PNG)

Anche se si dispone di una sottoscrizione che supporta Azure Rights Management, il servizio è disabilitato per impostazione predefinita. Per attivarlo, è possibile usare l'interfaccia di amministrazione di Office 365 o il portale di Azure classico:

-   Se si dispone di una sottoscrizione di Office 365 che include Azure Rights Management o una sottoscrizione di Office 365 che esclude Azure Rights Management, ma si dispone di una sottoscrizione di Azure RMS Premium: **Usare l’interfaccia di amministrazione di Office 365**.

-   Se non si dispone di una sottoscrizione Office 365: **Usare il portale di Azure classico**.

![](../Image/AzRMS_Tutorial_1_Screenshots.png)

#### Per attivare Rights Management mediante l'interfaccia di amministrazione di Office 365

1.  Passare al [portale di Office 365](https://portal.office.com/) e accedere con l'account aziendale o dell’istituto di istruzione.

2.  Se l'interfaccia di amministrazione di Office 365 non viene visualizzata automaticamente, selezionare l'icona di avvio delle app in alto a sinistra e scegliere **Amministratore**. Il riquadro **Amministratore** viene visualizzato solo agli amministratori di Office 365.

    > [!TIP]
    > Per la guida all'interfaccia di amministrazione, vedere [Informazioni sull'interfaccia di amministrazione di Office 365 - Guida per gli amministratori](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  Nel riquadro sinistro fare clic su **IMPOSTAZIONI SERVIZIO**.

4.  Fare clic su **Rights Management**.

5.  Nella pagina **RIGHTS MANAGEMENT** fare clic su **Gestione**.

6.  Nella pagina **Rights Management** fare clic su **attiva**.

7.  Quando viene chiesto**se si desidera attivare Rights Management**, fare clic **attiva**.

Viene visualizzato il messaggio di avvenuta attivazione di Rights management e l'opzione di disattivazione (potrebbe essere necessario aggiornare manualmente la pagina).

A questo punto, non scegliere **funzionalità avanzate**. Con questa operazione viene infatti visualizzato il portale di Azure classico in cui è possibile configurare i modelli, che non sono necessari per questa esercitazione. Chiudere invece l’interfaccia di amministrazione di Office 365.

#### Per attivare Rights Management dal portale di Azure

1.  Accedere al [portale di Azure classico](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  Nel riquadro sinistro fare clic su **ACTIVE DIRECTORY**.

3.  Nella pagina **active directory** fare clic su **RIGHTS MANAGEMENT**.

4.  Selezionare la directory da gestire per [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], fare clic su **ATTIVA** e confermare l'azione.

Come **STATO RIGHTS MANAGEMENT** ora verrà visualizzato **Attivo** e l'opzione **ATTIVA** verrà sostituita da **DISATTIVA**.

Sebbene nel portale sia possibile configurare anche altre opzioni relative a Rights Management, queste non sono necessarie ai fini dell'esercitazione ed è pertanto possibile chiudere il portale di Azure classico.

Quelle sopra indicate sono tutte le operazioni da eseguire per il primo passaggio. Il servizio viene attivato in modo che a questo punto tutti gli utenti dell'organizzazione possano iniziare a proteggere i documenti riservati e importanti. In un ambiente di produzione è possibile limitare inizialmente gli utenti che possono effettuare questa operazione, in modo da eseguire un'implementazione graduale. Questo tuttavia non è necessario ai fini dell'esercitazione.

Anche se la procedura corrispondente non è inclusa in questa esercitazione, è probabile che per una distribuzione di produzione si desideri configurare modelli personalizzati. I modelli consentono agli utenti di applicare rapidamente le impostazioni corrette quando ne hanno bisogno per proteggere i file. Quando si attiva Rights Management, si ottengono automaticamente 2 modelli predefiniti ed è probabile che, in un ambiente di produzione, si desideri integrare tali modelli con modelli personalizzati. I modelli, tuttavia, non sono necessari per questa esercitazione ed è pertanto possibile procedere con il passaggio successivo.

|Se si desiderano altre informazioni|Informazioni aggiuntive|
|---------------------------------------|---------------------------|
|Informazioni sull'attivazione di Rights Management e sul controllo di chi può proteggere file e messaggi di posta elettronica quando il servizio è attivato   →|[Attivazione di Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md)|
|Informazioni sui modelli predefiniti e su come creare nuovi modelli personalizzati   →|[Configurazione di modelli personalizzati per Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md)|

## Passaggio 2: Installare l’applicazione di condivisione Rights Management
![](../Image/AzRMS_QuickStartSteps2.PNG)

L’applicazione di condivisione Rights Management (nota anche come “app di condivisione RMS”) non è un requisito per Azure Rights Management, ma è consigliabile per tutti i computer e i dispositivi mobili che supportano Azure Rights Management. L'applicazione di condivisione RMS si integra con le applicazioni di Office installando un componente aggiuntivo di Office, così da consentire agli utenti di proteggere facilmente i file direttamente dalla barra multifunzione. Consente inoltre di proteggere tutti i tipi di file tramite l'applicazione di protezione generica per i file non supportati in modo nativo da Azure Rights Management e un sito di rilevamento dei documenti per gli utenti che desiderano rilevare e revocare i file protetti. Il sito di rilevamento dei documenti verrà usato più avanti in questa esercitazione.

Questa applicazione può essere scaricata gratuitamente e offre un'installazione tramite script per gli ambienti di produzione. In questa esercitazione viene tuttavia installata localmente.

![](../Image/AzRMS_Tutorial_2_Screenshots.png)

#### Per scaricare e installare l’applicazione di condivisione Rights Management

1.  Accedere alla pagina [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) nel sito Web Microsoft.

2.  Nella sezione **Computer** fare clic sull'icona relativa all’**app RMS per Windows** e salvare il file di installazione **Setup.exe** dell’applicazione di condivisione Microsoft Rights Management.

3.  Per un'installazione locale, è necessario usare un account amministratore per eseguire il file Setup.exe scaricato. Se viene chiesto di continuare, fare clic su**Sì**.

4.  Nella pagina **Installazione di Microsoft RMS** fare clic su **Avanti** e attendere il completamento dell'installazione.

5.  Al termine dell'installazione, fare clic su **Riavvia** per riavviare il computer o su **Chiudi** per completare l'installazione.

A questo punto è possibile iniziare a proteggere i file che contengono le informazioni da condividere, ma solo con utenti specificati.

|Se si desiderano altre informazioni|Informazioni aggiuntive|
|---------------------------------------|---------------------------|
|Informazioni su un'installazione locale dell'applicazione di condivisione Rights Management per Windows e istruzioni per l’utente   →|[Guida dell'utente dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339006.aspx)|
|Informazioni su un'installazione tramite script dell'applicazione di condivisione Rights Management per Windows e altre informazioni tecniche   →|[Guida dell'amministratore dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339003.aspx)|
|Informazioni sulla differenza tra protezione nativa e protezione generica   →|[Qual è la differenza tra protezione generica e protezione integrata (nativa)?](https://technet.microsoft.com/library/dn574738.aspx)|

## Passaggio 3: Inviare tramite posta elettronica il documento che si desidera proteggere
![](../Image/AzRMS_QuickStartSteps3.PNG)

Per questo passaggio, creare e salvare un documento di Word che rappresenta il documento che si desidera proteggere e denominarlo **Confidential.docx**. Ai fini di questa esercitazione non è importante l’effettivo contenuto del testo. Verrà tuttavia definito un testo, in modo verificare con maggiore semplicità che il destinatario autorizzato possa leggerlo. Ad esempio, si potrebbe scrivere: **Se il testo è leggibile dall'allegato di posta elettronica, il mittente ha correttamente condiviso un file protetto con Azure RMS.**

È quindi possibile condividere in modo sicuro il documento tramite posta elettronica.

![](../Image/AzRMS_Tutorial_3_Screenshots.png)

#### Per condividere in modo sicuro il documento tramite posta elettronica

1.  Usando Outlook, creare un nuovo messaggio e allegare il file appena creato.

2.  Nella casella **A** digitare uno o più indirizzi di posta elettronica aziendali. Assicurarsi di specificare un indirizzo di posta elettronica aziendale, ad esempio **janetm@contoso.com** o **p.dover@fabrikam.com**. Azure Rights Management, infatti, non supporta gli indirizzi di posta elettronica personali che vengono generalmente assegnati dal provider di servizi Internet usato a casa. Non è importante se la persona a cui si sta inviando il messaggio dispone o meno di Azure Rights Management.

3.  Digitare un oggetto, ad esempio **Documento riservato**, quindi digitare un breve messaggio di posta elettronica, ad esempio **Questo documento è riservato e non può essere condiviso con altri utenti.**

4.  Nella scheda **Messaggio**, nel gruppo **RMS**, fare clic su **Condividi file protetto** e quindi fare di nuovo clic su **Condividi file protetto**:

5.  Nella finestra di dialogo **Condividi file protetto**:

    1.  Selezionare **Visualizzatore - Solo visualizzazione**.

        In questo modo i destinatari saranno in grado di visualizzare il documento, ma non di modificarlo o stamparlo.

    2.  Selezionare l'opzione per l'**invio di un messaggio di posta elettronica quando qualcuno tenta di aprire il documento**.

        Si riceverà una notifica tramite posta elettronica ogni volta che i destinatari tentano di aprire l'allegato. La notifica verrà inviata anche quando qualcun altro tenta di aprire il messaggio, ad esempio se il destinatario lo inoltra a un collega. In quest'ultimo scenario l'accesso viene negato e, in base ai dettagli dell'utente, sarà possibile decidere se inviare a tale persona una copia del documento che potrà aprire.

    3.  Selezionare l'opzione per la **revoca immediata dell'accesso a specifici documenti**.

        Per questa opzione è necessario che i destinatari siano connessi a Internet ogni volta che aprono l'allegato. L'opzione offre comunque il vantaggio che, se in un secondo momento si revoca il documento, il successivo tentativo di apertura da parte dei destinatari avrà esito negativo. Se non si seleziona questa opzione, i destinatari potrebbero essere in grado di aprire il documento anche senza una connessione Internet, con lo svantaggio che, se in un secondo momento si revoca il documento, potrebbe verificarsi un ritardo nell’applicazione di tale scelta.

    4.  Fare clic su **Invia subito**.

        Il messaggio con l’allegato viene inviato agli indirizzi di posta elettronica specificati. Oltre al messaggio di posta elettronica, vengono visualizzate le istruzioni per leggere il documento allegato e protetto da Azure Rights Management.

Ora che è stato inviato il documento protetto, è possibile chiedere ai destinatari di attenderne l'arrivo e quindi di aprirlo. Non chiudere Outlook, perché verrà usato di nuovo nel passaggio finale per rilevare l'allegato.

|Se si desiderano altre informazioni|Informazioni aggiuntive|
|---------------------------------------|---------------------------|
|Istruzioni complete e metodi alternativi per la protezione dei file condivisi tramite posta elettronica   →|[Proteggere un file che si condivide tramite posta elettronica usando l'applicazione di condivisione Rights Management](https://technet.microsoft.com/library/dn574735.aspx)|
|Informazioni sulle opzioni della finestra di dialogo **Condividi file protetto** →|[Opzioni della finestra di dialogo per l’applicazione di condivisione Rights Management](https://technet.microsoft.com/library/dn574738.aspx)|

## Passaggio 4: Chiedere ai destinatari di aprire il documento inviato tramite posta elettronica
![](../Image/AzRMS_QuickStartSteps4.PNG)

I destinatari possono usare molti dispositivi per leggere il documento protetto inviato come allegato di posta elettronica. I dispositivi includono iPad, iPhone, tablet e telefoni Android, computer Mac e computer Windows.

Chiedere di leggere il messaggio di posta elettronica inviato. Verrà visualizzato il messaggio di posta elettronica e, prima di esso, il testo seguente:

**Il mittente ha protetto gli allegati con Microsoft RMS. Per aprirli,** [è necessario](http://aka.ms/rms) **eseguire l'accesso.**

Quando si fa clic sul collegamento, vengono visualizzate le istruzioni per installare l'app di condivisione RMS e, se necessario, per accedere a un account gratuito. L'account gratuito concede una sottoscrizione per RMS per utenti singoli. Questa sottoscrizione assicura che gli utenti autorizzati possano sempre leggere un documento protetto, anche se l'organizzazione non dispone di Azure RMS. A questo punto è possibile leggere l'allegato protetto seguendo le istruzioni seguenti.

![](../Image/AzRMS_Tutorial_4_Screenshots.png)

#### Per visualizzare l'allegato del documento protetto

1.  Poiché si tratta di un documento di Word protetto da Azure Rights Management, il messaggio di posta elettronica presenta due allegati. Si tratta in effetti di due versioni dello stesso file con estensioni diverse. Aprire la versione con l’estensione di file **.ppdf** (**Confidential.ppdf**).

    Se si dispone di una versione di [Office sul dispositivo che supporta Rights Management](https://technet.microsoft.com/library/dn655136.aspx), è possibile aprire l'altra versione del file (**Confidential.docx**) in modo da aprirla in Word.

2.  Se vengono richiesti il nome utente e la password, immettere il nome utente nello stesso formato dell'indirizzo di posta elettronica usato per inviare il messaggio di posta elettronica e l’allegato, ad esempio **janetm@contoso.com** o **p.dover@fabrikam.com**. Come password digitare quella fornita al momento dell'iscrizione a RMS per utenti singoli. In alternativa, se l'organizzazione dispone di Azure RMS, immettere la normale password aziendale.

Il documento viene aperto ed è possibile leggerne il contenuto. Ad esempio, si potrebbe leggere **Se il testo è leggibile dall'allegato di posta elettronica, il mittente ha correttamente condiviso un file protetto con Azure RMS.** Dal momento che il documento è di sola lettura, non è possibile modificare il contenuto.

Come passaggio facoltativo, è possibile richiedere al destinatario di inoltrare il messaggio di posta elettronica ad altri utenti non inclusi nel messaggio originale Anche se questi utenti lavorano per un'organizzazione dotata di Azure Rights Management o richiedono una propria sottoscrizione a RMS per utenti singoli, non saranno in grado di aprire l'allegato. Se vengono accettati per il nome utente, l'accesso al documento verrà comunque negato.

Ora che il destinatario ha aperto l'allegato e, facoltativamente, lo ha inoltrato a qualcun altro, si prevede di ricevere una notifica tramite posta elettronica che segnala questa attività. I messaggi di posta elettronica, tuttavia, vanno facilmente persi nel corso tempo. Il modo migliore per rilevare chi ha avuto accesso al documento consiste nell'usare il sito di rilevamento dei documenti, come illustrato nel passaggio finale.

|Se si desiderano altre informazioni|Informazioni aggiuntive|
|---------------------------------------|---------------------------|
|Istruzioni complete per la visualizzazione dei file protetti da Azure Rights Management   →|[Visualizzare e usare i file che sono stati protetti da Rights Management](https://technet.microsoft.com/library/dn574741.aspx)|
|Informazioni sulla sottoscrizione gratuita, RMS per utenti singoli   →|[RMS per utenti singoli e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|Informazioni sulle due versioni del file allegato al messaggio e-mail   →|[Che cos'è il file .ppdf che viene creato automaticamente?](https://technet.microsoft.com/library/dn574738.aspx)|

## Passaggio 5: Rilevare il documento protetto
![](../Image/AzRMS_QuickStartSteps5.PNG)

> [!NOTE]
> Per questo passaggio è necessario disporre di una sottoscrizione che supporta il rilevamento dei documenti. Per verificare se la sottoscrizione comprende il rilevamento dei documenti, vedere [Offerte di Rights Management Services (RMS) a confronto](https://technet.microsoft.com/dn858608.aspx).

Questo passaggio è facoltativo, anche se la maggior parte degli utenti desidera sapere se l'allegato inviato alle persone è stato aperto, quando e da dove. Ad esempio:

-   Si aspetta una risposta da un utente entro un determinato periodo di tempo, ma dal sito di rilevamento dei documenti si ricava che il documento non è stato aperto anche se si avvicina la scadenza. Si invia un messaggio di posta elettronica di controllo o si telefona all’utente per un veloce promemoria.

-   Dopo che l’utente ha aperto il documento, è previsto l'invio di un messaggio di controllo per sapere se ha domande da porre o richiede informazioni aggiuntive.

![](../Image/AzRMS_Tutorial_5_Screenshots.png)

#### Per rilevare il documento protetto

1.  In Outlook, nella scheda **Home**, nel gruppo **RMS**, fare clic su **Rileva utilizzo**.

2.  Se viene visualizzata la pagina **Proteggi e condividi nelle condizioni**, fare clic su **Accedi** e fornire nuovamente il nome utente e la password.

3.  Nella pagina **Documenti condivisi** sarà presente il documento allegato al messaggio di posta elettronica, **Confidential.docx**. Al momento è l'unico file visualizzato, ma se vengono condivisi altri documenti protetti, l'elenco si allunga di conseguenza.

    In questa pagina viene indicato quando il documento è stato condiviso (quando è stato inviato il messaggio di posta elettronica con l'allegato protetto), la data dell'ultima attività e il nome del destinatario a cui è stato inviato il messaggio. Fare clic sul nome del documento per altri dettagli.

4.  Nella nuova pagina, che ha il nome del file selezionato, verranno visualizzati i dettagli di riepilogo solo per il documento in questione e un elenco di altre opzioni disponibili per quest'ultimo (**Elenco**, **Sequenza temporale**, **Mappa** e **Impostazioni**).

    Fare clic su ogni opzione per esplorare i diversi modi di rilevare il documento protetto. In alternativa, sempre nella pagina **Riepilogo**, fare clic su **Apri in Excel** per esportare le informazioni in un foglio di calcolo oppure fare clic su **Revoca accesso** per arrestare la condivisione del documento.

È possibile tornare a questo sito per rilevare altre attività relative al documento protetto o, se necessario, per revocare l'accesso. È anche possibile accedere al sito dal dispositivo mobile o dal tablet, usando un browser con il collegamento seguente: [rilevamento documenti](http://go.microsoft.com/fwlink/?LinkId=529562)

|Se si desiderano altre informazioni|Informazioni aggiuntive|
|---------------------------------------|---------------------------|
|Istruzioni complete per il rilevamento dei documenti   →|[Rilevare e revocare i documenti quando si usa l'applicazione di condivisione RMS](https://technet.microsoft.com/library/dn986611.aspx)|
|Video di due minuti che spiega e illustra il rilevamento dei documenti   →|[Revoca e rilevamento dei documenti di Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)|
|Per la risoluzione dei problemi e le domande dei clienti   →|[Domande frequenti relative al rilevamento dei documenti](https://technet.microsoft.com/dn947488)|

## Passaggi successivi
In questa esercitazione è stato esaminato un solo scenario relativo a come Azure RMS può semplificare la protezione dei dati. Per altri usi comuni, vedere la sezione [Azure RMS in azione](https://technet.microsoft.com/library/jj585026.aspx) dell'articolo [Informazioni su Microsoft Azure Rights Management](../Topic/What_is_Azure_Rights_Management_.md). In questo articolo sono presenti altre sezioni che potrebbero risultare utili, ad esempio quelle relative al funzionamento di Azure RMS e ai problemi aziendali che questo componente può risolvere.

Quando si è pronti a iniziare la distribuzione di Azure RMS, vedere l'argomento [Guida di orientamento per la distribuzione di Microsoft Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) in cui sono illustrati i passaggi di distribuzione e sono disponibili collegamenti a istruzioni procedurali.

## Vedere anche
[Introduzione a Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

