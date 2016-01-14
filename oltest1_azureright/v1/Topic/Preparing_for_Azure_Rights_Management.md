---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Preparazione per Azure Rights Management
Dopo essersi iscritti per una sottoscrizione cloud e aver configurato l'organizzazione con un account per [!INCLUDE[o365_1](../Token/o365_1_md.md)] o Azure Active Directory, si è pronti per abilitare il servizio [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

Prima di procedere all'abilitazione del servizio, assicurarsi di soddisfare i requisiti seguenti:

-   Account e gruppi utente nel cloud creati manualmente o che sono stati creati automaticamente e sincronizzati dai Servizi di dominio Active Directory (AD DS).

    Quando si sincronizzano gli account e i gruppi locali, non è necessario sincronizzare tutti gli attributi. Per un elenco degli attributi che devono essere sincronizzati per Azure RMS, vedere questa [sezione di Azure RMS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) nella documentazione di Azure Active Directory. Per facilitare la distribuzione, è consigliabile usare [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) per la connessione delle directory locali ad Azure Active Directory, ma si può usare qualsiasi metodo di sincronizzazione di directory che ottiene lo stesso risultato.

-   Gruppi abilitati alla posta nel cloud da usare con Rights Management. Possono essere gruppi predefiniti o gruppi creati manualmente, che contengono utenti che useranno Rights Management.

    Se si dispone di Exchange Online, è possibile creare e utilizzare i gruppi abilitati alla posta tramite il centro di amministrazione di Exchange. Se si dispone di AD DS locale e si esegue la sincronizzazione in Azure AD, è possibile creare e utilizzare i gruppi abilitati alla posta che sono gruppi di protezione o gruppi di distribuzione.

## Abilitare Rights Management
Per impostazione predefinita, [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] è disabilitato quando ci si iscrive per l'account [!INCLUDE[o365_2](../Token/o365_2_md.md)] o Azure AD. Per abilitare [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] per l'organizzazione, è necessario attivare il servizio. Per altre informazioni, vedere [Attivazione di Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

