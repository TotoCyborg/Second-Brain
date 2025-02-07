---
connections:
  - "[[VPN]]"
---
Una valida alternativa all'IPsec è rappresentata dai protocolli SSL/TLS (Security Sockets Layer/Transport Layer security). Le differenze tra SSL e TLS sono minime, in genere vengono implementati entrambi rendendoli interoperabili, Il TSL è un protocollo del livello Session ed è uno standard IETF e deriva dal SSL.

Il protocollo SSL/TLS è composto da due livelli: 
- Record Protocol, che opera subito sopra un protocollo di livello Transport (come TCP)  ed è utilizzato per incapsulare protocolli di livello superiore;
- Handshake Protocol, che rappresenta il livello superiore e si occupa della fase di negoziazione in cui si autentica l'interlocutore e si stabilisce la crittografia comune;

Per realizzare un SSL/TSL bisogna utilizzare tale protocollo al posto di IKE nell'IPsec, per la fase di autenticazione degli estremi del tunnel e la creazione delle chiavi. Per definizione, SSL/TLS è un semplice protocollo Client/Server che ha lo scopo di autenticare il server da parte del client e, opzionalmente, anche il client da parte del server, e di creare un canale cifrato sicuro per la comunicazione tra i due.

L’autenticazione si basa su **certificati digitali** firmati da una Certification Authority (CA)**. Il server invia il proprio certificato al client, che ne verifica la validità controllando la firma digitale. Se valida, il server viene autenticato, altrimenti la connessione fallisce. I passaggi per una connessione sicura sono:
- **Client → Server**: invia la richiesta di connessione con gli algoritmi di crittografia supportati e un valore random per la pre-master key;
- **Server → Client**: invia il certificato digitale, la scelta degli algoritmi e il proprio valore random;
- **Client → Server**: verifica il certificato, invia il proprio certificato e la pre-master key cifrata con la chiave pubblica del server, poi richiede il passaggio alla comunicazione cifrata;
- **Server → Client**: conferma l’avvenuta autenticazione e avvia la comunicazione cifrata;

Mettendo a confronto i due protocolli, IPsec e SSL/TLS:
- **IPsec** è un’**architettura complessa** con più protocolli, mentre **SSL/TLS** è un **protocollo definito tramite RFC**;
- **IPsec** offre più metodi di autenticazione, ma **SSL/TLS** si basa solo sui certificati digitali;
- **SSL/TLS** può autenticare solo il server senza il client, mentre **IPsec** richiede autenticazione reciproca;
- **SSL/TLS opera a livello Session**, proteggendo i dati fino alla consegna. **IPsec opera a livello Network**, proteggendo tutto il traffico IP ma non i dati dopo l’arrivo all’host;
- **SSL/TLS funziona solo con TCP**, mentre IPsec protegge tutti i protocolli sopra IP (TCP, UDP, ICMP);