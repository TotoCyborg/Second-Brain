---
connections:
  - "[[Firewall]]"
---
L'Access Control List o ACL è un insieme di istruzioni da applicare alle interfacce di un router allo scopo di gestire il traffico, si utilizzano le ACL per fornire un livello base di sicurezza e aumentare la performance della rete e decidere quale tipo di traffico può essere trasmesso. Queste vengono elaborate dal router in maniera sequenziale nell'ordine in cui sono state inserite le varie clausole, appena un pacchetto soddisfa una delle condizioni il resto delle ACL non viene preso più in considerazione, il pacchetto viene quindi eliminato o inoltrato secondo le istruzioni.

L'ultima istruzione di un ACL è sempre una negazione implicita 'deny ip any any' che nega qualsiasi tipo di traffico, essa viene inserita automaticamente n ogni ACL, anche se non visibile. Proprio per questo che in un'ACL deve essere presente almeno un permit, diversamente l'unico risultato sarebbe la negazione di qualsiasi traffico per ogni direzione.

Quando le ACL vengono inserite all'interno dell'interfaccia bisogna specificare la direzione, che può essere in uscita o in ingresso sull'interfaccia. Con traffico in entrata si intende il traffico che arriva sul router prima dell'accesso alla tabella di routing, con traffico in uscita si intende il traffico già entrato nel router e sottoposto ad elaborazione per l'inoltro.

Le ACL possono essere:
- Standard ACL (1-99), controllano solo gli indirizzi sorgenti di tutti i pacchetti IP, individuano il traffico a livello 3, in base al solo IP sorgente. A quell'IP sarà pertanto concesso o negato l'accesso a qualsiasi servizio;
- Extended ACL(100-199), controllano entrambi gli indirizzi, sorgente e destinazione, individuano il traffico sino al livello 4, in base ai protocolli TCP o UDP e ai numeri di porta sorgente e di destinazione;

Sia le standard che le numeriche possono essere:
- Numbered (numeriche), con identificativo basato sui numeri da 1 a 99 e da 1300 a 1999 per le standard, da 100 a 199 e da 2000 a 2699 per le extended;
- Named (con nome),  identificate da un nome scelto dall'amministratore;

Su un router si può definire un'ACL per ogni controllo di livello 3 (come IP o Appletalk), per ogni interfaccia logica (ogni interfaccia 'subif' può avere la propria ACL), per ogni direzione (IN o OUT). Per esempio, in un interfaccia Ethernet 0/0 di un router che instrada solo il protocollo IP, possiamo avere per quest'interfaccia al massimo 2 ACL. 

Un altro aspetto molto importante è il posizionamento delle ACL:
- Posizionamento di ACL extended,  devono essere posizionate il più vicino possibile alla sorgente da filtrare, poiché posizionarle lontane dalla sorgente sarebbe inefficiente, in quanto i pacchetti attraverserebbero troppe zone prima di essere bloccati o filtrati;
- Posizionamento di ACL standard, devono essere posizionate il più vicino possibile alla destinazione poiché le ACL standard filtrano i pacchetti solo in base all'indirizzo sorgente, il posizionamento nei pressi dell'interfaccia sorgente potrebbe bloccare del traffico ritenuto valido;

## Configurazione di ACL standard numeriche

	Router(config)#access-list numero_ACL deny|permit ip_sorgente maschera_wildcard

## Configurazione di ACL extended numeriche

	Router(config)#access-list numero_ACL [deny|permit] protocollo ip-sorgente wildcard ip-destinazione wildcard condizione       applicazione

## Configurazione di ACL standard con nome

	Router(config)#ip access-list standard nome_ACL
	Router(config-std-nacl)# [deny|permit] ip-sorgente

## Configurazione di ACL extended con nome

	Router(config)#ip access-list extended nome-ACL
	 Router(config-ext-nacl)# deny-permit protocollo ip_sorgente wildcard_mask
	Ip_destinazione wildcard_mask condizione applicazione