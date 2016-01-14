---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Domande frequenti su Azure Rights Management
Alcune domande frequenti su Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], noto anche come Azure RMS:

## Quali sono i requisiti necessari e i passaggi da eseguire per distribuire Azure RMS?
Vedere innanzitutto l'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) contenente informazioni su opzioni di sottoscrizione cloud, modalità d'uso dei server locali con Azure RMS, scenari di distribuzione attualmente non supportati e applicazioni e dispositivi supportati da Azure RMS, e un collegamento se si ha bisogno di un elenco di indirizzi IP e di nomi di dominio per firewall o server proxy. Può essere utile consultare anche gli altri argomenti della sezione [Introduzione a Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md), per acquisire indicazioni di base su come [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] può aiutare a proteggere i dati dell'organizzazione, sul funzionamento del servizio con le applicazioni, sul confronto con la versione locale di Active Directory Rights Management e sui termini e le abbreviazioni specifiche di [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

Quando si è pronti per testare o distribuire Azure RMS per la propria organizzazione, usare la [Guida di orientamento per la distribuzione di Microsoft Azure Rights Management](../Topic/Azure_Rights_Management_Deployment_Roadmap.md), che contiene un elenco dei passaggi da eseguire, collegamenti ad altri argomenti e istruzioni procedurali.

Se sono necessarie informazioni, risorse e opzioni di supporto aggiuntive, vedere [Informazioni e supporto per Rights Management di Windows Azure](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

## È possibile integrare Azure RMS con il server locale?
Sì. Azure RMS può essere integrato con i server in locale, ad esempio Exchange Server, SharePoint e file server Windows. A tale scopo, si utilizza il [Connettore Rights Management](https://technet.microsoft.com/library/dn375964.aspx). In alternativa, se si è solo interessati all'uso della funzionalità Infrastruttura di classificazione file con Windows Server, è possibile usare i [cmdlet di protezione RMS](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). È inoltre possibile sincronizzare ed eseguire la federazione dei controller di dominio di Active Directory con Azure AD per un'esperienza di autenticazione più semplice per gli utenti, ad esempio utilizzando [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Azure RMS genera e gestisce automaticamente i certificati XrML come richiesto, quindi non utilizza un'infrastruttura PKI locale. Per ulteriori informazioni sull'utilizzo dei certificati in Azure RMS, vedere la sezione [Procedura dettagliata del funzionamento di Azure RMS: primo utilizzo, protezione del contenuto, uso del contenuto](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough) nell’argomento [Informazioni su Microsoft Azure Rights Management](../Topic/What_is_Azure_Rights_Management_.md).

## Dispongo di una distribuzione ibrida di Exchange con alcuni utenti su Exchange Online e altri su Exchange Server; questo è supportato da Azure RMS?
Assolutamente e l'aspetto interessante è che gli utenti saranno in grado di proteggere e utilizzare senza problemi messaggi di posta elettronica e allegati protetti con le due distribuzioni di Exchange. Per questa configurazione, [attivare Azure RMS](https://technet.microsoft.com/library/jj658941.aspx) e [abilitare IRM per Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), quindi [distribuire e configurare il connettore RMS](https://technet.microsoft.com/library/dn375964.aspx) per Exchange Server.

## Se distribuisco Azure RMS nell'ambiente di produzione, la mia azienda è bloccata nella soluzione o esiste il rischio di perdere l'accesso ai contenuti protetti con Azure RMS?
No, si ha sempre il controllo dei dati e si può continuare ad accedere ad essi, anche se si decide di non usare più Azure RMS. Per altre informazioni, vedere [Rimozione delle autorizzazioni e disattivazione di Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md).

Tuttavia, prima di disabilitare la distribuzione di Azure RMS, desideriamo sapere e comprendere il motivo per cui è stata presa questa decisione. Se Azure RMS non soddisfa i requisiti aziendali, contattarci se sono previste nuove funzionalità per l’immediato futuro o se esistono alternative. Inviare un messaggio di posta elettronica a [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) e saremo lieti di discutere i requisiti tecnici e aziendali.

## È possibile determinare quali utenti possono usare Azure RMS per proteggere i contenuti?
Sì, Azure RMS include controlli di selezione utenti per questo scenario. Per ulteriori informazioni, vedere la sezione [Configurazione dei controlli di selezione utenti per una distribuzione graduale](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls) dell’argomento [Attivazione di Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md).

## È possibile impedire agli utenti di condividere documenti protetti con aziende specifiche?
Uno dei vantaggi principali offerti da Azure RMS è il supporto della collaborazione business-to-business senza che sia necessario configurare trust espliciti per ogni azienda partner, in quanto l'autenticazione viene eseguita automaticamente da Azure AD.

Non sono disponibili opzioni di amministrazione che consentano di impedire agli utenti di condividere documenti in modo sicuro con aziende specifiche. Si supponga, ad esempio, di voler bloccare un'azienda che non si considera attendibile o una società concorrente. Impedire ad Azure RMS di inviare documenti protetti agli utenti di queste società non ha alcuna utilità, in quanto gli utenti condividerebbero i documenti in modalità non protetta, con maggiori rischi per l'azienda stessa. Inoltre, non sarebbe possibile identificare gli utenti che condividono i documenti aziendali riservati e i rispettivi destinatari in queste aziende, mentre questo è possibile quando i documenti o i messaggi di posta elettronica sono protetti tramite Azure RMS.

## Quando condivido un documento protetto con qualcuno all'esterno della mia azienda, come viene autenticato questo utente?
Azure RMS utilizza sempre un account di Azure Active Directory e un indirizzo di posta elettronica associato per l'autenticazione utente, semplificando la collaborazione business-to-business per gli amministratori. Se l'altra organizzazione utilizza i servizi di Azure, gli utenti avranno già account in Azure Active Directory, anche se questi account vengono creati e gestiti in locale e poi sincronizzati in Azure.  Se l'organizzazione dispone di Office 365, dietro le quinte, questo servizio utilizza anche Azure Active Directory per gli account utente.  Se l'organizzazione dell'utente non dispone di account gestiti in Azure, gli utenti possono iscriversi ad [RMS per utenti singoli](https://technet.microsoft.com/library/dn592127.aspx), che consente di creare un tenant e una directory di Azure non gestiti per l'organizzazione con un account per l'utente, in modo che questo utente possa quindi essere autenticato per Azure RMS.

Il metodo di autenticazione per questi account può variare a seconda di come l'amministratore dell’altra organizzazione ha configurato gli account di Azure Active Directory. Ad esempio, è possibile utilizzare password create per questi account, Multi-Factor Authentication (MFA), la federazione o password create in servizi di dominio di Active Directory e quindi sincronizzate con Azure Active Directory.

## È possibile aggiungere utenti all'esterno della mia azienda per i modelli personalizzati?
Sì.  La creazione di modelli personalizzati che gli utenti finali (e gli amministratori) possono scegliere dalle applicazioni rende rapida e semplice l’applicazione della protezione delle informazioni, attraverso i criteri specificati. Una delle impostazioni nel modello riguarda chi è in grado di accedere al contenuto ed è possibile specificare utenti e gruppi all'interno dell'organizzazione e utenti al suo esterno.

Per specificare utenti all'esterno dell'organizzazione, usare il [modulo Windows PowerShell per Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx).

-   **Usare un oggetto di definizione dei diritti per creare o aggiornare un modello**:    specificare gli indirizzi di posta elettronica esterni e i relativi diritti in un oggetto di definizione dei diritti, che verrà quindi usato per creare o aggiornare un modello. È possibile specificare l'oggetto di definizione dei diritti usando il cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) per creare una variabile e quindi fornire questa variabile al parametro -RightsDefinition con il cmdlet [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) (per un nuovo modello) o [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) (per modificare un modello esistente). Tuttavia, se si stanno aggiungendo questi utenti a un modello esistente, sarà necessario definire gli oggetti di definizione dei diritti per i gruppi esistenti nei modelli e non solo gli utenti esterni.

Per altre informazioni sui modelli personalizzati, vedere [Configurazione di modelli personalizzati per Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

## Quali dispositivi e quali tipi di file sono supportati da Azure RMS?
Per un elenco dei dispositivi supportati, vedere la sezione [Dispositivi client che supportano Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices) dell'argomento [Requisiti per Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md). Dal momento che non tutti i dispositivi supportati consentono l'uso di tutte le funzionalità RMS, consultare anche la tabella [Funzionalità del dispositivo client](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities) nello stesso argomento.

Azure RMS supporta tutti i tipi di file. Per file di testo, di immagine, di Microsoft Office (file di Word, Excel e PowerPoint), file .pdf e alcuni altri tipi di file di applicazione, Azure RMS fornisce protezione nativa, incluse crittografia e applicazione di diritti (autorizzazioni). Per tutte le altre applicazioni e tipi di file, la protezione generica fornisce funzionalità di incapsulamento e autenticazione dei file che consentono di verificare se un utente è autorizzato ad aprire il file.

Per un elenco delle estensioni di file supportate in modo nativo da Azure RMS, vedere la sezione [Tipi di file e estensioni di file supportati](http://technet.microsoft.com/library/dn339003.aspx) della [Guida dell'amministratore dell'applicazione di condivisione Rights Management](http://technet.microsoft.com/library/dn339003.aspx). Le estensioni di file non incluse nell'elenco sono supportate mediante l'uso dell'applicazione RMS sharing, che applica automaticamente la protezione generica a tali file.

## Quando verrà supportata la migrazione da AD RMS?
La migrazione da una distribuzione locale di Rights Management, ad esempio AD RMS, non è stata supportata nelle versioni iniziali di Azure RMS, ma è attualmente supportata.

Per altre informazioni, vedere [Migrazione da AD RMS ad Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

## Desideriamo davvero utilizzare BYOK con Azure RMS, ma abbiamo appreso che non è compatibile con Exchange Online, cosa consigliate?
Non lasciare che questa limitazione attuale ritardi la distribuzione di Azure RMS. Se si dispone di Exchange Online e si desidera utilizzare BYOK, si consiglia di distribuire Azure RMS nella modalità predefinita per la gestione delle chiavi, con cui Microsoft genera e gestisce la chiave. In questo modo, si ottengono ora tutti i vantaggi della protezione di file e messaggi di posta elettronica importanti, con l'opzione per passare a BYOK in un secondo momento (ad esempio, quando Exchange Online supporterà BYOK).

Tuttavia, se i criteri aziendali richiedono di utilizzare un modulo di protezione hardware (HSM) e ciò altrimenti bloccherebbe la distribuzione di Azure RMS, un'altra opzione consiste nel distribuire Azure RMS con BYOK ora, con funzionalità di RMS ridotte per Exchange. Per ulteriori informazioni, vedere la sezione [Prezzi e restrizioni della modalità BYOK](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) dell’argomento [Pianificazione e implementazione della chiave del tenant di Azure Rights Management](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

## Una funzionalità che cerco non sembra funzionare con le librerie protette di SharePoint, è previsto il supporto per la mia funzionalità?
Attualmente, SharePoint supporta documenti protetti da RMS utilizzando le librerie protette IRM, che non supportano i modelli personalizzati, il rilevamento dei documenti e alcune altre funzionalità.  Per altre informazioni, espandere la sezione [SharePoint Online e OneDrive for Business: configurazione di IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) nell'argomento [Supporto di Microsoft Azure Rights Management da parte delle applicazioni](../Topic/How_Applications_Support_Azure_Rights_Management.md).

Se si è interessati a una funzionalità specifica che non è ancora supportata, assicurarsi di controllare gli annunci nel [blog del team RMS](http://blogs.technet.com/b/rms/).

## Come è possibile configurare One Drive for Business in SharePoint Online, in modo che gli utenti possano condividere i propri file in modo sicuro con le persone all'interno e all'esterno della società?
Per impostazione predefinita, in qualità di amministratore di Office 365, non si configura questo oggetto. L'operazione viene eseguita dagli utenti.

Proprio come gli amministratori del sito di SharePoint abilitano e configurano IRM per una raccolta di SharePoint che possiedono, OneDrive for Business è progettato per consentire agli utenti di attivare e configurare IRM per la propria raccolta OneDrive for Business.  Tuttavia, usando PowerShell, è possibile eseguire questa operazione per gli utenti. Per istruzioni, espandere la sezione [SharePoint Online e OneDrive for Business: configurazione di IRM](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline) nell'articolo [Configurazione di applicazioni per Rights Management di Windows Azure](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

## Sono disponibili suggerimenti per una corretta distribuzione di RMS?
Dopo aver supervisionato un elevato numero di distribuzioni e ascoltato il parere di clienti, partner, consulenti e tecnici del servizio di supporto, uno dei principali suggerimenti che possiamo fornire è **Progettare e distribuire criteri semplici per i diritti d'uso**.

Poiché Azure RMS supporta la condivisione sicura dei dati con qualsiasi utente, si possono raggiungere livelli di protezione delle informazioni molto elevati, ma bisogna impostare criteri rigorosi per i diritti d'uso. Per la maggior parte delle organizzazioni, l'impatto maggiore risulta dall'esigenza di impedire la perdita dei dati applicando il modello predefinito dei criteri per i diritti d'uso che limita l'accesso agli utenti dell'organizzazione. Si possono anche applicare criteri più specifici, ad esempio impedire agli utenti di stampare o modificare documenti, ma è preferibile impostarli solo per documenti che richiedono un alto livello di sicurezza. Evitare di applicare tutti questi criteri più restrittivi in un'unica soluzione pianificandone invece un approccio per fasi.

## Quali funzionalità possono o non possono essere usate con le diverse sottoscrizioni per Azure RMS?
Le funzionalità RMS supportate presentano alcune differenze per le diverse sottoscrizioni a pagamento che supportano Azure RMS (Office 365, Azure RMS Premium ed Enterprise Mobility Suite). Per un elenco, vedere [Confronto tra le offerte di Rights Management Services (RMS)](http://technet.microsoft.com/dn858608)

La sottoscrizione gratuita che supporta Azure RMS (RMS per utenti singoli) supporta l'utilizzo di contenuti protetti da Azure RMS. Per altre informazioni, vedere [RMS per utenti singoli e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Dov'è possibile trovare informazioni tecniche sulla sottoscrizione Azure RMS gratuita (RMS per utenti singoli), ad esempio il suo funzionamento, come assumere il controllo degli account e quali sono i domini che non è possibile usare?
Le risposte a queste domande sono disponibili nell'argomento [RMS per utenti singoli e Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md).

## Come possiamo riottenere l'accesso ai file che sono stati protetti da un dipendente che ora ha lasciato l'organizzazione?
Utilizzare la funzionalità per utenti con privilegi avanzati di Azure RMS, che consente agli utenti autorizzati di disporre di diritti completi di proprietario per tutte le licenze d'uso che sono state concesse dal tenant RMS dell'organizzazione. Questa stessa funzionalità consente ai servizi autorizzati di indicizzare e analizzare i file, in base alle esigenze.

Per altre informazioni, vedere [Configurazione degli utenti con privilegi avanzati per Rights Management di Azure e servizi di individuazione o ripristino dei dati](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

## Rights Management può impedire l'acquisizione di schermate?
Rights Management blocca l'acquisizione di schermate dalla maggior parte degli strumenti di acquisizione di schermate usati comunemente, contribuendo a evitare la divulgazione accidentale o per negligenza di informazioni riservate o sensibili. Tuttavia, vi sono molti modi in cui un utente può condividere i dati visualizzati sullo schermo e acquisire una schermata è solo uno di questi metodi. Ad esempio, un utente che desidera condividere informazioni visualizzate può scattare una foto dei dati con la fotocamera del telefono, ridigitarli o semplicemente comunicarli verbalmente a qualcuno.

Come dimostrano questi esempi, la tecnologia da sola non sempre può impedire la condivisione non autorizzata dei dati da parte degli utenti. Anche se Rights Management può contribuire a salvaguardare i dati importanti tramite i criteri di autorizzazione e per l'uso, questa soluzione Enterprise Rights Management deve essere usata insieme ad altri controlli. Ad esempio, implementare la sicurezza fisica, selezionare e monitorare attentamente le persone che hanno accesso in modo autorizzato ai dati dell'organizzazione e investire nella formazione degli utenti per aiutarli a capire quali dati non devono essere condivisi.

## Dov'è possibile reperire le informazioni di supporto per Azure RMS, ad esempio le note legali, le informazioni sulla conformità e i contratti di servizio?
Azure RMS supporta altri servizi e si basa inoltre su altri servizi. Per informazioni correlate ad Azure RMS, ma non riferite alla modalità di utilizzo del servizio Azure RMS, esaminare le risorse seguenti:

**Note legali e privacy:**

-   Per informazioni sul contratto di Microsoft Azure: [Contratto di Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Per informazioni sulla privacy di Microsoft Azure: [Informativa sulla privacy di Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Sicurezza, conformità e controllo:**

Vedere la sezione [Requisiti di sicurezza, conformità e normativi](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance) nell'argomento [Informazioni su Microsoft Azure Rights Management](../Topic/What_is_Azure_Rights_Management_.md). Inoltre:

-   Per le certificazioni esterne per Azure RMS: [Centro protezione di Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

-   Per informazioni su FIPS 140: [Convalida di FIPS 140](https://technet.microsoft.com/library/security/cc750357.aspx)

**Contratti di servizio:**

-   Contratto di servizio per Azure RMS, in base al paese selezionato: [Contratto di servizio](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Contratto di servizio per Azure Active Directory: [Contratti di servizio](http://azure.microsoft.com/support/legal/sla/)

**Documentazione:**

-   Sito della documentazione di Azure Active Directory: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Libreria di Azure Active Directory: [Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Libreria di Office 365: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Cosa fare se la domanda non è presente?
Usare i collegamenti e le risorse elencati in [Informazioni e supporto per Rights Management di Windows Azure](../Topic/Information_and_Support_for_Azure_Rights_Management.md).

Inoltre, esistono Domande frequenti progettate per gli utenti finali:

-   [Domande frequenti sull'applicazione di condivisione Rights Management per Windows](https://technet.microsoft.com/dn467883)

-   [Domande frequenti sull'applicazione di condivisione Rights Management per piattaforme mobili e Mac](https://technet.microsoft.com/dn451248)

-   [Domande frequenti relative al rilevamento dei documenti](http://go.microsoft.com/fwlink/?LinkId=523977)

La pagina delle domande frequenti verrà aggiornata periodicamente e le nuove aggiunte saranno pubblicate negli annunci mensili di aggiornamento della documentazione sul blog del [team di Microsoft Rights Management (RMS)](http://blogs.technet.com/b/rms/).

> [!TIP]
> È possibile utilizzare il [tag dei documenti](http://blogs.technet.com/b/rms/archive/tags/docs/) sul blog, per trovare più facilmente questi annunci.

## Vedere anche
[Introduzione a Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

