---
connections:
  - "[[TPSIT]]"
---

#  Cos'è l'Ingegneria del Software

L’ingegneria del software è una disciplina dell’informatica che si occupa dello **sviluppo sistematico, controllato e documentato del software**, trattando quest’ultimo **non come un semplice codice**, ma come un **prodotto complesso** da progettare, costruire e mantenere nel tempo.

### Obiettivi principali:

- Realizzare software **affidabili**, **efficienti** e **manutenibili**;
- Ridurre i **costi di produzione e gestione**;
- Favorire il **riuso del codice** e l’evoluzione del sistema;
- Garantire **qualità** e **aderenza ai requisiti del cliente**.

Un software include:

- Codice sorgente (uno o più programmi),
- Documentazione tecnica e funzionale,
- Manuali per l’utente e per la manutenzione,
- Specifiche per test e collaudo.

---

# Il Ciclo di Vita del Software

Il **ciclo di vita del software** (_Software Development Life Cycle - SDLC_) rappresenta l’intero processo che va dalla nascita di un’idea alla dismissione del prodotto. È composto da fasi ben precise, che garantiscono ordine, qualità e tracciabilità. Le fasi principali del progetto possono essere seguite secondo modelli di processo diversi, come:

- **Modello a cascata** (waterfall): sequenziale, semplice ma rigido;
- **Modello a V**: aggiunge verifiche e validazioni per ogni fase;
- **Modello incrementale**: lo sviluppo avviene per fasi successive;
- **Modello agile (es. Scrum)**: cicli brevi, collaborazione continua, adattabilità ai cambiamenti.

---

##  1. Fase di Analisi

L’obiettivo dell’analisi è **capire cosa vuole il cliente** e tradurlo in specifiche precise. È una delle fasi più delicate, perché ogni errore si riflette sull’intero progetto. Inoltre è bene specificare che **correggere un errore in fase di esercizio può costare fino a 200 volte di più** rispetto a intercettarlo durante l’analisi, come afferma **Barry Boehm**. Da ciò emerge l'importanza di investire in una raccolta e validazione dei requisisti efficace, di non sottovalutare il design architetturale e di evitare dei salti prematuri nella programmazione.

### Tipi di analisi:

- **Fattibilità**: valuta costi, benefici, tempi, tecnologie, rischi;
- **Requisiti funzionali**: cosa deve fare il sistema;
- **Requisiti non funzionali**: prestazioni, sicurezza, usabilità, compatibilità;
- **Interfaccia utente**: modalità d'interazione uomo-macchina;
- **Analisi dei dati**: informazioni da gestire, loro struttura e flussi;
- **Test strategy**: definizione dei test sin dall'inizio (approccio TDD - Test Driven Development).

Per effettuare quest'analisi si usano dei particolari strumenti come l'UML (Unified Modeling Language), lo Use Case Diagram o l'Activity Diagram e delle specifiche testuali o tabelle dei requisiti.

---

##  2. Progettazione

Serve a definire **come sarà implementato** il sistema, trasformando i requisiti in una struttura logica e tecnica. Lavora su due livelli principali:

- **Architetturale**: vengono effettuate una suddivisione in componenti o moduli e delle scelte di design (client-server, microservizi, architetture REST...);
- **Di dettaglio**: vengono definiti gli algoritmi, le strutture dati, le interfacce tra i moduli e i diagrammi tecnici (come diagrammi di classe e di sequenza), spesso supportati da pseudocodice esplicativo.

> Una buona progettazione permette di avere software scalabile, estensibile e testabile.

---

##  3. Realizzazione (o sviluppo)

È la fase in cui il progetto prende forma attraverso la **programmazione vera e propria** e spesso si adottano degli ambienti di sviluppo integrati (IDE) e framework vari per velocizzare e standardizzare il lavoro.

- Scelta del linguaggio (es. Java, Python, C#, PHP…);
- Rispetto degli standard di codifica;
- Uso di **versionamento del codice** (Git, GitHub/GitLab);
- **Test unitari** automatici e manuali;
- **Build automatizzate** (CI/CD).

---

##  4. Testing

Il software viene testato per garantire che rispetti i requisiti e non contenga errori. Vengono effettuati diversi tipi di test:

- **Unit test**: singole funzioni o moduli;
- **Integration test**: moduli collegati tra loro;
- **System test**: l’intero sistema;
- **Acceptance test**: verifica con il cliente.

> I test possono essere manuali o automatici. L’uso di strumenti come **JUnit, Selenium, Postman, Jenkins** è ormai standard.

---

##  5. Rilascio e Avviamento

Dopo la fase di testing, il software viene **installato, configurato e consegnato al cliente**. Questa fase comprende diverse attività fondamentali per garantire una transizione efficace all’uso reale del sistema:

- **Distribuzione**: il software viene rilasciato nell’ambiente previsto, che può essere on-premise (in locale), su cloud oppure tramite uno store mobile, a seconda della tipologia dell’applicazione;
- **Documentazione finale**: viene fornita tutta la documentazione tecnica e d’uso necessaria, sia per gli utenti finali che per i tecnici addetti alla manutenzione;
- **Collaudo operativo**: si effettuano test direttamente nell’ambiente reale del cliente, utilizzando dati concreti per verificare che tutto funzioni come previsto;
- **Formazione**: gli utenti ricevono supporto e formazione, per imparare a utilizzare il sistema in modo corretto e autonomo;
- **Avviamento**: il sistema entra ufficialmente in funzione, e viene garantito un primo periodo di assistenza tecnica per risolvere eventuali criticità iniziali.

---

##  6. Manutenzione

Il software viene mantenuto in efficienza nel tempo, questa è la fase più lunga e costosa. Vi sono diverse tipologie di manutenzione

- **Correttiva**: risoluzione di bug post-rilascio;
- **Adattativa**: modifiche dovute a variazioni normative, ambienti o hardware;
- **Evolutiva**: nuove funzionalità, estensioni;
- **Preventiva**: interventi per migliorare la struttura e prevenire guasti futuri.

---

# Gli Stakeholder

Gli attori coinvolti nel processo sono chiamati **stakeholder**. Comprendere i loro ruoli aiuta a evitare incomprensioni e rallentamenti, vi possono essere diversi tipi di stakeholder:

- **Cliente (committente)**: definisce gli obiettivi e fornisce i fondi;
- **Utente finale**: utilizzerà il software;
- **Project manager**: gestisce tempi, costi, risorse;
- **Analista funzionale**: traduce i bisogni del cliente in specifiche tecniche;
- **Sviluppatori**: realizzano il prodotto;
- **Tester/QA**: assicurano la qualità;
- **Tecnici di supporto**: gestiscono manutenzione, formazione e assistenza.

---

# La Qualità del Software

Un software può definirsi di qualità se è:

- **Corretto**: soddisfa i requisiti dichiarati;
- **Affidabile**: funziona correttamente in ogni situazione;
- **Efficiente**: ottimizza le risorse hardware;
- **Manutenibile**: facile da aggiornare o modificare;
- **Portabile**: adattabile a più ambienti;
- **Usabile**: intuitivo, accessibile, coerente;
- **Sicuro**: protegge dati e funzionalità.

---

# Approccio moderno: DevOps e Agile

Negli ultimi anni, le aziende adottano metodologie **agili** e pratiche **DevOps**, che fondono sviluppo e operatività. Si adottano sprint brevi (2-3 settimane), una collaborazione continua tra team, l'automazione dei test e delle distribuzioni, un continuo feedback immediato dagli utenti ed aggiornamenti frequenti