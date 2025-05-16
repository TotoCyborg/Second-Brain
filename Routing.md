---
connections:
  - "[[Sistemi e Reti]]"
---

Il routing (instradamento) è una funzione del livello Network del modello TCP/IP. Viene svolta da un dispositivo di rete chiamato **router** (o sistema intermedio), che per ottimizzare il percorso dei pacchetti deve conoscere ed eventualmente aggiornare una serie di informazioni. Solo sulla base di queste informazioni il router può avviare il processo di **forwarding**, stabilendo verso quale linea inviare il pacchetto.

---

*Il Router*
Un router è un dispositivo hardware dedicato a far comunicare reti differenti ed eterogenee, instradando i pacchetti nella giusta direzione. È connesso a due o più reti e decide il percorso che i dati devono seguire, basandosi sulle informazioni sullo stato delle reti collegate.

La funzione principale del router è quella di reindirizzare i messaggi tra reti di computer affinché possano raggiungere la destinazione finale. Le due attività fondamentali che svolge sono: la scelta del percorso migliore (routing) e l’invio dei pacchetti sull’interfaccia di uscita corretta (forwarding).

Un router, essendo un computer dedicato al routing, necessita di un sistema operativo. Dal punto di vista hardware deve avere almeno due schede di rete. Un router dotato di una scheda di rete verso la LAN e una verso la WAN può essere configurato come **gateway**, condividendo l’accesso a Internet per tutti i computer della rete locale. In questo caso, l’interfaccia del router che funge da gateway diventa la “via di uscita” degli host dalla LAN.

---

*Routing Table*
È fondamentale che il router costruisca nella propria memoria cache una **tabella di instradamento** (routing table), che gli consenta di memorizzare le informazioni necessarie a identificare il percorso ottimale verso le reti remote. Questa tabella è una lista di tutte le reti raggiungibili, con informazioni sulle modalità di instradamento.

Quando il router esegue il forwarding di un pacchetto, consulta la routing table per cercare l’indirizzo di rete corrispondente all’IP di destinazione.

Ogni riga (entry) della tabella di routing contiene quattro campi:
- l'indirizzo IP della rete raggiungibile (network address),
- l’indirizzo del router successivo (next hop),
- l’interfaccia del router a cui inoltrare il pacchetto (interface),
- la metrica, cioè un valore che rappresenta il costo del percorso. Il router sceglierà il percorso con il costo minore.

---

*Routing Statico e Dinamico*
Il funzionamento del router dipende da come viene creata la routing table. Se viene inserita manualmente dall’amministratore, si parla di **routing statico**, utilizzabile soprattutto in piccole reti. Se invece la tabella viene costruita automaticamente dal router in base alle informazioni ricevute tramite protocolli di routing, si parla di **routing dinamico**.

Il routing statico è indicato quando i segmenti di LAN non sono molti.

---