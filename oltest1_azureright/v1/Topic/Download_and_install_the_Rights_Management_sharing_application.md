---
description: na
keywords: na
title: Download and install the Rights Management sharing application
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
---
# Scaricare e installare l’applicazione di condivisione Rights Management
Non è necessario essere un amministratore locale per installare l'applicazione di condivisione RMS. Tuttavia, se non si ricopre questo ruolo e si usa Office 2010, sono previste alcune limitazioni. Per altre informazioni, vedere la sezione [Se non si è un amministratore locale e si usa Office 2010](#BKMK_SetupOffice2010) di questo argomento.

### Per scaricare e installare l’applicazione di condivisione Rights Management

1.  Visitare la pagina [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) nel sito Web Microsoft.

2.  Nella sezione **Computer** fare clic sull'icona relativa all’**app RMS per Windows** e salvare il file di installazione **Setup.exe** dell’applicazione di condivisione Microsoft Rights Management.

3.  Fare doppio clic sul file Setup.exe che è stato scaricato. Se viene richiesto di continuare, fare clic su **Sì**.

4.  Nella pagina **Installazione di Microsoft RMS** fare clic su **Avanti** e attendere la fine dell'installazione.

    > [!NOTE]
    > L'applicazione di condivisione RMS richiede il Framework Microsoft .NET, versione minima 4.0. Il programma di installazione verifica se viene installato e in caso contrario, verrà visualizzato un messaggio con un collegamento per installarlo.

5.  Al termine dell'installazione, fare clic su **Riavvia** per riavviare il computer e completare l'installazione. Fare clic su **Chiudi** e riavviare il computer in un secondo momento per completare l'installazione.

Ora è possibile iniziare a proteggere i file o a leggere quelli protetti da altri utenti.

## <a name="BKMK_SetupOffice2010"></a>Se non si è un amministratore locale e si usa Office 2010
Se si accede al computer senza diritti amministrativi locali e il programma di installazione rileva che nel sistema è installato Office 2010, verrà visualizzato un messaggio di avviso in cui si specifica che alcuni scenari non sono compatibili con questa configurazione. Questi scenari includono:

-   Se l'organizzazione usa Azure RMS anziché una versione locale di RMS:

    -   Non saranno disponibili le funzionalità Information Rights Management (IRM) di Office, come l'opzione **Non inoltrare** per i messaggi di posta elettronica e le autorizzazioni **Limita accesso** che è possibile impostare dal menu **File** di Word ed Excel. È possibile invece usare l'opzione di condivisione protetta disponibile sulla barra multifunzione e le opzioni del menu di scelta rapida di Esplora file.

-   Se l'organizzazione usa una versione locale di RMS anziché Azure RMS:

    -   Non sarà possibile leggere documenti protetti inviati da utenti appartenenti a un'altra organizzazione in cui viene usato Azure RMS.

Se non si è un amministratore locale ma si usa Office 365 o Office 2013, il messaggio non viene visualizzato e questi scenari sono supportati.

È possibile continuare l'installazione tenendo conto di queste limitazioni oppure è possibile interrompere l'installazione e scegliere di effettuarla di nuovo selezionando l'opzione **Esegui come amministratore** quando si esegue il file Setup.exe nel passaggio 3 o di affidarla a un amministratore. Gli amministratori possono infatti [generare lo script dell'installazione](https://technet.microsoft.com/library/dn339003.aspx) in modo che venga eseguita automaticamente.

## Esempi e altre istruzioni
Per esempi di come è possibile utilizzare l'applicazione di condivisione Rights Management e procedure, vedere le sezioni seguenti della Guida dell’utente dell’applicazione di condivisione Rights Management:

-   [Esempi per l'utilizzo dell’applicazione di condivisione RMS](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

-   [Come procedere](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## Vedere anche
[Guida dell'utente dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md)

