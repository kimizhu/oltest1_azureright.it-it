---
description: na
keywords: na
title: Scenario - Retain Control of Documents Stored in SharePoint
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89
---
# Scenario - Mantenere il controllo dei documenti archiviati in SharePoint
Questa sezione contiene istruzioni per l'amministratore e linee guida per l'utente.Prima di informare gli utenti su questa configurazione, è necessario completare le istruzioni per gli amministratori.

## Istruzioni per gli amministratori
![](../Image/AzRMS_AdminBanner.png)

Usare queste istruzioni per garantire che i documenti di Office archiviati in SharePoint possano essere controllati tramite le raccolte protette.Ad esempio, i documenti vengono protetti automaticamente dalle perdite di dati accidentali o previste dagli utenti e l'amministratore può bloccare l'accesso al contenuto anche dopo che questo è stato scaricato o sincronizzato.I file da proteggere dovrebbero essere quelli destinati alla collaborazione su documenti o piani di progettazione oppure alle consegne.Quando si configurano le raccolte protette per SharePoint, i file di Office archiviati in tali raccolte saranno protetti da Azure Rights Management.

Le istruzioni sono adatte ai casi seguenti:

-   Dipendenti che condividono dati e collaborano usando documenti di Office.

-   I documenti contengono informazioni non pubbliche, ma non necessariamente riservate al solo uso interno.

-   Dipendenti che non devono impostare o modificare le autorizzazioni definite da un amministratore a livello di raccolta.

## Requisiti per questo scenario
Per questo scenario, sono necessari i requisiti seguenti:

|Verifica|Requisito|Altre informazioni|
|------------|-------------|----------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Definizione di account e gruppi per Office 365 o Azure Active Directory|[Preparazione per Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Attivazione di Azure Rights Management|[Attivazione di Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Se si usa SharePoint Server: Distribuzione del connettore RMS e configurarlo per SharePoint|[Distribuzione del connettore di Azure Rights Management](https://technet.microsoft.com/library/dn375964.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Configurazione di SharePoint per IRM e le raccolte protette|[Configurare Information Rights Management (IRM) nell'interfaccia di amministrazione di SharePoint](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[Applicare Information Rights Management a un elenco o a una raccolta](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

## Istruzioni per l'utente
Non sono disponibili istruzioni specifiche per gli utenti relative a questo scenario, in quanto le raccolte protette non richiedono alcuna azione particolare da parte degli utenti.I documenti sono protetti automaticamente, in base alle autorizzazioni definite da un amministratore di SharePoint per il sito.Tuttavia, può essere necessario informare gli utenti e l'help desk su quali siano le raccolte protette e su come limitare l'uso dei documenti.Ad esempio, a causa delle limitazioni correnti, questi documenti possono essere visualizzati,ma non modificati con i dispositivi mobili.

È possibile inviare come comunicazione di posta elettronica standard al reparto o team pertinente l'esempio seguente, dopo la configurazione di una raccolta di SharePoint per l'uso di Azure RMS.

### Esempio di documentazione per l'utente
![](../Image/AzRMS_ExampleBanner.png)

##### Annuncio IT: Modifiche apportate al sito relativo a report e previsioni di vendita

-   Il sito di SharePoint relativo a **report e previsioni di vendita** è ora configurato per la collaborazione protetta.Da questo momento, è necessario modificare i fogli di calcolo e i documenti Word archiviati direttamente in questo sito. Ad esempio, non è possibile salvarli in un percorso diverso per modificarli in un secondo momento o inviarli tramite posta elettronica a un altro utente.È possibile visualizzarli con i dispositivi mobili, ma per modificarli è necessario usare un computer Windows.

**Serve assistenza?**

-   Contattare l'help desk: helpdesk@vanarsdelltd.com

