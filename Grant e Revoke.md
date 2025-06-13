---
connections:
  - "[[Informatica]]"
---

# 🛡️ GRANT, REVOKE e gestione dei permessi in MySQL

## 🔎 Cos'è la gestione dei privilegi?

In un database multiutente (come MySQL), è fondamentale **controllare chi può fare cosa**. Per questo esistono **permessi (privilegi)** che permettono di assegnare agli utenti determinati diritti, ad esempio:

- leggere dati (SELECT),
    
- modificarli (UPDATE),
    
- creare o cancellare tabelle (CREATE, DROP),
    
- gestire altri utenti (GRANT OPTION).
    

Questa gestione si fa tramite i comandi **`GRANT`** e **`REVOKE`**.

---

## ✅ `GRANT`: concedere permessi

Il comando `GRANT` serve a **concedere uno o più privilegi** a un utente o gruppo di utenti.

### 📌 Sintassi base:

```sql
GRANT privilegio [, ...] 
ON nome_oggetto 
TO 'utente'@'host';
```

### 📌 Esempi pratici:

1. **Concedere accesso in lettura a una tabella:**
    

```sql
GRANT SELECT ON scuola.Studenti TO 'giulia'@'localhost';
```

2. **Permettere l’inserimento e la modifica:**
    

```sql
GRANT INSERT, UPDATE ON scuola.Esami TO 'luca'@'localhost';
```

3. **Consentire la creazione di tabelle in tutto il database:**
    

```sql
GRANT CREATE ON scuola.* TO 'mario'@'localhost';
```

4. **Permettere a un utente di gestire i privilegi altrui:**
    

```sql
GRANT ALL PRIVILEGES ON scuola.* TO 'admin'@'localhost' WITH GRANT OPTION;
```

📌 L'opzione `WITH GRANT OPTION` permette all’utente di **concedere a sua volta i permessi ricevuti** ad altri utenti.

---

## ⛔ `REVOKE`: revocare permessi

Il comando `REVOKE` fa l’opposto di `GRANT`: **rimuove uno o più privilegi** concessi in precedenza.

### 📌 Sintassi:

```sql
REVOKE privilegio [, ...]
ON nome_oggetto
FROM 'utente'@'host';
```

### 📌 Esempi:

1. **Revocare la modifica dei dati:**
    

```sql
REVOKE UPDATE ON scuola.Studenti FROM 'giulia'@'localhost';
```

2. **Revocare tutti i permessi su un database:**
    

```sql
REVOKE ALL PRIVILEGES ON scuola.* FROM 'luca'@'localhost';
```

3. **Revocare il permesso di concedere privilegi:**
    

```sql
REVOKE GRANT OPTION ON scuola.* FROM 'admin'@'localhost';
```

---

## 👤 Creazione di un utente

Prima di concedere permessi, è necessario **creare l’utente**:

```sql
CREATE USER 'salvo'@'localhost' IDENTIFIED BY 'password123';
```

> Se non crei l’utente prima, `GRANT` fallisce (a meno che non sia già stato creato da un amministratore).

---

## 🔍 Consultare i permessi di un utente

Puoi vedere i privilegi di un utente con:

```sql
SHOW GRANTS FOR 'salvo'@'localhost';
```

Esempio di output:

```sql
GRANT SELECT, INSERT ON scuola.* TO 'salvo'@'localhost';
```

---

## 💡 Dove si applicano i permessi?

I permessi possono essere assegnati a diversi **livelli di granularità**:

- **Globali**: su tutti i database → `GRANT ALL ON *.*`
    
- **Per database**: `GRANT ALL ON nomeDB.*`
    
- **Per tabella**: `GRANT SELECT ON nomeDB.nomeTabella`
    
- **Per colonna** (meno usato): `GRANT SELECT(nomeColonna) ON tabella`
    
- **Per routine**: su stored procedures e funzioni.
    

---

## 🔒 Privilegi comuni

|Privilegio|Descrizione|
|---|---|
|`SELECT`|Leggere i dati|
|`INSERT`|Inserire nuovi dati|
|`UPDATE`|Modificare dati esistenti|
|`DELETE`|Cancellare dati|
|`CREATE`|Creare database o tabelle|
|`DROP`|Eliminare tabelle o database|
|`ALTER`|Modificare strutture (es. aggiungere colonne)|
|`INDEX`|Creare o gestire indici|
|`GRANT OPTION`|Concedere a terzi i permessi ricevuti|
|`ALL PRIVILEGES`|Tutti i privilegi disponibili|

---

## 🧼 Cancellare utenti e privilegi

### Eliminare un utente:

```sql
DROP USER 'salvo'@'localhost';
```

### Rimuovere tutti i privilegi:

```sql
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'salvo'@'localhost';
```

---

## 🧠 Riassunto visivo

- `CREATE USER`: crea un nuovo utente nel DBMS.
    
- `GRANT`: assegna privilegi (lettura, scrittura, modifica, gestione).
    
- `REVOKE`: rimuove privilegi precedentemente assegnati.
    
- `SHOW GRANTS`: visualizza i permessi attivi per un utente.
    
- `DROP USER`: elimina completamente un utente dal sistema.
    

---

## ✅ Conclusione

Il controllo dei privilegi è fondamentale per la sicurezza di un database. Usare correttamente **`GRANT` e `REVOKE`** ti permette di:

- isolare ruoli e responsabilità,
    
- prevenire accessi non autorizzati,
    
- proteggere i dati da modifiche accidentali o malevoli.
    

In MySQL, questa gestione è molto flessibile e precisa, e padroneggiarla dimostra una **maturità tecnica da livello professionale**, perfetta per farti brillare all'orale o in qualsiasi progetto serio.
