---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# Operazioni relative alla chiave del tenant di Azure Rights Management
A seconda della topologia di chiave del tenant (gestita da Microsoft o dal cliente), i livelli di controllo e di responsabilità per la chiave del tenant di Rights Management di Microsoft Azure (Azure RMS) dopo l'implementazione sono diversi.

Uno scenario in cui l'utente gestisce la propria chiave è denominato scenario BYOK (Bring Your Own Key). Per altre informazioni su questo scenario e sul modo in cui effettuare una scelta tra le due topologie di chiave del tenant, vedere [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

Nella tabella seguente vengono indicate le operazioni che è possibile eseguire a seconda della topologia di chiave del tenant di Azure RMS scelta.

|Operazione del ciclo di vita|Gestione di Microsoft (impostazione predefinita)|Gestione del cliente (scenario BYOK)|
|--------------------------------|----------------------------------------------------|----------------------------------------|
|Revocare la chiave del tenant|No (automatica)|No (automatica)|
|Ridistribuire la chiave del tenant|Sì|Sì|
|Eseguire il backup e il ripristino della chiave del tenant|No|Sì|
|Esportare la chiave del tenant|Sì|No|
|Rispondere a una violazione di sicurezza|Sì|Sì|
Dopo aver identificato la topologia implementata, leggere una delle sezioni seguenti per ottenere altre informazioni su queste operazioni per la chiave del tenant di Azure RMS.

## <a name="BKMK_MSManagedOperations"></a>Gestione di Microsoft: operazioni del ciclo di vita della chiave del tenant
Se Microsoft gestisce la chiave del tenant per Azure Rights Management (impostazione predefinita), usare le sezioni seguenti per ottenere altre informazioni sulle operazioni del ciclo di vita rilevanti per questa topologia:

-   [Revocare la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [Ridistribuire la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [Eseguire il backup e il ripristino della chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [Esportare la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [Rispondere a una violazione di sicurezza](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>Revocare la chiave del tenant
Quando si annulla la sottoscrizione di Azure RMS, l'uso della chiave del tenant in Azure RMS viene interrotto e non è necessaria alcuna azione da parte dell'utente.

### <a name="BKMK_MSRekey"></a>Ridistribuire la chiave del tenant
Il processo di ridistribuzione della chiave è denominato anche rollover della chiave. Non ridistribuire la chiave tenant a meno che non sia effettivamente necessario. Alcuni client precedenti, ad esempio Office 2010, non erano progettati per gestire in modo efficiente le modifiche delle chiavi. In questo scenario è necessario cancellare lo stato di RMS nei computer tramite Criteri di gruppo o un meccanismo equivalente. In alcuni casi è tuttavia opportuno forzare la ridistribuzione della chiave del tenant, Ad esempio:

-   La società è stata divisa in due o più società. Quando si ridistribuisce la chiave del tenant, la nuova società non potrà accedere al nuovo contenuto pubblicato dai dipendenti e sarà in grado di accedere al vecchio contenuto se dispone di una copia della chiave del tenant precedente.

-   Eventuale violazione della copia master della chiave del tenant (copia in proprio possesso).

Per ridistribuire la chiave del tenant, chiamare il Servizio Supporto Tecnico Clienti Microsoft fornendo prova del proprio ruolo di amministratore di tenant.

Quando si ridistribuisce la chiave del tenant, il nuovo contenuto è protetto tramite la nuova chiave. Poiché questo processo viene eseguito per fasi, per un certo periodo di tempo parte del nuovo contenuto continuerà a essere protetto tramite la chiave del tenant precedente. Il contenuto protetto in precedenza rimane tale rispetto alla chiave del tenant precedente. Per supportare questo scenario, Azure RMS mantiene la chiave del tenant precedente in modo da emettere licenze per il vecchio contenuto.

### <a name="BKMK_MSBackup"></a>Eseguire il backup e il ripristino della chiave del tenant
Microsoft è responsabile delle operazioni di backup della chiave del tenant e non è necessaria alcuna azione da parte dell'utente.

### <a name="BKMK_MSExport"></a>Esportare la chiave del tenant
Per esportare la configurazione di Azure RMS e la chiave del tenant, seguire le istruzioni descritte nei tre passaggi seguenti.

##### Passaggio 1: Avviare l'esportazione

-   A tale scopo, contattare il Servizio Supporto Tecnico Clienti Microsoft. È necessario provare di essere un amministratore di tenant di Azure RMS.

##### Passaggio 2: Attendere la verifica

-   Microsoft verifica che la richiesta di rilasciare la chiave del tenant RMS sia legittima. L'operazione può richiedere fino a 3 settimane.

##### Passaggio 3: Ricevere istruzioni sulla chiave dal Servizio Supporto Tecnico Clienti Microsoft

-   Il Servizio Supporto Tecnico Clienti Microsoft invierà una configurazione di Azure RMS e una chiave del tenant crittografata in un file protetto da password con estensione tpd. A tale scopo, il Servizio Supporto Tecnico Clienti Microsoft invia all'utente che ha avviato l'esportazione un messaggio di posta elettronica in cui è disponibile uno strumento da eseguire da un prompt dei comandi nel modo seguente:

    ```
    AadrmTpd.exe -createkey
    ```
    In questo modo viene generata una coppia di chiavi RSA e le parti pubblica e privata vengono salvate come file nella cartella corrente. Ad esempio: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** e **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Rispondere al messaggio di posta elettronica ricevuto dal Servizio Supporto Tecnico Clienti Microsoft allegando il file con il nome che inizia con **PublicKey**. A questo punto il Servizio Supporto Tecnico Clienti Microsoft invierà all'utente un file TDP con estensione xml crittografato tramite la chiave RSA. Copiare questo file nella stessa cartella in cui è stato eseguito lo strumento AadrmTpd in origine ed eseguire nuovamente lo strumento, utilizzando il file che inizia con **PrivateKey** e il file da CSS. Ad esempio:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    L'output del comando deve essere costituito da due file, ovvero il file con estensione tpd protetto da password e un file che ne contiene la password. Per scopi di riferimento incrociato, a entrambi deve essere associato lo stesso GUID come file di chiave pubblica e privata utilizzati per l’esecuzione del comando AadrmTpd.exe -createkey:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Eseguire il backup di questi file e archiviarli in modo sicuro per garantire che sia possibile decrittografare contenuto protetto tramite la chiave del tenant specifica. Se inoltre si esegue la migrazione ad AD RMS, è possibile importare tale file con estensione tpd (il file che inizia con **ExportedTDP**) nel proprio server AD RMS.

##### Passaggio 4: In corso: Proteggere la chiave del tenant

-   Dopo aver ricevuto la chiave del tenant, tenerla in posizione sicura per evitare che utenti malintenzionati possano accedere e decrittografare tutti i documenti protetti dalla chiave.

    Se la chiave del tenant viene esportata perché non si desidera più usare Azure RMS, è consigliabile disattivare il tenant RMS. Non aspettare di effettuare questa operazione dopo aver ricevuto la chiave del tenant, in quanto questa precauzione consente di ridurre le conseguenze dovute all'accesso alla chiave del tenant da parte di utenti malintenzionati. Per istruzioni, vedere [Rimozione delle autorizzazioni e disattivazione di Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

### <a name="BKMK_MSBreach"></a>Rispondere a una violazione di sicurezza
Indipendentemente dall'affidabilità, nessun sistema di sicurezza può considerarsi completo se non prevede un processo di risposta alle violazioni di sicurezza. La chiave del tenant può essere violata o rubata e anche se è protetta in modo efficiente, potrebbero essere presenti vulnerabilità nella tecnologia dei moduli di protezione hardware di generazione corrente e nella lunghezza e negli algoritmi correlati alle chiavi correnti.

Microsoft ha predisposto un team apposito per rispondere agli eventi imprevisti correlati alla sicurezza che possono verificarsi nei suoi prodotti e servizi. Non appena riceve un report plausibile su un evento imprevisto, il team si attiva per esaminarne l'ambito, la causa radice e le soluzioni. Se l'evento imprevisto influisce sulle risorse dell'utente, Microsoft invierà un messaggio di posta elettronica di notifica agli amministratori di tenant di Azure RMS all'indirizzo indicato al momento della sottoscrizione.

In caso di violazione di sicurezza, l'azione più efficace che l'utente o Microsoft possa intraprendere dipende dall'ambito della violazione stessa. Microsoft collaborerà con l'utente durante l'intero processo. Nella tabella seguente vengono descritte alcune situazioni tipiche e la risposta più probabile, sebbene la risposta esatta dipenda da tutte le informazioni raccolte durante l'analisi.

|Descrizione evento imprevisto|Risposta probabile|
|---------------------------------|----------------------|
|Perdita della chiave del tenant.|Ridistribuire la chiave del tenant. Vedere la sezione [Ridistribuire la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey) in questo argomento.|
|Diritti di accesso alla chiave del tenant ottenuti da un utente non autorizzato o da malware, ma nessuna perdita della chiave.|La ridistribuzione della chiave del tenant non è sufficiente ed è necessaria un'analisi della causa radice. Se l'utente non autorizzato ha ottenuto l'accesso a causa di un bug del processo o del software, questo problema deve essere risolto.|
|Vulnerabilità scoperta nell'algoritmo RSA o nella lunghezza della chiave oppure attacchi di forza bruta diventati realizzabili a livello di calcolo.|Microsoft deve aggiornare Azure RMS per supportare nuovi algoritmi e lunghezze maggiori della chiave che siano resilienti e invitare tutti i clienti a rinnovare le proprie chiavi tenant.|

## <a name="BKMK_BYOKManagedOperations"></a>Gestione del cliente: operazioni del ciclo di vita della chiave del tenant
Se la gestione della chiave del tenant per Azure Rights Management viene effettuata dall'utente (scenario BYOK), usare le sezioni seguenti per ottenere altre informazioni sulle operazioni del ciclo di vita rilevanti per questa topologia:

-   [Revocare la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [Ridistribuire la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [Eseguire il backup e il ripristino della chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [Esportare la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [Rispondere a una violazione di sicurezza](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>Revocare la chiave del tenant
Quando si annulla la sottoscrizione di Azure RMS, l'uso della chiave del tenant in Azure RMS viene interrotto e non è necessaria alcuna azione da parte dell'utente.

### <a name="BKMK_BYOKRekey"></a>Ridistribuire la chiave del tenant
Il processo di ridistribuzione della chiave è denominato anche rollover della chiave. Non ridistribuire la chiave tenant a meno che non sia effettivamente necessario. Alcuni client precedenti, ad esempio Office 2010, non erano progettati per gestire in modo efficiente le modifiche delle chiavi. In questo scenario è necessario cancellare lo stato di RMS nei computer tramite Criteri di gruppo o un meccanismo equivalente. In alcuni casi è tuttavia opportuno forzare la ridistribuzione della chiave del tenant, Ad esempio:

-   La società è stata divisa in due o più società. Quando si ridistribuisce la chiave del tenant, la nuova società non potrà accedere al nuovo contenuto pubblicato dai dipendenti e sarà in grado di accedere al vecchio contenuto se dispone di una copia della chiave del tenant precedente.

-   Eventuale violazione della copia master della chiave del tenant (copia in proprio possesso).

Quando si ridistribuisce la chiave del tenant, il nuovo contenuto è protetto tramite la nuova chiave. Poiché questo processo viene eseguito per fasi, per un certo periodo di tempo parte del nuovo contenuto continuerà a essere protetto tramite la chiave del tenant precedente. Il contenuto protetto in precedenza rimane tale rispetto alla chiave del tenant precedente. Per supportare questo scenario, Azure RMS mantiene la chiave del tenant precedente in modo da emettere licenze per il vecchio contenuto.

Per reimpostare la chiave del tenant, generare e creare una nuova chiave tramite Internet o personalmente, usando le procedure descritte nella sezione [Implementazione della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

### <a name="BKMK_BYOKBackup"></a>Eseguire il backup e il ripristino della chiave del tenant
L'utente è responsabile del backup della chiave del tenant. Se la chiave del tenant è stata generata dall'utente in un modulo di protezione hardware Thales, per eseguire il backup della chiave è sufficiente eseguire il backup del file della chiave in formato token, del file relativo all'ambiente e delle schede amministrative.

Se la chiave è stata trasferita tramite le procedure descritte nella sezione [Implementazione della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK) dell'argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md), Azure RMS manterrà il file della chiave in formato token per protezione da eventuali errori dei nodi di Azure RMS. È tuttavia opportuno tenere presente che questa azione non rappresenta un backup completo. Se ad esempio è necessaria una copia in testo non crittografato della chiave da usare all'esterno di un modulo di protezione hardware Thales, Azure RMS non sarà in grado di recuperarla perché dispone solo di una copia non recuperabile.

### <a name="BKMK_BYOKExport"></a>Esportare la chiave del tenant
In uno scenario BYOK non è possibile esportare la chiave del tenant da Azure RMS. La copia presente in Azure RMS è non recuperabile. Per eliminare questa chiave in modo che non venga più usata, contattare il Servizio Supporto Tecnico Clienti Microsoft.

### <a name="BKMK_BYOKBreach"></a>Rispondere a una violazione di sicurezza
Indipendentemente dall'affidabilità, nessun sistema di sicurezza può considerarsi completo se non prevede un processo di risposta alle violazioni di sicurezza. La chiave del tenant può essere violata o rubata e anche se è protetta in modo efficiente, potrebbero essere presenti vulnerabilità nella tecnologia dei moduli di protezione hardware di generazione corrente e nella lunghezza e negli algoritmi correlati alle chiavi correnti.

Microsoft ha predisposto un team apposito per rispondere agli eventi imprevisti correlati alla sicurezza che possono verificarsi nei suoi prodotti e servizi. Non appena riceve un report plausibile su un evento imprevisto, il team si attiva per esaminarne l'ambito, la causa radice e le soluzioni. Se l'evento imprevisto influisce sulle risorse dell'utente, Microsoft invierà un messaggio di posta elettronica di notifica agli amministratori di tenant di Azure RMS all'indirizzo indicato al momento della sottoscrizione.

In caso di violazione di sicurezza, l'azione più efficace che l'utente o Microsoft possa intraprendere dipende dall'ambito della violazione stessa. Microsoft collaborerà con l'utente durante l'intero processo. Nella tabella seguente vengono descritte alcune situazioni tipiche e la risposta più probabile, sebbene la risposta esatta dipenda da tutte le informazioni raccolte durante l'analisi.

|Descrizione evento imprevisto|Risposta probabile|
|---------------------------------|----------------------|
|Perdita della chiave del tenant.|Ridistribuire la chiave del tenant. Vedere la sezione [Ridistribuire la chiave del tenant](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey) in questo argomento.|
|Diritti di accesso alla chiave del tenant ottenuti da un utente non autorizzato o da malware, ma nessuna perdita della chiave.|La ridistribuzione della chiave del tenant non è sufficiente ed è necessaria un'analisi della causa radice. Se l'utente non autorizzato ha ottenuto l'accesso a causa di un bug del processo o del software, questo problema deve essere risolto.|
|Vulnerabilità scoperta nella tecnologia del moduli di protezione hardware di generazione corrente.|Microsoft deve aggiornare i moduli di protezione hardware. Se si ritiene che la vulnerabilità abbia provocato l'esposizione di chiavi, Microsoft inviterà tutti i clienti a rinnovare le chiavi tenant.|
|Vulnerabilità scoperta nell'algoritmo RSA o nella lunghezza della chiave oppure attacchi di forza bruta diventati realizzabili a livello di calcolo.|Microsoft deve aggiornare Azure RMS per supportare nuovi algoritmi e lunghezze maggiori della chiave che siano resilienti e invitare tutti i clienti a rinnovare le proprie chiavi tenant.|

## Vedere anche
[Uso di Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

