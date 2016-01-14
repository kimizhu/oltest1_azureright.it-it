---
description: na
keywords: na
title: Rights Management sharing application: Version release history
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
---
# Applicazione di condivisione Rights Management: Cronologia delle versioni
Il team di Rights Management aggiorna regolarmente l'applicazione di condivisione di condivisione Rights Management con correzioni e nuove funzionalità. Utilizzare le informazioni seguenti per visualizzare gli elementi nuovi o modificati in una versione. La versione più recente è elencata per prima.

Non sono elencate le versioni precedenti al 1 gennaio 2015.

> [!NOTE]
> Per commenti o domande sull'applicazione di RMS sharing, inviare un messaggio di posta elettronica a [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question).

## Versione 1.0.2004.0
**Rilasciata**: 11/12/2015

**Correzioni**:

-   Miglioramenti relativi ai messaggi di errore (precisione e chiarezza).

-   Miglioramenti di prestazioni durante la crittografia e la decrittografia di contenuti.

**Nuove funzionalità**:

-   Supporto per l'installazione da parte di utenti non amministratori, in modo che anche utenti standard possano installare l'applicazione di condivisione RMS.

    Sono tuttavia previste alcune limitazioni per gli utenti standard che eseguono Office 2010. Per altre informazioni, vedere la sezione [Se non si è un amministratore locale e si usa Office 2010](../Topic/Download_and_install_the_Rights_Management_sharing_application.md#BKMK_SetupOffice2010) delle istruzioni utente di [Scaricare e installare l’applicazione di condivisione Rights Management](../Topic/Download_and_install_the_Rights_Management_sharing_application.md).

## Versione 1.0.1908.0
**Rilasciata**: 16/9/2015

**Correzioni**:

-   Supporto per Multi-Factor Authentication (MFA) per Azure RMS, che rimuove inoltre la dipendenza dall’Assistente per l'accesso Microsoft per applicazioni che utilizzano l’autenticazione moderna.

    Per altre informazioni, vedere la sezione [Multi-Factor Authentication (MFA) e Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_MFA) in [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Versione 1.0.1784.0
**Rilasciata**: 30/07/2015

**Correzioni**:

-   L'intervallo di aggiornamento predefinito per i modelli di criteri viene ridotto da 7 giorni per 1 giorno.

-   Numero inferiore di regressioni e bug secondari.

## Versione 1.0.1770.0
**Rilasciata**: 25/04/2015

**Correzioni**:

-   A questo punto, solo i proprietari e i comproprietari possono rimuovere la protezione, non i co-autori.

-   Ora è possibile proteggere i file che si trovano in una condivisione di rete.

**Nuove funzionalità**:

-   Supporto per rilevamento e revoca dei documenti. Per altre informazioni, vedere [Rilevare e revocare i documenti quando si utilizza l'applicazione di condivisione RMS](../Topic/Track_and_revoke_your_documents_when_you_use_the_RMS_sharing_application.md).

-   Il supporto del modello quando si sceglie **Condividi file protetto**:

    -   Ora è possibile selezionare i modelli.

    -   Anziché il dispositivo di scorrimento, verranno visualizzati una casella di riepilogo che include i modelli e le autorizzazioni personalizzate.

    -   Non si visualizzano più le opzioni per **Consenti consumo su tutti i dispositivi** e **Applica restrizioni d'uso**. Al contrario, **Protezione generica** viene selezionato automaticamente in base al tipo di file.

    Per altre informazioni, vedere [Opzioni della finestra di dialogo per l’applicazione di condivisione Rights Management](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md).

## Versione 1.0.1667.0
**Rilasciata**: 19/01/2015

**Correzioni**:

-   Supporto per i caratteri in cinese nel visualizzatore PPDF dell’app di RMS sharing.

-   Miglioramento della gestione degli errori e della messaggistica.

-   Correggere un problema con la notifica di aggiornamento automatico quando è disponibile per il download una versione più recente dell'applicazione.

**Nuove funzionalità**:

-   **Supporto per più domini di posta elettronica all'interno dell'organizzazione**: Se si utilizza AD RMS e gli utenti dell'organizzazione dispongono di più domini di posta elettronica, questo aggiornamento consente loro di utilizzare contenuti protetti dagli utenti dell'organizzazione in altri domini. Per altre informazioni, vedere la sezione [Solo AD RMS: Supporto per più domini di posta elettronica all'interno dell'organizzazione](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains) nell'argomento [Guida dell'amministratore dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md).

