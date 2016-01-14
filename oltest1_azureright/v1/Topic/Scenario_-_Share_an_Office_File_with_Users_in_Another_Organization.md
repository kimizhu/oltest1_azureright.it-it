---
description: na
keywords: na
title: Scenario - Share an Office File with Users in Another Organization
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10a4d7b-f57a-4a43-b66e-477777be59cc
---
# Scenario - Condivisione di un file di Office con utenti di un&#39;altra organizzazione
Questa sezione contiene istruzioni di amministrazione, un modello per le istruzioni per l'utente e un esempio di come potrebbero apparire le istruzioni per l'utente finale.Prima di poter assegnare la documentazione dell'utente finale ai propri utenti, è necessario completare le istruzioni per gli amministratori.

## Istruzioni per gli amministratori
![](../Image/AzRMS_AdminBanner.png)

Utilizzare queste istruzioni e il modello seguente per creare le proprie istruzioni per l'utente finale per consentire agli utenti di inviare in modo sicuro tramite posta elettronica un file di Office a persone in un'altra organizzazione.Il file di Office, ad esempio, potrebbe essere un documento di Word, un foglio di calcolo di Excel o una presentazione di PowerPoint contenente informazioni del listino prezzi di un partner, un elenco di prodotti per un rivenditore o un elenco dei tempi di consegna con potenziali clienti.Quando gli utenti seguono le istruzioni, il file allegato al messaggio di posta elettronica sarà protetto da Rights Management di Azure.

Le istruzioni sono adatte per il seguente set di circostanze:

-   Il dipendente deve inviare informazioni al di fuori dell'organizzazione, sotto forma di documento di Office.

-   Il documento contiene informazioni che non sono pubbliche, ma non sono esclusivamente per uso interno.

-   I destinatari non hanno i requisiti per condividere ulteriormente le informazioni con altri utenti, stamparle o utilizzarle come parte della propria documentazione.Se questo non si verifica, è possibile modificare le istruzioni modificando le autorizzazioni di sola visualizzazione in un'altra opzione che consenta al destinatario di modificare l'allegato.

-   Il dipendente è interessato a conoscere quando il documento viene aperto da un utente esterno.

Nelle istruzioni per l’utente che seguono, sostituire *&lt;nome del tipo di documento di Office &gt;* con il tipo di documento che gli utenti invieranno.Utilizzare termini specifici e familiari per i loro flussi di lavoro, ad esempio "listino", "tempi di consegna" e "proposta di offerta" anziché "documento di Word" e "foglio di calcolo di Excel".Sostituire anche *&lt;dettagli contatto&gt;* con istruzioni su come gli utenti possono contattare il supporto tecnico, ad esempio un collegamento di sito Web, indirizzo di posta elettronica o numero di telefono.

Successivamente, apportare ulteriori modifiche alle istruzioni e assegnare tali istruzioni agli utenti.Ad esempio, aggiungere il documento a un sito di SharePoint o inviarlo tramite posta elettronica.

Modifiche che è possibile apportare alle istruzioni:

-   Nel passaggio 2, suggeriamo **Visualizzatore - Solo visualizzazione** per le autorizzazioni, rendendo il documento allegato, ma non l'originale, di sola lettura per i destinatari.Se questa restrizione non è adatta per il proprio requisito aziendale, modificare questa opzione per un altro set di autorizzazioni, ad esempio **Revisore - Visualizzazione e modifica**.

-   Nel passaggio 3, è consigliabile selezionare **Consenti di revocare immediatamente l'accesso a questi documenti** in modo che non si verifichino ritardi se gli utenti revocano il documento in un secondo momento, ma questa opzione richiede che il destinatario abbia sempre una connessione a Internet per aprire l’allegato.Questo passaggio richiede anche di disporre di una sottoscrizione che supporti il rilevamento e la revoca dei documenti.Eliminare questo passaggio se non è adatto per gli utenti.

-   Nel passaggio 4, è consigliabile l'opzione **Invia un messaggio di posta elettronica quando qualcuno tenta di aprire il documento**.Se gli utenti tracciano i documenti utilizzando il portale di rilevamento dei documenti, è possibile decidere che la notifica tramite posta elettronica non è necessaria ed eliminare questo passaggio.

-   I passaggi non includono l'impostazione di una data di scadenza.Se l'allegato è urgente, aggiungere un altro passaggio per impostare una scadenza appropriata, ad esempio 90 giorni dall'invio del messaggio di posta elettronica.

> [!NOTE]
> Per ulteriori informazioni su ciascuna delle opzioni selezionabili dagli utenti, vedere [Opzioni della finestra di dialogo per l'applicazione di condivisione di Rights Management](https://technet.microsoft.com/library/dn574738.aspx)

## Requisiti per questo scenario
Affinché le istruzioni per l'utente per questo scenario funzionino, devono verificarsi le seguenti condizioni:

|Check|Requisito|Se sono necessarie ulteriori informazioni|
|---------|-------------|---------------------------------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Sono stati preparati account e gruppi per Office 365 o Azure Active Directory|[Preparazione per Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Azure Rights Management non è attivato|[Attivazione di Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|L’applicazione di condivisione Rights Management è distribuita nei computer degli utenti che eseguono Windows|[Distribuzione automatica dell'applicazione di condivisione Microsoft Rights Management](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Gli utenti dispongono di Outlook da Office 2013|Se gli utenti dispongono di Office 2010, sostituire la schermata con una versione equivalente, in modo che l'immagine corrisponda a ciò che gli utenti vedono.|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|La sottoscrizione di Azure RMS include il rilevamento dei documenti|Se la sottoscrizione per Azure RMS non include la revoca e il rilevamento dei documenti, gli utenti non saranno in grado di completare tutti i passaggi delle istruzioni per l’utente.In questo caso, acquistare una sottoscrizione che supporti queste funzionalità o modificare le istruzioni per l’utente per rimuovere i passaggi che utilizzano queste funzionalità.<br /><br />Per verificare il supporto della propria sottoscrizione: [Confronto tra le offerte di Rights Management Services (RMS)](https://technet.microsoft.com/dn858608)|

## Istruzioni per l’utente
Copiare e incollare le istruzioni seguenti per gli utenti finali e modificarle secondo le istruzioni dell’amministratore per questo scenario.La documentazione dell’esempio mostra come questo set di istruzioni apparire agli utenti, dopo le personalizzazioni.

![](../Image/AzRMS_UsersBanner.png)

#### Come condividere un &lt; nome del tipo di documento di Office&gt;

1.  Creare il messaggio di posta elettronica specificando l'indirizzo o gli indirizzi di posta elettronica, digitare il messaggio e allegare il *&lt;nome del tipo di documento di Office&gt;* al messaggio di posta elettronica.Quindi nella scheda **MESSAGGIO** fare clic su **Condividi file protetto** all’interno del gruppo **RMS**, quindi fare nuovamente clic su **Condividi file protetto**:

    ![](../Image/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  Nella finestra di dialogo **Condividi file protetto** selezionare **Visualizzatore - Solo visualizzazione**:

    ![](../Image/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Selezionare **Consenti di revocare immediatamente l'accesso a questi documenti**.

    ![](../Image/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Selezionare **Inviami un'e-mail quando qualcuno tenta di aprire questi documenti**:

    ![](../Image/AzRMS_SharedProtected_EmailMe.PNG)

5.  Fare clic su **Invia subito**:

    ![](../Image/AzRMS_ShareProtected_SendNow.PNG)

Quando un utente nella riga **A**, **Cc** o **Ccn** riceve questo messaggio di posta elettronica, viene visualizzato un messaggio che fornisce le istruzioni da seguire per leggere il *&lt;nome del tipo di documento di Office &gt;* allegato.Essi possono leggere il documento su diversi dispositivi, tra cui iPad, iPhone, tablet e telefoni Android, computer Mac e computer Windows.

Utilizzare il [portale di rilevamento dei documenti](https://track.azurerms.com/) per rilevare se e quando aprono il &lt;nome del tipo di documento di Office&gt; allegato.Considerare di contattarli con una chiamata telefonica di follow-up appena si nota che hanno aperto il &lt;nome del tipo di documento di Office&gt;.

**Serve assistenza?**

-   Per informazioni aggiuntive:

    -   [Protezione di un file che si condivide tramite posta elettronica](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Rilevamento e revoca di documenti](https://technet.microsoft.com/library/dn986611.aspx)

-   Contattare il supporto tecnico:

    -   *&lt;dettagli contatto&gt;*

### Esempio di documentazione per l’utente
![](../Image/AzRMS_ExampleBanner.png)

##### Come condividere un listino prezzi con il cliente

1.  Creare il messaggio di posta elettronica specificando l'indirizzo o gli indirizzi di posta elettronica, digitare il messaggio e allegare l’ultimo listino prezzi al messaggio di posta elettronica.Quindi nella scheda **MESSAGGIO** fare clic su **Condividi file protetto** all’interno del gruppo **RMS**, quindi fare nuovamente clic su **Condividi file protetto**:

    ![](../Image/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  Nella finestra di dialogo **Condividi file protetto** selezionare **Visualizzatore - Solo visualizzazione**:

    ![](../Image/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Selezionare **Consenti di revocare immediatamente l'accesso a questi documenti**.

    ![](../Image/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Selezionare **Inviami un'e-mail quando qualcuno tenta di aprire questi documenti**:

    ![](../Image/AzRMS_SharedProtected_EmailMe.PNG)

5.  Fare clic su **Invia subito**:

    ![](../Image/AzRMS_ShareProtected_SendNow.PNG)

Quando un utente nella riga **A**, **Cc** o **Ccn** riceve questo messaggio di posta elettronica, viene visualizzato un messaggio che fornisce le istruzioni da seguire per leggere il listino prezzi allegato.Essi possono leggere il documento su diversi dispositivi, tra cui iPad, iPhone, tablet e telefoni Android, computer Mac e computer Windows.

Utilizzare il [portale di rilevamento dei documenti](https://track.azurerms.com/) per rilevare se e quando aprono il listino prezzi allegato.Considerare di contattarli con una chiamata telefonica di follow-up appena si nota che hanno aperto il listino prezzi.

**Serve assistenza?**

-   Per informazioni aggiuntive:

    -   [Protezione di un file che si condivide tramite posta elettronica](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Rilevamento e revoca di documenti](https://technet.microsoft.com/library/dn986611.aspx)

-   Contattare il supporto tecnico:

    -   E-mail: helpdesk@vanarsdelltd.com

