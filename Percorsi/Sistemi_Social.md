---
connections:
  - "[[Social Media]]"
---

# VPN
---

Le **VPN (Virtual Private Network)** sono tecnologie che permettono di **trasmettere dati in modo sicuro su reti pubbliche** come Internet, creando un **tunnel cifrato** tra il dispositivo dell’utente e un server remoto. Questa struttura protegge i dati da intercettazioni, garantendo **riservatezza, integrità e autenticazione** nella comunicazione.

Esistono principalmente **due tipologie di VPN**:

- La **Remote Access VPN**, utilizzata da singoli utenti per collegarsi da remoto a una rete privata (es. rete aziendale), molto utile per lavoratori in smart working o studenti a distanza;
    
- La **Site-to-Site VPN**, che collega due o più reti locali geograficamente distanti tra loro, come se fossero un’unica rete, ed è molto usata tra diverse sedi di un’azienda.
    

Per realizzare il tunnel VPN in modo sicuro si utilizzano protocolli specifici. Uno dei più importanti è **IPsec (Internet Protocol Security)**, un insieme di protocolli che opera a livello rete (livello 3 OSI). IPsec offre tre componenti fondamentali:

1. **AH (Authentication Header)**: garantisce l'autenticità del mittente e l'integrità del pacchetto, ma **non cripta** il contenuto;
    
2. **ESP (Encapsulating Security Payload)**: aggiunge la **crittografia** dei dati, assicurando anche integrità e autenticazione;
    
3. **IKE (Internet Key Exchange)**: gestisce lo **scambio e la negoziazione delle chiavi crittografiche**, fondamentale per avviare e mantenere la comunicazione cifrata.
    

IPsec può operare in:

- **Transport mode**: dove viene cifrato solo il contenuto del pacchetto IP (payload), mantenendo l’header visibile;
    
- **Tunnel mode**: dove l’intero pacchetto IP originale viene incapsulato in un nuovo pacchetto IP, garantendo la **massima sicurezza**. È il più usato nelle Site-to-Site VPN.
    

Un altro protocollo usato nelle VPN è **SSL/TLS**, che funziona a livello di trasporto e viene sfruttato per stabilire connessioni sicure tramite il browser (HTTPS) o client dedicati. È più facile da configurare e spesso utilizzato per connessioni **Remote Access**.

Nel contesto dei **social media**, l’utilizzo delle VPN diventa fondamentale per garantire **libertà e privacy**. In molti paesi autoritari, i social sono **censurati o limitati**; le VPN permettono agli utenti di **aggirare questi blocchi** attraverso server in altri paesi. Inoltre, proteggono la comunicazione dell’utente quando usa reti pubbliche, impedendo a malintenzionati di intercettare messaggi, credenziali o contenuti privati.

In conclusione, le VPN — grazie a protocolli come **IPsec** e **SSL/TLS** — non solo forniscono sicurezza tecnica, ma hanno anche un **impatto sociale e politico**, specialmente in relazione all’uso libero e sicuro dei **social media**, tutelando la privacy e la libertà digitale degli utenti.
