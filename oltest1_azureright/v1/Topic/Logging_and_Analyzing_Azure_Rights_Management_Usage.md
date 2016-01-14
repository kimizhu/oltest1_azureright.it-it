---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Registrazione e analisi dell&#39;uso di Rights Management di Windows Azure
Le informazioni riportate in questo argomento consentono di comprendere l'uso della funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management (RMS). Il servizio Azure Rights Management è in grado di registrare qualsiasi richiesta eseguita per l'organizzazione, incluse le richieste provenienti dagli utenti, le azioni effettuate dagli amministratori di Rights Management dell'organizzazione e quelle effettuate da operatori Microsoft a supporto della distribuzione di Azure Rights Management.

È quindi possibile usare i log di Azure Rights Management per supportare gli scenari aziendali seguenti:

-   Analisi per ottenere informazioni aziendali accurate.

    Azure Rights Management scrive i log in formato W3C esteso in un account di archiviazione di Azure predefinito. L'amministratore può quindi indirizzare questi log in un repository di sua scelta, ad esempio un database, un sistema di elaborazione analitica online (OLAP) o un sistema MapReduce, per analizzare le informazioni e generare report. È possibile, ad esempio, identificare gli utenti che accedono ai dati protetti da RMS e determinare quali dati protetti vengono visualizzati, da quali dispositivi e da quali postazioni. È inoltre possibile stabilire se gli utenti possono leggere correttamente il contenuto protetto. È infine possibile identificare gli utenti che hanno letto un importante documento protetto.

-   Monitoraggio per evitare eventuali abusi.

    Le informazioni fornite dalla funzionalità di registrazione di Azure Rights Management sono disponibili quasi in tempo reale, consentendo un monitoraggio continuo dell'uso di Rights Management da parte della società. Il 99,9% dei log sono disponibili entro 15 minuti dall'inizio di un'azione avviata da RMS.

    È possibile, ad esempio, scegliere di ricevere un avviso nel caso in cui si verifichi un improvviso picco di accessi a dati protetti da RMS al di fuori del normale orario di lavoro. Un picco di questo tipo potrebbe indicare che un utente malintenzionato sta raccogliendo informazioni da vendere alla concorrenza. È possibile anche scegliere di ricevere un avviso se uno stesso utente sembra accedere ai dati da due indirizzi IP differenti nell'arco di un breve periodo di tempo. Questo evento può indicare infatti che un account utente è stato compromesso.

-   Esecuzione di analisi per scopi legali.

    Se si verifica una perdita di informazioni, è probabile che all'amministratore vengano richiesti i nominativi degli utenti che hanno avuto accesso a specifici documenti e l'indicazione delle informazioni visualizzate di recente da una persona sospetta. Se si usa Azure Rights Management e la relativa funzione di registrazione, è possibile rispondere a questo tipo di domande. Gli utenti che usano contenuto protetto, infatti, devono sempre ottenere una licenza di Rights Management per aprire immagini e documenti protetti con Azure Rights Management, anche se i file vengono spostati tramite posta elettronica o copiati in unità USB o altri dispositivi di archiviazione. Questo significa che, quando i dati vengono protetti con Azure Rights Management, è possibile usare i log di Azure Rights Management come fonte certa di informazioni per l'esecuzione di analisi a scopi legali.

> [!NOTE]
> Se si è interessati solo alla registrazione delle attività amministrative di Azure Rights Management, e non alle modalità con cui viene usato il servizio, è possibile usare il cmdlet [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) di Windows PowerShell per Azure Rights Management.
> 
> È possibile usare il portale di Azure classico anche per report generali sull'utilizzo, tra cui **Utilizzo di RMS**, **Utenti RMS più attivi**, **Utilizzo dispositivi RMS** e **Utilizzo applicazioni abilitate per RMS**. Per accedere a questi report dal portale di Azure classico, fare clic su **Active Directory**, selezionare e aprire una directory e quindi fare clic su **REPORT**.

Per altre informazioni sulla funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management, vedere le sezioni seguenti.

-   [Come abilitare la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [Come accedere e usare i log sulle modalità di utilizzo di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [Come gestire l'archiviazione dei log di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [Come delegare l'accesso ai log sulle modalità di utilizzo di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [Come interpretare i log sulle modalità di utilizzo di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [Riferimenti Windows PowerShell](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>Come abilitare la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management
La registrazione delle modalità di utilizzo di Azure Rights Management è una funzionalità opzionale e per usarla è necessario seguire una procedura specifica. Quando si usa questa funzionalità, non si verificano cambiamenti nel funzionamento di Azure Rights Management e il processo di registrazione è gratuito. È tuttavia necessario fornire un account di archiviazione di Azure per i log e per lo spazio occupato verrà addebitato un costo.

Prima di iniziare a usare la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management, verificare che siano soddisfatti i prerequisiti seguenti:

|Requisito|Altre informazioni|
|-------------|----------------------|
|Una sottoscrizione gestita dal reparto IT che includa Azure Rights Management|È necessario disporre di una sottoscrizione di Microsoft Azure Rights Management gestita dall'organizzazione. Le organizzazioni che usano RMS per utenti singoli non possono usare la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management.<br /><br />Se nell'organizzazione sono presenti persone che usano RMS per utenti singoli, la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management costituisce un valido motivo per trasformare tali sottoscrizioni in sottoscrizioni di Microsoft Azure Rights Management.<br /><br />Per altre informazioni sulle sottoscrizioni che includono Azure RMS, vedere la sezione [Sottoscrizioni cloud che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) nell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).<br /><br />Per altre informazioni su RMS per utenti singoli, vedere [RMS per utenti singoli e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|Sottoscrizione di Azure|È necessario disporre di una sottoscrizione di Azure e di spazio di archiviazione sufficiente in Azure per i log di Azure Rights Management.|
|Windows PowerShell per Azure Rights Management|Scaricare e installare il modulo Windows PowerShell per Azure Rights Management (se non già scaricato). I cmdlet di Windows PowerShell consentono di configurare e gestire i log sulle modalità di utilizzo di Azure Rights Management.<br /><br />Per altre informazioni, vedere [Installazione di Windows PowerShell per Microsoft Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).|
Per abilitare la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management seguire la procedura descritta di seguito, inclusi i passaggi per la creazione di un account di archiviazione di Azure e la configurazione di Azure per l'utilizzo dell'account durante l'archiviazione dei log di Rights Management.

> [!NOTE]
> La procedura presuppone che l'utente disponga di un account Azure. Sebbene la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management supporti account individuali, è preferibile usare account aziendali o dell'istituto di istruzione. Si consiglia inoltre di creare un account di archiviazione dedicato per i log di Rights Management. È necessario condividere le chiavi di accesso alle risorse di archiviazione con Azure Rights Management e potenzialmente con altri utenti, se anche questi useranno i file di log.
> 
> Per altre informazioni sull'archiviazione di Azure, vedere la [documentazione di Azure relativa all'archiviazione](http://azure.microsoft.com/documentation/services/storage/).

#### Come creare un account di archiviazione e abilitare la funzionalità di registrazione della modalità di utilizzo di Azure Rights Management

1.  Accedere al [portale di Azure](https://portal.azure.com/).

2.  Nel menu Hub selezionare **Nuovo** -&gt; **Dati e archiviazione** -&gt; **Account di archiviazione**.

    > [!TIP]
    > Se questa opzione non è visualizzata, controllare di avere una sottoscrizione di Azure oltre alla sottoscrizione per Rights Management.

3.  Mantenere il modello di distribuzione predefinito **Classico** e fare clic su **Crea**.

    Specificare il nome dell'account di archiviazione e, se necessario, modificare le opzioni selezionate relative a **Piano tariffario**, **Gruppo di risorse**, **Sottoscrizione** e **Aggiungi al dashboard**. Successivamente, fare clic su **CREA**. Attendere che l'attività **Creazione dell'account di archiviazione** sia completata.

4.  Fare clic sull'account di archiviazione appena creato e quindi su **Impostazioni**.

5.  Nel pannello **Impostazioni** fare clic sull'icona **Chiavi**.

6.  Nel pannello **Gestisci chiavi** copiare il valore di **CHIAVE DI ACCESSO PRIMARIA** e chiudere il pannello.

7.  Avviare Windows PowerShell usando l'opzione **Esegui come amministratore**. Eseguire il comando [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) per connettersi al servizio Azure Rights Management:

    ```
    Connect-AadrmService
    ```

8.  Usare il comando [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) per specificare il percorso di archiviazione dei log sulle modalità di utilizzo di Azure Rights Management, sostituendo *&lt;Access_Key&gt;* con la chiave di accesso primaria copiata al passaggio 6 e *&lt;StorageAccount&gt;* con il nome dell'account di archiviazione creato al passaggio 3:

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. Usare il comando [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx) per abilitare la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management:

    ```
    Enable-AadrmUsageLogFeature
    ```
    Verrà visualizzato un messaggio simile al seguente: **La funzionalità di registrazione dell'uso è abilitata per il servizio Rights Management.**

Dopo aver abilitato la funzionalità di registrazione delle modalità di utilizzo, Azure Rights Management inizia a registrare tutte le azioni relative all'organizzazione salvandole nell'account di archiviazione. La funzionalità di registrazione delle informazioni è disponibile solo dopo il completamento della procedura.

Per altre informazioni sulle modalità di creazione di account di archiviazione, vedere la sezione [Creare un account di archiviazione](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) dell'articolo [Informazioni sugli account di archiviazione di Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) nella documentazione di Azure.

## <a name="BKMK_AccesAndUseLogs"></a>Come accedere e usare i log sulle modalità di utilizzo di Azure Rights Management
Azure Rights Management scrive i log nell'account di archiviazione di Azure sotto forma di una serie di BLOB. Ciascun blob contiene uno o più record di log in formato W3C esteso. I nomi dei blob sono numeri e corrispondono all'ordine di creazione. La sezione [Come interpretare i log sulle modalità di utilizzo di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret) più avanti in questo argomento contiene altre informazioni sui contenuti dei log e sulla relativa creazione.

In seguito a un'azione di Azure Rights Management, la visualizzazione dei log nell'account di archiviazione può richiedere un po' di tempo. La maggior parte dei log viene visualizzata entro 15 minuti.

L'account di archiviazione creato per i log sulle modalità di utilizzo di Azure Rights Management è simile a una cassetta postale. Sebbene non sia ottimizzato per la lettura diretta dei log, supporta questa funzione. Per ottenere migliori prestazioni e ridurre i costi, si consiglia di scaricare i log in uno spazio di archiviazione locale, ad esempio una cartella o un database, oppure in un repository MapReduce.

È possibile scaricare i log sulle modalità di utilizzo in due modi:

-   Usando il cmdlet [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx) di Windows PowerShell.

    Questo è il modo più semplice per accedere ai log. Questo cmdlet esegue il download dei log nel computer dell'utente, scaricando ciascun blob come file in una posizione specificata.

-   Usando [Azure Storage SDK](http://www.windowsazure.com/en-us/develop/net/) per scrivere un'applicazione personalizzata con cui scaricare i log.

    Rispetto al cmdlet Get-AadrmUsageLogs, un'applicazione personalizzata fornisce maggiore flessibilità. È possibile, ad esempio, delegare ad altri utenti il download dei log o l'esecuzione di un processo che non richiede l'utilizzo delle credenziali amministrative di Azure Rights Management. È possibile anche eseguire il polling dei log in tempo reale per monitorare eventuali utilizzi impropri.

#### Per scaricare i log sulle modalità di utilizzo con PowerShell

-   Avviare Windows PowerShell usando l'opzione **Esegui come amministratore** ed eseguire **Get-AadrmUsageLog –Path &lt;location&gt;**. Ad esempio, dopo avere creato una cartella denominata **logs** sull'unità E:

    -   Per scaricare tutti i log disponibili nella cartella E:\logs: `Get-AadrmUsageLog -Path "e:\logs"`

    -   Per scaricare uno specifico intervallo di BLOB: `Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

Quando si eseguono questi cmdlet, Windows PowerShell visualizza il nome dell'ultimo blob scaricato. È possibile assegnare questo nome a una variabile, operazione che consente di eseguire il cmdlet Get-AadrmUsageLog in un ciclo oppure di pianificare un processo, scaricando di volta in volta i log in modo incrementale.

Ad esempio:

**PS C:\&gt; $LastBlobName = Get-AadrmUsageLog –Path "e:\logs"**

**1527**

**PS C:\&gt; $LastBlobName**

**1527**

> [!TIP]
> È possibile aggregare tutti i file di log scaricati in un formato CSV mediante [Log Parser di Microsoft](http://www.microsoft.com/download/details.aspx?id=24659), uno strumento che consente di eseguire conversioni tra formati di log noti. È possibile usare questo strumento anche per convertire i dati in formato SYSLOG o per importarli in un database. Dopo avere installato Log Parser, eseguire **LogParser.exe /?** per informazioni e supporto sull'uso dello strumento. È ad esempio possibile eseguire il comando riportato di seguito per importare tutte le informazioni in un file in formato .log: **logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**.

È possibile sospendere e riprendere la registrazione delle modalità di utilizzo. Quando si sospende la registrazione, Azure Rights Management conserva le informazioni sull'account di archiviazione, in modo che sia possibile riprendere facilmente il processo.

#### Per sospendere e riprendere la registrazione delle modalità di utilizzo

-   Per sospendere la registrazione, usare il seguente cmdlet: [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   Per riprendere la registrazione, usare il seguente cmdlet: [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   Per verificare se la registrazione è abilitata o disabilitata, usare il seguente cmdlet: [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    Il valore **True** indica che la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management è abilitata, mentre il valore **False** indica che è disabilitata.

## <a name="BKMK_ManageStorage"></a>Come gestire l'archiviazione dei log di Azure Rights Management
Viene addebitato un costo per lo spazio di archiviazione usato per la conservazione dei log di Azure Rights Management.

Azure Rights Management non gestisce automaticamente i file di log sulle modalità di utilizzo. Se non viene eseguita alcuna azione, tali file di log rimangono nell'account di archiviazione. Tuttavia, per conservare spazio e ridurre i costi di archiviazione, dopo il download è consigliabile eliminare i file di log, interamente o in parte. Poiché Azure Rights Management non usa questi file, con un'unica eccezione, è possibile procedere all'eliminazione in qualsiasi momento.

Il file che non deve essere eliminato né modificato è denominato **metadata** e si trova nel contenitore **rms-metadata**. Azure Rights Management usa questo BLOB per tenere traccia dell'ultimo numero di BLOB usato. Se si elimina questo file, Azure Rights Management avvia un nuovo contenitore per i log, con un numero di BLOB che inizia da 1. Tutti i futuri download eseguiti mediante il cmdlet Get-AadrmUsageLog useranno questo nuovo contenitore per i file di log. Come risultato, i log presenti nel contenitore originale vengono conservati ma resi orfani. L'unico modo per scaricare i log orfani consiste nell'usare Azure Storage SDK.

> [!TIP]
> Anziché gestire in prima persona l'archiviazione dei log di Azure Rights Management, è possibile delegare questa funzione a un'altra società condividendo il nome e la chiave di accesso dell'account di archiviazione. Per altre informazioni, vedere più avanti in questo argomento la sezione [Come delegare l'accesso ai log sulle modalità di utilizzo di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate).

In alcuni casi, può essere necessario rigenerare le chiavi di accesso alle risorse di archiviazione. Ad esempio:

-   La gestione dei log sulle modalità di utilizzo di Azure Rights Management viene affidata a un'altra società.

-   Si sospetta che la chiave di accesso alle risorse di archiviazione sia compromessa.

Se si verificano queste condizioni, e se in precedenza è stata usata la chiave di accesso primaria, per assicurare la continuità del servizio è possibile usare la chiave di accesso secondaria. Quando si rigenera la chiave di accesso non usata in precedenza, Azure Rights Management viene configurato per l'uso della nuova chiave. Seguire questa procedura per rigenerare la chiave di accesso secondaria e configurare Azure Rights Management per l'uso di questa chiave.

#### Per rigenerare la chiave di accesso secondaria

1.  Accedere al [portale di Azure](https://portal.azure.com/).

2.  Fare clic su **Tutte le risorse** e cercare la propria risorsa di archiviazione digitando il nome della risorsa nella casella di testo.

3.  Selezionare la risorsa di archiviazione e scegliere **Impostazioni**.

4.  Fare clic sull'icona **Chiavi**.

5.  Nella sezione **Gestisci chiavi** fare clic su **Rigenera chiave secondaria**. Scegliere Sì per confermare la rigenerazione della chiave di accesso secondaria e copiare la nuova chiave negli Appunti.

    Non chiudere il portale Azure.

6.  Avviare Windows PowerShell con l'opzione **Esegui come amministratore** e usare il cmdlet [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) per configurare Azure Rights Management per l'uso della nuova chiave di accesso, sostituendo *&lt;StorageAccount&gt;* con il nome dell'account di archiviazione e *&lt;Access_Key&gt;* con la chiave di accesso secondaria rigenerata appena copiata:

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > Anche se durante l'esecuzione di questo comando è possibile passare a un altro account di archiviazione, questa azione rende orfani i log precedenti, ai quali non sarà più possibile accedere mediante il cmdlet Set-AadrmUsageLogStorageAccount o analoghi comandi e funzioni di gestione.

7.  Tornare al portale di Azure e, nella sezione **Gestisci chiavi**, rigenerare la chiave di accesso primaria.

Per altre informazioni sulle modalità di gestione delle chiavi di accesso alle risorse di archiviazione, vedere la sezione [Gestire le chiavi di accesso alle risorse di archiviazione](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) dell'articolo [Informazioni sugli account di archiviazione di Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/) nella documentazione di Azure.

## <a name="BKMK_Delegate"></a>Come delegare l'accesso ai log sulle modalità di utilizzo di Azure Rights Management
È possibile delegare l'accesso ai log di RMS condividendo il nome e la chiave di accesso dell'account di archiviazione. In alcuni casi può essere necessario delegare l'accesso a un altro utente amministratore, a uno sviluppatore dell'organizzazione o a un fornitore di software indipendente (ISV). Poiché non dispongono delle credenziali di amministratore di RMS, questi utenti non possono usare il cmdlet Get-AardrmUsageLog per scaricare i log di RMS. Per eseguire questa operazione, devono invece usare Windows Storage SDK o, in alternativa, possono scrivere un'applicazione per leggere i log direttamente da Archiviazione di Azure.

Se l'account di archiviazione è riservato ai log di RMS, la condivisione del nome e della chiave di accesso è sicura. Infatti, anche se altri utenti dispongono della chiave di accesso dell'amministratore, questi non possono usare tale chiave per accedere ad altri account di archiviazione o per usare l'account tenant di RMS.

## <a name="BKMK_Interpret"></a>Come interpretare i log sulle modalità di utilizzo di Azure Rights Management
Usare le informazioni seguenti come riferimento per interpretare i log sulle modalità di utilizzo di Azure Rights Management.

### Layout dell'account di archiviazione
Alla prima scrittura dei log nell'account di archiviazione, Azure Rights Management crea i due contenitori seguenti.

-   **Rms-metadata**: questo contenitore è riservato ad Azure Rights Management e non deve essere modificato o eliminato.

-   **Rms-logs-&lt;guid&gt;**: questo è il contenitore in cui Azure Rights Management crea e salva i log. Se non si desidera più conservare le informazioni registrate, è possibile eliminare senza problemi qualsiasi file presente in questo contenitore.

Nel corso del tempo, è possibile che Azure Rights Management crei contenitori **Rms-logs-&lt;guid&gt;** aggiuntivi. Se, ad esempio, il contenitore **Rms-metadata** risulta danneggiato o viene accidentalmente eliminato, Azure Rights Management ne reimposta il contenuto e crea un nuovo contenitore **Rms-logs-&lt;guid&gt;** per tutti i futuri log. I log presenti nel vecchio contenitore non vengono eliminati ma resi orfani.

### Sequenza dei log
Azure Rights Management scrive i log sotto forma di una serie di BLOB, ciascuno dei quali contiene uno o più record di log in formato W3C esteso.

Il nome di ciascun blob è un numero. All'interno di ciascun contenitore di log il primo BLOB è denominato 000000001 e i seguenti vengono denominati in sequenza in base all'ordine di creazione. Ciascun blob contiene uno o più record di log. A ciascun record di log è associato un timestamp UTC che indica il momento in cui Azure Rights Management ha gestito la richiesta corrispondente.

> [!IMPORTANT]
> Il sistema di registrazione di Azure Rights Management è ottimizzato per generare i log in modo rapido piuttosto che in stretto ordine sequenziale. È quindi possibile che l'ordine dei blob, così come quello dei record di log all'interno di un blob, non segua la sequenza cronologica. L'unico motivo per cui i blob sono denominati in sequenza è consentire all'utente di scaricarli facilmente in modo incrementale.
> 
> Di seguito sono riportati due esempi di potenziali risultati di sequenze di log:
> 
> -   I record di log presenti nel BLOB 000000004 potrebbero sovrapporsi cronologicamente a quelli presenti nel BLOB 000000003. In un caso estremo, tutti i record di log presenti nel BLOB 000000004 potrebbero essere stati generati prima di tutti quelli presenti nel BLOB 000000003.
> -   È possibile che il primo record di log presente in un blob sia stato generato dopo il secondo, ma che l'archiviazione sia stata eseguita in ordine inverso.

Prima di analizzare i log sulle modalità di utilizzo di Azure Rights Management, si consiglia di scaricarli e importarli in un archivio in cui sia possibile ordinarli in base al relativo timestamp. Per altre informazioni sul download dei log, vedere la sezione [Come accedere e usare i log sulle modalità di utilizzo di Azure Rights Management](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs) di questo argomento.

Anche se i log non sono necessariamente in ordine cronologico, la maggior parte di essi viene registrata entro 15 minuti dalla richiesta. Per questo motivo, quando si identificano i log desiderati usando il relativo timestamp, si consiglia di aggiungere 15 minuti all'ora a cui si è interessati e di procedere quindi al download. Grazie a questa strategia, vengono scaricati praticamente tutti i log.

Un altro elemento da tenere in considerazione è che il timestamp associato a ciascun record di log indica l'ora locale del server Azure Rights Management che ha elaborato la richiesta. Poiché Azure Rights Management viene eseguito su più server in diversi data center, in alcuni casi i log possono sembrare fuori sequenza, anche se sono stati ordinati in base al relativo timestamp. Lo sfasamento è tuttavia minimo, in genere inferiore al minuto, e nella maggior parte dei casi non crea problemi per l'analisi dei log.

### Formato dei blob
Ciascun blob è scritto in formato di log W3C esteso ed inizia con le due righe seguenti:

**#Software: RMS**

**#Version: 1.1**

La prima riga indica che si tratta di log di Azure Rights Management, mentre la seconda indica che il resto del BLOB segue la specifica della versione 1.1. È importante che le applicazioni che analizzano questi log verifichino queste due righe prima di procedere con l'analisi della restante parte del blob.

La terza riga è costituita da un elenco di nomi separati da caratteri di tabulazione:

**#Fields: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip**

Ciascuna delle righe seguenti è un record di log. I valori dei campi seguono lo stesso ordine della riga precedente e sono separati da caratteri di tabulazione. La tabella riportata di seguito consente di interpretare i campi.

|Nome campo|Tipo di dati W3C|Descrizione|Valore di esempio|
|--------------|--------------------|---------------|---------------------|
|date|Date|La data UTC in cui è stata gestita la richiesta.<br /><br />L'origine è l'orologio locale del server che ha gestito la richiesta.|25-06-2013|
|time|Ora|L'ora in cui è stata gestita la richiesta, in formato UTC 24 ore.<br /><br />L'origine è l'orologio locale del server che ha gestito la richiesta.|21.59.28|
|row-id|Testo|Il GUID univoco del record di log.<br /><br />Questo valore è utile quando i log vengono aggregati o copiati in un altro formato.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|request-type|Nome|Il nome dell'API RMS richiesta.|AcquireLicense|
|user-id|String|L'utente che ha effettuato la richiesta.<br /><br />Questo valore è riportato tra virgolette singole. Alcuni tipi di richiesta sono anonimi, e in questo caso il valore è ”.|‘joe@contoso.com’|
|result|String|La stringa ‘Success’ indica che la richiesta è stata eseguita con esito positivo.<br /><br />Se la richiesta ha avuto esito negativo, il tipo di errore viene riportato tra virgolette singole.|‘Success’|
|correlation-id|Testo|GUID comune tra il log del client e il log del server RMS per una determinata richiesta.<br /><br />Questo valore può essere utile per la risoluzione dei problemi del client.|cab52088-8925-4371-be34-4b71a3112356|
|content-id|Testo|GUID, riportato tra parentesi graffe, che identifica il contenuto protetto, ad esempio un documento.<br /><br />In questo campo è presente un valore solo se la richiesta è di tipo AcquireLicense. Per tutti gli altri tipi di richiesta il campo è vuoto.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|owner-email|String|Indirizzo di posta elettronica del proprietario del documento.|alice@contoso.com|
|issuer|String|Indirizzo di posta elettronica del soggetto emittente il documento.|alice@contoso.com (o) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|Template-id|String|ID del modello usato per proteggere il documento.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|File-name|String|Nome del documento protetto.|TopSecretDocument.docx|
|Date-published|Date|Data in cui è stato protetto il documento.|2015-10-15T21:37:00|
|c-info|String|Informazioni sulla piattaforma client che effettua la richiesta.<br /><br />La stringa specifica varia a seconda dell'applicazione (ad esempio, il sistema operativo o il browser).|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|c-ip|Address|L'indirizzo IP del client che effettua la richiesta.|64.51.202.144|

#### Eccezioni per il campo user-id
Anche se nel campo user-id è in genere riportato il nome dell'utente che ha effettuato la richiesta, esistono due eccezioni in cui il valore del campo non indica un utente reale:

-   Viene visualizzato il valore **'microsoftrmsonline@&lt;YourTenantID&gt;.rms.&lt;region&gt;.aadrm.com'**.

    Questo valore indica che la richiesta viene effettuata da un servizio di Office 365, ad esempio Exchange Online o SharePoint Online. Nella stringa, *&lt;YourTenantID&gt;* indica il GUID del tenant e *&lt;region&gt;* l'area in cui il tenant è registrato. Ad esempio, **na** indica l'America del Nord, **eu** l'Europa e **ap** l'Asia.

-   Si sta usando il connettore RMS.

    Le richieste provenienti da questo connettore vengono registrate con il nome dell'entità servizio generato automaticamente da RMS quando si installa il connettore RMS.

#### Tipi di richiesta tipici
Azure Rights Management supporta diversi tipi di richiesta. La tabella seguente elenca i tipi di richiesta più comuni.

|Tipo di richiesta|Descrizione|
|---------------------|---------------|
|AcquireLicense|Un client da un computer basato su Windows richiede una licenza per contenuto protetto con RMS.|
|AcquirePreLicense|Un client richiede una licenza per contenuto protetto con RMS per conto dell'utente.|
|AcquireTemplates|È stata eseguita una chiamata per acquisire modelli in base agli ID modello.|
|AcquireTemplateInformation|È stata eseguita una chiamata per ottenere gli ID del modello dal servizio.|
|AddTemplate|Viene eseguita una chiamata dal portale di Azure classico per aggiungere un modello.|
|BECreateEndUserLicenseV1|Viene eseguita una chiamata da un dispositivo mobile per creare un contratto di licenza con l'utente finale.|
|BEGetAllTemplatesV1|Viene eseguita una chiamata da un dispositivo mobile (back-end) per ottenere tutti i modelli.|
|Certify|Il client sta certificando la protezione del contenuto.|
|Decrypt|Il client tenta di decrittografare il contenuto protetto con RMS.|
|DeleteTemplateById|Viene eseguita una chiamata dal portale di Azure classico per eliminare un modello in base a un ID modello.|
|ExportTemplateById|Viene eseguita una chiamata dal portale di Azure classico per esportare un modello in base a un ID modello.|
|FECreateEndUserLicenseV1|Richiesta analoga ad AcquireLicense, ma inviata da dispositivi mobili.|
|FECreatePublishingLicenseV1|Questa richiesta corrisponde a una combinazione di Certify e GetClientLicensorCert ed è inviata da client mobili.|
|FEGetAllTemplates|Viene eseguita una chiamata da un dispositivo mobile (front-end) per ottenere i modelli.|
|GetAllTemplates|Viene eseguita una chiamata dal portale di Azure classico per ottenere tutti i modelli.|
|GetClientLicensorCert|Il client richiede un certificato di distribuzione, da usare in un secondo tempo per proteggere i contenuti, da un computer basato su Windows.|
|GetConfiguration|Un cmdlet di PowerShell Azure viene chiamato per ottenere la configurazione del tenant di Azure RMS.|
|GetConnectorAuthorizations|Viene eseguita una chiamata dai connettori RMS per ottenere la rispettiva configurazione dal cloud.|
|GetTenantFunctionalState|Il portale di Azure classico controlla se Azure RMS è attivato.|
|GetTemplateById|Viene eseguita una chiamata dal portale di Azure classico per ottenere un modello specificando un ID modello.|
|ExportTemplateById|Viene eseguita una chiamata dal portale di Azure classico per esportare un modello specificando un ID modello.|
|FindServiceLocationsForUser|Viene eseguita una chiamata per effettuare una query di URL, che consente di chiamare la richiesta Certify o AcquireLicense.|
|ImportTemplate|Viene eseguita una chiamata dal portale di Azure classico per importare un modello.|
|ServerCertify|Viene eseguita una chiamata da un client abilitato per RMS, come SharePoint, per certificare il server.|
|SetUsageLogFeatureState|Viene eseguita una chiamata per abilitare la funzionalità di registrazione delle modalità di utilizzo.|
|SetUsageLogStorageAccount|Viene eseguita una chiamata per specificare il percorso dei log di Azure RMS.|
|SignDigest|Viene eseguita una chiamata quando una chiave viene usata a scopo di firma. In genere, viene eseguita una chiamata per ogni richiesta AcquireLicence (o FECreateEndUserLicenseV1), Certify e GetClientLicensorCert (o FECreatePublishingLicenseV1).|
|UpdateTemplate|Viene eseguita una chiamata dal portale di Azure classico per aggiornare un modello esistente.|

## <a name="BKMK_PowerShell"></a>Riferimenti Windows PowerShell
Usare i cmdlet di Windows PowerShell seguenti per configurare e usare la funzionalità di registrazione delle modalità di utilizzo di Azure Rights Management:

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Per altre informazioni sull'uso di Windows PowerShell per Azure Rights Management, vedere [Amministrazione di Rights Management di Windows Azure mediante Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Vedere anche
[Uso di Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

