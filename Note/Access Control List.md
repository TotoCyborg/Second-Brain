---
connections:
  - "[[Firewall]]"
---
L'Access Control List o ACL è un insieme di istruzioni da applicare alle interfacce di un router allo scopo di gestire il traffico, si utilizzano le ACL per fornire un livello base di sicurezza e aumentare la performance della rete e decidere quale tipo di traffico può essere trasmesso. Queste vengono elaborate dal router in maniera sequenziale nell'ordine in cui sono state inserite le varie clausole, appena un pacchetto soddisfa una delle condizioni il resto delle ACL non viene preso più in considerazione, il pacchetto viene quindi eliminato o inoltrato secondo le istruzioni.
Le ACL possono essere:
- Standard ACL, che specificano delle limitazioni ai pacchetti guardando esclusivamente l'indirizzo della sorgente e vanno posizionate il più vicino possibile alla destinazione finale;
- Extended ACL, che porgono le limitazioni ai pacchetti in base a molte specifiche, come il protocollo usato o la porta a cui è indirizzato il pacchetto;