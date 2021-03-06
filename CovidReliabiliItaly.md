---
title: 'Covid-19 Data ReliabilIt(al)y: con quali numeri studieremo ciò che è successo?'
subtitle: 'Un approccio critico ai dati del monitoraggio ufficiale sulla diffusione della pandemia in Italia'
author:
- name: Emanuele Degani
  email: degani@stat.unipd.it
  affiliation: Università degli Studi di Padova
output:
  prettydoc::html_pretty:
    theme: leonids
    toc: yes
    highlight: null
    keep_md: true
---



## Contesto e motivazioni

E' il 30 gennaio 2020 quando i primi due casi di soggetti positivi al virus SARS-CoV-2 vengono rilevati in Italia: due turisti originari della provincia di Wuhan (Cina), che si trovavano in Italia dal 23 Gennaio, successivamente ricoverati in isolamento all'ospedale Spallanzani di Roma. Da quel giorno, le nostre vite sono state stravolte dalla necessità di fronteggiare una delle epidemie più letali dell'ultimo millennio: le parole distanziamento sociale, *lockdown*, tamponi, quarantena, isolamento, vaccini, sono diventate improvvisamente parte del linguaggio quotidiano e hanno costretto chiunque a dover riorganizzare la propria vita di conseguenza. La pagina [Pandemia di COVID-19 in Italia](https://it.wikipedia.org/wiki/Pandemia_di_COVID-19_in_Italia) rappresenta un diario dell'epidemia in Italia a partire dalla scoperta del primo *paziente zero* fino ad oggi.

Quanto sappiamo circa l'evoluzione dell'epidemia in Italia proviene dal **Monitoraggio Ufficiale** condotto dalla Protezione Civile, reso pubblico a partire dal 24 febbraio 2020. Chiunque ha in mente l'immagine della quotidiana conferenza stampa alle ore 17 presieduta dal Capo del Dipartimento della Protezione Civile Angelo Borrelli in cui si dava informazione ai media ed all'intera popolazione dei numeri ufficiali della pandemia: i nuovi positivi, i deceduti, i guariti, il numero di tamponi effettuati, etc... hanno messo di fronte il nostro paese alla **necessità di saper leggere ed interpretare questi dati**, e possibilmente di essere in grado di prevedere il loro andamento futuro sulla base delle decisioni prese dal Governo per arginare l'epidemia. Il monitoraggio ufficiale ha, nel suo insieme, una portata storica: sia per l'entità del fenomeno oggetto di studio, sia per la frequenza di aggiornamento, sia per la decisione di rendere accessibili a qualunque cittadino tali dati attraverso la loro quotidiana pubblicazione su una [*repository* pubblica](https://github.com/pcm-dpc/COVID-19). 

![*Il complicato processo di raccolta dei dati che porta alla quotidiana pubblicazione. La Figura è presa da https://github.com/pcm-dpc/COVID-19#aggiornamento-e-flusso-dei-dati.*](https://raw.githubusercontent.com/pcm-dpc/COVID-19/master/assets/img/dpc-covid19-flusso-dati-it.png)

Nelle settimane e mesi successivi scienziati, ricercatori, ingegneri, giornalisti, semplici cittadini e studiosi di tutto il mondo hanno usufruito dei dati raccolti all'interno di questa *repository* per raccontare con un approccio quantitativo l'evolvere della pandemia nel nostro paese, valutare l'efficacia delle misure di contenimento adottate (*lockdown*, introduzione del regime di suddivisione delle regioni in fascia di colore, etc...) e tentare di dare un racconto personale ai numeri. Con l'avanzare dei giorni, si è via via resa sempre più impellente la necessità di poter avere un'immediata comparazione grafica sull'andamento temporale delle variabili prese in esame: il [cruscotto geografico interattivo](https://opendatadpc.maps.arcgis.com/apps/dashboards/b0c68bce2cce478eaac82fe38d4138b1) costruito dal Dipartimento della Protezione Civile si è rivelato non sufficiente e di difficile consultazione, e sono nati numerosi portali, realizzati sia da privati cittadini che da redazioni di giornali, con lo scopo di **rendere i dati del contagio facilmente leggibili**, interpretabili e confrontabili con l'evolvere del tempo. Mi permetto di menzionare tra gli altri (e di certo uno tra i primi diffusosi a livello nazionale) [il lavoro del sottoscritto](http://achab94.shinyapps.io/covid-19/), che a partire dalla fine di Febbraio 2020 si aggiorna quotidianamente con i nuovi dati sul contagio resi disponibili dalla Protezione Civile. Da Marzo 2020 ad oggi quasi 90mila utenti diversi hanno consultato i grafici e le analisi che ho via via deciso di produrre ed approfondire a seconda delle esigenze del momento. Questi numeri raccontano quanto i media non siano stati in grado di raccontare in modo chiaro e semplice i numeri di questa pandemia: si è dovuto attendere mesi prima che i telegiornali riportassero il confronto del dato giornaliero sui nuovi contagi con quello alla settimana successiva ed al numero dei tamponi effettuati, e tuttora in molti faticano a raccontare con precisione il significato di ciascuna delle variabili che pubblicamente vengono aggiornate. 

Di particolare interesse, è la [sezione *Issues*](https://github.com/pcm-dpc/COVID-19/issues) di tale *repository*, contenente un considerevole numero di segnalazioni di errori di *data-entry* (molte delle quali poi risolte), discussioni tra utenti in merito all'**attendibilità** dei numeri forniti ed al significato associato, proposte di miglioramento e richieste relative al funzionamento della *repository*. Esemplare in tal senso è stata la [PR #847](https://github.com/pcm-dpc/COVID-19/pull/847) dell'utente @miccoli, che implementava un workflow automatizzato per l'individuazione di inconsistenze e/o errori del formato dei dati, **mai presa in considerazione**.

I numeri contenuti all'interno di questa *repository* rappresentano l'immagine ufficiale, scattata quotidianamente sui livelli nazionali, regionali e provinciali, dell'evolvere dell'epidemia e in quanto tale devono necessariamente essere precisi, coerenti e consistenti nel tempo. Trattandosi di **numeri ufficiali**, hanno l'obbligo di non poter ammettere alcun tipo di errore od incosistenza, per due ragioni di fondo: (1) questi dati sono quelli sui quali si svolge il **dibattito pubblico** e si costruiscono le **strategie decisionali** per tentare di arginare la pandemia; (2) questi dati sono la **fotografia** che lasceremo ai posteri di ciò che il nostro paese ha vissuto, giorno per giorno. **In alcun modo possiamo permetterci che questa fotografia sia sbiadita, confusa, illeggibile o di difficile consultazione** e, ancora peggio, che possa esserne messa in discussione la veridicità.

Lo scopo di questo lavoro è quello di fissare alcune delle principali **inconsistenze** ed errori che tutt'oggi, 04 Agosto 2021, esistono all'interno della *repository.* L'intenzione è quella di **sensibilizzare** e portare all'attenzione pubblica il rischio immenso che stiamo correndo: quello di non poter possedere in futuro di uno strumento affidabile che possa permettere di studiare, rappresentare e raccontare quanto vissuto nel nostro paese durante l'evolversi della pandemia. Un qualunque approccio quantitativo, presente o futuro, necessita infatti la disponibilità di **dati**, ovvero numeri che abbiano una loro interpretabilità, validità e coerenza nel tempo. 

Nel seguito, presento alcuni grafici che permettono di comprendere immediatamente alcune delle falle principali tutt'ora presenti nei dati ufficiali, allegando un commento personale. Il **focus** è unicamente sul **livello nazionale**, coi dati collezionati nel dataset `dpc-covid19-ita-andamento-nazionale.csv`, ma molte delle incongruenze hanno origine nei rispettivi sotto-livelli regionali e provinciali. 

Rimando a [questo link](https://github.com/pcm-dpc/COVID-19/blob/master/dati-andamento-covid19-italia.md) per ogni informazione sul formato dei dati pubblicati all'interno del monitoraggio ufficiale, sul loro livello di disaggregazione e sul significato di ciascuna variabile. Riporto inoltre il link delle [**note quotidiane**](https://github.com/pcm-dpc/COVID-19/blob/master/note/dpc-covid19-ita-note.csv) ufficiali che accompagnano l'aggiornamento giornaliero dei dati, all'interno delle quali vengono collezionate le comunicazioni inviate dagli enti regionali e/o provinciali in accompagnamento alla trasmissione quotidiana dei dati. Tali note sono uno strumento fondamentale, anche se di difficile consultazione, per la lettura e l'utilizzo dei dati.

Questa pagine, le analisi ed i grafici presentati sono stati realizzati utilizzando le librerie `rmarkdown`, `dplyr` e `ggplot2` di `R`. Il codice è interamente disponibile [a questa pagina](https://github.com/Achab94/covid19reliabil-italy/blob/main/CovidReliabiliItaly.Rmd), ed è chiaramente aperto a suggerimenti, critiche e contributi.

## L'evoluzione dei decessi giornalieri

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-1-1.png" style="display: block; margin: auto;" />

La prima variable che decido di prendere in esame è anche la più importante per comprendere l'entità devastante che l'epidemia ha avuto sulla popolazione italiana: il **numero di pazienti deceduti** a causa del virus. Il grafico mostra il conteggio giornaliero di tale variabile, un punto per ciascun giorno. La linea blu rappresenta un **lisciamento** della serie storica visualizzata, eseguito tramite una media mobile di ampiezza 7, e permette di cogliere più facilmente l'andamento *medio* della variabile nel tempo.

In rosso sono evidenziati due dati del tutto **inverosimili**. Il primo riguarda il numero di decessi giornalieri avvenuti il 24 Giugno 2020, che corrisponde a -31: un dato ovviamente errato per una variabile che, per sua natura, può assumere **solo valori positivi** (o tuttalpiù uguali a zero). Il secondo dato riguarda invece il 15 Agosto 2020 (Ferragosto) e, se corrispondesse alla realtà, corrisponderebbe ad un aumento di quasi 53 volte il dato del giorno precedente (passando da 3 a 158 decessi giornalieri). 

Andando a leggere le note quotidiane riferite al 15 Agosto 2020, si legge: 

> La Regione Emilia Romagna comunica che a seguito di una verifica interna dei dati sui decessi, la Ausl di Parma ha comunicato 154 decessi avvenuti in marzo, aprile e maggio e finora non conteggiati.

Una scelta del tutto **fuoriluogo** quella di rimediare ad un errore di conteggio assegnando la differenza di computo ad un giorno preciso, anzichè spalmarla nei giorni precedenti o, ancor meglio, aggiornare i dati dei mesi precedenti con il conteggio corretto. Nessuna nota permette invece di trovare una ragione che *giustifichi* il numero negativo di decessi in data 24 Giugno 2020.

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-2-1.png" style="display: block; margin: auto;" />

Un secondo aspetto molto curioso riguarda invece il cosiddetto **effetto wekeend** che si può osservare molto facilmente zoommando il grafico precedente sul sottoperiodo temporale riguardante la seconda ondata (da Ottobre 2020 a Giugno 2021, indicativamente) e colorando ciascun punto con un colore diverso, a seconda che quel giorno sia un giorno infrasettimanale (dal martedì al venerdì) o del weekend (sabato, domenica e lunedì, che comunque tiene parzialmente conto del conteggio accumulato la domenica sera ed il lunedì mattina stesso). La serie storica presenta una marcata oscillazione con periodicità settimanale, per la quale il martedì ed il giovedì sembrano i giorni della settimana in cui si osservano più decessi, mentre la domenica ed il lunedì quelli in cui se ne osservano di meno. Questo effetto non trova **alcuna corrispondenza scientifica**, com'è ovvio, ed è davvero inverosimile aspettarsi che il virus sia più letale in alcuni giorni della settimana e lo sia meno in altri. 

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-3-1.png" style="display: block; margin: auto;" />

La particolarità del fenomeno è ancora più evidente se si va a rappresentare la **somma** dei decessi registrati nei diversi giorni della settimana, per il sottoperiodo considerato nella figura precedente. In tale periodo, stante i numeri ufficiali, il martedì sono stati registrati circa 15000 decessi: **il 50\% in più** di quelli avvenuti di domenica (circa 10000).

Una spiegazione *plausibile*, per quanto comunque **metodologicamente inaccettabile**, è che in taluni casi (per determinate regioni e/o province) i conteggi sui decessi nei giorni del weekend avvengano in realtà nei giorni successivi, o addirittura che il consolidamento del conteggio avvenga durante la settimana per mancanza di personale durante il weekend. L'effetto oscillatorio dei decessi è un effetto spurio, che nulla ha che fare con il fenomeno in esame.

## L'evoluzione dei dimessi e guariti giornalieri

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-4-1.png" style="display: block; margin: auto;" />

Una seconda variabile di notevole importanza riguarda il numero quotidiano di **pazienti dimessi o guariti** dal virus.  Anche in questo caso, si registra un valore del tutto anomalo in data 15 Giugno 2021 corrispondente a 53074 pazienti dimessi o guariti in un solo giorno. Andando a leggere le [note giornaliere](https://github.com/pcm-dpc/COVID-19/blob/master/note/dpc-covid19-ita-note.csv) in tale data, si legge: 

> La Regione Campania riporta che, a seguito delle periodiche verifiche, si è riscontrato un disallineamento che, dopo un accurato e dettagliato controllo da parte delle ASL, ha evidenziato 48.078 soggetti ancora riportati erroneamente in "Isolamento Domiciliare" e che, pertanto, sono stati assegnati alla categoria "guariti".

La spiegazione motiva il dato anomalo, evidenziando peraltro un gravissimo errore sul conteggio dei pazienti trattati in isolamento domiciliare, ma **non dà alcuna valida ragione** sul perchè questo numero debba essere improvvisamente aggiunto al conteggio complessivo da un giorno all'altro, rendendo illeggibile la lettura complessiva dell'andamento di tale conteggio nel tempo. 

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-5-1.png" style="display: block; margin: auto;" />

Questo inserimento ha un effetto di inconsistenza anche sulle altre variabili collegate contenute all'interno del dataset: si veda ad esempio il grafico qui sopra che rappresenta la **variazione giornaliera sul numero totale dei pazienti positivi in un tale giorno**.

## Tamponi eseguiti e casi testati

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-6-1.png" style="display: block; margin: auto;" />

Un'altra variabile che è stata al centro del dibattito pubblico, in particolare durante la seconda ondata dell'epidemia, riguarda il **numero di tamponi effettuati ogni giorno**. Il grafico mostra l'evoluzione temporale di tale numero e, di nuovo, evidenzia un dato del tutto anomalo per questa variabile in data 17 Dicembre 2020, nella quale sarebbero stati eseguiti -47510 tamponi. Nessuna spiegazione viene data nelle note ufficiali della *repository* che, curiosamente, per quel giorno addirittura non esistono.

E' anche evidente un **cambio di regime** sul trend generale, avvenuto a metà Gennaio 2021 con l'introduzione nel conteggio del numero di tamponi effettuati dei test antigenici (i cosiddetti *tamponi rapidi*). In questo caso, la scelta dei manutentori della *repository* è stata quella di introdurre due nuove variabili, `tamponi_test_molecolare` e `tamponi_test_antigenico_rapido`, che a partire da quel momento conteggiassero quanti dei tamponi giornalieri effettuati appartenessero all'una o all'altra tipologia. Una scelta più corretta e coerente sarebbe stata dunque quella di eliminare la variable `tamponi`, aggregando i suoi valori precedenti alla metà di Gennaio 2021 alla variabile `tamponi_test_molecolare` (che in tal periodo ha entrate `NA`), ed introducendo come è stato fatto la variabile `tamponi_test_antigenico_rapido` che per sua natura ha iniziato il suo conteggio in tale periodo. L'attuale variabile `tamponi` sarebbe ugualmente ottenibile dalla somma delle due, e rischia di creare **inutile confusione**.

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-7-1.png" style="display: block; margin: auto;" />

Un fenomeno ancora più emblematico si verifica andando ad osservare il **numero giornaliero dei soggetti testati**, il cui monitoraggio è stato introdotto a partire dalla metà di Aprile 2020 e che per facilità mostro a partire da Maggio 2020. Nelle date 05 Dicembre 2020 e 06 Dicembre 2020, i dati ufficiali riportano che sono stati testati, rispettivamente, 894721 e -732995 casi. Questi numeri sono chiaramente privi di qualunque fondamento, per una variabile che per sua natura **non può assumere valori negativi** (si veda anche il dato anomalo in data 18 Dicembre 2020) e su una scala totalmente diversa rispetto all'andamento giornaliero, come si può notare dal grafico stesso.

Andando a leggere le [note quotidiane](https://github.com/pcm-dpc/COVID-19/blob/master/note/dpc-covid19-ita-note.csv) riferite al giorno 06 Dicembre 2020, si legge: 

> Il Molise comunica che il dato delle persone testate di ieri era 89.725 e non 897.250.

Un errore di *data-entry* facilmente risolvibile implementando un sistema di *data-checking* automatico quotidiano avrebbe **evitato** tutto questo. Ancora più grave, l'errore però è stato trascinato anche al giorno successivo di conseguenza: una volta essersi accorti dell'errore di comunicazione della regione Molise in data 05 Dicembre 2020, anzichè correggere il dato incorretto il giorno successivo, se ne è andati a commettere un secondo, eliminando la differenza tra 897250 e 89725 il giorno successivo. La conseguenza: l'introduzione di due valori tutt'ora totalmente infondati ed inconcludenti, dei quali si conosce la causa e il modo in cui correggerli adeguatamente.

Relativamente al dato anomalo in data 18 Dicembre 2020, dalle solite [note quotidiane](https://github.com/pcm-dpc/COVID-19/blob/master/note/dpc-covid19-ita-note.csv) si legge:

> La Regione Basilicata segnala che il dato delle persone testate è stato ricalcolato e verificato con la piattaforma regionale covid-19.

Una spiegazione del tutto insiddisfacente: ad esempio, a quanto corrisponde il ricalcolo?

## Il conteggio dei pazienti positivi e dei pazienti attualmente positivi

Una variabile che ha creato grande confusione riguarda il **conteggio dei soggetti positivi al virus**. Il dataset correttamente distingue due conteggi: la variabile `totale_casi`, che rappresenta la somma aggregata del numero di soggetti che hanno contratto il virus entro un tal giorno, e la variabile `totale_positivi`, che rappresenta il numero di soggetti che in un tal giorno sono *ancora* positivi al virus. Relativamente alla variabile `totale_positivi`, a partire dalla metà di Gennaio 2021 sono state anche introdotte due ulteriori variabili (`totale_positivi_test_molecolare` e `totale_positivi_test_antigenico_rapido`) che contano, quotidianamente, quanti dei pazienti sono stati rilevati positivi mediante test molecolare o test antigenico rapido. 

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-8-1.png" style="display: block; margin: auto;" />

E' di particolare interesse andare ad utilizzare questa distinzione nel conteggio per rapportarla con il numero di test molecolari e test antigenici rapidi, rispettivamente, ed ottenere un'**approssimazione dell'incidenza giornaliera alle due diverse tipologie di tampone**. Il grafico mostra l'evoluzione delle due serie storiche, con una marcata differenza nei due tassi di incidenza spiegabile dal fatto che la positività ad un test antigenico rapido deve essere confermata con un test molecolare. Evidenziamo due dati del tutto anomali: il tasso di incidenza dei positivi al test molecolare in data 22 Marzo 2021 e quello dei positivi al test antigenico rapido in data 24 Giugno 2021. 

Il primo riguarda un valore decisamente anomalo, **troppo alto** (significherebbe che in quel giorno più di un test molecolare su quattro effettuati è risultato positivo) ed è motivato dalla seguente nota pubblicata in tale giorno:

> La PA Bolzano comunica che a seguito di un ricalcolo dei dati è emerso che i test antigenici positivi confermati dall'esito del test molecolare eseguiti prima del 15.01.2021 non sono stati conteggiati fino ad oggi. Pertanto oggi vengono aggiunti 10692 unità ai casi confermati da test molecolare, di cui 27 risultati positivi in data 21.03.2021 e 10665 risultati positivi prima del 15.01.2021.

Il secondo riguarda invece un valore che fuorisce dal dominio naturale di esistenza di tale variabile, e deriva da un numero negativo di pazienti risultati positivi al test antigenico rapido in tale giorno. Anche in questo caso, la nota pubblicata aiuta a fare chiarezza:

> La Regione Veneto comunica che il dato dei casi confermati da test antigenico è diminuito rispetto a ieri in quanto i test confermati da molecolari sono stati ricollocati. L'incongruenza dei decessi (-3 rispetto a ieri) sembra da riferirsi ad una riattribuzione a decessi non covid correlati).

In entrambi i casi, si tratta di errori derivanti da riconteggi/riallocamenti che vengono erroneamente imputati ad un giorno preciso, anzichè essere spalmati nei giorni precedenti o, ancora meglio, essersi sforzati di andare a risalire al dato preciso dei giorni in esame.

## Il conteggio dei pazienti ricoverati in terapia intensiva

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-9-1.png" style="display: block; margin: auto;" />

Un'altra variabile di notevole importanza per capire l'andamento dell'impatto di ciascuna ondata epidemica riguarda il **conteggio dei pazienti ricoverati in terapia intensiva**. Nel grafico mostriamo la variazione giornaliera di tale numero: un valore positivo significa che in quel giorno sono entrate più persone in terapia intensiva di quante non ne sono uscite e, al contrario, un valore negativo significa che in quel giorno sono uscire più persone in terapia intensiva di quante non ne siano entrate. Per chiarità, puntualizzo che *l'uscita* corrisponde sia ad una guarigione/dimissione, che al decesso. 

Il saldo dell'occupazione delle terapie intensive in data 03 Novembre 2020 rappresenta un dato anomalo, come si può notare dal grafico. Le [note quotidiane](https://github.com/pcm-dpc/COVID-19/blob/master/note/dpc-covid19-ita-note.csv) della *repository* al giorno successivo, 04 Novembre 2020, riportano:

> La Regione Campania comunica che nei dati di ieri, per mero errore materiale, sono stati aggiunti 45 posti di Terapia Intensiva in più.

Si tratta dunque di un errore noto, dei quali ci si è accorti e si è consapevoli, ma che nessuno ha provveduto a correggere adeguatamente. 

## Il conteggio dei positivi in isolamento domiciliare

<img src="CovidReliabiliItaly_files/figure-html/unnamed-chunk-10-1.png" style="display: block; margin: auto;" />

In modo simile, andiamo a considerare il **saldo giornaliero dei soggetti positivi al virus che rimangono in auto-isolamento domiciliare**, ovvero che non vengono ospedalizzati. Il dato anomalo riguarda la data 15 Giugno 2021, la cui spiegazione è già stata affrontata nella sezione *L'evoluzione dei dimessi e guariti giornalieri*.

## Considerazioni finali

Gli esempi mostrati in questo approfondimento sono solo alcuni dei casi più lampanti che motivano la necessità di predisporre un'attività di riconsolidamento dell'intera *repository*. Andando a consultare le [note ufficiali della *repository*](https://github.com/pcm-dpc/COVID-19/blob/master/note/dpc-covid19-ita-note.csv) si può notare come, quotidianamente, esista una correzione e/o una segnalazione che va a supporto del dato specifico di una certa regione e/o provincia. Le cause sono di molteplice natura, ma hanno un **impatto** sul conteggio complessivo del dato nazionale e, di conseguenza, sulle principali variabili che vengono quotidianamente monitorate e commentate da giornali, telegiornali ed analisti. Ancora più grave, come ho mostrato, molte delle segnalazioni di errori sulla comunicazione dei dati da parte degli uffici regionali e/o provinciali **non vengono corrette**.

Come ho cercato di mostrare, in alcuni casi è possibile ricostruire una spiegazione riguardante l'esistenza di dati con valori anomali rispetto al loro trend storico e/o valori che fuoriescono dal dominio di definizione della variabile stessa. La spiegazione deve essere scovata all'interno delle note, che peraltro sono **redatte in italiano** (quindi del tutto inconsultabili dall'intera comunità scientifica internazionale), e certamente non sono di immmediata lettura e consultazione.

**In ogni caso, saper dare una spiegazione non significa accettare di conseguenza che questi dati siano una rappresentazione soddisfacente dell'evoluzione della pandemia in Italia**. Nonostante sia apprezzabile lo sforzo messo in atto dalla Presidenza del Consiglio dei Ministri e dal Dipartimento di Protezione Civile per rendere pubblicamente disponibili, con frequenza quotidiana, i *nuovi numeri dell'epidemia*, mi chiedo se questa scelta sia realizzabile in modo soddisfacente alla luce dei troppi errori di comunicazione, conteggio, consolidamento che gli uffici regionali e/o provinciali commettono e se, invece, non fosse più corretto pubblicare i dati giornalieri a distanza di qualche giorno e solo dopo aver realizzato un'opportuna attività di controllo del dato, consolidamento ed eventuale modifica rispetto ad errori di conteggio e/o trasmissione segnalati nei giorni successivi. 

Mi chiedo anche se, alla luce di alcuni degli esempi mostrati in questo approfondimento, sia davvero così necessario possedere il dato quotidiano per alcune delle variabili contenute all'interno del dataset. Mi riferisco ad esempio al conteggio dei tamponi effettuati e dei casi testati quotidianamente, due variabili per le quali è ben noto (ed evidente dai grafici che ho mostrato) una stagionalità di tipo settimanale che abbassa il loro conteggio nei giorni del fine settimana, in cui molte farmacie e hub sono chiusi al pubblico. Che senso ha possedere il numero di tamponi effettuati il martedì e la domenica, se questi due giorni non sono per nulla paragonabili? Non sarebbe meglio possedere il dato aggregato della settimana, o pubblicare il dato al quale è stato effettuato un lisciamento tramite media mobile o tecniche affini?

Le critiche mosse all'interno di queste righe hanno lo scopo di sensibilizzare e provare a smuovere una coscienza critica sull'errore che stiamo commettendo nell'accettare che il monitoraggio ufficiale di un fenomeno dalla portata storica come questo possa possedere falle, dati del tutto privi di fondamento, non coerenti con l'andamento storico della variabile di riferimento e, per taluni dei quali, senza avere alcuna spiegazione in merito sul perchè siano stati registrati, e dunque osservati. La sperenza è quella di riuscire a rendere il più possibile evidente come sia **necessario predisporre di un processo di revisione e consolidamento dei dati già pubblicati**, e contestualmente di un controllo quotidiano sull'attendibilità dei numeri che aggiornano la *repository*. Non possiamo ritrovarci un domani senza la capacità di spiegare alcune incongruenze presenti nei dati che vantano il titolo di essere ufficiali. E' un obbligo morale che il nostro paese deve sentire nei confronti di chi ha pagato più di tutti i risvolti drammatici di questa pandemia, e di quanti un domani si troveranno a studiare e tentare di approcciare scientificamente l'evoluzione dell'epidemia e l'impatto delle varie ondate nei territori del nostro paese. E' dunque auspicabile che una seria attività di analisi, consolidamento e *data-checking* vadano a motivare ad alcune di queste criticità, e conseguentemente a modificare a posteriori i dati osservati nei mesi precedenti. 

Il rischio nel non voler affrontare immediatamente questa questione, accettando che i dati osservati in passato siano veri in quanto tali, e non più modificabili, andrà a ripercuotersi nei prossimi mesi ed anni con l'incapacità di dare una risposta alle domande che inevitabilmente sorgeranno su alcune di tali incongruenze. 

Siamo ancora in tempo per aggiustare gli errori in corsa, tenendo anche conto che il monitoraggio prosegue tutto'ggi e, inevitabilmente, lo farà ancora per i prossimi mesi. E' un dovere che il nostro Paese ha nei confronti della comunità scientifica nazionale ed internazionale (quest'ultima, peraltro, non dispone di un facile accesso ai dati ed alla loro spiegazione in lingua inglese), e di quanti in futuro studieranno l'entità che la pandemia di Covid-19 ha avuto nel nostro paese, l'efficacia delle scelte pubbliche intraprese per tentare di agginarla, e gli effetti devastanti che ha avuto nel tessuto demografico italiano.

