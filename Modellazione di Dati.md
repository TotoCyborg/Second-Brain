---
connections:
  - "[[Informatica]]"
---

# Modellazione dei Dati – Approfondimento Completo

La **modellazione dei dati** è il processo attraverso il quale si costruisce una rappresentazione semplificata della realtà, con l'obiettivo di progettare una base di dati coerente, efficiente e interrogabile. Essa permette di astrarre la complessità del mondo reale individuando gli elementi fondamentali (entità, attributi, relazioni) e organizzandoli secondo regole formali.

Questo processo avviene a **più livelli di astrazione**, ciascuno dei quali consente di avvicinarsi progressivamente all'implementazione concreta nel database:

## 1. Livelli di astrazione nella progettazione

Il primo passo è la **progettazione concettuale**, che descrive il significato dei dati senza vincoli tecnici. Seguono la progettazione **logica**, in cui si definisce come quei dati verranno strutturati nel modello scelto (es. relazionale), e infine la progettazione **fisica**, che riguarda la memorizzazione reale.

In sintesi, i tre livelli sono:

- **Livello concettuale**: rappresenta la realtà in termini di entità, attributi e relazioni. È indipendente dal tipo di database.
    
- **Livello logico**: descrive l'organizzazione dei dati secondo un modello specifico (es. tabelle relazionali), ma ancora indipendente dal software usato.
    
- **Livello fisico**: definisce come i dati verranno memorizzati su disco, tenendo conto di performance, spazio e accessi.
    

Questa suddivisione consente di separare le scelte progettuali di alto livello dai dettagli tecnici, favorendo la chiarezza e la manutenzione del sistema.

## 2. Il modello E/R (Entity-Relationship)

Nella fase concettuale si utilizza il **modello Entità/Relazione**, introdotto da Peter Chen nel 1976. Questo modello permette di rappresentare graficamente le componenti fondamentali di un sistema informativo.

Le principali componenti del modello E/R sono:

- **Entità**: insiemi di oggetti con caratteristiche comuni e significato autonomo nel contesto. Ad esempio, _Studente_, _Corso_, _Docente_.
    
- **Relazioni (o associazioni)**: legami logici tra due o più entità. Per esempio, uno _studente_ "sostiene" un _esame_.
    
- **Attributi**: proprietà che descrivono entità o relazioni, come il nome di uno studente o il voto di un esame.
    

Ogni relazione ha una **cardinalità**, che esprime il numero di istanze coinvolte. Le più comuni sono:

- **1:1** – Un'entità è collegata a una sola istanza dell'altra.
    
- **1:N** – Un'entità può essere collegata a più istanze dell'altra (es. un docente insegna più corsi).
    
- **N:M** – Più istanze di un'entità sono collegate a più istanze dell'altra (es. studenti e corsi).
    

Ogni entità possiede almeno un attributo che funge da **chiave primaria**, cioè un identificatore univoco per ciascuna istanza. Questo è fondamentale per mantenere l'integrità del modello e, successivamente, del database.

## 3. Traduzione nel modello logico

Una volta definito lo schema concettuale, si passa alla **progettazione logica**. Nel caso del **modello relazionale**, le entità diventano **tabelle**, gli attributi diventano **colonne** e le relazioni vengono gestite tramite **chiavi esterne** o **tabelle associative**.

Ad esempio:

- L’entità _Studente_ diventa una tabella con colonne come `matricola`, `nome`, `cognome`, ecc.
    
- Una relazione _sostiene_ tra _Studente_ e _Esame_ (N:M) diventa una nuova tabella chiamata, ad esempio, `Sostenimenti`, con colonne `matricola`, `idEsame`, `data`, `voto`.
    

Durante questa fase si introducono i **vincoli di integrità**, che garantiscono la coerenza dei dati:

- **Integrità di entità**: ogni tabella deve avere una chiave primaria unica.
    
- **Integrità referenziale**: ogni chiave esterna deve corrispondere a un valore valido della chiave primaria referenziata.
    
- **Vincoli di dominio**: ogni campo deve rispettare il tipo di dato e i limiti definiti.
    

Il livello logico è fondamentale perché prepara i dati all’interrogazione e alla manipolazione tramite linguaggi come **SQL**.

## 4. Livello fisico e gestione tramite DBMS

Nel **livello fisico** si stabilisce come i dati saranno realmente archiviati. Si tratta di una fase molto tecnica, che riguarda aspetti come:

- la struttura dei file che contengono le tabelle,
    
- l’uso di **indici** per velocizzare le ricerche,
    
- le strategie di **caching** e **buffering** per migliorare le performance,
    
- la gestione della **concorrenza** tra utenti.
    

Tutta questa complessità viene gestita dal **DBMS (Database Management System)**, ovvero il software che consente di:

- creare e modificare il database secondo il modello logico definito,
    
- garantire sicurezza, integrità e accesso concorrente,
    
- fornire strumenti per interrogare e aggiornare i dati, come il linguaggio **SQL**, che offre comandi come:
    
    - `SELECT` per consultare i dati,
        
    - `INSERT` per aggiungerli,
        
    - `UPDATE` per modificarli,
        
    - `DELETE` per rimuoverli.
        

Il DBMS, oltre a gestire le operazioni, garantisce anche il rispetto delle **proprietà ACID** (Atomicità, Coerenza, Isolamento, Durabilità), fondamentali per la corretta gestione delle transazioni.

## 5. Conclusione

La modellazione dei dati è un’attività centrale nella progettazione di un sistema informativo, perché consente di rappresentare con rigore la realtà, traducendola in strutture dati coerenti e interrogabili. Attraverso i tre livelli di astrazione – concettuale, logico e fisico – è possibile passare da un’idea astratta a un sistema concreto, affidabile ed efficiente. Solo comprendendo a fondo questi livelli, e padroneggiando strumenti come il modello E/R e i DBMS, è possibile progettare basi di dati solide, scalabili e mantenibili nel tempo.
