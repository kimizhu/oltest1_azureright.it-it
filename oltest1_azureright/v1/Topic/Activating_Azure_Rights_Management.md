---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# Attivazione di Azure Rights Management
Quando si attiva [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), l'azienda può iniziare a proteggere i dati importanti usando le applicazioni e i servizi che supportano questa soluzione di protezione delle informazioni. Gli amministratori possono inoltre gestire e monitorare i file e i messaggi di posta elettronica protetti di proprietà dell'azienda. È necessario abilitare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] prima di poter iniziare a usare le funzionalità IRM (Information Rights Management) in Office, SharePoint ed Exchange.

Per altre informazioni su Azure Rights Management prima di attivare il servizio, ad esempio sui problemi aziendali che permette di risolvere, sui casi di utilizzo tipici e su come funziona, vedere [Informazioni su Microsoft Azure Rights Management](../Topic/What_is_Azure_Rights_Management_.md)

> [!IMPORTANT]
> Prima di attivare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], assicurarsi che il piano di servizio dell'organizzazione includa i servizi [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. In caso contrario, non sarà possibile attivare Azure RMS.
> 
> Per altre informazioni, vedere la sezione [Sottoscrizioni cloud che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) dell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

Dopo l'attivazione di Azure RMS, tutti gli utenti dell'organizzazione potranno applicare la protezione delle informazioni ai propri file e tutti gli utenti potranno aprire (utilizzare) i file protetti da Azure RMS. Se si preferisce, tuttavia, è possibile limitare l'applicazione della protezione delle informazioni solo ad alcuni utenti, usando i controlli di selezione utenti per una distribuzione graduale. Per altre informazioni, vedere la sezione [Configurazione dei controlli di selezione utenti per una distribuzione graduale](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) di questo argomento.

## Attivazione di Rights Management
Per attivare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], usare una delle procedure descritte di seguito.

> [!TIP]
> È anche possibile usare il cmdlet [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx) di Windows PowerShell per attivare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

#### Per attivare Rights Management mediante l'interfaccia di amministrazione di Office 365

1.  Dopo avere sottoscritto un piano di Office 365 che include Rights Management, [accedere a Office 365 un account aziendale o dell'istituto di istruzione](https://portal.office.com/) con privilegi di amministratore per la distribuzione di Office 365 corrente.

2.  Se l'interfaccia di amministrazione di Office 365 non viene visualizzata automaticamente, selezionare l'icona di avvio delle app in alto a sinistra e scegliere **Amministratore**. Il riquadro **Amministratore** viene visualizzato solo dagli amministratori di Office 365.

    > [!TIP]
    > Per la guida all'interfaccia di amministrazione, vedere [Informazioni sull'interfaccia di amministrazione di Office 365 - Guida per gli amministratori](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  Nel riquadro sinistro fare clic su **IMPOSTAZIONI SERVIZIO**.

4.  Fare clic su **Rights Management**.

    > [!NOTE]
    > Se questa opzione non è visualizzata, è possibile che il piano di servizio o la versione del prodotto non sia in grado di supportare Rights Management oppure che non sia stato ancora effettuato l'aggiornamento per supportare Rights Management.
    > 
    > Per verificare di disporre del supporto, usare le informazioni contenute nella sezione [Sottoscrizioni cloud che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) dell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md). Se il piano di servizio o la versione del prodotto è supportata ma l'opzione Rights Management non è visibile, è possibile che il servizio non sia stato ancora aggiornato. Per avere assistenza relativamente a tale problema, inviare un messaggio di posta elettronica ad [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS).

5.  Nella pagina **RIGHTS MANAGEMENT** fare clic su **Gestisci**.

6.  Nella pagina **Rights Management** fare clic su **attiva**.

7.  Quando viene visualizzata la richiesta **Attivare Rights Management?**, fare clic su **Attiva**.

Verranno quindi visualizzati il messaggio **Rights Management è attivato** e l'opzione di disattivazione.

#### Per attivare Rights Management dal portale di Azure classico

1.  Dopo aver creato un account Azure, [accedere al portale di Azure classico](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  Nel riquadro sinistro fare clic su **ACTIVE DIRECTORY**.

3.  Nella pagina **active directory** fare clic su **RIGHTS MANAGEMENT**.

4.  Selezionare la directory da gestire per [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], fare clic su **ATTIVA** e confermare l'azione.

    > [!NOTE]
    > Se questa opzione non è visualizzata, è possibile che il piano di servizio o la versione del prodotto non sia in grado di supportare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].
    > 
    > Per verificare di disporre del supporto per RMS, usare le informazioni contenute nella sezione [Sottoscrizioni cloud che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) dell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md). Per avere assistenza relativamente a tale problema, inviare un messaggio di posta elettronica ad [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS).

Come **STATO RIGHTS MANAGEMENT** ora verrà visualizzato **Attivo** e l'opzione **ATTIVA** verrà sostituita da **DISATTIVA**.

### Valori di stato e descrizioni di Rights Management nel portale di Azure classico
Oltre allo stato **Attivo**, che indica che il servizio Rights Management è abilitato e pronto all'uso, è possibile che siano visualizzati anche gli stati **Inattivo**, **Non disponibile** o **Non autorizzato**.

|Valore dello stato|Descrizione|
|----------------------|---------------|
|**Attivo**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] è abilitato e pronto all'uso.|
|**Inattivo**|[!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] è disabilitato e deve essere attivato affinché l'organizzazione possa proteggere i file.|
|**Unavailable**|Il servizio [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] è inattivo. Riprovare.|
|**Non autorizzato**|Non si hanno le autorizzazioni necessarie a visualizzare lo stato del servizio [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. Ad esempio, l'account è bloccato oppure l'utente non è l'amministratore globale del tenant selezionato.|

## <a name="BKMK_OnboardingControls"></a>Configurazione dei controlli di selezione utenti per una distribuzione graduale
Se non si vuole permettere a tutti gli utenti di proteggere immediatamente i file usando Azure RMS, sarà possibile configurare controlli di selezione utenti usando il comando [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) di Windows PowerShell. È possibile eseguire questo comando prima o dopo l'attivazione di Azure RMS.

> [!IMPORTANT]
> Per usare questo comando, è necessaria almeno la versione **2.1.0.0** del [modulo Windows PowerShell per Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Per controllare quale versione è installata, eseguire: **(Get-Module aadrm –ListAvailable).Version**

Se, ad esempio, inizialmente si vuole permettere solo agli amministratori del gruppo "IT department" (con ID oggetto fbb99ded-32a0-45f1-b038-38b519009503) di proteggere i contenuti per finalità di test, usare il comando seguente:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Si noti che per questa opzione di configurazione è necessario specificare un gruppo. Non è possibile specificare singoli utenti.

Oppure se si vuole assicurare che solo gli utenti con licenza valida per l'uso di Azure RMS possano proteggere i contenuti:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Quando si usano questi controlli di selezione utenti, tutti gli utenti dell'organizzazione potranno utilizzare sempre i contenuti protetti dal sottoinsieme di utenti, ma non potranno applicare direttamente la protezione delle informazioni da applicazioni client. Non potranno ad esempio visualizzare nei client Office i modelli predefiniti pubblicati automaticamente quando viene attivato Azure RMS oppure eventuali modelli personalizzati configurati dall'utente.  Per ottenere lo stesso risultato, le applicazioni lato server, come Exchange, possono implementare controlli specifici per i singoli utenti per l'integrazione con RMS.

## Passaggi successivi
Dopo aver attivato [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] per l'organizzazione, usare la [Guida di orientamento per la distribuzione di Microsoft Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) per verificare se può essere necessario eseguire operazioni di configurazione aggiuntive prima di distribuire [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] a utenti e amministratori. Ad esempio, per usare [modelli personalizzati](http://technet.microsoft.com/library/dn642472.aspx) per semplificare l'applicazione ai file della protezione delle informazioni, connettere i server locali in modo che usino [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], installando il [connettore RMS](http://technet.microsoft.com/library/dn375964.aspx), e distribuire l'[applicazione Rights Management](http://technet.microsoft.com/library/jj585031.aspx) che supporta la protezione di tutti i tipi di file su tutti i dispositivi. I servizi di Office, ad esempio Exchange Online e SharePoint Online, richiedono operazioni di configurazione aggiuntive prima che sia possibile usare le funzionalità di Information Rights Management (IRM). Se tuttavia non si prevede di eseguire operazioni di configurazione aggiuntive, usare [Uso di Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) come guida operativa per una corretta distribuzione nell'organizzazione.

Per informazioni sul funzionamento delle applicazioni con [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], vedere [Supporto di Microsoft Azure Rights Management da parte delle applicazioni](../Topic/How_Applications_Support_Azure_Rights_Management.md).

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

