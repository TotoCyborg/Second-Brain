---
connections:
  - "[[Sistemi e Reti]]"
---
Il firewall è una linea di difesa che filtra tutti i pacchetti sia in entrata che in uscita da una rete, secondo regole prestabilite che contribuiscono alla sicurezza della rete stessa, questo si può comunemente realizzare tramite un PC, l'apposito software e le [[Access Control List]] che servono per configurarlo. I firewall si possono distinguere in 3 categorie in base al livello dello stack TCP/IP in cui operano:

- [Application Level Firewall]: intercetta le trasmissioni a livello Application valutando il contenuto applicativo dei pacchetti, come i [[Proxy]];
- [Packet Filtrer Firewall]: lavora a livello Network e Transport, è più veloce dell'Application perché controlla solo l'header e poiché il firewall non gestisce i dati all'interno del pacchetto viene solitamente  impiegato nei punti di origine della connessione a Internet;
- [Stateful Packet Inspection Firewall]: agisce solo a livello Transport, controlla e analizza tutto il pacchetto dati. Questo tipo di firewall può controllare lo stato di connessione TCP e compilare le informazioni ottenute su una tabella;
