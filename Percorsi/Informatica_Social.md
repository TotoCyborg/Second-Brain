---
connections:
  - "[[Social Media]]"
---

# Basi di dati e DBMS
---

I **social media** sono applicazioni complesse che gestiscono quotidianamente miliardi di dati: profili utente, contenuti pubblicati, messaggi privati, reazioni, commenti, relazioni tra utenti, impostazioni personali e molto altro. Per organizzare e manipolare in modo efficiente queste informazioni è indispensabile l’uso delle **basi di dati**, e in particolare dei **DBMS (Database Management System)**.

Una **base di dati** è una collezione strutturata di dati correlati tra loro. Nei social media, le basi di dati contengono per esempio tabelle come:

- **utenti** (con dati anagrafici, email, password cifrate);
    
- **post** (contenuti pubblicati, autore, timestamp);
    
- **relazioni** (amici, follower, blocchi);
    
- **messaggi** (mittente, destinatario, contenuto).
    

Il **DBMS** è il software che consente di creare, modificare, interrogare e mantenere queste basi di dati, garantendo **efficienza, sicurezza e consistenza**. Alcune delle sue funzioni principali includono:

- la **gestione dei dati persistenti**, salvati su disco anche dopo la chiusura dell’applicazione;
    
- l’**accesso concorrente**, permettendo a milioni di utenti di usare l’app nello stesso momento;
    
- il mantenimento dei **vincoli di integrità** (come chiavi primarie e chiavi esterne);
    
- la **gestione dei permessi** e la **protezione dei dati** contro accessi non autorizzati.
    

I social network usano sia **DBMS relazionali**, come **MySQL** o **PostgreSQL**, per i dati strutturati, sia **sistemi NoSQL** (come **MongoDB** o **Cassandra**) per contenuti più flessibili o ad alto volume, come immagini, commenti o reazioni.

Questi dati vengono poi gestiti e interrogati con **linguaggi di query**, in particolare **SQL**, che consente di selezionare informazioni, aggiornarle, inserirle o cancellarle in modo controllato e preciso. Esempi reali: recuperare i post più recenti di un utente, cercare gli amici comuni tra due profili o suggerire contenuti basati sulle interazioni precedenti.

Un altro ruolo fondamentale del DBMS nei social media è legato alla **personalizzazione dell’esperienza utente**: i dati raccolti vengono analizzati e filtrati per proporre suggerimenti, pubblicità mirata, gruppi affini, aumentando così l’efficacia della piattaforma. Tutto ciò sarebbe impossibile senza un sistema in grado di **archiviare, indicizzare e interrogare grandi quantità di dati in tempo reale**.

In sintesi, i **DBMS** sono il cuore dell’architettura dei social media: senza di essi non sarebbe possibile né gestire miliardi di dati ogni giorno né offrire un’esperienza personalizzata e dinamica agli utenti. Essi rappresentano la **spina dorsale informatica** che sostiene tutta la complessità delle piattaforme social.
