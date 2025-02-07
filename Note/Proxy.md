---
connections:
  - "[[Firewall]]"
---
Un proxy è un programma che si frappone tra client e server facendo da tramite, il client si collega al proxy e gli invia la richiesta, il proxy a sua volta si collega al server a cui inoltra la richiesta del client, infine il proxy inoltra la risposta al client. Al suo interno troviamo l'utilizzo di diverse tecniche come [[NAT]] e PAT ed essi lavorano a livello Application, il loro compito principale è garantire la connettività e il caching ai client a loro collegati, ai dini dell'efficienza della rete. 

Questo si colloca prossimo al client in modo da permettere un miglioramento delle prestazioni e una riduzione del consumo di banda, e tra i suoi compiti principali vi sono:
- Connettività: permettendo ad una rete privata di accedere a Internet tramite un solo PC;
- Privacy: permettendo di mascherare il vero IP del client;
- Caching: permettendo di immagazzinare per un certo tempo i risultati delle richieste di un client;
- Monitoraggio: permettendo di tenere traccia di tutte le operazioni effettuate; 
- Amministrazione: permettendo di applicare le regole definite dell'amministratore di sistema per determinare quali richieste inoltrate, quali rifiutare e limitare l'ampiezza di banda utilizzata dai client;
- Filtraggio: permettendo di svolgere funzioni di firewall a livello Application, garantendo protezione a scapito della velocità della rete;
- Restrizioni: permettendo di creare una zona neutra o terza zona, nota anche come [[DMZ]], dove il traffico tra le due è fortemente limitato e controllato;

I proxy possono essere utilizzati in diversi modi, a seconda di dove vengono collocati:
- Single Proxy Topology, che è la scelta più semplice poiché utilizza un singolo Proxy Server per servire l'intera rete, è però solo sufficiente per un piccolo gruppo di client;
- Multiple Proxy Vertically Topology, che è la scelta migliore per reti medio-grandi poiché si configurano più proxy, uno primario a cui gli altri si connettono e più secondari che agiscono come fossero dei client di quello primario. Questa è una tecnica che consente a qualsiasi client di avere il filtraggio dei pacchetti personalizzato;
- Multiple Proxy Horizontally Topology, ottimo in quanto bilancia il carico tra i server in base alle richieste dei client, in tal modo le informazioni sul trattamento dei pacchetti personalizzati si distribuiscono ai server di pari livello per riuscire a garantire la risoluzione in locale;

Il proxy si avvale di determinate tecniche come NAT e PAT per 