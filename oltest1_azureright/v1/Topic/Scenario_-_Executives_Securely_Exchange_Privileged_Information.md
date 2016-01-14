---
description: na
keywords: na
title: Scenario - Executives Securely Exchange Privileged Information
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d
---
# Scenario - Scambiarsi informazioni con privilegi tra dirigenti
Questa sezione contiene istruzioni per l'amministratore e linee guida per l'utente.Prima di informare gli utenti su questa configurazione, è necessario completare le istruzioni per gli amministratori.

## Istruzioni per gli amministratori
![](../Image/AzRMS_AdminBanner.png)

Usare queste istruzioni affinché i dirigenti possano scambiarsi in modo sicuro messaggi e allegati tramite posta elettronica e i criteri limitino automaticamente l'accesso ai dirigenti senza che sia necessario alcun intervento da parte di questi ultimi.I messaggi di posta elettronica e gli eventuali allegati saranno protetti da Azure Rights Management.

Le istruzioni sono adatte ai casi seguenti:

-   Dirigenti che condividono informazioni riservate tra loro, da non condividere con altri utenti.

-   Quando inviano questi messaggi, i dirigenti devono semplicemente inviarli a un indirizzo di posta elettronica dell'ufficio anziché a uno personale.

## Requisiti per questo scenario
Per questo scenario, sono necessari i requisiti seguenti:

|Verifica|Requisito|Altre informazioni|
|------------|-------------|----------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Definizione di account e gruppi per Office 365 o Azure Active Directory:<br /><br />-   Un gruppo abilitato per la posta denominato **Dirigenti**<br />-   Tutti i dirigenti sono membri del gruppo **Dirigenti**|[Preparazione per Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Gestione della chiave tenant di Azure Rights Management tramite Microsoft. Non viene usato il sistema BYOK|[Pianificazione e implementazione della chiave tenant di Azure Rights Management](https://technet.microsoft.com/library/dn440580.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Attivazione di Azure Rights Management|[Attivazione di Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Abilitazione di Exchange Online per Azure Rights Management|Espandere [Exchange Online:](https://technet.microsoft.com/library/jj585031.aspx) in [Configurazione delle applicazioni per Azure Rights Management](https://technet.microsoft.com/library/jj585031.aspx).|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Configurazione di un modello personalizzato, come descritto di seguito|[Configurazione di modelli personalizzati per Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Configurazione di una regola di protezione del trasporto per IRM, come descritto di seguito|[Creare una regola di protezione del trasporto](https://technet.microsoft.com/library/dd302432.aspx)|

#### Per configurare il modello personalizzato per i messaggi dei dirigenti:

1.  Nel portale di Azure: Creare un nuovo modello personalizzato per Azure Rights Management, contenente i valori e le impostazioni seguenti:

    -   Nome: **Dirigenti**

    -   Diritti:  Concedere al gruppo dei dirigenti abilitati per la posta i diritti di **Comproprietario**

2.  Pubblicare il nuovo modello.

3.  Aggiornare i modelli per Exchange Online usando il comando Windows PowerShell per Exchange Online:

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates –RMSOnline
    ```

#### Per configurare la protezione automatica dei messaggi di posta elettronica da e verso i dirigenti:

-   Nell'interfaccia di amministrazione di Exchange: Creare una nuova regola di flusso di posta, contenente i valori e le impostazioni seguenti:

    -   Fare clic sull'icona Nuovo e selezionare **Applica la protezione dei diritti ai messaggi**

    -   Nella pagina **Nuova regola**:

        -   Specificare un nome, ad esempio **Applica i modelli Dirigenti ai messaggi di posta elettronica dei dirigenti**

        -   In **Applica questa regola se** selezionare **Il mittente** ... **è un membro di questo gruppo** e selezionare **Dirigenti**.

        -   Fare clic su **Aggiungi condizione**, selezionare **Il destinatario** ... **è un membro di questo gruppo** e selezionare **Dirigenti**.

        -   In **Fai quanto segue** assicurarsi che l'opzione **Applica la protezione dei diritti al messaggio con** sia selezionata, fare clic su **Scegli un elemento** per selezionare il modello **Dirigenti**.

        -   Assicurarsi che in **Scegli una modalità per la regola** sia selezionata l'opzione **Applica**.

        -   Fare clic su **Salva**.

## Istruzioni per l'utente
Non esistono istruzioni specifiche per gli utenti relative a questo scenario, in quanto la protezione dei messaggi di posta elettronica da e verso i dirigenti non richiede alcuna azione particolare da parte degli utenti.I messaggi di posta elettronica e gli eventuali allegati vengono protetti automaticamente in modo che solo i membri del gruppo Dirigenti possano accedervi.Tuttavia, può essere necessario informare i dirigenti e l'help desk sulla protezione automatica dei messaggi e su come limitare l'uso di tali messaggi.Ad esempio, se i messaggi o gli allegati vengono inoltrati ad altri utenti, non possono essere letti in modo corretto.

È possibile inviare come comunicazione di posta elettronica standard ai dirigenti l'esempio seguente, dopo la configurazione di Exchange Online per questo scenario.

### Esempio di documentazione per l'utente
![](../Image/AzRMS_ExampleBanner.png)

##### Annuncio IT: Protezione automatica dei messaggi di posta elettronica dei dirigenti

-   Da questo momento, ogni volta che si inviano messaggi di posta elettronica a un altro dirigente della società, i contenuti dei messaggi e gli eventuali allegati verranno protetti automaticamente in modo che solo un altro dirigente della società possa accedervi per leggere le informazioni, stamparlo, copiarlo e così via.Questa restrizione si applica anche se il messaggio di posta elettronica viene inoltrato ad altri utenti o se vengono salvati gli allegati.Questa protezione consente di impedire la perdita di dati contenenti informazioni sensibili o riservate.

    Si noti che se si desidera che altri utenti possano leggere e modificare le informazioni contenute in questi messaggi di posta elettronica, è necessario inviarle separatamente.

    Quando si inviano informazioni aziendali riservate a un altro dirigente, ricordarsi di inviarle al relativo indirizzo di posta elettronica dell'ufficio e non a un indirizzo personale.

**Serve assistenza?**

-   Contattare l'help desk: helpdesk@vanarsdelltd.com

