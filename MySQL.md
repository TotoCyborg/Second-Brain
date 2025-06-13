---
connections:
  - "[[Informatica]]"
---

# 🧠 Panoramica generale – SQL & MySQL (senza JOIN)

Nel campo della gestione dei dati, **SQL** (Structured Query Language) è il linguaggio standard per l’interrogazione dei database relazionali, mentre **MySQL** è un sistema di gestione (DBMS) che utilizza SQL per permettere la creazione, manipolazione e interrogazione di basi di dati.

- SQL è un **linguaggio**, non un software.
    
- MySQL è un **DBMS** open source che usa SQL per gestire database.
    
- SQL funziona anche su altri DBMS come PostgreSQL, Oracle, SQL Server.
    

---

# 🔧 Struttura del linguaggio SQL

SQL si divide in **categorie funzionali**, ciascuna con uno scopo specifico:

### 📌 1. DDL – Data Definition Language

Serve per **creare o modificare la struttura** del database.

Esempi:

```sql
CREATE TABLE Studenti (
  matricola INT PRIMARY KEY,
  nome VARCHAR(30),
  cognome VARCHAR(30)
);

ALTER TABLE Studenti ADD email VARCHAR(50);
DROP TABLE Esami;
```

### 📌 2. DML – Data Manipulation Language

Permette di **gestire i dati** all’interno delle tabelle.

Esempi:

```sql
INSERT INTO Studenti VALUES (1001, 'Luca', 'Bianchi');
UPDATE Studenti SET nome = 'Marco' WHERE matricola = 1001;
DELETE FROM Studenti WHERE matricola = 1001;
```

### 📌 3. DQL – Data Query Language

È la parte usata per **interrogare i dati**.

Esempio:

```sql
SELECT nome, cognome FROM Studenti WHERE cognome = 'Verdi';
```

Include:

- Filtri (`WHERE`),
    
- Ordinamenti (`ORDER BY`),
    
- Raggruppamenti (`GROUP BY`),
    
- Condizioni su gruppi (`HAVING`).
    

### 📌 4. DCL – Data Control Language

Serve a **gestire permessi** e accessi degli utenti.

Esempio:

```sql
GRANT SELECT ON Studenti TO 'utente1'@'localhost';
REVOKE SELECT ON Studenti FROM 'utente1'@'localhost';
```

---

# 🛠️ Cos’è MySQL

**MySQL** è un sistema di gestione di database relazionali (RDBMS), usato per:

- creare database e tabelle,
    
- inserire, modificare, interrogare dati,
    
- gestire utenti e permessi,
    
- automatizzare backup e repliche.
    

✅ È gratuito, open source e compatibile con molti linguaggi (PHP, Python, Java...).

---

# 📁 Concetti fondamentali

## Tabelle e record

Un database contiene **tabelle**, simili a fogli di calcolo, che a loro volta contengono:

- **record** (le righe),
    
- **campi** o **attributi** (le colonne).
    

Esempio tabella `Studenti`:

|matricola|nome|cognome|classe|
|---|---|---|---|
|1001|Luca|Bianchi|5A|
|1002|Elena|Verdi|5B|

## Chiavi

- **Chiave primaria (PRIMARY KEY)**: identifica univocamente ogni riga.
    
- **Chiave esterna (FOREIGN KEY)**: collega una tabella a un’altra.
    

Esempio:

```sql
CREATE TABLE Esami (
  id INT PRIMARY KEY,
  matricola INT,
  voto INT,
  FOREIGN KEY (matricola) REFERENCES Studenti(matricola)
);
```

---

# 📋 Esempi pratici (senza `JOIN`)

## ▶️ Creazione database e tabelle

```sql
CREATE DATABASE Scuola;
USE Scuola;

CREATE TABLE Studenti (
  matricola INT PRIMARY KEY,
  nome VARCHAR(30),
  cognome VARCHAR(30),
  classe CHAR(2)
);

CREATE TABLE Esami (
  id INT PRIMARY KEY,
  materia VARCHAR(20),
  matricola INT,
  voto INT,
  FOREIGN KEY (matricola) REFERENCES Studenti(matricola)
);
```

## ▶️ Inserimento dati

```sql
INSERT INTO Studenti VALUES (1001, 'Luca', 'Bianchi', '5A');
INSERT INTO Esami VALUES (1, 'Informatica', 1001, 28);
```

## ▶️ Interrogazioni semplici

```sql
SELECT nome, cognome 
FROM Studenti 
WHERE classe = '5A';
```

## ▶️ Collegamento tra tabelle con uguaglianza delle chiavi

```sql
SELECT Studenti.nome, Studenti.cognome, Esami.voto
FROM Studenti, Esami
WHERE Studenti.matricola = Esami.matricola
  AND Esami.voto >= 28;
```

Questo tipo di scrittura è perfettamente valido, soprattutto in contesto scolastico o se ti senti più sicuro così.

---

# 🧮 Funzioni di aggregazione

SQL permette di fare calcoli sui dati:

```sql
SELECT AVG(voto), COUNT(*) FROM Esami WHERE materia = 'Informatica';
```

Funzioni disponibili:

- `AVG()`: media,
    
- `SUM()`: somma,
    
- `COUNT()`: numero di righe,
    
- `MAX()`, `MIN()`: massimo/minimo.
    

---

# 🔒 Sicurezza in MySQL

MySQL permette di creare utenti e dare permessi personalizzati:

```sql
CREATE USER 'salvo'@'localhost' IDENTIFIED BY 'password';
GRANT SELECT, INSERT ON Scuola.* TO 'salvo'@'localhost';
FLUSH PRIVILEGES;
```

Puoi decidere:

- a quali database ha accesso,
    
- cosa può fare (solo leggere? anche scrivere?),
    
- da quale macchina può connettersi.
    

---

# 🔄 Transazioni e integrità

Le **transazioni** permettono di eseguire più operazioni come fossero una sola:

```sql
START TRANSACTION;
UPDATE Conti SET saldo = saldo - 100 WHERE id = 1;
UPDATE Conti SET saldo = saldo + 100 WHERE id = 2;
COMMIT;
```

In caso di errore:

```sql
ROLLBACK;
```

MySQL supporta il modello **ACID**:

- **Atomicità**: tutto o niente,
    
- **Consistenza**: mantiene regole e vincoli,
    
- **Isolamento**: le transazioni non interferiscono tra loro,
    
- **Durabilità**: i dati non si perdono dopo il salvataggio.
    

---

# ✅ Conclusione

SQL è il linguaggio con cui interroghi e gestisci un database; MySQL è il programma che lo esegue. Usare correttamente SQL (nella forma classica, senza JOIN) ti consente di lavorare con i dati in modo strutturato, potente e professionale. Conoscere questi strumenti ti darà un vantaggio enorme non solo all'esame, ma anche in ambito lavorativo.
