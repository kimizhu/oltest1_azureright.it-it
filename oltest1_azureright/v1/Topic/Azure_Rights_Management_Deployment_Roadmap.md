---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Guida di orientamento per la distribuzione di Microsoft Azure Rights Management
Per preparare l'ambiente e implementare e gestire Microsoft Azure Rights Management (RMS) per l'organizzazione, eseguire la procedura seguente:

Tuttavia, se si vuole provare rapidamente Azure RMS per conto proprio, anziché implementarlo in un ambiente di produzione, vedere [Esercitazione di avvio rapido per Azure Rights Management](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> Prima di eseguire i seguenti passaggi, leggere [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Passaggio 1: Confermare di avere una sottoscrizione che include Azure Rights Management
Sono disponibili più tipi di sottoscrizione che includono [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Vedere la sezione [Sottoscrizioni cloud che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) nell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) e verificare che la sottoscrizione includa la funzionalità che si vuole usare nell'organizzazione facendo riferimento alla tabella in [Offerte di Rights Management Services (RMS) a confronto](https://technet.microsoft.com/dn858608).

## Passaggio 2: preparare l'account tenant per l'utilizzo di Rights Management
Prima di iniziare a usare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], effettuare la seguente preparazione:

1.  Verificare che il tenant di Azure o Office 365 contenga gli account utente e i gruppi che verranno usati da Azure RMS per autenticare gli utenti dell'organizzazione. Se necessario, creare questi account e gruppi o sincronizzarli dalla directory locale. Per altre informazioni, vedere [Preparazione per Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  Decidere se si desidera che Microsoft gestisca la chiave del tenant (impostazione predefinita) oppure generare e gestire personalmente la chiave del tenant. Questo servizio è noto come BYOK (Bring Your Own Key). Si noti che attualmente non è possibile usare il servizio BYOK se si usa Exchange Online. Per altre informazioni, vedere [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Installare il modulo Windows PowerShell per [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] in almeno un computer con accesso a Internet. È possibile eseguire questo passaggio subito o più avanti. Per altre informazioni, vedere [Installazione di Windows PowerShell per Microsoft Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Se attualmente si usano i servizi Rights Management locali, eseguire una migrazione per spostare le chiavi, i modelli e gli URL nel cloud. Per altre informazioni, vedere [Migrazione da AD RMS ad Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  Attivare Rights Management in modo da poter iniziare a usare il servizio. Se è richiesta una distribuzione graduale, configurare i controlli di selezione utenti per limitare l'utilizzo a utenti specifici. Per altre informazioni, vedere [Attivazione di Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

Facoltativamente, considerare la possibilità di configurare quanto segue:

-   Modelli personalizzati se i modelli di criteri predefiniti per i diritti di utilizzo non sono sufficienti per l'organizzazione. È possibile eseguire questo passaggio subito o più avanti. Per altre informazioni, vedere [Configurazione di modelli personalizzati per Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   Registrazione dei dati di utilizzo per monitorare le modalità con cui l'organizzazione usa Rights Management. È possibile eseguire questo passaggio subito o più avanti. Per altre informazioni, vedere [Registrazione e analisi dell'uso di Rights Management di Windows Azure](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## Passaggio 3: Configurare le applicazioni e i servizi per Rights Management
La configurazione delle applicazione può includere l'installazione dell'applicazione di condivisione Rights Management e l'abilitazione del supporto per le funzionalità IRM (Information Rights Management) in SharePoint Online o Exchange Online. Per altre informazioni, vedere [Configurazione di applicazioni per Rights Management di Windows Azure](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Se sono disponibili servizi IT esistenti che devono esaminare i file che verranno protetti da Azure RMS, ad esempio soluzioni di prevenzione per la perdita di dati, gateway con crittografia del contenuto e prodotti antimalware, configurare gli account del servizio per utenti con privilegi avanzati per Azure RMS. Per altre informazioni, vedere [Configurazione degli utenti con privilegi avanzati per Rights Management di Azure e servizi di individuazione o ripristino dei dati](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Se si dispone di servizi locali da usare con Microsoft Azure Rights Management, installare e configurare il relativo connettore. Per altre informazioni, vedere [Distribuzione del connettore di Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Passaggio 4: Pubblicare e utilizzare il contenuto protetto da diritti
È possibile pubblicare e utilizzare il contenuto protetto e registrare come la società usa Rights Management. Per altre informazioni, vedere [Uso di Azure Rights Management](../Topic/Using_Azure_Rights_Management.md).

## Passaggio 5: Amministrare Rights Management per l'account tenant in base alle esigenze
Quando si inizia a usare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], è possibile avvalersi del modulo [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] per Windows PowerShell per eseguire tramite script o automatizzare le modifiche di carattere amministrativo. Per altre informazioni, vedere [Amministrazione di Rights Management di Windows Azure mediante Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

