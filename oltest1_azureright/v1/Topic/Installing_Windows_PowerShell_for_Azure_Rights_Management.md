---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# Installazione di Windows PowerShell per Microsoft Azure Rights Management
Usare le informazioni seguenti come riferimento per installare Windows PowerShell per Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

È possibile usare questo modulo di Windows PowerShell per amministrare [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] dalla riga di comando usando qualsiasi computer dotato di connessione a Internet e che soddisfa i prerequisiti elencati nella sezione seguente. Windows PowerShell per [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] supporta l'utilizzo di script per l'automazione oppure può essere necessario per scenari di configurazione avanzata. Per altre informazioni sulle attività di amministrazione e sulle configurazioni supportate dal modulo, vedere [Amministrazione di Rights Management di Windows Azure mediante Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Prerequisiti
In questa tabella sono riportati i prerequisiti per l'installazione e l'utilizzo di Windows PowerShell per [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Requisito|Altre informazioni|
|-------------|----------------------|
|Una versione di Windows in grado di supportare il modulo di amministrazione di [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]|Controllare l'elenco dei sistemi operativi supportati nella sezione **Requisiti di sistema** della [pagina di download per Azure Rights Management Administration Tool](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Versione minima di Windows PowerShell: 2.0|Il supporto per il modulo di amministrazione di [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] è stato introdotto per la prima volta in Windows PowerShell 2.0.<br /><br />Per impostazione predefinita, con la maggior parte dei sistemi operativi Windows viene installata almeno la versione 2.0 di Windows PowerShell. Se è necessario installare Windows PowerShell 2.0, vedere [Installare Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx).<br /><br />Suggerimento: È possibile verificare quale versione di Windows PowerShell sia in esecuzione digitando **$PSVersionTable** in una sessione di Windows PowerShell.|
|Versione minima di Microsoft .NET Framework: 4.5<br /><br />Nota: Questa versione di Microsoft .NET Framework è inclusa nei sistemi operativi successivi. È pertanto necessario installarla manualmente se il sistema operativo client è inferiore a Windows 8.0 o se il sistema operativo server è inferiore a Windows Server 2012.|Se la versione minima di Microsoft .NET Framework non è ancora installata, è possibile scaricare [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />La versione minima di Microsoft .NET Framework è necessaria per alcune classi usate dal modulo di amministrazione di [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|
|Assistente per l'accesso ai Microsoft Online Services 7.0|L'Assistente per l'accesso ai Microsoft Online Services è necessario per l'autenticazione di [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].<br /><br />Per altre informazioni, vedere l'[Area download: Assistente per l'accesso ai Microsoft Online Services per professionisti IT - RTW.](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## Come installare il modulo di amministrazione di Rights Management

1.  Passare all'Area download Microsoft e [scaricare Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721), contenente il modulo di amministrazione di [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] per Windows PowerShell.

2.  Nella cartella locale in cui è stato scaricato e salvato il file del programma di installazione di [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] fare doppio clic sul file eseguibile scaricato per la propria piattaforma (WindowsAzureADRightsManagementAdministration_x64 o WindowsAzureADRightsManagementAdministration_x86.exe) per avviare l'installazione guidata del modulo di amministrazione di Azure AD Rights Management.

3.  Completare la procedura guidata.

Windows PowerShell per [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] è ora installato.

## Passaggi successivi
Per visualizzare i cmdlet disponibili, avviare Windows PowerShell con l'opzione **Esegui come amministratore** e digitare quanto segue:

```
Get-Command -Module aadrm
```
Utilizzare il comando `the Get-Help <cmdlet_name>` per visualizzare le informazioni della Guida per un cmdlet specifico.

Per altre informazioni:

-   Elenco completo dei cmdlet disponibili: [Cmdlet di Azure Rights Management](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Elenco dei principali scenari di configurazione che supportano Windows PowerShell: [Amministrazione di Rights Management di Windows Azure mediante Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Prima di poter eseguire i comandi che consentono di configurare il servizio [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], è necessario connettersi al servizio usando il cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx). Al termine dell'esecuzione dei comandi di configurazione desiderati, disconnettersi dal servizio usando il cmdlet [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx).

> [!NOTE]
> Se [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] non è stato ancora attivato, è possibile attivarlo usando il cmdlet [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) dopo essersi connessi al servizio.

## Vedere anche
[Amministrazione di Rights Management di Windows Azure mediante Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

