---
description: na
keywords: na
title: Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
---
# Configurazione degli utenti con privilegi avanzati per Rights Management di Azure e servizi di individuazione o ripristino dei dati
La funzionalità per utenti con privilegi avanzati di Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) garantisce che gli utenti e i servizi autorizzati possano sempre leggere e controllare i dati che Azure RMS consente di proteggere per l'organizzazione. Se necessario, rimuovere la protezione o modificare la protezione applicata in precedenza. Un utente con privilegi avanzati dispone sempre dei diritti completi di proprietario per tutte le licenze concesse dal tenant RMS dell'organizzazione. Questa possibilità viene definita anche "ragionamento sui dati" e riveste un ruolo di importanza critica nel mantenimento del controllo sui dati dell'organizzazione. Ad esempio, utilizzare questa funzionalità per uno qualsiasi dei seguenti scenari:

-   Un dipendente lascia l'organizzazione ed è necessario leggere i file che ha protetto.

-   Un amministratore IT deve rimuovere il criterio di protezione corrente che è stato configurato per i file e applicare un nuovo criterio di protezione.

-   Exchange Server deve indicizzare le caselle postali per le operazioni di ricerca.

-   Si dispone di servizi IT esistenti per le soluzioni di prevenzione della perdita dei dati, per il gateway di crittografia del contenuto (CEG) e per i prodotti anti-malware che richiedono l'analisi dei file che sono già protetti.

-   È necessario decrittografare i file per questioni di controllo, legali o per altri motivi di conformità.

Per impostazione predefinita, questo ruolo non è abilitato e a esso non sono assegnati utenti. Viene abilitata automaticamente per l'utente se si configura il connettore Rights Management per Exchange, e non è necessaria per i servizi standard che eseguono Exchange Online, SharePoint Online o SharePoint Server.

Se è necessario attivare manualmente la funzionalità per utenti con privilegi avanzati, utilizzare il cmdlet Windows PowerShell [Enable AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), e poi assegnare gli utenti (o gli account del servizio) in base alle esigenze usando il cmdlet [Aggiungi AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx). È possibile disporre di uno o più utenti con privilegi avanzati per l'organizzazione, ma è necessario aggiungere singoli utenti; i gruppi non sono supportati.

> [!NOTE]
> Se non è ancora installato il modulo Windows PowerShell per [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], vedere [Installazione di Windows PowerShell per Microsoft Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Le procedure consigliate per la funzionalità per utenti con privilegi avanzati:

-   Limitare e monitorare gli amministratori che vengono assegnati a un amministratore globale per il tenant di Office 365 o Azure RMS. o a chi viene assegnato il ruolo di GlobalAdministrator utilizzando il cmdlet [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx). Questi utenti possono abilitare la funzionalità per utenti con privilegi avanzati e assegnare agli utenti (e a se stessi) la condizione di utenti con privilegi avanzati, e potenzialmente decrittografare tutti i file che l'organizzazione protegge.

-   Per visualizzare quali utenti e account di servizio vengono assegnati come utenti con privilegi avanzati, utilizzare il [cmdlet Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx).  Come tutte le azioni di amministrazione, quelle di abilitare o disabilitare la caratteristica con privilegi avanzati, e aggiungere o rimuovere gli utenti con privilegi avanzati che vengono registrati, possono essere controllate tramite il comando [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx). Quando gli utenti con privilegi avanzati decrittografare i file, questa azione viene registrata e può essere controllata con [registra utilizzo](https://technet.microsoft.com/library/dn529121.aspx).

-   Se non è necessaria la funzionalità per utenti con privilegi avanzati per i servizi quotidiani, abilitare la funzionalità solo quando è necessario e disabilitarla nuovamente utilizzando il cmdlet [Disable AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx).

L'estratto seguente di log mostra alcune voci di esempio dall’utilizzo del cmdlet Get-AadrmAdminLog. In questo esempio, l'amministratore di Contoso Ltd conferma che la funzionalità per utenti con privilegi avanzati è disabilitata, aggiunge Richard Simone come utente con privilegi avanzati, verifica che Richard sia l’unico utente con privilegi avanzati configurato per Azure RMS, e poi abilita la funzionalità per utenti con privilegi avanzati in modo che Richard ora sia in grado di decrittografare alcuni file che sono stati protetti da un dipendente che ora ha lasciato l'azienda.

`2015-08-01T18:58:20	admin@contoso.com	GetSuperUserFeatureState	Passed	Disabled`
`2015-08-01T18:59:44	admin@contoso.com	AddSuperUser -id rsimone@contoso.com	Passed	True`
`2015-08-01T19:00:51	admin@contoso.com	GetSuperUser	Passed	rsimone@contoso.com`
`2015-08-01T19:01:45	admin@contoso.com	SetSuperUserFeatureState -state Enabled	Passed	True`

## <a name="BKMK_RMSProtectionModule"></a>Opzioni di scripting per gli utenti con privilegi avanzati
Spesso, la persona cui viene assegnato il ruolo di utente con privilegi avanzati per [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] dovrà rimuovere la protezione da più file, in più posizioni. Sebbene sia possibile effettuare questa operazione manualmente, è più efficiente (e spesso più affidabile) eseguire uno script. A tale scopo, [scaricare lo strumento di protezione RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Poi, utilizzare il cmdlet [Unprotect RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) e [Protect RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx)   come richiesto.

> [!IMPORTANT]
> Sebbene lo strumento di protezione RMS sia progettato per gli utenti con privilegi avanzati per rimuovere la protezione dai file di massa per scopi di ripristino, la versione corrente dello strumento non supporta l'autenticazione dell’utente per Azure RMS. Fino a quando non viene risolta questa limitazione, è necessario utilizzare un account del servizio principale per l'autenticazione con Azure RMS prima di poter rimuovere file di protezione.  Per ulteriori informazioni e istruzioni, vedere [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/azure/mt433202.aspx).

Per ulteriori informazioni su questi cmdlet, vedere [cmdlet protezione RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Il modulo Windows PowerShell RMSProtection fornito con lo strumento di protezione RMS è diverso da e integra il principale [modulo Windows PowerShell per Azure Rights Management](https://technet.microsoft.com/library/jj585027.aspx). Supporta sia Azure RMS che AD RMS.

## Vedere anche
[Configurazione di Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

