---
connections:
  - "[[Routing]]"
---

*Il Routing Gerarchico*
Le tabelle di routing di grandi dimensioni possono causare seri problemi: saturano la memoria del router e rallentano le trasmissioni, costringendo la CPU a elaborazioni complesse per calcolare i percorsi ottimali. Inoltre, gli aggiornamenti frequenti delle routing table, dovuti ai continui scambi di informazioni tra numerosi router, aumentano il traffico di rete e riducono le prestazioni complessive.

Quando una rete diventa troppo grande e non è più possibile inserire tutte le destinazioni nelle tabelle dei router, è necessario riorganizzarla. In questi casi si adotta il principio del “divide et impera”. In pratica, invece di mantenere un’unica rete estesa, la si suddivide in più reti di dimensioni più contenute (dette regioni). All’interno di ciascuna regione, la comunicazione avviene secondo protocolli standard. Le connessioni tra regioni sono garantite da router dedicati che, a loro volta, comunicano tra loro come se facessero parte di una rete separata.

Questo approccio prende il nome di **routing gerarchico**. Secondo questo modello, la rete viene suddivisa in regioni interconnesse. Ogni router conosce in dettaglio solo la topologia della propria regione, ma non quella delle altre. Questo comporta un peggioramento delle prestazioni globali, poiché i percorsi non sono ottimizzati a livello interregionale.

---

*Gli Autonomous System*
Nei primi anni Ottanta, Internet era considerata un’unica rete in cui ogni router possedeva una tabella di instradamento con una voce per ogni rete raggiungibile e l’indirizzo del router da contattare. Questo modello centralizzato non era più sostenibile con la crescita della rete. Si decise quindi di suddividere Internet in più domini chiamati **Autonomous System (AS)**, ciascuno costituito da un insieme di router e LAN organizzati secondo criteri topologici o amministrativi.

Ogni AS è identificato da un numero unico assegnato dall’IANA. I router che collegano diversi AS vengono spesso chiamati **gateway**, poiché svolgono il compito di inoltrare pacchetti da una rete verso l’esterno.

###### Comunicazione tra router

All’interno di un AS, le informazioni di raggiungibilità vengono scambiate tramite uno o più protocolli adattivi, detti **Interior Protocol**. Gli AS tra loro si scambiano informazioni di raggiungibilità attraverso protocolli chiamati genericamente **Exterior Protocol**.

Se un router deve inoltrare un messaggio verso un altro router appartenente allo stesso AS, si parla di comunicazione tra **Interior Router (IR)**, e nella sua tabella sarà presente l'informazione necessaria. Se invece il messaggio è destinato a un router in un altro AS, verrà inoltrato a una coppia di **Exterior Router (ER)**, uno per ciascun AS coinvolto. Ogni ER conosce le reti raggiungibili tramite i link che lo collegano ad altri ER, ma non conosce la struttura interna degli AS esterni.

Gli accordi tra gestori di diversi AS per definire politiche di transito e raggiungibilità sono chiamati **accordi di peering**.

---

*I Protocolli di Routing: Interior ed Exterior*
###### Interior Gateway Protocol (IGP)

I protocolli IGP sono utilizzati **all’interno** di un AS per regolare l’instradamento dei pacchetti. Sono chiamati protocolli **intradominio**. Possono essere classificati in base all’algoritmo che utilizzano:

- Distance Vector:
    
    - **RIP** (Routing Information Protocol): usa come metrica il numero di hop.
        
    - **IGRP** (Interior Gateway Routing Protocol): protocollo Cisco, supera i limiti di RIP supportando più metriche (banda, ritardo, carico, affidabilità).
        
    - **EIGRP** (Enhanced IGRP): sempre di Cisco, migliora IGRP pur mantenendone le metriche.
        
- Link State:
    
    - **OSPF (Open Shortest Path First)**.
        
    - **Integrated IS-IS (Intermediate System to Intermediate System)**: standard ISO e poi adottato anche da IETF.
        

###### Exterior Gateway Protocol (EGP)

I protocolli EGP sono utilizzati **tra diversi AS**, per questo si definiscono protocolli **extradominio**. Il principale protocollo utilizzato su Internet è il **BGP (Border Gateway Protocol)**, nella sua versione attuale **BGP-4**. BGP utilizza un algoritmo di tipo **Path Vector**, simile al Distance Vector, ma invece di contare semplicemente gli hop, costruisce un vettore contenente l’elenco degli AS da attraversare per raggiungere una destinazione.

---

