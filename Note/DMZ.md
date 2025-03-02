---
connections:
  - "[[Proxy]]"
---
Per aumentare di molto la sicurezza di una rete è buona norma dividerla in zone, in base al traffico e alla funzione se se ne identificano diverse, nei casi più semplici vi sono solo due zone che sono attestate sui due lati del firewall:
- zona LAN, ovvero il segmento privato e protetto che comprende tutti gli host e i server i cui servizi sono riservati all'uso interno;
- zona WAN, ovvero la parte esterna a cui appartengono gli apparati di routing che sostengono il traffico da e per la rete locale, Internet e sedi remote dell'azienda;

Vi sono casi in cui è necessaria la creazione di una terza zona detta DMZ (DeMilitarized Zone), che per definizione è un'area in cui sia il traffico LAN che quello WAN sono fortemente limitati e controllati, tale configurazione viene normalmente utilizzata per permettere ai server posizionati sulla DMZ di fornire servizi all'esterno senza compromettere la sicurezza della rete aziendale interna.


Nella DMZ solitamente si colloca la posta elettronica, con l'installazione di un server mail all'interno della rete aziendale che comporta la pubblicazione del servizio SMTP. Praticamente, il server che pubblica il servizio SMTP viene collocato in questa zona ed eventualmente insieme a lui, anche la web mail, l'antispam e l'antivirus, in LAN restano il server che ospita il database delle caselle e gli altri servizi. Un altro caso tipico sono gli Application Server che isolano un database residente in LAN, ma ne offrono un'interfaccia verso l'esterno.

Una DMZ, per esporre all'esterno i servizi di un'azienda, può essere realizzata in due modi:
- vicolo cieco: viene realizzato mediante un firewall con due porte, una verso la LAN e una verso la DMZ, oltre a quella verso la WAN;
- zona cuscinetto: viene creata aggiungendo un secondo firewall che prende il nome di external firewall, esso ha il compito di separare la rete pubblica dalla DMZ. Il primo, l'internal firewall, separa la DMZ dalla zona LAN vera e propria, questo garantisce una sicurezza migliore dei database presenti in LAN;