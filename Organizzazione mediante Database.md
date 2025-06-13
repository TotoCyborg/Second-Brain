---
connections:
  - "[[Informatica]]"
---

# Il Database e il DBMS

Un **database** è una **collezione di dati logicamente correlati**, organizzati in modo coerente per **soddisfare i fabbisogni informativi di un'organizzazione**.  
I dati contenuti in un database sono **condivisi tra più utenti e applicazioni**, e gestiti centralmente tramite un **Database Management System (DBMS)**, ovvero un sistema software specializzato che si occupa della **definizione, manipolazione, protezione e accesso ai dati**.

## Funzioni principali del DBMS

Il DBMS fornisce diversi strumenti e linguaggi che consentono di interagire con il database. Tra le funzionalità più importanti:

- **DDL (Data Definition Language)**: consente di definire e modificare la **struttura delle tabelle**, dei vincoli, degli indici e degli altri oggetti del database;
    
- **DML (Data Manipulation Language)**: permette di **inserire, modificare, eliminare e consultare i dati** presenti nel database;
    
- **QL (Query Language)**: consente di effettuare **interrogazioni complesse** per l'analisi e la ricerca delle informazioni;
    
- **SQL (Structured Query Language)**: è il linguaggio standardizzato che **unifica tutte le operazioni di definizione e manipolazione dei dati**, permettendo anche la gestione dei permessi e dei vincoli.
    

## Vantaggi offerti dai DBMS

Rispetto all’organizzazione tradizionale dei dati, un sistema basato su DBMS offre numerosi **vantaggi**:

- **Facilità di accesso ai dati**: grazie a linguaggi dichiarativi come SQL, anche utenti non tecnici possono consultare le informazioni;
    
- **Indipendenza dei dati**: le applicazioni non dipendono dalla struttura fisica o logica del database, e i dati possono essere riorganizzati senza modificare i programmi;
    
- **Riduzione della ridondanza e dell’inconsistenza**: i dati vengono memorizzati una sola volta e sono accessibili da più applicazioni, evitando duplicazioni;
    
- **Integrità dei dati**: i vincoli e le regole stabilite nel database garantiscono che i dati siano sempre coerenti, validi e accurati;
    
- **Controllo dell’accesso e della sicurezza**: il DBMS gestisce utenti, permessi e protezioni contro accessi non autorizzati.
    

---

# Dai dati alla struttura del database: i modelli

La costruzione di un database avviene **progressivamente**, attraverso diversi livelli di rappresentazione:

###### 1. Realtà da modellare

È il **mondo reale** o l’insieme dei processi e delle entità che si vogliono rappresentare. Ad esempio, in un’università: studenti, corsi, esami, docenti.

###### 2. Modello concettuale

È una rappresentazione **astratta e indipendente dalla tecnologia** usata per descrivere la realtà.  
Viene realizzato attraverso **modelli concettuali** come l’**Entità-Relazione (E-R)**, che definisce le entità, le loro proprietà (attributi) e le relazioni tra esse. Questo è il primo passo nella progettazione di un database.

###### 3. Modello logico

Il modello concettuale viene **trasformato in un modello logico**, che rispetta le **regole di un particolare modello di dati**. Il più usato è il **modello relazionale**, dove i dati vengono organizzati in **tabelle** collegate da **chiavi primarie e chiavi esterne**.  
È in questa fase che si applicano le **forme normali** per normalizzare i dati ed evitare ridondanze.

###### 4. Modello fisico

Il modello logico viene poi convertito nel **modello fisico**, cioè in una rappresentazione che **considera gli aspetti tecnici e di archiviazione** del DBMS utilizzato. Include decisioni come il tipo di indice, i tipi di dato, l’organizzazione delle tabelle nei file, e le prestazioni.

###### 5. Database attivo

Infine, si crea il **database vero e proprio**, che è il risultato dell’applicazione di tutti i modelli precedenti. Il database è ora **operativo**, pronto per essere interrogato, aggiornato e mantenuto nel tempo.
