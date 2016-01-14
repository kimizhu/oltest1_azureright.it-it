---
description: na
keywords: na
title: Dialog box options for the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
---
# Opzioni della finestra di dialogo per l’applicazione di condivisione Rights Management
Utilizzare queste informazioni per specificare le opzioni nella finestra di dialogo **Aggiungi protezione** o nella finestra di dialogo **Condividi file protetto** dell'applicazione di RMS sharing. Questa finestra di dialogo verrà visualizzata quando si [protegge un file da condividere](http://technet.microsoft.com/library/dn574735.aspx) oppure [protegge un file nella posizione](http://technet.microsoft.com/library/dn574733.aspx) e si scelgono autorizzazioni personalizzate.

> [!IMPORTANT]
> Se le opzioni visualizzate sono diverse da quelle documentate qui, probabilmente non è installata l'ultima versione dell’applicazione di condivisione. È possibile scaricare l'ultima versione dalla pagina di [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).
> 
> Come è possibile sapere se si dispone della versione più recente? Cercare **applicazione di condivisione Microsoft Rights Management** elencata in Programmi e funzionalità e verificare il numero di versione corrispondente. Per visualizzare e utilizzare le opzioni nella tabella, la versione deve essere almeno **1.0.1770.0**. È possibile verificare il numero di versione più recente dalla pagina di download.

Oltre alle opzioni che è possibile scegliere, è inoltre possibile chiedersi:

-   [Che cos'è il file .ppdf che viene creato automaticamente?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)

-   [Qual è la differenza tra protezione generica e protezione integrata (nativa)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative)

|Opzione|Descrizione|
|-----------|---------------|
|**UTENTI**|Se non è ancora stato specificato un indirizzo di posta elettronica di Outlook, digitare gli indirizzi di posta elettronica delle persone che si desidera siano in grado di aprire il file.<br /><br />Se l'organizzazione utilizza la versione locale di Rights Management (AD RMS), gli indirizzi di posta elettronica che è possibile specificare sono limitati alle persone all'interno dell'organizzazione. Quando si applica questo e si tenta di specificare indirizzi di posta elettronica esterni, verrà visualizzato un messaggio che indica che la configurazione aziendale consente la condivisione del contenuto protetto solo all'interno della società. Tuttavia, se l'organizzazione utilizza Azure RMS, questi indirizzi di posta elettronica possono essere forniti per le persone all'interno dell'organizzazione o per le persone in un'altra organizzazione.<br /><br />Ad esempio: janetm@contoso.com; p.dover@fabrikam.com|
|**Protezione generica**|Se questa opzione è selezionata, significa che il file selezionato non può essere protetto in modo nativo. Per altre informazioni, vedere la sezione [Qual è la differenza tra protezione generica e protezione integrata (nativa)?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_GenericNative) in questo argomento.|
|**Visualizzatore - Solo visualizzazione**<br /><br />**Revisore - Visualizzazione e modifica**<br /><br />**Co-autore - Visualizzazione, modifica, copia e stampa**<br /><br />**Comproprietario – Tutte le autorizzazioni** **Note:** Tutte queste opzioni hanno un'icona rotonda prima del nome, che rappresenta un globo mondiale. Questa icona viene utilizzata perché in genere si seleziona una di queste opzioni quando si invia l'allegato a un utente in un'altra organizzazione.|Se si desidera definire i diritti del documento protetto, selezionare una delle seguenti opzioni. Fare clic su ogni opzione per visualizzare una descrizione.<br /><br />Quando si sceglie una di queste opzioni, solo gli utenti specificate in **UTENTI** dispongono dei diritti specificati per aprire e utilizzare il documento. Ad esempio, se eseguono l’inoltro ad un altro utente, il documento non viene visualizzato.|
|Modelli di criteri configurati dall'amministratore.<br /><br />Ad esempio, se il nome della società è Contoso, Ltd: **Contoso, Ltd - Solo visione riservata** **Note:** Tutte queste opzioni hanno un'icona quadrata prima del nome, che rappresenta l’edificio di una sede. Questa icona viene utilizzata perché in genere si seleziona una di queste opzioni quando si invia l'allegato a un utente nell'organizzazione.|Quando si condivide un documento con le persone che lavorano per l'organizzazione, vengono visualizzati i modelli di criteri disponibili configurati dall'amministratore. Scegliere uno dei seguenti quando non è possibile condividere il documento all'esterno dell'organizzazione.<br /><br />Quando si sceglie una di queste opzioni, l'amministratore definisce i diritti del documento e chi può aprirlo.|
|**Scadenza dei documenti**|Selezionare questa opzione solo per i file per i quali i tempi sono importanti che gli utenti selezionati non devono essere in grado di aprire dopo una data specificata. Sarà comunque possibile aprire il file originale, ma dopo la mezzanotte (del fuso orario corrente) del giorno specificato, altri utenti non potranno aprire il file.<br /><br />Questa opzione non è disponibile se si seleziona un modello di criteri configurati dall'amministratore.|
|**Invia un messaggio di posta elettronica quando qualcuno tenta di aprire i documenti**|**Note:** Questa opzione è attualmente in anteprima.<br />Selezionare questa opzione se si desidera ricevere notifiche di posta elettronica ogni volta che un utente tenta di aprire il documento che si vuole proteggere. Il messaggio di posta elettronica indicherà chi ha tentato di aprire il file, quando e se l’operazione è stata eseguita.<br /><br />Questa opzione è disponibile solo se l'organizzazione utilizza Azure RMS. Se l'organizzazione utilizza la versione locale di Rights Management (AD RMS), questa opzione non verrà visualizzata.|
|**Consenti di revocare immediatamente l'accesso a questi documenti**|Scegliere questa opzione se potrebbe essere necessario revocare l'accesso ai documenti in un secondo momento utilizzando il sito di rilevamento dei documenti e la revoca deve avvenire immediatamente. Tuttavia, l’impostazione di questa opzione prevede che mentre il documento non è revocato, gli utenti richiedono sempre una connessione a Internet per leggere il documento, ogni volta che accedono ad esso. Potrebbero esistere alcuni scenari in cui gli utenti non possono connettere il proprio dispositivo a Internet e non sono in grado di leggere il documento nel modo previsto.<br /><br />Se non si sceglie questa opzione, è ancora possibile revocare i documenti in un secondo momento, utilizzando il sito di rilevamento dei documenti. Tuttavia, poiché gli utenti non richiedono sempre una connessione a Internet per leggere il documento, non sapranno immediatamente che il documento è revocato e potranno continuare a leggerlo fino all’autenticazione successiva con Azure RMS. Per impostazione predefinita, il numero massimo di giorni per cui qualcuno potrebbe continuare a leggere un documento protetto revocato è 30 giorni, ma un amministratore può modificare questo valore affinché sia minore o maggiore di 30 giorni.<br /><br />Questa opzione è disponibile solo se l'organizzazione utilizza Azure RMS. Se l'organizzazione utilizza la versione locale di Rights Management (AD RMS), questa opzione non verrà visualizzata.|

## <a name="BKMK_GenericNative"></a>Qual è la differenza tra protezione generica e protezione integrata (nativa)?

-   Quando si **protegge genericamente un file**, gli utenti non autorizzati non possono aprire il file. Dopo che gli utenti autorizzati hanno aperto il file, potrebbero inoltrarlo non protetto ad altre persone o salvarlo in un percorso a cui potrebbero accedere altri utenti. Tuttavia, essi visualizzano un messaggio che li informa delle autorizzazioni di cui dispongono per il file e viene richiesto loro di accettarle, ma non è possibile applicare questa protezione. Inoltre, quando si protegge in modo generico un file, non è possibile limitare le autorizzazioni in modo diverso dall’autorizzazione. Ad esempio non è possibile limitare il contenuto alla sola visualizzazione o senza consentire la stampa:

    > [!NOTE]
    > Un file protetto in modo generico ha sempre l'estensione **.pfile**.

-   In confronto, quando si utilizza la **protezione integrata (nativa)** di Rights Management con le applicazioni che la supportano (ad esempio, i file di Office), la protezione si applica al file anche se il file viene poi inviato a un altro utente o viene salvato in un altro percorso. Quando si proteggono i file, è possibile utilizzare autorizzazioni restrittive come sola lettura o l'autorizzazione per modificare, ma non stampare o copiare. Ad esempio, è possibile selezionare **Visualizzatore - Solo visualizzazione**, in modo che il contenuto non possa essere modificato, stampato o copiato.

Per informazioni tecniche aggiuntive, vedere la sezione [Livelli di protezione – nativo e generico](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection) in [Guida dell'amministratore dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md).

## <a name="BKMK_PPDF"></a>Che cos'è il file .ppdf che viene creato automaticamente?

-   Quando si condivide un file protetto tramite posta elettronica (condivisione protetta), l'applicazione di RMS sharing crea automaticamente una versione **.ppdf** del file di Word, Excel, PowerPoint o PDF. Questa è una versione protetta di sola lettura del file che possono aprire solo gli utenti autorizzati e assicura che i destinatari possano sempre leggere l'allegato, anche se utilizzano un dispositivo mobile che non dispone di un'applicazione che supporta in modo nativo Rights Management. Se queste persone hanno installato l’app RMS sharing, saranno in grado di leggere l'allegato.

    In questo scenario, a differenza di un file protetto in modo generico, la limitazione dell'utilizzo viene applicata. Il destinatario non sarà in grado di salvare questa versione del file e se inoltra l'allegato a un altro utente, le restrizioni originali rimangono con il documento. Solo gli utenti autorizzati per il documento protetto saranno in grado di aprirlo.

    > [!NOTE]
    > Un file .ppdf viene creato automaticamente quando si condivide con protezione (condivisione tramite posta elettronica), ma non viene creato quando si utilizza la protezione locale.

## Esempi e altre istruzioni
Per esempi di come è possibile utilizzare l'applicazione di condivisione Rights Management e procedure, vedere le sezioni seguenti della Guida dell’utente dell’applicazione di condivisione Rights Management:

-   [Esempi per l'utilizzo dell’applicazione di condivisione RMS](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Come procedere](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Vedere anche
[Guida dell'utente dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md)

