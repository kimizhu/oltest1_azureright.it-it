---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Estensione di Active Directory Rights Management Services per dispositivi mobili
L'estensione Active Directory Rights Management Services (AD RMS) per dispositivi mobili viene eseguita sopra una distribuzione di AD RMS esistente. In questo modo gli utenti di dispositivi mobili possono proteggere e utilizzare dati riservati se il dispositivo supporta la versione più recente del client RMS e usa app abilitate per RMS. Ad esempio, gli utenti di questi dispositivi possono eseguire le operazioni seguenti:

-   Usare l'app di condivisione RMS per utilizzare file di testo protetti in formati diversi, ad esempio con estensione txt, csv e xml.

-   Usare l'app di condivisione RMS per utilizzare file di immagine protetti, ad esempio con estensione jpg, gif e tif.

-   Usare l'app di condivisione RMS per aprire qualsiasi file a cui sia stata applicata la protezione generica (formato pfile).

-   Usare l'app di condivisione RMS per proteggere i file di immagine nel dispositivo.

-   Usare un visualizzatore PDF per dispositivi mobili abilitato per RMS per aprire file PDF protetti con l'applicazione di condivisione RMS per Windows o con un'altra applicazione abilitata per RMS.

-   Usare altre app di fornitori di software che offrono app abilitate per RMS compatibili con tipi di file che supportano RMS in modo nativo.

-   Usare app abilitate per RMS sviluppate internamente e scritte con RMS SDK.

> [!NOTE]
> È possibile scaricare l'app di condivisione RMS dalla pagina [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) del sito Web Microsoft.
> 
> Per altre informazioni sui diversi tipi di file supportati da RMS, vedere la sezione [Tipi ed estensioni di file supportati](http://technet.microsoft.com/library/dn339003.aspx) della guida dell'amministratore dell'applicazione di condivisione Rights Management.

L'estensione per dispositivi mobili non è necessaria per utilizzare o creare messaggi di posta elettronica protetti nei dispositivi in cui si usano applicazioni di posta che supportano Exchange ActiveSync IRM. Questo supporto nativo per RMS e dispositivi mobili è stato introdotto con Exchange 2010 Service Pack 1.

Consultare le sezioni seguenti per distribuire l'estensione Active Directory Rights Management Services (AD RMS) per dispositivi mobili:

-   [Prerequisiti dell'estensione AD RMS per dispositivi mobili](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Configurare ADFS per l'estensione AD RMS per dispositivi mobili](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Configurare ADFS per l'estensione AD RMS per dispositivi mobili](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [Specificare il record DNS SRV per l'estensione AD RMS per dispositivi mobili](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Distribuire l'estensione AD RMS per dispositivi mobili](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Prerequisiti dell'estensione AD RMS per dispositivi mobili
Prima di installare l'estensione AD RMS per dispositivi mobili, assicurarsi che siano presenti le dipendenze seguenti.

|Requisito|Ulteriori informazioni|
|-------------|--------------------------|
|Distribuzione di AD RMS esistente in Windows Server 2012 R2 o Windows Server 2012. **Note:** AD RMS deve usare un database completo basato su Microsoft SQL Server in un server distinto e non il database interno di Windows che viene spesso usato per i test nello stesso server.|Per la documentazione su AD RMS, vedere [Active Directory Rights Management Services](http://technet.microsoft.com/library/hh831364.aspx) nella raccolta di documentazione su Windows Server.|
|ADFS distribuito in Windows Server 2012 R2|Per la documentazione su ADFS, vedere [Guida alla distribuzione di ADFS in Windows Server 2012 R2](http://technet.microsoft.com/library/dn486820.aspx) nella raccolta di documentazione su Windows Server.<br /><br />ADFS deve essere configurato per l'estensione per dispositivi mobili. Per le istruzioni, vedere la sezione [Configurare ADFS per l'estensione AD RMS per dispositivi mobili](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) di questo argomento.|
|Record SRV in DNS|Creare uno o più record SRV nel dominio o nei domini aziendali:<br /><br />-   Un record per ogni suffisso di dominio di posta elettronica che verrà usato dagli utenti<br />-   Un record per ogni nome FQDN usato dai cluster RMS per proteggere il contenuto<br /><br />Quando gli utenti specificano il loro indirizzo di posta elettronica dal dispositivo mobile, il suffisso di dominio viene usato per identificare se devono usare un'infrastruttura AD RMS o Azure RMS. Quando il record SRV viene trovato, i client vengono reindirizzati al server AD RMS che risponde a tale URL.<br /><br />Quando gli utenti utilizzano contenuto protetto con un dispositivo mobile, l'applicazione client cerca in DNS un record che corrisponde al nome FQDN nell'URL del cluster che ha protetto il contenuto. Il dispositivo viene quindi indirizzato al cluster AD RMS specificato nel record DNS e acquisisce una licenza per aprire il contenuto. Nella maggior parte dei casi, il cluster RMS sarà lo stesso che ha protetto il contenuto.<br /><br />Per informazioni su come specificare i record SRV, vedere la sezione [Specificare il record DNS SRV per l'estensione AD RMS per dispositivi mobili](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) di questo argomento.|
|Client attualmente supportati:<br /><br />-   Dispositivi Android con la versione più recente dell'app di condivisione RMS per Android|Versione minima di Android: 4.0.3.<br /><br />Scaricare l'app di condivisione RMS per Android dal sito [Microsoft Connect](https://connect.microsoft.com/site1170/Downloads) e trasferirla localmente nel dispositivo.|

### <a name="BKMK_ADFS"></a>Configurare ADFS per l'estensione AD RMS per dispositivi mobili
È necessario prima di tutto configurare ADFS e quindi autorizzare l'app di condivisione RMS per Android.

##### Passaggio 1: Configurare ADFS

-   È possibile eseguire uno script di Windows PowerShell per configurare automaticamente ADFS in modo da supportare l'estensione AD RMS per dispositivi mobili oppure specificare manualmente le opzioni e i valori di configurazione:

    -   Per configurare automaticamente ADFS, copiare e incollare quanto segue in un file di script di Windows PowerShell e quindi eseguirlo:

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Per configurare manualmente ADFS, usare queste impostazioni:

        |Configurazione|Valore|
        |------------------|----------|
        |**Trust della relying party**|api.rms.rest.com|
        |**Regola di attestazione**|**Archivio attributi**: Active Directory<br /><br />**Indirizzi di posta elettronica**: E-Mail-Address<br /><br />**User-Principal-Name**: UPN<br /><br />**Proxy-Address**: https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### Passaggio 2: Autorizzare l'app di condivisione RMS per Android

-   Per aggiungere il supporto per i dispositivi Android, eseguire il comando di Windows PowerShell seguente:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>Specificare il record DNS SRV per l'estensione AD RMS per dispositivi mobili
È necessario creare record DNS SRV per ogni dominio di posta elettronica che si vuole venga usato dagli utenti. Se tutti gli utenti usano domini figlio di un singolo dominio padre e tutti gli utenti di questo spazio dei nomi contiguo usano lo stesso cluster RMS, è possibile usare un solo record SRV nel dominio padre. RMS troverà i record DNS appropriati.

I record SRV hanno il formato seguente: _rmsdisco._http._tcp. *&lt;suffissopostaelettronica&gt;**&lt;numeroporta&gt;**&lt;FQDNclusterRMS&gt;*

Se ad esempio l'organizzazione ha utenti con gli indirizzi di posta elettronica seguenti:

-   utente@contoso.com

-   utente@sales.contoso.com

-   utente@fabrikam.com

e non ci sono altri domini figlio di contoso.com che usano un cluster RMS diverso da quello denominato **rmsserver.contoso.com**, creare due record DNS SRV con questi valori:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Oltre a questi record DNS SRV per i domini di posta elettronica, è necessario crearne un altro nei domini utente. Questo record deve specificare gli URL del cluster RMS che protegge il contenuto. Ogni file protetto con RMS include un URL del cluster che lo ha protetto. I dispositivi mobili usano il record DNS SRV e il nome FQDN dell'URL specificato nel record per trovare il cluster RMS in grado di supportarli.

Se ad esempio il cluster RMS è **rmsserver.contoso.com**, creare un record DNS SRV con i valori seguenti: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>Distribuire l'estensione AD RMS per dispositivi mobili
Prima di installare l'estensione AD RMS per dispositivi mobili, assicurarsi che siano presenti i prerequisiti descritti nella sezione precedente e che si conosca l'URL del server ADFS. Quindi procedere come segue:

1.  Scaricare l'estensione AD RMS per dispositivi mobili dal sito [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  Eseguire Setup.exe per avviare l'installazione guidata dell'estensione Active Directory Rights Management Services per dispositivi mobili.

3.  Quando richiesto, immettere l'URL del server ADFS configurato in precedenza.

4.  Completare la procedura guidata.

Eseguire questa procedura guidata in tutti i nodi del cluster RMS.

