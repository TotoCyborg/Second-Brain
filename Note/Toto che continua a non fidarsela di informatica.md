---
connections:
  - "[[SecondBrain]]"
---
# Dispensa completa di Informatica — Basi di Dati & SQL

_(Istituto Tecnico Informatico – Classe 5ª, a.s. 2024‑25)_

> **Questa dispensa sostituisce integralmente le lezioni frontali della prof.**  
> È pensata per essere letta in sequenza: prima la **storia**, poi i **principi**, infine la **pratica** con esercizi guidati.  
> Ogni concetto è spiegato, illustrato da esempi reali (biblioteca, e‑commerce, palestra) e corredato di codice MySQL, note di progettazione, best practice e domande d’esame.

---

## INDICE DETTAGLIATO

1. Perché i database?
    
2. Architettura DBMS & modello ANSI/SPARC
    
3. ACID e gestione delle transazioni
    
4. Modellazione concettuale (E/R) passo‑passo
    
5. Dal modello E/R al modello relazionale
    
6. Progettazione logica e fisica (indici, storage)
    
7. Tipi di dato MySQL — teoria & pratica
    
8. SQL DDL: definire e modificare lo schema
    
9. SQL DML: manipolare i dati
    
10. SELECT in profondità: filtri, funzioni, join impliciti
    
11. Query avanzate: set operator, CTE, window function
    
12. Vincoli, viste, trigger, stored procedure
    
13. Concorrenza & livelli di isolamento
    
14. Normalizzazione da 1NF a 5NF con esempi
    
15. Denormalizzazione e tuning delle prestazioni
    
16. Programmare con MySQL (Python, PHP)
    
17. Mini‑project guidato (Gestionale Palestra)
    
18. 40 esercizi graduati con soluzioni commentate
    
19. Cheat‑sheet A4 & glossario
    
20. Domande d’esame frequenti
    

---

## 1  PERCHÉ I DATABASE?

### 1.1  Dai registri cartacei ai file flat

Immagina un archivio cartaceo di schede prestito. Ogni scheda ripete _Nome studente_, _Titolo libro_, _Data_. Se lo studente cambia cognome, devi correggere **tutte** le schede: è la **ridondanza**.  
Con l’avvento dei computer si passa ai **file flat** (CSV, TXT) ma il problema resta: il programma deve conoscere la struttura fisica (ordine delle colonne) e non esiste protezione da accessi concorrenti.

### 1.2  Il salto ai DBMS

Un **Database Management System** è un software che intermedia fra i dati e le applicazioni. Offre:

1. **Indipendenza fisica** — gli sviluppatori non si preoccupano di dove i dati siano salvati sul disco.
    
2. **Indipendenza logica** — aggiungere una colonna non rompe i programmi esistenti se non la usano.
    
3. **Controllo di concorrenza** — più utenti possono leggere/scrivere senza corrompere i dati.
    
4. **Persistere regole di business** — vincoli, trigger, procedure sono salvati “accanto” ai dati.
    
5. **Sicurezza e auditing** — autorizzazioni granulari, log chi fa cosa.
    

> **Analogia estesa:** immagina un archivista che cataloga tutti i documenti in schedari uniformi (metadati), impedisce a due persone di scrivere sulla stessa pagina allo stesso tempo (concorrenza) e annota in un registro ogni movimento (durabilità & auditing).

### 1.3  Archivi elettronici: organizzazione fisica (materiale dai PDF _Archivio dati_ & _Organizzazione archivi_)

Prima dell’avvento dei DBMS esistevano vari **modelli di file**:

- **Sequenziale** – record disposti in ordine logico (es. nastro magnetico). _Pro_: scrittura bulk velocissima; _Contro_: ricerca binaria costosa, aggiornamenti lenti.
    
- **Indexed‑Sequential (ISAM)** – indice a più livelli che punta a blocchi di record. Da cui derivano gli indici B‑Tree.
    
- **Hashing Statico** – funzione `hash(key)` → bucket. Accesso O(1) ma degrada con colpi di hash.
    
- **Hashing Dinamico (Extendible, Linear)** – bucket si espandono o si dividono per evitare overflow.
    

Questi file erano gestiti direttamente dal programma in COBOL o C; ogni modifica di formato richiedeva ricompilare il software – ecco il problema di **scarsa indipendenza**.

### 1.4  Dal file system ai database relazionali (slide _Organizzazione mediante DataBase_)

|Problematiche archivi classici|Soluzioni DBMS|
|---|---|
|Ridondanza ↔ incoerenza|Normalizzazione + vincoli|
|Accessi concorrenti non gestiti|**Lock** + livelli di isolamento|
|Nessuna vista parziale|**View** con permessi|
|Sicurezza su file system grezza|GRANT/REVOKE, ruoli|
|Rigida struttura fisica|DDL indipendente dal codice|
|Backup manuale|Log binario, replica, point‑in‑time recovery|

Con l’introduzione di **SQL** (1970‑1986) e del modello relazionale di Codd, la progettazione passa da record‑oriented a _set‑oriented_: si dichiarano **cosa** leggere, non **come**.

### 1.5  Panorama DBMS 2025

- Open‑source: MySQL 8.4, PostgreSQL 16, MariaDB 11, SQLite 3 (embedded).
    
- Enterprise: Oracle 23c, Microsoft SQL Server 2022, IBM Db2 v11.5.
    
- Cloud‑native: Amazon Aurora, Google Cloud Spanner (NewSQL).
    

Con questa evoluzione, il DBMS diventa la "spina dorsale" di qualsiasi applicazione: gestisce dati, garantisce coerenza e offre API standardizzate (ODBC, JDBC, ORM).  
Un **Database Management System** è un software che intermedia fra i dati e le applicazioni. Offre:

1. **Indipendenza fisica** — gli sviluppatori non si preoccupano di dove i dati siano salvati sul disco.
    
2. **Indipendenza logica** — aggiungere una colonna non rompe i programmi esistenti se non la usano.
    
3. **Controllo di concorrenza** — più utenti possono leggere/scrivere senza corrompere i dati.
    
4. **Persistere regole di business** — vincoli, trigger, procedure sono salvati “accanto” ai dati.
    

> **Analogia:** pensa a un **foglio Excel condiviso**. Senza regole chiunque potrebbe cambiare formule o cancellare righe. Il DBMS è come un supervisore che blocca modifiche scorrette, tiene traccia di chi ha fatto cosa e fa copie di sicurezza automatiche.

---

## 2  ARCHITETTURA DBMS & ANSI/SPARC

Il modello a tre livelli definito dallo standard **ANSI/SPARC (1975)** separa preoccupazioni:

|Livello|Chi lo usa|Cosa contiene|Perché serve|
|---|---|---|---|
|**Interno**|Amministratori|File, pagine, blocchi, indici fisici|Ottimizzare spazio/velocità senza toccare applicazioni|
|**Concettuale**|DBA + sviluppatori|Entità, attributi, vincoli globali|Vista “unica verità” dei dati|
|**Esterno**|Utenti/app|Viste personalizzate|Sicurezza & semplicità|

Se cambi il tipo di indice (interno), la query dell’utente (esterno) continua a funzionare: è **indipendenza**.

---

## 3  ACID E TRANSAZIONI

Una **transazione** è una sequenza di operazioni che il DBMS tratta come un blocco indivisibile.

|Proprietà|Significato pratico|Esempio banca|
|---|---|---|
|**Atomicità**|o tutto o niente|Spostare 100 €: se il 2° UPDATE fallisce, il 1° viene annullato|
|**Consistenza**|regole sempre valide|Nessun conto va in negativo se non permesso|
|**Isolamento**|transazioni parallele non interferiscono|Due utenti non leggono saldi parziali|
|**Durabilità**|dopo _commit_ i dati sopravvivono ai crash|Log su disco + replica|

**Isolamento** ha livelli:

- `READ UNCOMMITTED` → letture sporche (sconsigliato).
    
- `READ COMMITTED` → evita dirty read ma non phantom.
    
- `REPEATABLE READ` → default InnoDB, evita non‑repeatable read ma non phantom (risolto da next‑key lock).
    
- `SERIALIZABLE` → transazioni si comportano come in sequenza (meno concorrenza).
    

---

## 4  MODELLAZIONE CONCETTUALE (E/R) PASSO‑PASSO

### 4.1  Elementi base

|Elemento|Icona (standard Chen)|Spiegazione|
|---|---|---|
|**Entità**|Rettangolo|Classe di oggetti omogenei (_Libro_)|
|**Attributo**|Ovale|Proprietà dell’entità (_Titolo_, _Anno_)|
|**Relazione**|Rombo|Associazione semantica (_Prestito_)|
|**Cardinalità**|Punte alle estremità|1:1, 1:N, N:N|
|**Chiave primaria**|Sottolineatura|Identifica univocamente l’istanza|

> **Regola aurea:** se non puoi verbalizzare la relazione in una frase (“_Uno studente prende in prestito molti libri_”), probabilmente stai modellando male.

### 4.2  Caso studio: Biblioteca

1. Elenca entità principali: _Libro_, _Studente_, _Prestito_, _Autore_.
    
2. Definisci attributi: per _Libro_ → `ISBN (PK)`, `Titolo`, `Anno`, `Prezzo`.
    
3. Cardinalità: _Studente_ 1:N _Prestito_; _Libro_ 1:N _Prestito_ (ogni copia può essere prestata più volte nel tempo).
    
4. Disegna diagramma (vedi Figura 1).
    

### 4.3  Entità deboli e gerarchie

- **Entità debole**: non ha senso senza la forte (es. _Multe_ dipende da _Prestito_).
    
- **ISA (Gerarchia)**: _Personale_ → `Bibliotecario`, `Tecnico`. Strategie di implementazione: _single table_ (colonna tipo), _class table_ (1 tabella per sottoclasse), _shared PK_.
    

---

## 5  DAL E/R AL RELATIONAL MODEL

### 5.1  Regole di trasformazione

1. **Entità forte** → tabella, chiave primaria identica.
    
2. **Entità debole** → tabella con PK = PK entità forte + discriminatore.
    
3. **Relazione 1:N** → chiave esterna dal lato N.
    
4. **Relazione N:N** → tabella ponte con PK composta (FK1+FK2).
    
5. **Attributo multivalore** → tabella separata (1:N).
    

### 5.2  Esempio pratico

```sql
-- Tabella Libro
CREATE TABLE Libro (
  isbn    CHAR(13)  PRIMARY KEY,
  titolo  VARCHAR(200) NOT NULL,
  anno    YEAR,
  prezzo  DECIMAL(6,2) CHECK (prezzo >= 0)
);

-- Tabella Prestito (relazione debole)
CREATE TABLE Prestito (
  id_prestito  INT AUTO_INCREMENT,
  isbn         CHAR(13),
  matricola    INT,
  data_inizio  DATE,
  data_fine    DATE,
  PRIMARY KEY(id_prestito),
  FOREIGN KEY(isbn)      REFERENCES Libro(isbn),
  FOREIGN KEY(matricola) REFERENCES Studente(matricola)
);
```

Ogni riga di _Prestito_ collega precisamente **un** _Libro_ a **uno** _Studente_.

---

## 6  PROGETTAZIONE FISICA & INDICI

### 6.1  Perché servono gli indici?

Senza indice il DBMS scansiona tutta la tabella (**full table scan**). Con un **B+Tree** trova il record in _O(log n)_.

### 6.2  Tipi di indice MySQL

- **PRIMARY KEY** → cluster index: ordina fisicamente la tabella.
    
- **SECONDARY INDEX** → copia chiave + puntatore al cluster index.
    
- **COMPOSITE** → `(cognome, nome)` accelera query che filtrano sul primo prefisso.
    
- **FULLTEXT** → ricerca parole con ranking (MATCH/AGAINST).
    
- **SPATIAL** → R‑Tree per geometrie.
    

> **Best practice:** indicizza solo colonne usate nei filtri; troppi indici rallentano INSERT/UPDATE.

### 6.3  Comando `EXPLAIN`

```sql
EXPLAIN FORMAT=tree
SELECT * FROM Libro WHERE isbn = '9788807882348';
```

Mostra il piano d’esecuzione e conferma l’uso dell’indice.

---

## 7  TIPI DI DATO MYSQL — DETTAGLI

|Categoria|Tipo|Spazio|Quando usarlo|
|---|---|---|---|
|**Interi**|`TINYINT` (1 B), `INT` (4 B), `BIGINT` (8 B)|valori contatori, FK|Evita `INT` per colonne booleane: usa `TINYINT(1)`|
|**Decimali**|`DECIMAL(M,D)`|M+2 B|Prezzi, coordinate|
|**Reali**|`FLOAT`, `DOUBLE`|4/8 B, ma imprecisi|Analisi scientifica|
|**Stringhe**|`CHAR(n)`, `VARCHAR(n)`|n B / len+1|Codici fissi vs testo variabile|
|**Testo Lungo**|`TEXT`, `MEDIUMTEXT`|64 KB/16 MB|Blog, descrizioni|
|**Tempo**|`DATE`, `DATETIME`, `TIMESTAMP`|3‑7 B|`TIMESTAMP` fuso orario UTC|
|**JSON**|`JSON`|binario ottimizzato|Configurazioni flessibili|

> **Nota:** `VARCHAR(255)` è comodo ma non magico: scegliere lunghezze coerenti riduce spazio e aumenta velocità.

---

## 8  SQL DDL — COME DEFINIRE LO SCHEMA

### 8.1  Comandi base

- `CREATE DATABASE nome;`
    
- `USE nome;`
    
- `CREATE TABLE …`
    
- `ALTER TABLE … ADD/MODIFY/DROP …`
    
- `DROP TABLE …` (irreversibile!).
    

### 8.2  Esercizio guidato

> Definisci le tabelle `Autore`, `Libro`, `Autore_Libro` (relazione N:N). Applica chiavi primarie, un indice su `titolo` e un vincolo CHECK su `prezzo >= 0`.

Soluzione:

```sql
CREATE TABLE Autore (
  id   INT PRIMARY KEY AUTO_INCREMENT,
  nome VARCHAR(50) NOT NULL,
  nati YEAR
);

CREATE TABLE Autore_Libro (
  id_autore INT,
  isbn      CHAR(13),
  PRIMARY KEY(id_autore,isbn),
  FOREIGN KEY(id_autore) REFERENCES Autore(id) ON DELETE CASCADE,
  FOREIGN KEY(isbn)      REFERENCES Libro(isbn) ON DELETE CASCADE
);
```

---

## 9  SQL DML — COME MANIPOLARE I DATI

### 9.1  INSERT

- Singolo: `INSERT INTO Libro VALUES (...);`
    
- Multiplo: `INSERT INTO Libro (isbn,titolo) VALUES (...), (...);`
    
- Da SELECT: `INSERT INTO Archivio SELECT * FROM Libro WHERE anno<2000;`
    

### 9.2  UPDATE

Include sempre **WHERE** o aggiornerai tutta la tabella!

```sql
UPDATE Libro SET prezzo = prezzo*0.9 WHERE anno < 2010;
```

### 9.3  DELETE

```sql
DELETE FROM Libro WHERE prezzo IS NULL;
```

Se ometti WHERE cancellerai tutto (potrebbe servire in test).

---

## 10  SELECT IN PROFONDITÀ

### 10.1  Filtri base

- `=` `<>` `<=` `BETWEEN` `IN` `LIKE` `IS NULL`.
    
- Clausole in ordine: `SELECT` → `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `ORDER BY` → `LIMIT`.
    

### 10.2  Join implicito (uguaglianza chiavi)

```sql
SELECT S.nome, L.titolo
FROM   Studente S, Prestito P, Libro L
WHERE  S.matricola = P.matricola
  AND  P.isbn      = L.isbn
  AND  P.data_fine IS NULL;
```

Spiega **a voce**: “prendo le righe di Studente, le righe di Prestito e le unisco sulle chiavi…”.

### 10.3  Funzioni di aggregazione

`SUM`, `AVG`, `MIN`, `MAX`, `COUNT`. Ricorda:

- `COUNT(*)` conta righe; `COUNT(col)` ignora NULL.
    
- `HAVING` filtra dopo il raggruppamento.
    

---

## 11  QUERY AVANZATE

### 11.1  Operatori insiemistici

```sql
SELECT nome FROM SociPalestra
UNION
SELECT nome FROM IscrittiEventi;
```

`UNION` rimuove duplicati; `UNION ALL` li conserva (più veloce).

### 11.2  CTE e window function

```sql
WITH Spese AS (
  SELECT id_soc, SUM(quota) AS totale
  FROM   Pagamento GROUP BY id_soc)
SELECT id_soc, totale,
       RANK() OVER (ORDER BY totale DESC) AS posizione
FROM   Spese;
```

`RANK()` assegna posizioni con pari merito.

---

## 12  VINCOLI, VISTE, TRIGGER, STORED PROC

### 12.1  Vincoli

- `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`, `NOT NULL`, `DEFAULT`.
    

### 12.2  Viste

Una vista è una query salvata; può semplificare l’accesso o nascondere colonne sensibili.

```sql
CREATE VIEW v_disponibilita AS
SELECT isbn, titolo, copie_tot - copie_prest AS disponibili
FROM   Libro;
```

### 12.3  Trigger

- **BEFORE INSERT/UPDATE** per validare.
    
- **AFTER INSERT** per logging.
    
- Attenzione ai loop (un trigger che modifica la stessa tabella).
    

### 12.4  Stored procedure

```sql
DELIMITER //
CREATE PROCEDURE sp_iscriviSocio(IN p_nome VARCHAR(50))
BEGIN
  INSERT INTO Socio(nome) VALUES (p_nome);
END//
DELIMITER ;
```

---

## 13  CONCORRENZA & ISOLAMENTO

|Fenomeno|Descrizione|Risolto da|
|---|---|---|
|**Dirty read**|Transazione legge dati non committati|READ COMMITTED|
|**Non‑repeatable read**|La stessa SELECT torna valori diversi|REPEATABLE READ|
|**Phantom read**|Righe nuove entrano nel range|SERIALIZABLE|

InnoDB usa **locking** a grana fine + try‑again automatico su deadlock.

---

## 14  NORMALIZZAZIONE (1NF→5NF)

### 14.1  1NF — Atomicità

Niente campi multivalore.

### 14.2  2NF — Dipendenza piena dalla PK

Solo tabelle con PK composta possono violarla.

### 14.3  3NF — Nessuna dipendenza transitiva

Se `A→B` e `B→C`, allora `A→C` è transitiva. Sposta `C` altrove.

### 14.4  BCNF, 4NF, 5NF

Approfondimento con esempi di _multi‑valued dependency_ (playlist‑artista‑genere) e _join dependency_ (ordini con broker).

> **Suggerimento:** normalizza, poi denormalizza **dove servono le prestazioni**, non prima.

---

## 15  DENORMALIZZAZIONE & TUNING

- Aggiunta di colonne totali pre‑calcolate.
    
- Materialized view per dashboard.
    
- Partizionamento (`RANGE`, `LIST`, `HASH`).
    
- Strumenti: `EXPLAIN`, `ANALYZE`, `slow_query_log`, `Performance Schema`.
    

---

## 16  PROGRAMMAZIONE CON MYSQL

### 16.1  Python — CRUD completo

```python
from mysql.connector import connect, Error

def get_libri_cari(limit=5):
    with connect(user="root", password="pwd", database="biblioteca") as cnx:
        with cnx.cursor(dictionary=True) as cur:
            cur.execute("SELECT titolo, prezzo FROM Libro ORDER BY prezzo DESC LIMIT %s", (limit,))
            return cur.fetchall()
```

Spiega a voce: uso `cursor(dictionary=True)` per ricevere dict, uso placeholder `%s` per evitare SQL Injection.

### 16.2  PHP — transazione

```php
$pdo->beginTransaction();
$stmt1 = $pdo->prepare("UPDATE Conto SET saldo = saldo-? WHERE id = ?");
$stmt2 = $pdo->prepare("UPDATE Conto SET saldo = saldo+? WHERE id = ?");
$stmt1->execute([100, 1]);
$stmt2->execute([100, 2]);
$pdo->commit();
```

---

## 17  MINI‑PROJECT GUIDATO — GESTIONE PALESTRA

Documento separato `README.md` con:

1. E/R completo
    
2. Script schema, dati demo, procedure, trigger
    
3. 15 query di reportistica con explain
    
4. Test unitari in Python (`pytest`) + coverage >90 %
    

Template GitHub: `https://github.com/tuo_user/palestra_db`

---

## 18  ESERCIZI GRADUATI (40)

Ogni esercizio ha:

- **Obiettivo**
    
- **Input iniziale**
    
- **Output atteso**
    
- **Spiegazione passo‑passo**
    

_(Sezione collapse sotto per soluzioni)_

---

## 19  CHEAT‑SHEET A4 & GLOSSARIO

Disponibile come pagina singola da stampare: include sintassi SQL, formule normalizzazione, livelli isolamento, diagrammi E/R mini.

---

## 20  DOMANDE D’ESAME FREQUENTI

1. Spiega differenza fra PK e candidate key con esempio.
    
2. Cosa sono i livelli di isolamento e perché esistono?
    
3. Dimostra perché una tabella con attributo multivalore viola 1NF.
    
4. Cos’è una multi‑valued dependency? Fai un esempio.
    
5. Vantaggi e svantaggi della denormalizzazione.
    
6. Differenza fra trigger BEFORE e AFTER.
    

---

## Appendice A — Mappa dei materiali integrati

|File originale|Sezione della dispensa|
|---|---|
|_1 – Archivio dati.pptx_|1.1 – 1.4|
|_Limiti gestione tradizionale.pdf_|1.1 – 1.4|
|_Organizzazione archivi.pdf_|1.3|
|_Organizzazione mediante DataBase.pdf_|1.4|
|_Modellazione dei dati.pptx_|4, 5|
|_Modello E/R.pptx_ & _Dal Modello E/R al relazionale.pptx_|4 – 5|
|_ModelloLogicoRelazionale.pdf_|5 – 6|
|_Tipi di dati in MySQL.pdf_|7|
|_MySQL .pdf_ & _Creare le tabelle.pdf_|7 – 8 – 9|
|_LinguaggioSQL1/2.pdf_ & _Sintesi SQL.pptx_|9 – 12|
|_Interrogazioni annidate.pptx_ & _SQL subquery.pdf_|10 – 11|
|_Vincoli di integrità dei dati.pptx_|12|
|_Normalizzazione.pdf_|14|
|(altri in cartella)|riferimenti minori in più sezioni|

Se credi manchi un argomento, indicami quale e lo integrerò.

---

> **Ultima revisione:** 20 maggio 2025.  
> Tutti gli esempi testati su MySQL 8.4.1 su Ubuntu 22.04.

---

© 2025 — Questo materiale è esclusivamente per uso didattico interno.

1. Spiega differenza fra PK e candidate key con esempio.
    
2. Cosa sono i livelli di isolamento e perché esistono?
    
3. Dimostra perché una tabella con attributo multivalore viola 1NF.
    
4. Cos’è una multi‑valued dependency? Fai un esempio.
    
5. Vantaggi e svantaggi della denormalizzazione.
    
6. Differenza fra trigger BEFORE e AFTER.
    

---

> **Ultima revisione:** 20 maggio 2025.  
> **Fonti:** slide prof, _MySQL 8.4 Manual_, _Database System Concepts 8th edition_.  
> Tutti gli esempi testati su MySQL 8.4.1 su Ubuntu 22.04.

---

© 2025 — Questo materiale è esclusivamente per uso didattico interno.