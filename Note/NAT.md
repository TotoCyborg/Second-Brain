---
connections:
  - "[[Proxy]]"
---
Il NAT (Network Address Translation) è una tecnica attuata dal router che sostituisce nell'intestazione di un pacchetto IP quest'ultimo con un altro indirizzo, spesso usato per permettere a una rete locale che usa una classe di indirizzi privata, di accedere a Internet usando un solo indirizzo pubblico. Ovvio che il NAT non è efficace come un firewall, esso usa una tabella con la corrispondenza tra i socket interni ed esterni in uso, quando un client richiede una pagina web a un server esterno, il  suo socket viene traslato e la corrispondenza viene registrata nella tabella, quando la risposta arriva, la tabella permette al router NAT di effettuare la traslazione inversa e inviare i dati.

Il NAT presenta diversi vantaggi:
- Limita il numero di IP pubblici necessari per collegare una LAN a Internet;
- Mantiene inalterata la configurazione degli host;
- Non modifica il funzionamento dei protocolli e delle applicazioni della rete Internet;
- Offre una flessibilità elevata grazie allo spazio molto esteso per gli indirizzi;
- Riduce i costi di accesso ad Internet;
- Garantisce maggior sicurezza per i PC ad Internet;

 Il NAT presenta 3 funzionalità:
 - Static NAT: ha a disposizione un solo IP pubblico e a qualunque pacchetto in uscita assegnerà tale indirizzo;
 - Dynamic NAT:  ha a disposizione un insieme di indirizzi pubblici tra cui sceglierne uno da assegnare ai pacchetti in uscita;
 - [[PAT]] (Port Address Translation);

Anche IPv6 implementa una forma di NAT con scopi del tutto diversi dal NAT IPv4, con IPv6 non serve risparmiare indirizzi pubblici, ma far comunicare reti IPv6 con reti IPv4 in 3 modi, come ipotizzato da IETF:
- dual-stack: prevede l'utilizzo del doppio stack IP nella pila TCP/IP, per inoltrare pacchetti IPv4 e IPv6. Senza dubbio è la tecnica più semplice da implementare, ma presenta alcuni svantaggi come l'aumento della complessità della rete. È da sottolineare che non risolve il problema del numero degli indirizzi IPv4, in quanto secondo questa tecnica un'interfaccia dev'essere sempre e cmq dotata dei due indirizzi IPv4 e IPv6;
- conversion: è realizzato tramite il protocollo NAT-PT (Network Address Translation - Protocol Translator) che permette la comunicazione tra reti IPv6 e IPv4, questo sistema sfrutta i concetti introdotti dalla tecnologia NAT convertendo l'indirizzo IPv6 in uno IPv4. È sconsigliato il suo utilizzo quando vi è la comunicazione tra un host dual-stack  e un host solo IPv6 o IPv4;
- tunneling per IPv6: incapsula il pacchetto IPv6 in uno IPv4, permettendone così il trasporto su reti IPv4, viene solitamente utilizzata per far fronte ai problemi di incompatibilità  tra le reti IPv4 e IPv6. Con il tunneling si stabilisce un collegamento point-to-point tra due host;

Nel tunneling per IPv6 esistono due modi di agire:
- 4to6: nel tunneling IPv4 di un pacchetto IPv6, i pacchetti IPv6 vengono incapsulati dall'host sorgente in pacchetti IPv4, inviati nel tunnel IPv4 e una volta giunti a destinazione, l'host ricevente li decapsula per riottenere l'indirizzo in IPv6;
- 6to6: il tunneling IPv6 su IPv4 è di difficile realizzazione sulle reti globali per le complicazioni che introduce a livello di routing e quindi il suo utilizzo è limitato ad applicazioni e comunicazioni in reti locali più o meno grosse;