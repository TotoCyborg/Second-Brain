---
connections:
  - "[[Sistemi e Reti]]"
---
Esistono sia reti private vere e proprie che collegano più sedi in una rete aziendale tramite canali dedicati, sia reti private virtuali. I vantaggi delle reti private sono:
- Larghezza di banda sempre disponibile;
- Nessun problema di accesso;
- Nessuna congestione del traffico;
- Sicurezza e prestazioni ottimali;

Abbiamo anche numerosi svantaggi:
- Alti costi ricorrenti di gestione;
- Lunghi tempi di configurazione;
- Mancanza di scalabilità;
- Rischio di blocco del canale in caso di guasto;

Per ovviare a questi problemi si ricorre alle reti private virtuali. Una VPN (Virtual Private Network) è una rete privata creata all'interno di un'infrastruttura di rete pubblica come Internet. Il rischio di blocco della rete è minimo grazie all'alto grado di ridondanza offerto dalla rete pubblica. Purtroppo vi sono anche delle problematiche, le principali sono 3:
- variabilità di tempo di trasferimento;
- controllo degli accessi;
- sicurezza delle trasmissioni;

Il primo problema viene affrontato tramite l'utilizzo delle WAN, il secondo e il terzo grazie ai fattori di autenticazione, cifratura e tunneling.
Esistono due tipi di VPN in commercio, le [[Remote-access VPN]] e le [[Site-to-site VPN]]. Ovviamente le VPN devono affrontare seri problemi nell'ambito sia della sicurezza dei dati che della riservatezza delle trasmissioni. In questo campo i fattori su cui bisogna concentrare la nostra attenzione sono 3:
- [[Autenticazione dell'Identità]];
- [[Cifratura]];
- [[Tunneling]];

 I principali protocolli usati per garantire la sicurezza della rete sono :
- [[IPsec]];
- [[SSLTLS]];
- BGP/MPLS (Border Gateway Protocol / Transport Layer Security);

In base ai protocolli che utilizzano e al grado di sicurezza che garantiscono, possiamo classificare le VPN in 3 categorie:
- [[Trusted VPN]], si affida al proprio Internet Service Provider (ISP);
- [[Secure VPN]], si affida ai protocolli per la sicurezza;
- [[Hybrid VPN]], si affida sia al proprio ISP che ai protocolli per la sicurezza;