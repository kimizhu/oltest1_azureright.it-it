---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# Guida dell&#39;amministratore dell&#39;applicazione di condivisione Rights Management
Utilizzare le seguenti informazioni se l'utente è responsabile per l'applicazione di condivisione Rights Management di Microsoft in una rete aziendale, o se si desiderano informazioni più tecniche rispetto a quelle presenti in [Guida dell'utente dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md) o [domande frequenti per l’applicazione di condivisione Rights Management di Microsoft per Windows](http://go.microsoft.com/fwlink/?LinkId=303971):

-   [Distribuzione automatica per l'applicazione di condivisione Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [Verificare l'esito positivo dell’installazione](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [Disinstallare i comandi](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [Eliminazione degli aggiornamenti automatici](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [Solo Azure RMS: Configurazione del rilevamento dei documenti](#BKMK_DocumentTracking)

    -   [Solo AD RMS: Supporto per più domini di posta elettronica all'interno dell'organizzazione](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [Panoramica tecnica per l'applicazione di condivisione Microsoft Rights Management](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [Livelli di protezione – nativo e generico](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [Tipi di file supportati e le estensioni di nome di file](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [Modifica del livello di protezione predefinito dei file](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> Se si ha familiarità con l'app di condivisione RMS o per ulteriori informazioni, vedere [come RMS protegge tutti i tipi di file, utilizzando l'applicazione di condivisione RMS](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app).

L’applicazione di condivisione RMS è più adatta per l'utilizzo con Azure RMS, perché questa configurazione di distribuzione supporta l'invio di allegati protetti agli utenti in un'altra organizzazione e opzioni quali le notifiche tramite posta elettronica e il rilevamento dei documenti con revoca.  Tuttavia, con alcune limitazioni, funziona anche con la versione locale, AD RMS. Per un confronto completo delle funzionalità supportate da Azure RMS e AD RMS, vedere [Confronto di Rights Management di Azure e AD RMS](https://technet.microsoft.com/library/jj739831.aspx). Se si dispone di AD RMS e si desidera eseguire la migrazione ad Azure RMS, vedere [Migrazione da AD RMS a Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx).

## <a name="BKMK_ScriptedInstall"></a>Distribuzione automatica per l'applicazione di condivisione Microsoft Rights Management
La versione di Windows dell'applicazione di condivisione RMS supporta un'installazione tramite script, che la rende ideale per le distribuzioni aziendali.

I soli prerequisiti per le installazioni sono che il computer esegua una versione minima di Windows 7 Service Pack 1 e che sia installata la versione minima 4.0 di Microsoft Framework. Se è necessario installare Microsoft .NET Framework 4.0, è possibile [Scaricarlo per l'installazione da Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=17718).

#### Per scaricare l'applicazione di condivisione RMS per la distribuzione automatica.

1.  Visitare la pagina [Applicazione di condivisione Rights Management di Microsoft per Windows](http://www.microsoft.com/download/details.aspx?id=40857) nel Microsoft Download Center e fare clic su **Download**.

2.  Selezionare e scaricare i file necessari. Sono disponibili due pacchetti di installazione client: uno per Windows a 64 bit (x64.zip applicazione di condivisione Microsoft Rights Management) e un altro per Windows a 32 bit (x86.zip applicazione di condivisione Microsoft Rights Management).

3.  Estrarre i file dai pacchetti di installazione compressi, ad esempio, facendo doppio clic su di essi. Poi copiare i file estratti in un percorso di rete a cui possono accedere i computer client.

I pacchetti di installazione per l'applicazione di condivisione RMS supporta diversi scenari di distribuzione e include quanto segue:

|Descrizione|Scenario di distribuzione|
|---------------|-----------------------------|
|Assistente per l'accesso a Microsoft Online|Necessario per:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2013 e Azure RMS se non è stato installato il [9 giugno 2015, l'aggiornamento per Office 2013](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Hotfix per Office (KB 2596501)|Necessario per:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS|
|Aggiornamento rapido per abilitare il Client AD RMS 1.0 a lavorare con Azure RMS (2843630 KB)|Necessario per:<br /><br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS|
|Client AD RMS e applicazione di condivisione RMS|Necessario per:<br /><br />-   Office 2016 o Office 2013 e Azure RMS o Active Directory RMS<br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS<br />-   Solo applicazione di condivisione RMS e componente aggiuntivo di Office|
|Componente aggiuntivo di Office per la barra multifunzione|Necessario per:<br /><br />-   Office 2016 o Office 2013 e Azure RMS o Active Directory RMS<br />-   Office 2010 e Azure RMS<br />-   Office 2010 e Active Directory RMS<br />-   Solo applicazione di condivisione RMS e componente aggiuntivo di Office|
|Strumento di preparazione Rights Management di Azure Active Directory|Necessario per:<br /><br />-   Office 2010 e Azure RMS|
Utilizzare le procedure seguenti per identificare i comandi necessari per distribuire l'applicazione di condivisione RMS per questi scenari di distribuzione:

-   **Office 2016 o Office 2013 e Azure RMS o Active Directory RMS**

    Gli utenti eseguono Office 2016 o Office 2013, l'organizzazione utilizza Azure RMS o Active Directory RMS e gli utenti collaborano con altre organizzazioni che utilizzano Azure RMS o Active Directory RMS.

-   **Office 2010 e Azure RMS**

    Gli utenti eseguono Office 2010, l'organizzazione utilizza Azure RMS e gli utenti collaborano con altre organizzazioni che utilizzano Azure RMS o Active Directory RMS.

-   **Office 2010 e Active Directory RMS**

    Gli utenti eseguono Office 2010, l'organizzazione utilizza AD RMS e gli utenti collaborano con altre organizzazioni che utilizzano Azure RMS.

-   **Solo applicazione di condivisione RMS e componente aggiuntivo di Office**

    Gli utenti eseguono Office  2016, Office 2013 oppure Office 2010, l'organizzazione utilizza AD RMS e gli utenti non hanno bisogno di collaborare con altre organizzazioni che utilizzano Azure RMS. Questa installazione consente di installare solo l'applicazione di condivisione e il componente aggiuntivo di Office.

> [!NOTE]
> In questi scenari, se l'organizzazione esegue AD RMS, gli utenti possono ricevere il contenuto protetto da altre organizzazioni che utilizzano Azure RMS, ma gli utenti non possono inviare contenuti protetti agli utenti di un'organizzazione che utilizza Azure RMS. Tuttavia, se l'organizzazione esegue Azure RMS, gli utenti possono inviare e ricevere contenuto protetto da altre organizzazioni.

Per completare l'installazione per ogni procedura, è necessario riavviare il computer. È possibile avviare un'operazione di riavvio automatico tramite un comando, ad esempio shutdown /i.

#### Per distribuire l'applicazione di condivisione RMS per Office 2016 o Office 2013 e Azure RMS o Active Directory RMS

-   In ogni computer in cui si desidera installare l'applicazione di condivisione RMS e dei relativi componenti, eseguire il comando seguente con privilegi elevati:

    ```
    setup.exe /s
    ```

Per verificare l'esito positivo, vedere la sezione [Verificare l'esito positivo dell’installazione](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in questo argomento.

#### Per distribuire l'applicazione di condivisione RMS per Office 2010 e Azure RMS

1.  È necessario essere amministratore globale per il tenant di Office 365 o Azure Active Directory in modo che sia possibile ottenere l'URL del servizio di certificazione dell'organizzazione eseguendo lo strumento di preparazione di Azure Active Directory Rights Management. È necessario eseguire questo strumento una sola volta, in un singolo computer. Quando si installa l'applicazione di condivisione RMS in ogni computer, si utilizzerà l'URL del servizio di certificazione:

    1.  Accedere a un computer utilizzando un account amministratore locale.

    2.  In tale computer [scaricare e installare l’Assistente per l’accesso a Microsoft Online](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Eseguire il comando seguente per vedere visualizzato sullo schermo l'URL del servizio di certificazione, che è possibile poi copiare e salvare per il passaggio successivo:

        -   Per Windows 8.1 e Windows 8, a 64 bit:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Per Windows 8.1 e Windows 8, a 32 bit:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Per Windows 7, a 64 bit:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Questo comando potrebbe richiedere di immettere le credenziali per Azure. Se il computer non è unito a un dominio, verrà richiesto di farlo. Se il computer è unito a un dominio, lo strumento potrebbe essere in grado di utilizzare credenziali memorizzate nella cache.

2.  In ogni computer in cui si installerà l'applicazione di condivisione RMS, eseguire il comando seguente con privilegi elevati:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  In ogni computer in cui si installerà l'applicazione di condivisione RMS,gli utenti devono eseguire il comando seguente (non servono privilegi elevati). Esistono diversi modi per ottenere tale scopo, tra cui chiedere agli utenti di eseguire il comando (ad esempio, un collegamento in un messaggio di posta elettronica o un collegamento nel portale di supporto tecnico) oppure è possibile aggiungere i relativi script di accesso:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Per verificare l'esito positivo, vedere la sezione [Verificare l'esito positivo dell’installazione](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in questo argomento.

#### Per distribuire l'applicazione di condivisione RMS per Office 2010 e Active Directory RMS

1.  In ogni computer in cui si installerà l'applicazione di condivisione RMS, eseguire il comando seguente con privilegi elevati:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  In ogni computer in cui si installerà l'applicazione di condivisione RMS,gli utenti devono eseguire il comando seguente (non servono privilegi elevati). Esistono diversi modi per ottenere tale scopo, tra cui chiedere agli utenti di eseguire il comando (ad esempio, un collegamento in un messaggio di posta elettronica o un collegamento nel portale di supporto tecnico) oppure è possibile aggiungere i relativi script di accesso:

    -   Per Windows 10, Windows 8.1 e Windows 8, a 64 bit:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Per Windows 10, Windows 8.1 e Windows 8, a 32 bit:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Per Windows 7, a 64 bit:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Per verificare l'esito positivo, vedere la sezione [Verificare l'esito positivo dell’installazione](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in questo argomento.

#### Per installare solo l'applicazione di condivisione RMS e il componente aggiuntivo di Office

1.  Installare il Client AD RMS e l’applicazione di condivisione utilizzando il comando seguente:

    -   Per Windows a 64 bit:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Per Windows a 32 bit:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Ad esempio: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Installare il componente aggiuntivo di Office utilizzando i comandi seguenti:

    -   Per la versione a 64 bit di Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Per la versione a 32 bit di Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Ad esempio: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Per verificare l'esito positivo, vedere la sezione [Verificare l'esito positivo dell’installazione](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted) in questo argomento.

### <a name="BKMK_verifyscripted"></a>Verificare l'esito positivo dell’installazione
È possibile utilizzare i file di log di installazione per verificare la corretta installazione.

##### Per verificare l'esito positivo di installazione per l'applicazione di condivisione RMS per Office 2016 o Office 2013 e Azure RMS o Active Directory RMS

-   Per verificare l'esito positivo del comando Setup.exe, in ogni computer, cercare il file di log di installazione **RMInstaller.log** nella cartella *%temp%\RMS_installer_ &lt; guid &gt;*, poi individuare il codice di uscita.

    Una corretta installazione dispone di un codice di uscita pari a 0 e qualsiasi altro numero indica un'installazione non riuscita.

    Nome del file di log di esempio: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### Per verificare l'esito positivo di installazione per l'applicazione di condivisione RMS per Office 2010 e Azure RMS

1.  Per verificare l'esito positivo del comando Setup.exe, in ogni computer, cercare il file di log di installazione **RMInstaller.log** nella cartella *%temp%\RMS_installer_ &lt; guid &gt;*, poi individuare il codice di uscita.

    Una corretta installazione dispone di un codice di uscita pari a 0 e qualsiasi altro numero indica un'installazione non riuscita.

    Nome del file di log di esempio: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Per verificare l'esito positivo per il comando RMSSetup.exe, l'utente deve avere i seguenti file creati nella cartella *%localappdata%\microsoft\drm*:

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    Esempio di un file CLC-&#42;.drm:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

##### Per verificare l'esito positivo di installazione per l'applicazione di condivisione RMS per Office 2010 e Active Directory RMS

1.  Per verificare l'esito positivo del comando Setup.exe, in ogni computer, cercare il file di log di installazione nella cartella *%temp%\RMS_installer_&lt;guid&gt;*, individuare il codice di uscita.

    Una corretta installazione dispone di un codice di uscita pari a 0 e qualsiasi altro numero indica un'installazione non riuscita.

    Nome del file di log di esempio: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Per verificare l'esito positivo del comando aadrmprep.exe, in ogni computer, cercare il testo seguente nel file di log di installazione: **aadrmprep.exe si è concluso con lo status ESITO POSITIVO**

    > [!NOTE]
    > In alcuni casi, l'installazione può eseguire due volta; la prima occorrenza avrà esito negativo e il secondo esito positivo.

    Se si desidera controllare manualmente le modifiche del Registro di sistema fatte da questo strumento, sono:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;certification url&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

##### Per verificare l'esito positivo di installazione solo per l'applicazione di condivisione RMS e il componente aggiuntivo Office

1.  Per verificare l'esito positivo del comando Setup_ipviewer.exe, cercare il testo seguente nel file di log di installazione: **Stato di esito positivo o di errore nell’installazione: 0**

    Righe di esempio da un'installazione corretta:

    **MSI (s) (F0:B8) [14:19:57:854]: Prodotto: Active Directory Rights Management Services Client 2.1 - Installazione completata.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer ha installato il prodotto. Nome del prodotto: Client 2.1. di Active Directory Rights Management Services Versione del prodotto: 1.0.1179.1. Lingua del prodotto: 1033. Produttore: Microsoft Corporation Stato di esito positivo o di errore nell’installazione: 0.**

2.  Per verificare l'esito positivo del componente aggiuntivo Office, in ogni computer, cercare il testo seguente nel file di log di installazione: **Stato di esito positivo o di errore nell’installazione: 0**

    Righe di esempio da un'installazione corretta:

    **MSI (s) (9C:88) [18:49:04:007]: Prodotto: Componenti aggiuntivi di Office di Microsoft RMS - Installazione completata.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer ha installato il prodotto. Nome del prodotto: Componenti aggiuntivi di Office di Microsoft RMS. Versione del prodotto: 1.0.7. Lingua del prodotto: 1033. Produttore: Microsoft Stato di esito positivo o di errore nell’installazione: 0.**

### <a name="BKMK_uninstallscripted"></a>Disinstallare i comandi
Non tutti i comandi di installazione necessari per tali distribuzioni supportano un comando di disinstallazione. È possibile disinstallare il client AD RMS e l'applicazione di condivisione, ed è possibile disinstallare il componente aggiuntivo di Office. Utilizzare i comandi seguenti per disinstallare questi elementi.

##### Per disinstallare il Client AD RMS e l’applicazione di condivisione RMS

-   Utilizzare i seguenti comandi:

    -   Per Windows a 64 bit:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Per Windows a 32 bit:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### Per disinstallare il componente aggiuntivo di Office

-   Utilizzare i seguenti comandi:

    -   Per la versione a 64 bit di Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Per la versione a 32 bit di Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>Eliminazione degli aggiornamenti automatici
Per impostazione predefinita, gli utenti vengono informati se esiste una versione successiva di applicazione di condivisione RMS e viene loro chiesto di scaricarla. È possibile eliminare questa notifica apportando la seguente modificare al Registro di sistema:

1.  Passare a **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e, se non è già presente, creare una nuova chiave denominata **RmsSharingApp**.

2.  Selezionare **RmsSharingApp**, creare un nuovo valore DWORD di **AllowUpdatePrompt**, e impostare il valore su **0**.

Poiché l'applicazione di condivisione RMS non è supportata da WSUS, è possibile utilizzare la tecnica seguente per verificare le eventuali nuove versioni dell'applicazione di condivisione RMS prima di distribuirla a tutti gli utenti:

1.  Nei computer di tutti gli utenti, eseguire uno script per eliminare gli aggiornamenti automatici. Nei computer utilizzati dagli amministratori per verificare le nuove versioni, non eseguire questo script.

2.  Quando una nuova versione è disponibile, gli amministratori la scaricano e la testano.

3.  Quando il test è completo e i problemi sono risolti, distribuire la versione più recente a tutti gli utenti utilizzando le istruzioni di distribuzione automatica in questa Guida.

### <a name="BKMK_DocumentTracking"></a>Solo Azure RMS: Configurazione del rilevamento dei documenti
Se si dispone di una sottoscrizione [che supporta il rilevamento dei documenti](https://technet.microsoft.com/en-us/dn858608), il sito di rilevamento dei documenti è abilitato per impostazione predefinita per tutti gli utenti dell'organizzazione.  Il rilevamento dei documenti mostra informazioni quali indirizzi di posta elettronica delle persone che hanno tentato di accedere ai documenti protetti condivisi dagli utenti, nel momento in cui queste persone hanno tentato di accedere, e la loro posizione. Se la visualizzazione di queste informazioni non è consentita all'interno dell'organizzazione a causa dei requisiti sulla privacy, è possibile disabilitare l'accesso al sito di rilevamento dei documenti tramite il cmdlet [Disable AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032). È possibile riabilitare l'accesso al sito in qualsiasi momento, utilizzando il [Enable AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037), ed è possibile verificare se l'accesso è attualmente abilitato o disabilitato utilizzando [Get AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

 Per eseguire questi cmdlet, è necessario disporre di almeno la versione **2.3.0.0** del modulo Azure RMS per Windows PowerShell.  Per istruzioni sull'installazione, vedere [Installazione di Windows PowerShell per Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx).

> [!TIP]
> Se in precedenza è stato scaricato e installato il modulo, controllare il numero di versione eseguendo: `(Get-Module aadrm –ListAvailable).Version`

Gli URL seguenti vengono utilizzati per il rilevamento dei documenti e devono essere consentiti (ad esempio, aggiungerli ai siti attendibili se si utilizza Internet Explorer con protezione avanzata):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > questo URL è per Bing maps.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>Solo AD RMS: Supporto per più domini di posta elettronica all'interno dell'organizzazione
Se si utilizza AD RMS e gli utenti dell'organizzazione hanno più domini di posta elettronica, forse a causa di una fusione o di un’acquisizione, è necessario apportare la seguente modifica al Registro di sistema:

1.  Passare a **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e, se non è già presente, creare una nuova chiave denominata **RmsSharingApp**.

2.  Selezionare **RmsSharingApp**, creare un nuovo valore multistringa denominato **FederatedDomains**, e poi aggiungere i domini e i sotto-domini utilizzati dall'organizzazione. I caratteri jolly non sono supportati.

    Ad esempio: La società Coho Vineyard &amp; Winery dispone di un dominio di posta elettronica standard di **cohovineyardandwinery.com**, ma in seguito a delle fusioni, utilizza anche i domini di posta elettronica **cohowinery.com**, **eastcoast.cohowinery.com**, e **cohovineyard**. Per i dati del valore **FederatedDomains**, l'amministratore immette: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Se non si apporta questa modifica al Registro di sistema, gli utenti potrebbero non essere in grado di utilizzare contenuti protetti da altri utenti nella propria organizzazione. Questa modifica del Registro di sistema non è necessaria se si usa Azure RMS.

## <a name="BKMK_AdminOverview"></a>Panoramica tecnica per l'applicazione di condivisione Microsoft Rights Management
L'applicazione di condivisione Microsoft Rights Management è un'applicazione facoltativa scaricabile per Microsoft Windows e altre piattaforme e che fornisce le operazioni seguenti:

-   Protezione di un singolo file o la protezione di blocco di più file nonché di tutti i file all'interno di una cartella selezionata.

-   Supporto completo per la protezione di qualsiasi tipo di file e un visualizzatore integrato per tipi di file di testo e di immagini utilizzati di frequente.

-   Protezione generica per i file che non supportano la protezione RMS.

-   Completa interoperabilità con i file protetti tramite Office Information Rights Management (IRM).

-   Completa interoperabilità con i file PDF protetti con SharePoint, FCI e PDF supportati di strumenti di creazione.

L’applicazione di condivisione Rights Management di Microsoft utilizza il nuovo [runtime Client AD RMS 2.1](http://www.microsoft.com/download/details.aspx?id=38396). Utilizzando la funzionalità di AD RMS 2.1, l'applicazione di condivisione Rights Management di Microsoft consente agli utenti finali un'esperienza semplice di protezione e di utilizzo.

Con la versione di ottobre 2013 di RMS, è possibile proteggere i documenti utilizzando Office 2010 in modo nativo e inviarli a persone in un'altra società, che possono quindi utilizzarli tramite Azure RMS. Inoltre, con questa versione, se si utilizza AD RMS in modalità crittografia 2, è possibile usare RMS per utenti singoli e utilizzare il contenuto delle persone in un'altra società che utilizza Azure RMS. Per ulteriori informazioni sulla modalità crittografia 2, vedere [Modalità di crittografia di AD RMS](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

### <a name="BKMK_LevelsofProtection"></a>Livelli di protezione – nativo e generico
Applicazione di condivisione Rights Management di Microsoft supporta la protezione a due livelli diversi, come descritto nella tabella seguente.

|Tipo di protezione|Nativo|Generico|
|----------------------|----------|------------|
|Descrizione|Per file di testo, di immagine, di Microsoft Office (file di Word, Excel e PowerPoint), file .pdf e altri tipi di file di applicazione, che supportano AD RMS, la protezione nativa fornisce un forte livello di protezione che include crittografia e applicazione di diritti (autorizzazioni).|Per tutte le altre applicazioni e tipi di file, la protezione generica fornisce un livello di protezione che include sia l’incapsulamento di file mediante l'autenticazione e il tipo di file .pfile per verificare se un utente è autorizzato per aprire il file.|
|Protezione|I file sono completamente crittografati e la protezione viene applicata nei modi seguenti:<br /><br />-   Prima di eseguire il rendering del contenuto protetto, deve verificarsi la riuscita dell'autenticazione per coloro che ricevono file tramite posta elettronica o a cui viene concesso l'accesso a esso tramite le autorizzazioni di file o di condivisione.<br />-   Inoltre, i diritti di utilizzo e i criteri impostati dal proprietario del contenuto quando i file sono protetti vengono completamente applicate quando viene eseguito il rendering del contenuto nel Visualizzatore IP (per i file protetti di testo e immagine) o l'applicazione associata (per tutti gli altri tipi di file supportati).|La protezione dei file viene applicata nei modi seguenti:<br /><br />-   Prima di eseguire il rendering del contenuto protetto, l'autenticazione deve avere esito positivo per coloro che sono autorizzati ad aprire il file e a cui viene concesso l’accesso ad esso. Se l'autorizzazione ha esito negativo, il file non si apre.<br />-   I diritti di utilizzo e i criteri impostati dal proprietario del contenuto vengono visualizzati per informare gli utenti autorizzati circa i criteri di utilizzo previsti.<br />-   Si verifica la registrazione di controllo di utenti autorizzati per l’apertura e l'accesso ai file, tuttavia, non vengono applicati diritti di utilizzo da applicazioni non supportare.|
|Impostazione predefinita per i tipi di file|Questo è il livello predefinito di protezione per i tipi di file seguenti:<br /><br />-   File di testo e di immagine<br />-   File di Microsoft Office (Word, Excel, PowerPoint)<br />-   Formato di documento portatile (.pdf)<br /><br />Per altre informazioni, vedere la sezione di seguito. [Tipi di file supportati e le estensioni di nome di file](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes).|Questa è la protezione predefinita per tutti gli altri tipi di file (ad esempio .vsdx, .rtf e così via) non è supportata tramite protezione completa.|
È possibile modificare il livello di protezione predefinito che applica l'applicazione di condivisione RMS. È possibile modificare il livello predefinito da nativo a generico, da generico a nativo, e anche impedire l'applicazione di condivisione RMS dalla protezione di applicazione. Per altre informazioni, vedere la sezione [Modifica del livello di protezione predefinito dei file](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection) di questo argomento.

### <a name="BKMK_SupportFileTypes"></a>Tipi di file supportati e le estensioni di nome di file
Nella tabella seguente sono elencati i tipi di file supportati in modo nativo dall’applicazione di condivisione Rights Management di Microsoft. Per questi tipi di file, l'estensione del nome file originale viene modificato quando viene applicato il prodotto nativo, e questi file diventano di sola lettura.

Inoltre, quando l'applicazione di condivisione RMS protegge in modo nativo un file di Word, Excel o PowerPoint che gli utenti proteggono tramite la condivisione, questa azione crea automaticamente un secondo file che è una copia dell'originale con lo stesso nome ma con un’estensione del nome file **.ppdf** ¹. Questa versione del file garantisce che i destinatari che installano l'applicazione di condivisione RMS possano sempre aprire il file in cui è applicata la protezione nativa.

Per i file protetti in modo generico, l'estensione del nome file originale viene sempre modificata in .pfile.

> [!WARNING]
> Se si dispone di firewall, proxy web o software di protezione che esaminano e agiscono in base alle estensioni di file, potrebbe essere necessario riconfigurare tali impostazioni per supportare queste nuove estensioni di file.

|Estensione del nome di file originale|Estensione del nome di file protetti tramite RMS|
|-----------------------------------------|----------------------------------------------------|
|.txt|.ptxt|
|.xml|.pxml|
|.jpg|.pjpg|
|.jpeg|.ppng|
|.pdf|ppdf|
|.png|.ppng|
|.tiff|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jif|.pjif|
|.jt|.pjt|
Rendering PDF con tecnologia Foxit ¹. Copyright © 2003-2014, Foxit Corporation.

Nella tabella seguente sono elencati i tipi di file che l'applicazione di condivisione Microsoft Rights Management supporta in modo nativo in Microsoft Office 2016, Office 2013 e Office 2010. Per questi file, l'estensione del nome di file rimane invariato dopo che il file viene protetto da RMS.

|Tipi di file supportati da Office|Tipi di file supportati da Office|
|-------------------------------------|-------------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="BKMK_ChangeDefaultProtection"></a>Modifica del livello di protezione predefinito dei file
È possibile modificare come l’applicazione di condivisione RMS protegge i file modificando il Registro di sistema. Ad esempio, è possibile forzare i file che supportano la protezione nativa ad essere protetti in modo generico dall'applicazione di condivisione RMS.

Motivi per cui è possibile eseguire questa operazione:

-   Per garantire che tutti gli utenti possano aprire il file dai dispositivi mobili.

-   Per verificare che tutti gli utenti possano aprire il file se non dispongono di un'applicazione che supporta la protezione nativa.

-   Per ospitare i sistemi di sicurezza che intervengono sui file tramite l'estensione del nome di file e possono essere riconfigurati per adattare l'estensione .pfile ma non possono essere riconfigurati per gestire più estensioni di nome di file per la protezione nativa.

Analogamente, è possibile forzare l'applicazione di condivisione RMS ad applicare la protezione nativa ai file che per impostazione predefinita, avrebbero la protezione generica applicata . Questo potrebbe essere appropriato se si dispone di un'applicazione che supporta APIs RMS, ad esempio, un'applicazione line-of-business scritta per gli sviluppatori interni o un'applicazione acquistata da un fornitore di software indipendenti (ISV).

È inoltre possibile forzare l'applicazione di condivisione RMS per la protezione dei file di blocco (non si applica protezione nativa o protezione generica). Ad esempio, questa potrebbe essere necessaria se si dispone di un'applicazione automatica o di un servizio che deve essere in grado di aprire un file specifico per elaborare il relativo contenuto. Quando si blocca la protezione per un tipo di file, gli utenti non possono utilizzare l'applicazione di condivisione RMS per proteggere un file con il tipo di file. Quando tentano, viene visualizzato un messaggio in base al quale l'amministratore ha impedito la protezione ed è necessario annullare la loro azione per proteggere il file.

Per configurare l'applicazione di condivisione RMS per applicare la protezione generica a tutti i file che, per impostazione predefinita, avrebbe una protezione nativa applicata , apportare le seguenti modifiche al Registro di sistema:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Creare una nuova chiave denominata **&#42;**.

    Questa impostazione indica i file con qualsiasi estensione di file.

2.  Nella chiave appena aggiunta di **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\ &#42;**, creare un nuovo valore stringa (REG_SZ) denominato **crittografia** che ha il valore dei dati **Pfile**.

    Questa impostazione determina l’applicazione di condivisione RMS applicando la protezione generica.

Queste due impostazioni determinano l'applicazione di condivisione RMS applicando la protezione generica a tutti i file con estensione del nome di file. Se questo è l'obiettivo, non è richiesta alcuna ulteriore configurazione. Tuttavia, è possibile definire eccezioni per specifici tipi di file, in modo che siano protetti comunque in modo nativo. A tale scopo, è necessario eseguire tre modifiche aggiuntive del Registro di sistema per ogni tipo di file:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Aggiungere una nuova chiave con il nome dell'estensione di nome file (senza il punto iniziale).

    Ad esempio, i file con estensione del nome di file .docx, creano una chiave denominata **DOCX**.

2.  Nella chiave del tipo di file appena aggiunto (ad esempio, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), creare un nuovo valore DWORD denominato **AllowPFILEEncryption** con un valore di **0**.

3.  Nella chiave del tipo di file appena aggiunto (ad esempio, **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**), creare un nuovo valore stringa denominato **crittografia** con un valore di **nativo**.

In seguito a queste impostazioni, tutti i file sono protetti in modo generico ad eccezione dei file che dispongono di un'estensione di file con estensione .docx, che sono protetti in modo nativo per l'applicazione di condivisione RMS.

Ripetere questi tre passaggi per altri tipi di file che si desidera definire come eccezioni, in quanto supportano protezione nativa e non si desidera che possano essere genericamente protetti mediante l'applicazione di condivisione RMS.

È possibile apportare modifiche di registro di sistema simile per altri scenari modificando il valore della stringa **Crittografia** che supporta i seguenti valori:

-   **Pfile**: Protezione generica

-   **Nativo**: Protezione nativa

-   **Off**: Protezione di blocco

## Vedere anche
[Guida dell'utente dell'applicazione di condivisione Rights Management](../Topic/Rights_Management_sharing_application_user_guide.md)

