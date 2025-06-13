---
connections:
  - "[[TPSIT]]"
---
# Evoluzione dei sistemi informativi

Nel tempo, i sistemi informativi si sono evoluti, passando da architetture centralizzate a strutture distribuite, per rispondere alla crescente domanda di scalabilità e disponibilità. Nei sistemi centralizzati, tutte le applicazioni e i dati risiedono su un unico elaboratore, e gli utenti accedono tramite terminali remoti privi di capacità di elaborazione. Nei sistemi distribuiti, invece, le applicazioni sono suddivise tra più nodi cooperanti che condividono carichi e funzionalità. Questa transizione ha portato a un miglioramento in termini di:

- Prestazioni;
- Affidabilità;
- Flessibilità;

---

# Tipologie di applicazioni in un sistema distribuito

In un sistema distribuito, ogni nodo può assumere ruoli diversi. Il **client** è il nodo che richiede e utilizza i servizi offerti da altri; il **server**, al contrario, elabora e fornisce tali servizi. Esistono poi gli **actor** (o peer), che svolgono contemporaneamente entrambi i ruoli, come avviene nei sistemi peer-to-peer.

---

# Classificazione dei sistemi distribuiti

I sistemi distribuiti possono essere classificati in base alla loro funzione:

- **Sistemi di calcolo**: comprendono soluzioni come il _cluster computing_, formato da PC omogenei connessi in rete locale, e il _grid computing_, che utilizza PC eterogenei e geograficamente distribuiti;
- **Sistemi informativi distribuiti**: includono esempi come il Web o i sistemi gestionali aziendali;
- **Sistemi pervasivi**: comprendono dispositivi mobili, wearable, reti domestiche e sensori IoT.

---

# Vantaggi dei sistemi distribuiti

Adottare un sistema distribuito offre molteplici vantaggi. L'affidabilità è garantita dalla ridondanza: anche in caso di guasto di un nodo, il sistema continua a funzionare. L'integrazione tra componenti eterogenei è facilitata, così come la trasparenza, che consente all'utente di percepire il sistema come un'unica entità.

Secondo lo standard ISO 10746, esistono otto forme di trasparenza:

- **Accesso** uniforme a risorse locali e remote;
- **Localizzazione** indipendente: l'utente non deve conoscere la posizione delle risorse;
- **Concorrenza**, **replicazione** e **gestione guasti** automatizzate;
- Supporto alla **mobilità**, **scalabilità** e **ottimizzazione delle prestazioni** senza impatto percepibile.


Altri benefici significativi includono:

- Costi inferiori rispetto ai sistemi centralizzati;
- Adozione di protocolli aperti e interoperabili;
- Maggiore facilità nella condivisione di risorse.

---

# Svantaggi dei sistemi distribuiti

Nonostante i vantaggi, i sistemi distribuiti presentano alcune criticità. La loro progettazione è più complessa e richiede competenze specifiche. Inoltre:

- Sono più vulnerabili a minacce di sicurezza come sniffing e spoofing;
- Dipendono fortemente da reti stabili e performanti;
- Lo sviluppo software è più articolato e necessita di strumenti dedicati.

---

# Architetture hardware

La classificazione di Flynn (1972) distingue le architetture sulla base del numero di flussi di dati e di istruzioni che un sistema può elaborare contemporaneamente. Questo approccio consente di comprendere il grado di parallelismo e le capacità elaborative di un'architettura di calcolo. Le quattro categorie fondamentali sono:

- **SISD (Single Instruction, Single Data)**: elabora una singola istruzione su un singolo dato per volta. È il modello più semplice e rappresenta i tradizionali computer sequenziali, come i personal computer. Non prevede parallelismo, ma può eseguire compiti complessi attraverso l'uso di tecniche di programmazione;
- **SIMD (Single Instruction, Multiple Data)**: applica la stessa istruzione simultaneamente a più dati. È molto efficiente per operazioni ripetitive su grandi insiemi di dati, come nel caso del rendering grafico e dell’elaborazione di immagini o segnali. Le GPU (Graphics Processing Unit) sono un esempio tipico di architettura SIMD;
- **MISD (Multiple Instruction, Single Data)**: esegue più istruzioni diverse su uno stesso flusso di dati. È una configurazione teorica e raramente implementata, ma potrebbe essere impiegata in contesti molto specializzati, come nei sistemi critici che richiedono elevati livelli di ridondanza e affidabilità (es. controllo di volo);
- **MIMD (Multiple Instruction, Multiple Data)**: ogni processore può eseguire istruzioni diverse su dati differenti, in parallelo. È il modello più flessibile e diffuso nei sistemi multiprocessore moderni. Si divide in:
    
    - **Memoria condivisa**: tutti i processori accedono alla stessa memoria centrale (multiprocessori), ideale per sistemi compatti;
    - **Memoria distribuita**: ogni processore ha una propria memoria locale e comunica con gli altri tramite messaggi (multicomputer), usato in cluster e supercomputer;

Nel confronto tra **cluster** e **grid**, il primo prevede nodi omogenei fisicamente vicini, connessi tramite rete locale ad alta velocità e gestiti centralmente. È adatto per calcoli scientifici o ambienti ad alte prestazioni. Il **grid computing**, invece, collega risorse eterogenee e distribuite geograficamente, spesso appartenenti a domini amministrativi diversi, e richiede politiche di sicurezza e gestione più complesse.

I **sistemi pervasivi** si basano su:

- Nodi piccoli e mobili;
- Connessione wireless;
- Capacità di autoconfigurazione e minima necessità di intervento tecnico;
- Nodi piccoli e mobili;
- Connessione wireless;
- Capacità di autoconfigurazione e minima necessità di intervento tecnico;

---

# Architetture software

Le architetture software nei sistemi distribuiti includono modelli diversi:

- **Terminali remoti**: privi di capacità elaborativa;
- **Client-server**: relazione di richiesta e risposta tra client e server;
- **Web-centric**: centralizzazione delle funzionalità in un server Web;
- **Cooperative**: nodi autonomi che collaborano tra loro;
- **Completamente distribuite**: assenza di nodo centrale, come nel P2P;
- **A livelli**: separazione tra interfaccia utente, logica applicativa e accesso ai dati.

---

# Comunicazione web e HTTP

Sul Web la comunicazione avviene principalmente tramite il protocollo **HTTP**, un protocollo di tipo **client-server** basato su **TCP** e operante di default sulla porta 80. Le connessioni possono essere:

- **Incanalate**: una richiesta alla volta;
- **Non incanalate**: più richieste parallele nella stessa connessione;

I messaggi HTTP si dividono in:

- **Request**: includono metodo (GET, POST...), URI, intestazioni e corpo;
- **Response**: includono versione, codice di stato, intestazioni e corpo (es. HTML, JSON);

I metodi più comuni sono:

- **GET**: per ottenere dati;
- **POST**: per inviare dati;
- **PUT**: per creare o aggiornare;
- **DELETE**: per rimuovere;

---

# Applicazioni web e architetture

Le tecnologie **client-side** (HTML, CSS, JavaScript) sono visibili e vengono eseguite nel browser, mentre quelle **server-side** (PHP, Java, Python) restano invisibili all’utente ed elaborano le richieste lato server.

In un’architettura **client-server**, il client invia richieste tramite un **socket** (IP + porta), e il server le gestisce. Le comunicazioni possono avvenire in:

- **Unicast**: singolo client;
- **Multicast**: più client in parallelo con thread dedicati;

L'**architettura a tre livelli (3-tier)** prevede:

1. **Presentation Layer**: interfaccia utente;
2. **Business Logic Layer**: logica applicativa;
3. **Data Access Layer**: interazione con i dati;

> Nei **thin client** la logica risiede sul server, mentre nei **thick client** parte della logica viene eseguita anche sul lato client.

---

# Protocolli e Socket

Nel livello applicazione del modello TCP/IP operano vari protocolli fondamentali:

- **HTTP**: navigazione web;
- **FTP**: trasferimento file;
- **SMTP, POP3, IMAP4**: gestione email;
- **DNS**: risoluzione dei nomi;
- **SNMP**: monitoraggio e gestione dei dispositivi di rete;

I **socket** identificano una connessione attraverso una combinazione unica di IP e porta. Ogni comunicazione attiva utilizza un **socket dinamico**, mentre un **socket di benvenuto** rimane in ascolto per accettare nuove connessioni in arrivo.

---

# Architetture di rete

Nel modello **client-server**, il server possiede un IP fisso e può essere potenziato tramite una server farm per bilanciare il carico di lavoro. I sistemi **peer-to-peer (P2P)**, invece, prevedono che ogni nodo sia allo stesso tempo client e server.

Le varianti includono:

- **P2P centralizzato**: un server principale conserva gli indici dei file;
- **P2P ibrido**: alcuni nodi, detti **super peer**, gestiscono il coordinamento e facilitano le comunicazioni tra i peer semplici.