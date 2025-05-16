---
connections:
  - "[[TPSIT]]"
---

Per ingegneria del software si intende tutta quella parte dell'informatica legata alla progettazione, produzione, riutilizzo e manutenzione degli applicativi finalizzata alla riduzione dei costi di produzione del software, migliorandone la qualità.

- Progettazione: studio di un problema e individuazione della soluzione informatica per risolverlo;
- Produzione: insieme delle fasi che portano a scrivere un programma in un linguaggio di programmazione e a renderlo funzionante per l'utente finale;
- Manutenzione: insieme delle attività di modifica e aggiornamento di un programma necessarie per poter continuare a usarlo nel tempo;
- Riutilizzo: possibilità di usare parti di programmi già realizzati per creare nuovi applicativi;

*Attori del Progetto*
Per attori si intendono quelle persone che a vario titolo sono coinvolte nel progetto e prendono il nome di stakeholder. Possiamo suddividerli in due gruppi principali:
- clienti: utilizzatori del sistema e/o committenti del lavoro. Tra i clienti possiamo inoltre distinguere:
	- cliente/utente: la persona che utilizzerà il sistema e che chiameremo utente finale;
	- cliente/committente: chi ha commissionato il lavoro e paga il sistema;
- fornitori: coloro che sviluppano e vendono il software come i commerciali delle aziende di software o i programmatori;

*Problemi*
I principali problemi che portano al fallimento nello sviluppo di un progetto sono:
- incomprensioni tra clienti e fornitori, in quanto le necessità dei clienti non vengono spesso comprese in modo adeguato dal fornitore;
- formalizzazione insufficiente delle decisioni, ovvero quando non viene formalizzato a sufficienza tutto ciò che è stato detto e deciso;

*Il Ciclo di Vita del Software*
Il **ciclo di vita del software** è l'insieme delle fasi che accompagnano un programma durante tutta la sua vita, dal momento in cui viene pensato al momento in cui viene cancellato perché non più utilizzato.

- Analisi preliminare;
- Progettazione del software;
- Realizzazione del software;
- Test, collaudo e rilascio in produzione;
- Termine del ciclo di vita del software;

## Il Ciclo di Vita del Software

**Analisi**
La fase di analisi è una delle attività fondamentali per la buona riuscita di un progetto informatico. Vista spesso solo come una formalità , rappresenta invece il punto di partenza e di riferimento. Durante la fase di analisi sono generati molti documenti, nei quali vengono formalizzate le informazioni che permettono di sviluppare il progetto.

Vengono effettuati vari tipi di analisi e a ciascuna di essa si associa uno specifico documento che ne riprende il nome, le principali sono:

*Analisi di Fattibilità*
È la fase di **analisi preliminare** che permette al PM, in collaborazione con il progettista e l'analista, di definire i primi obiettivi dell'applicazione richiesta o da proporre  a un committente. Il **Project Manager** è il responsabile del progetto, con funzioni di pianificazione, controllo e definizione delle attività che porteranno al risultato finale. L’analisi di fattibilità permette quindi al PM di capire se il progetto è realizzabile sia dal punto di vista tecnico, sia dal punto di vista economico. Produce normalmente un documento in cui si specificano i primi requisiti, vale a dire i vincoli funzionali o prestazionali.

*Analisi dei Requisiti*
Consiste nella **formalizzazione** di ciò che si vuole realizzare: in uno o più documenti si elencano e si dettagliano le funzionalità richieste dal cliente. Viene svolta da un'analista, sulla base di colloqui e interviste effettuati con il cliente.
I requisiti vengono classificati in due tipologie fondamentali:
- requisiti **funzionali**, essi descrivono i servizi o le funzioni offerti dal sistema che sono normalmente attivati da un'azione dell'utente;
- requisiti **non funzionali**, essi descrivono vincoli sui servizi offerti dal sistema, e sullo stesso processo di sviluppo;

La **corretta definizione dei requisiti** è una delle attività che determinano la riuscita di un progetto e che talvolta si tende erroneamente a sottovalutare. Applicarsi nella definizione dei requisiti è fondamentale per darsi la possibilità di analizzare a fondo il contesto e le problematiche organizzative e tecniche con cui ci si dovrà misurare nell'ambito del progetto.

I modelli di ciclo di vita del software moderni hanno abbandonato l’idea che sia possibile identificare i requisiti di un sistema software a priori: tendono a privilegiare approcci iterativi.

*Analisi dell'Interfaccia Utente*
L'interfaccia utente è quella componente di un sistema software che permette e abilita l'interazione e la comunicazione del sistema con gli utenti che lo utilizzano.
E una componente fondamentale del progetto software. Un sistema può infatti funzionare in modo eccellente, ma non aver successo a causa di una cattiva progettazione dell'interfaccia.

*Analisi dell'Architettura del Sistema*
Consiste in uno o più documenti che descrivono il modo in cui il progetto verrà realizzato. Definisce le componenti software da realizzare, cominciando a entrare nel merito della progettazione.

*Analisi dei Dati*
L'analisi dei dati è un processo di studio, verifica, ispezione, pulizia, trasformazione e infine di modellazione dei dati che il sistema informatico dovrà trattare. Questa attività è normalmente svolta da analisti esperti di basi si dati.

*Analisi dei Test*
Il testing del software ha lo scopo di individuare le carenze di correttezza, completezza e affidabilità delle componenti software in corso di sviluppo. 
Consiste nell'esecuzione del software da collaudare, da solo o in combinazione ad altro software di servizio, e nel valutare se il comportamento rispetta i requisiti. I documenti che descrivono l'analisi dei test contengono l'elenco dei casi che devono essere testati, indicando nel dettaglio le condizioni da riprodurre.

**Progettazione**

*Architettura di Progetto*
In questa fase viene impostata la soluzione generale definendo bene le strutture dei dati e descrivendo a grandi linee la struttura e il funzionamento di ogni componente che dovrà far parte del sistema.

*Disegno di Dettaglio*
Viene approfondito il progetto dal punto di vista realizzativo e vengono descritte le specifiche di dettaglio utilizzando un opportuno linguaggio di progetto. Vengono cioè descritte, per tutte le parti componenti il prodotto finale, le modalità di interazione con i dati e tra loro e gli algoritmi di funzionamento.

**Realizzazione**

*Programmazione*
Vengono codificate nel linguaggio di programmazione scelto le varie procedure e vengono effettuate le prime prove di funzionamento per eliminare gli errori più grossolani (sintattici e logici).

*Test*
Una volta analizzato, progettato e sviluppato il software, viene avviato un ciclo di test e collaudo, per verificarne la correttezza, ovvero la rispondenza ai vari requisiti definiti in fase di analisi.

*Integrazione e Test del Sistema*
Si eseguono dei test approfonditi e si integrano tra loro le differenti componenti del sistema. Si effettuano dei test per verificare se i moduli continuano a funzionare insieme agli altri.
Il testing non deve essere visto come un'attività affidata al caso, ma come un'attività sistematica che ha lo scopo di verificare tutti i modi di mandare in errore il software.

Per svolgerlo in modo corretto ed efficace e importante quindi:
- progettare e documentare una serie di casi di test;
- definire i risultati attesi;
- eseguire registrando i risultati ottenuti;
- confrontare quanto ottenuto con quanto atteso;

**Avvio di Produzione**

*Rilascio del Prodotto (release)*
Viene consegnato al committente il prodotto software completo e la relativa documentazione, compreso il manuale d'uso. Il sistema viene installato presso il cliente in quella che sarà la sua locazione definitiva.

*Collaudo*
Vengono effettuati test specifici con il personale del cliente e utilizzando dei dati di prove reali. A fronte di errori funzionali dovuti a incomprensioni e malintesi tra il committente e il progettista si provvede alla loro correzione. Si realizzano i primi corsi si istruzione per il personale del cliente.

*Avviamento*
Il sistema entra in produzione, cioè comincia a essere utilizzato concretamente dal cliente anche se in questa fase il fornitore affianca ancora per un certo periodo il cliente correggendo eventuali anomalie che dovessero emergere. Vengono avviati corsi più specifici e approfonditi.

**Manutenzione**
La fase di manutenzione accompagna la vita di un prodotto software da subito dopo il suo rilascio fino alla sua fine, cioè fino al momento in cui non verrà più visualizzato Vi sono varie tipologie di manutenzione.

*Manutenzione Correttiva*
La più diffusa attività di manutenzione si ha quando si evidenziano malfunzionamenti dovuti a casi particolari non sufficientemente testati o non considerati. È da ricordare che pur in presenza di test e prove molto approfondite, è sempre possibile che si presentino dei casi non previsti.

*Manutenzione Adattiva*
Un altro tipo di manutenzione è la modifica nel tempo di funzionalità esistenti per adeguarle alle mutate condizioni. Per esempio, quando si tratta di programmi gestionali e contabili, questi vanno adeguati alle variazioni fiscali, promulgazioni di nuove leggi o a mutate condizioni sociali.

*Manutenzione Evolutiva*
Vi è poi la manutenzione di tipo migliorativo o accrescitivo in cui vengono inserite nuove funzionalità che soddisfino nuove esigenze dell'utenza sorte dopo lo sviluppo del prodotto. Per esempio, il calcolo e la stampa di statistiche o nuovi prospetti, o la gestione automatica di attività svolte manualmente. Oppure ci si adegua a nuove tecnologie nate successivamente all'avvio del sistema. 

**Software di Qualità**
Tre sono le caratteristiche che deve avere un software per potersi definire di qualità:
- il prodotto deve rispecchiare fedelmente le reali necessità delle persone per cui il software è realizzato (il cliente);
- deve essere facilmente manutenibile in modo immediato e localizzato, senza sconvolgere l'organizzazione del sistema;
- deve essere ben documentato, sia per quanto riguarda il manuale utente, sia per tutta la documentazione di progetto;

Il software non è infatti solo un insieme di programmi, ma comprende anche tutta la documentazione per la definizione, lo sviluppo e la manutenzione degli stessi. Di questo fatto ci si dimentica e spesso si provvede alla stesura della documentazione solo a progetto finito, quando alcune delle informazioni sono ormai andate perse.

**Progettare il Software**
