---
description: na
keywords: na
title: Decommissioning and Deactivating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
---
# Rimozione delle autorizzazioni e disattivazione di Azure Rights Management
Si può sempre decidere se l'organizzazione protegge il contenuto utilizzando [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) e se si decide che non si desidera più utilizzare questa soluzione di protezione delle informazioni, si può essere certi che non si verrà bloccati dal contenuto protetto in precedenza. Se non è necessario l'accesso continuo a contenuti protetti precedentemente, è sufficiente disattivare il servizio e lasciare scadere la sottoscrizione di Azure Rights Management. Per esempio, è opportuno procedere dopo aver completato i test di [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] prima della distribuzione in un ambiente di produzione.

Tuttavia, se è stata eseguita la distribuzione di [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] nell'ambiente di produzione, assicurarsi di disporre di una copia della chiave tenant di Azure Rights Management prima di disattivare il servizio e di eseguire questa operazione prima della scadenza della sottoscrizione, perché in tal modo è possibile mantenere l'accesso al contenuto protetto da Azure Rights Management dopo la disattivazione del servizio. Se si utilizza la soluzione BYOK con cui si genera e gestisce la propria chiave in un modulo HSM, si dispone già della chiave tenant di Azure Rights Management. Ma se è stata gestita da Microsoft (impostazione predefinita), vedere le istruzioni per l'esportazione della chiave tenant nell’argomento [Operazioni relative alla chiave del tenant di Azure Rights Management](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md).

> [!TIP]
> Anche dopo la scadenza della sottoscrizione, il tenant di Azure Rights Management rimane disponibile per l'utilizzo del contenuto per un periodo esteso. Tuttavia, non sarà più possibile esportare la chiave tenant.

Quando si dispone della chiave tenant di Azure Rights Management, è possibile distribuire Rights Management in locale (AD RMS) e importare la chiave tenant come un dominio di pubblicazione trusted (TPD). Quindi sono disponibili le seguenti opzioni per la rimozione delle autorizzazioni della distribuzione di Azure Rights Management:

|Se si verifica questo...|… effettuare la seguente operazione:|
|----------------------------|----------------------------------------|
|Si desidera che tutti gli utenti continuino a utilizzare Rights Management, ma che usino una soluzione locale, anziché Azure RMS    →|Utilizzare il cmdlet [Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) per indirizzare gli utenti esistenti alla distribuzione locale quando utilizzano il contenuto protetto dopo questa modifica. Gli utenti utilizzeranno automaticamente l'installazione di AD RMS per utilizzare il contenuto protetto.<br /><br />Affinché gli utenti utilizzino il contenuto protetto prima di questa modifica, reindirizzare i client alla distribuzione locale utilizzando la chiave di registro **LicensingRedirection** per Office 2016 oppure Office 2013, come descritto nella [sezione sull’individuazione del servizio](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) nelle note sulla distribuzione dei client di RMS e la chiave di registro **LicenseServerRedirection** per Office 2010, come descritto in [Impostazioni del registro di Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Si desidera interrompere completamente l'utilizzo delle tecnologie di Rights Management    →|Concedere a un amministratore designato [diritti di utente con privilegi avanzati](https://technet.microsoft.com/library/mt147272.aspx) e assegnare a questa persona lo [Strumento di protezione di RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />L'amministratore può quindi utilizzare lo strumento per decrittografare in gruppo nelle cartelle i file che erano stati protetti da Azure Rights Management, in modo che tornino allo stato non protetto e pertanto possano essere letti senza una tecnologia di Rights Management, ad esempio Azure RMS o AD RMS. Questo strumento può essere utilizzato con Azure RMS e AD RMS, pertanto è possibile scegliere di decrittografare i file prima o dopo la disattivazione di Azure RMS o una combinazione.|
|Non si è in grado di identificare tutti i file che sono stati protetti da Azure RMS o si desidera che tutti gli utenti siano in grado di leggere automaticamente i file protetti che non erano disponibili    →|Distribuire un’impostazione del registro su tutti i computer client utilizzando la chiave di registro **LicensingRedirection** per Office 2016 e Office 2013, come descritto nella [sezione sull’individuazione del servizio](https://technet.microsoft.com/library/jj159267%28v=ws.10%29.aspx) nelle note sulla distribuzione dei client di RMS e la chiave di registro **LicenseServerRedirection** per Office 2010, come descritto in [Impostazioni del registro di Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Distribuire anche un'altra impostazione del registro per impedire agli utenti di proteggere nuovi file impostando **DisableCreation** su **1**, come descritto nelle [Impostazioni del registro di Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Si desidera un servizio di ripristino manuale controllato per tutti i file che non erano disponibili    →|Concedere [diritti di utente con privilegi avanzati](https://technet.microsoft.com/library/mt147272.aspx) a utenti designati in un gruppo di ripristino dei dati e fornire loro lo [Strumento di protezione di RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256), in modo che possano rimuovere la protezione dei file quando richiesto dagli utenti standard.<br /><br />Su tutti i computer distribuire l’impostazione del registro per impedire agli utenti di proteggere nuovi file impostando **DisableCreation** su **1**, come descritto nelle [Impostazioni del registro di Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Per ulteriori informazioni sulle procedure in questa tabella, vedere le risorse seguenti:

-   Per informazioni su AD RMS e riferimenti sulla distribuzione, vedere [Panoramica di Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx).

-   Per istruzioni sull’importazione della chiave tenant di Azure RMS come file TPD, vedere [Aggiungere un dominio di pubblicazione trusted](https://technet.microsoft.com/library/cc771460.aspx).

-   Per installare il modulo Windows PowerShell per Azure RMS, per impostare l'URL di migrazione, vedere [Installazione di Windows PowerShell per Microsoft Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Quando si è pronti per disattivare il servizio di Azure RMS dell'organizzazione, utilizzare le istruzioni seguenti.

## Disattivazione di Rights Management
Per disattivare [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], usare una delle procedure descritte di seguito.

> [!TIP]
> È inoltre possibile utilizzare il cmdlet di Windows PowerShell [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), per disattivare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Per disattivare Rights Management mediante l'interfaccia di amministrazione di Office 365

1.  [Accedere a Office 365 con l'account aziendale o dell'istituto di istruzione](https://portal.office.com/) con i privilegi di amministratore per la distribuzione di Office 365.

2.  Se l'interfaccia di amministrazione di Office 365 non viene visualizzata automaticamente, selezionare l'icona di avvio delle app in alto a sinistra e scegliere **Amministratore**. Il riquadro **Amministratore** viene visualizzato solo dagli amministratori di Office 365.

    > [!TIP]
    > Per la guida all'interfaccia di amministrazione, vedere [Informazioni sull'interfaccia di amministrazione di Office 365 - Guida per gli amministratori](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  Nel riquadro sinistro fare clic su **IMPOSTAZIONI SERVIZIO**.

4.  Fare clic su **Rights Management**.

5.  Nella pagina **RIGHTS MANAGEMENT** fare clic su **Gestione**.

6.  Nella pagina **rights management** fare clic su **disattiva**.

7.  Quando viene chiesto **Si desidera disattivare Rights Management?** fare clic su **disattiva**.

Verrà visualizzato il messaggio che indica che **Rights Management non è attivato** con l'opzione per l'attivazione.

#### Per disattivare Rights Management dal portale di Azure

1.  Accedere al [portale di Azure classico](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  Nel riquadro sinistro fare clic su **ACTIVE DIRECTORY**.

3.  Nella pagina **active directory** fare clic su **RIGHTS MANAGEMENT**.

4.  Selezionare la directory da gestire per [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], fare clic su **DISATTIVA** e confermare l'azione.

Lo **STATO DI RIGHTS MANAGEMENT** dovrebbe ora essere **Inattivo** e l’opzione **DISATTIVA** viene sostituita da **ATTIVA**.

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

