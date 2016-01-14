---
description: na
keywords: na
title: Protect a file that you share by email by using the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c1cd1d3-78dd-4f90-8b37-dcc9205a6736
---
# Proteggere un file che si condivide tramite e-mail utilizzando l&#39;applicazione di condivisione Rights Management
Quando si protegge un file che si condivide tramite posta elettronica, si crea una nuova versione del file originale. Il file originale rimane non protetto e la nuova versione è protetta e automaticamente collegata a un messaggio di posta elettronica che si invia in seguito.

In alcuni casi (per i file creati da Microsoft Word, Excel e PowerPoint), l'applicazione di condivisione RMS crea due versioni del file che collega al messaggio di posta elettronica. La seconda versione del file è un’estensione di file **.ppdf** ed è una copia shadow PDF del file. Questa versione del file garantisce che i destinatari possano leggere sempre il file, anche se non dispongono della stessa applicazione installata che è stata utilizzata per crearlo. Questo accade spesso quando gli utenti leggono la posta elettronica su dispositivi mobili e desiderano visualizzare gli allegati di posta elettronica. Ciò che serve per aprire il file è l'applicazione di condivisione RMS. Poi, è possibile leggere il file allegato, ma non sarà possibile modificarlo fino a quando non sarà stata aperta l'altra versione del file utilizzando un'applicazione che supporta RMS.

Se l'organizzazione utilizza Azure RMS, è possibile tenere traccia dei file che protetti tramite la condivisione:

-   Selezionare un'opzione per ricevere messaggi di posta elettronica quando qualcuno tenta di aprire tali allegati protetti. Ogni volta che si accede al file, si riceverà una notifica su chi ha tentato di aprire il file e quando, e se ha avuto esito positivo (se viene autenticato correttamente) o meno.

-   Utilizzare il sito di rilevamento della documentazione. È anche possibile interrompere la condivisione del file, revocando l’accesso ad esso nel sito di rilevamento dei documenti. Per altre informazioni, vedere [Rilevare e revocare i documenti quando si utilizza l'applicazione di condivisione RMS](../Topic/Track_and_revoke_your_documents_when_you_use_the_RMS_sharing_application.md).

## Utilizzo di Outlook: Proteggere un file da condividere tramite posta elettronica

1.  Creare il messaggio di posta elettronica e allegare il file. Quindi, nella scheda **Messaggio**, nel gruppo **RMS**, fare clic su **Condividi file protetto** e quindi fare nuovamente clic su **Condividi file protetto**:

    ![](../Image/ADRMS_MSRMSApp_SP_OutlookToolbar.png)

    Se non viene visualizzato il pulsante, è probabile che l'applicazione di RMS sharing non sia installata nel computer, che non sia installata l’ultima versione o che il computer debba essere riavviato per completare l'installazione. Per ulteriori informazioni su come installare l'applicazione di sharing, vedere [Scaricare e installare l’applicazione di condivisione Rights Management](../Topic/Download_and_install_the_Rights_Management_sharing_application.md).

2.  Specificare le opzioni desiderate per questo file nella [finestra di dialogo condivisione protetta](http://technet.microsoft.com/library/dn574738.aspx), quindi fare clic su **Invia ora**.

### Altri modi per proteggere un file da condividere tramite posta elettronica
Oltre a condividere un file protetto utilizzando Outlook, è inoltre possibile utilizzare queste alternative:

-   Da Esplora File: Questo metodo funziona per tutti i file.

-   Da un'applicazione di Office: Questo metodo funziona per le applicazioni supportate dall'applicazione di condivisione RMS utilizzando il componente aggiuntivo di Office in modo da visualizzare il gruppo **RMS** sulla barra multifunzione.

##### Utilizzando Esplora File o un'applicazione di Office: Proteggere un file da condividere tramite posta elettronica

1.  Usare una delle seguenti opzioni:

    -   Per Esplora File: Fare click con il destro sul file, selezionare **Protezione con RMS**, quindi selezionare **Condivisione protetta**:

        ![](../Image/ADRMS_MSRMSApp_ShareProtectedMenu.png)

    -   Per le applicazioni di Office, Word, Excel e PowerPoint: Assicurarsi che il file sia stato salvato prima. Poi, nella scheda **Home**, nel gruppo **RMS**, fare clic su **Condividi file protetto** e quindi fare di nuovo clic su **Condividi file protetto**:

        ![](../Image/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

    Se non vengono visualizzate queste opzioni per la protezione, è probabile che l'applicazione di applicazione RMS non sia installata nel computer o che il computer debba essere riavviato per completare l'installazione. Per ulteriori informazioni su come installare l'applicazione di sharing, vedere [Scaricare e installare l’applicazione di condivisione Rights Management](../Topic/Download_and_install_the_Rights_Management_sharing_application.md).

2.  Specificare le opzioni desiderate per questo file nella [finestra di dialogo condivisione protetta](http://technet.microsoft.com/library/dn574738.aspx), poi fare clic su **Invia**.

3.  È possibile visualizzare rapidamente una finestra di dialogo che indica che il file è protetto, poi viene visualizzato un messaggio di posta elettronica creato per indicare ai destinatari che gli allegati sono protetti con Microsoft RMS e che si deve accedere. Quando si fa clic sul collegamento per l'accesso, vengono visualizzate le istruzioni e i collegamenti per garantire che possano aprire l'allegato protetto.

    Esempio:

    ![](../Image/ADRMS_MSRMSApp_EmailMessage.PNG)

    Per sapere...: [Che cos'è il file .ppdf che viene creato automaticamente?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)

4.  Facoltativo: È possibile modificare qualsiasi elemento che si desidera nel messaggio di posta elettronica. Ad esempio, è possibile aggiungere o modificare l'oggetto o il testo del messaggio.

    > [!WARNING]
    > Sebbene sia possibile aggiungere o rimuovere utenti dal messaggio di posta elettronica, ciò non modifica le autorizzazioni per l'allegato specificato nella finestra di dialogo **condivisione protetta**. Se si desidera modificare le autorizzazioni, ad esempio, concedere a un nuovo utente le autorizzazioni per aprire il file, chiudere il messaggio di posta elettronica senza salvarlo o inviarlo, e tornare al passaggio 1.

5.  Inviare il messaggio di posta elettronica.

## Esempi e altre istruzioni
Per esempi di come è possibile utilizzare l'applicazione di condivisione Rights Management e procedure, vedere le sezioni seguenti della Guida dell’utente dell’applicazione di condivisione Rights Management:

-   [Esempi per l'utilizzo dell’applicazione di condivisione RMS](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Come procedere](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Vedere anche
[Guida dell'utente dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md)

