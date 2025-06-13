---
connections:
  - "[[Informatica]]"
---


# Archivio e organizzazione tradizionale dei dati

Un **archivio** è un insieme strutturato di informazioni, organizzato per essere facilmente consultabile e conservato nel tempo. Per essere considerato tale, un archivio deve rispettare alcune condizioni fondamentali:  
innanzitutto, tra le informazioni contenute deve esserci un **nesso logico**, ovvero un criterio che giustifica la loro aggregazione. Le informazioni devono inoltre essere **rappresentate in un formato leggibile** (dall'uomo o dalla macchina) e memorizzate su un **supporto stabile e persistente**, che permetta la lettura e la scrittura anche a distanza di tempo. Infine, l’organizzazione deve essere tale da **favorire l’accessibilità** e la consultazione dei dati da parte degli utenti o dei programmi.

 *Record e File*

All’interno di un archivio, le informazioni sono suddivise in **unità logiche chiamate record**, ognuna delle quali rappresenta un’entità completa, come ad esempio una persona, un libro o una transazione. Ogni record è composto da **campi**, e ogni campo contiene un valore relativo a una caratteristica dell’entità.  
L’insieme dei record che condividono la stessa struttura costituisce un **file**, ovvero una raccolta omogenea di dati logicamente coerenti. Ad esempio, un file può contenere i record di tutti gli studenti di una scuola, con campi come nome, cognome, età, classe.

---

# Organizzazione tradizionale degli archivi

L'organizzazione di un archivio ha l'obiettivo di **ottimizzare l’uso dello spazio** e **ridurre i tempi di ricerca**, in un’epoca in cui l'accesso ai dati avveniva soprattutto tramite supporti magnetici come nastri o dischi rigidi con prestazioni limitate. Si distinguono diverse tecniche organizzative.

 *Organizzazione sequenziale*

In questo metodo, i record sono memorizzati **uno dopo l'altro**, seguendo l’ordine cronologico o logico di inserimento. Ogni record è separato da un delimitatore chiamato **EOR** (End of Record).  
L’accesso avviene in maniera **sequenziale**, cioè per leggere un certo record è necessario scorrere tutti i precedenti. È un modello simile a quello del pacco di schede: per trovare un’informazione, bisogna controllare una per una.

La scrittura può avvenire in qualsiasi punto del file, ma se si scrive in una posizione intermedia, tutti i record successivi vengono cancellati. Questo limita molto la flessibilità e rende difficoltose le modifiche. Inoltre, i tempi di ricerca aumentano notevolmente con l'aumentare delle dimensioni dell’archivio.  
Nonostante ciò, questo metodo ha il vantaggio di essere semplice da implementare ed è adatto a casi in cui l'elaborazione avviene in blocco, come nei registri contabili o nei sistemi di archiviazione cronologica.

 *Organizzazione ad accesso diretto (o random)*

Con questo tipo di organizzazione, **tutti i record hanno la stessa lunghezza** e sono memorizzati in posizioni fisse, calcolabili. Ciò consente di accedere a un record specifico direttamente, senza scorrere i precedenti.  
L’accesso avviene tramite **calcolo dell’offset**, ovvero si determina la posizione fisica del record all'interno del file sulla base di un identificatore.

Questo metodo garantisce una maggiore rapidità nell’accesso, ma impone una struttura molto rigida: i campi devono essere fissi, e non è possibile usare record di lunghezza variabile. Inoltre, se si desidera inserire un nuovo record, si è spesso costretti a **sovrascrivere** uno già esistente, in quanto non c’è una gestione dinamica dello spazio libero.

 *Organizzazione ad accesso indicizzato*

Per superare i limiti delle due modalità precedenti, si è sviluppato il modello ad **accesso indicizzato**. In questo sistema, ai record è associata una **chiave univoca**, utilizzata per identificarli. Le chiavi e i riferimenti ai record corrispondenti vengono memorizzati in un **file di indice** ad accesso diretto, il che consente di trovare rapidamente il record associato a una determinata chiave.

Questo metodo unisce la velocità dell’accesso diretto con una maggiore flessibilità nella gestione dei dati, permettendo anche operazioni di aggiornamento e inserimento meno invasive.

 *Organizzazione sequenziale ad indice*

Simile al modello precedente, in questo caso i record sono memorizzati in **ordine di immissione**, ma l’accesso è comunque ottimizzato grazie alla presenza di un indice, che contiene le chiavi di ricerca.  
Il vantaggio principale di questo modello è la possibilità di combinare **efficienza di accesso** e **semplicità nella memorizzazione**, soprattutto quando i dati vengono letti frequentemente in ordine.

Tuttavia, l’indice ha un **costo di costruzione e aggiornamento**: ogni inserimento, eliminazione o modifica comporta operazioni sull’indice, che può diventare molto complesso in archivi di grandi dimensioni.

---

# Limiti dell’organizzazione tradizionale

Il principale limite degli archivi tradizionali è rappresentato dalla **forte dipendenza dal software** che li gestisce. Spesso la struttura del file è progettata per un’applicazione specifica, e risulta difficile da riutilizzare o interfacciare con altri sistemi.

Tra i problemi più evidenti:

- **Dipendenza dei dati**: se il software che gestisce l’archivio cambia o smette di funzionare, i dati rischiano di diventare inaccessibili;
    
- **Isolamento dei dati**: ogni applicazione gestisce i propri dati, senza condivisione o integrazione con altri sistemi;
    
- **Ridondanza e inconsistenza**: lo stesso dato può essere memorizzato più volte in file diversi, portando a possibili contraddizioni;
    
- **Difficoltà nella gestione dell’integrità**: mancano strumenti automatici per garantire che i dati siano corretti e coerenti;
    
- **Anomalie di concorrenza**: più utenti che accedono contemporaneamente allo stesso archivio possono generare conflitti o errori;
    
- **Bassa sicurezza**: l’accesso non è regolato da veri meccanismi di autorizzazione o cifratura;
    
- **Backup e ripristino complessi**: non esistono strumenti integrati per effettuare copie di sicurezza o recuperare i dati dopo un guasto.
    