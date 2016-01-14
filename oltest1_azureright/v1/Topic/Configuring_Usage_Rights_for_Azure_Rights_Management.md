---
description: na
keywords: na
title: Configuring Usage Rights for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
---
# Configurazione dei diritti di utilizzo per Azure Rights Management
Quando si imposta la protezione su file o messaggi di posta elettronica mediante Azure Rights Management (Azure RMS) e non si usa un modello, è necessario configurare personalmente i diritti di utilizzo. Inoltre, quando si configurano modelli personalizzati per Azure RMS, si selezionano i diritti di utilizzo che verranno applicati automaticamente quando utenti, amministratori o servizi configurati selezionano il modello. Ad esempio, nel portale di Azure classico è possibile selezionare ruoli che configurano un raggruppamento logico di diritti di utilizzo oppure è possibile configurare singoli diritti.

Le informazioni incluse in questo argomento consentono di configurare i diritti di utilizzo desiderati per l'applicazione in uso e comprendere come tali diritti vengono interpretati dalle applicazioni.

## Diritti di utilizzo e relative descrizioni
Nella tabella seguente sono elencati e descritti i diritti d'uso supportati da supporta Rights Management e come vengono utilizzati e interpretati. In questa tabella il **Nome comune** è in genere come potrebbero essere visualizzati o indicati come riferimento i diritti d’uso, come una versione più semplice del valore a parola singola che viene utilizzato nel codice (il valore **Encoding in policy**). La **Costante o valore API** è il nome dell’SDK per una chiamata API MSIPC, utilizzato quando si scrive un'applicazione abilitata per RMS che controlla un diritto d’uso o aggiunge un diritto d’uso a un criterio.

|Nome comune|Codifica nei criteri|Descrizione|Implementazione nei diritti personalizzati di Office|Nome nel portale di Azure classico|Nome nei modelli AD RMS|Costante o valore API|Informazioni aggiuntive|
|---------------|------------------------|---------------|--------------------------------------------------------|--------------------------------------|---------------------------|-------------------------|---------------------------|
|Modifica contenuto, Modifica|DOCEDIT|Consente di modificare, riorganizzare, formattare o filtrare il contenuto all'interno dell'applicazione. Non concede il diritto di salvare la copia modificata.|Come parte delle opzioni **Modifica** e **Controllo completo**.|**Modifica contenuto**|**Modifica**|Non applicabile|Nelle applicazioni di Office questo diritto consente anche di salvare il documento.|
|Salva|EDIT|Consente di salvare il documento nella posizione corrente.|Come parte delle opzioni **Modifica** e **Controllo completo**.|**Salva file**|**Salva**|IPC_GENERIC_WRITEL"EDIT"|Nelle applicazioni di Office questo diritto consente anche di modificare il documento.|
|Commento|COMMENTO|Consente di aggiungere annotazioni o commenti al contenuto.|Non implementato|Non implementato|Non implementato|IPC_GENERIC_COMMENTL"COMMENT"|Questo diritto è disponibile nell’SDK, è disponibile come criterio ad hoc nel modulo di protezione RMS per Windows PowerShell ed è stato implementato in alcune applicazioni di fornitori di software. Tuttavia, non è ampiamente utilizzato e non è attualmente supportato dalle applicazioni di Office.|
|Salva con nome, Esporta|EXPORT|Abilita l'opzione per il salvataggio del contenuto con un nome file differente (Salva con nome). A seconda dell'applicazione, il file potrebbe essere salvato senza protezione.|Come parte delle opzioni **Modifica** e **Controllo completo**.|**Esporta contenuto (Salva con nome)**|**Esporta (Salva con nome)**|IPC_GENERIC_EXPORTL"EXPORT"|Consente di eseguire anche altre opzioni di esportazione nelle applicazioni, ad esempio **Invia a OneNote**.|
|Inoltra|FORWARD|Abilita l'opzione per l'inoltro di un messaggio di posta elettronica e per l'aggiunta di destinatari nelle righe **A** e **Cc**.|Negato quando si usa il criterio standard **Non inoltrare**.|**Inoltra**|**Inoltra**|IPC_EMAIL_FORWARDL"FORWARD"|Non consente al server d'inoltro di concedere diritti ad altri utenti come parte dell'azione di inoltro.|
|Controllo completo|OWNER|Concede tutti i diritti al documento. È possibile eseguire tutte le azioni disponibili.|Come l'opzione personalizzata **Controllo completo**.|**Controllo completo**|**Controllo completo**|IPC_GENERIC_ALLL"OWNER"|Include la possibilità di rimuovere la protezione.|
|Stampa|PRINT|Abilita le opzioni per la stampa del contenuto.|Come l’opzione **Stampa contenuto**  nelle autorizzazioni personalizzate. Non è un'impostazione per ogni destinatario.|**Stampa**|**Stampa**|IPC_GENERIC_PRINTL"PRINT|Nessuna informazione aggiuntiva|
|Rispondi|REPLY|Abilita l'opzione Rispondi in un client di posta elettronica. Non sono consentite modifiche delle righe **A** o **Cc**.|Non applicabile|**Rispondi**|**Rispondi**|IPC_EMAIL_REPLY|Nessuna informazione aggiuntiva|
|Rispondi a tutti|REPLYALL|Abilita l'opzione **Rispondi a tutti** in un client di posta elettronica, ma non consente di aggiungere destinatari nelle righe **A** o **Cc**.|Non applicabile|**Rispondi a tutti**|**Rispondi a tutti**|IPC_EMAIL_REPLYALLL"REPLYALL"|Nessuna informazione aggiuntiva|
|Visualizza, Apri, Leggi|VIEW|Consente all’utente di aprire il documento e visualizzarne il contenuto.|Come l'opzione **Visualizza** del criterio personalizzato **Leggi**.|**Visualizza contenuto**|**Visualizza**|IPC_GENERIC_READL"VIEW"|Nessuna informazione aggiuntiva|
|Copia|EXTRACT|Abilita le opzioni per la copia dei dati nello stesso documento o in un altro.|Come l'opzione del criterio personalizzato **Consenti agli utenti con accesso in lettura di copiare il contenuto**.|**Copia ed estrai contenuto**|**Estrai**|IPC_GENERIC_EXTRACTL"EXTRACT"|In alcune applicazioni consente anche di salvare l'intero documento in un formato non protetto.|
|Visualizza diritti|VIEWRIGHTSDATA|Consente all’utente di visualizzare i criteri applicati al documento.|Non implementato|**Visualizza diritti assegnati**|**Visualizza diritti**|IPC_READ_RIGHTSL"VIEWRIGHTSDATA"|Ignorato da alcune applicazioni.|
|Modifica diritti|EDITRIGHTSDATA|Consente all'utente di modificare il criterio applicato al documento. Include la rimozione della protezione.|Non implementato|**Modifica diritti**|**Modifica diritti**|IPC_WRITE_RIGHTSL"EDITRIGHTSDATA"|Nessuna informazione aggiuntiva|
|Consenti macro|OBJMODEL|Abilita l'opzione per l'esecuzione di macro o per l'accesso, a livello di programmazione o in remoto, al contenuto di un documento.|Come l'opzione del criterio personalizzato **Consenti accesso a livello di programmazione**. Non è un'impostazione per ogni destinatario.|**Consenti macro**|**Consenti macro**|Non applicabile|Nessuna informazione aggiuntiva|

## Diritti inclusi nei livelli di autorizzazioni
Alcune applicazioni raggruppano i diritti di utilizzo in livelli di autorizzazioni, per semplificare la selezione dei diritti di utilizzo che in genere vengono usati insieme. Questi livelli di autorizzazioni consentono di astrarre un livello di complessità dagli utenti, in modo che questi possano scegliere opzioni che sono basate sul ruolo.  Ad esempio, **Revisore** e **Coautore**. Anche se queste opzioni spesso mostrano agli utenti un riepilogo dei diritti, potrebbero non includere tutti i diritti elencati nella tabella precedente.

Usare la tabella seguente per un elenco di questi livelli di autorizzazioni e un elenco completo dei diritti che contengono.

|Livello di autorizzazioni|Applicazioni|Diritti inclusi (nome comune)|
|-----------------------------|----------------|---------------------------------|
|Visualizzatore|Portale di Azure classico<br /><br />Applicazione di condivisione Rights Management per Windows|Visualizza, Apri, Leggi<br /><br />Rispondi<br /><br />Rispondi a tutti|
|Revisore|Portale di Azure classico<br /><br />Applicazione di condivisione Rights Management per Windows|Visualizza, Apri, Leggi<br /><br />Salva<br /><br />Modifica contenuto, Modifica<br /><br />Rispondi<sup>*</sup><br /><br />Rispondi a tutti<sup>*</sup><br /><br />Inoltra<sup>*</sup>|
|Coautore|Portale di Azure classico<br /><br />Applicazione di condivisione Rights Management per Windows|Visualizza, Apri, Leggi<br /><br />Salva<br /><br />Modifica contenuto, Modifica<br /><br />Copia<br /><br />Visualizza diritti<br /><br />Modifica diritti<br /><br />Consenti macro<br /><br />Salva con nome, Esporta<br /><br />Stampa<br /><br />Rispondi<sup>*</sup><br /><br />Rispondi a tutti<sup>*</sup><br /><br />Inoltra<sup>*</sup>|
|Comproprietario|Portale di Azure classico<br /><br />Applicazione di condivisione Rights Management per Windows|Visualizza, Apri, Leggi<br /><br />Salva<br /><br />Modifica contenuto, Modifica<br /><br />Copia<br /><br />Visualizza diritti<br /><br />Modifica diritti<br /><br />Consenti macro<br /><br />Salva con nome, Esporta<br /><br />Stampa<br /><br />Rispondi<sup>*</sup><br /><br />Rispondi a tutti<sup>*</sup><br /><br />Inoltra<sup>*</sup><br /><br />Controllo completo|
<sup>*</sup> Non applicabile per l'applicazione di condivisione Microsoft Rights Management per Windows

## Diritti inclusi nei modelli predefiniti
I diritti inclusi con i modelli predefiniti sono i seguenti:

|Nome visualizzato|Diritti inclusi (nome comune)|
|---------------------|---------------------------------|
|&lt;nome organizzazione&gt; - Solo visualizzazione riservata|Visualizza, Apri, Leggi|
|&lt;nome organizzazione&gt; - Riservato|Visualizza, Apri, Leggi<br /><br />Salva<br /><br />Modifica contenuto, Modifica<br /><br />Visualizza diritti<br /><br />Consenti macro<br /><br />Inoltra<br /><br />Rispondi<br /><br />Rispondi a tutti|

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

