---
connections:
  - "[[VPN]]"
---
L'IPsec è la scelta più frequente per realizzare sia le Site-to-site VPN con topologia a maglia completa che le Remote-access VPN con topologia a stella. Questo non è un singolo protocollo, ma piuttosto un'intera infrastruttura di sicurezza a livello Network composta da 3 protocolli:
- Authentication Header (AH): garantisce l'autenticazione e l'integrità del messaggio, ma non offre confidenzialità. Viene definito nell'RFC 4302;
- Encapsulating Security Payload (ESP): fornisce autenticazione, confidenzialità e integrità del messaggio. Viene definito nell'RFC4303;
- Internet Key Exchange (IKE): implementa lo scambio delle chiavi per il flusso crittografico. Viene definito nell'RFC 7296;

IPsec utilizza il protocollo **ESP** per l’invio sicuro dei datagrammi, poiché fornisce confidenzialità rispetto ad **AH**. In **IPv4**, AH ed ESP sono header di protocollo, mentre in **IPv6** sono extension header. Il protocollo **IKE**, invece, opera a livello Application sia in IPv4 che in IPv6. IPsec può funzionare in due modalità:
- **Trasporto**: aggiunge gli header AH/ESP tra l’header IP e il protocollo di trasporto (TCP/UDP);
- **Tunnel**: incapsula completamente il pacchetto IP originario;

Per garantire la sicurezza, due host stabiliscono una **Security Association (SA)** tramite **IKE**. Poiché le SA sono unidirezionali, ne servono due per una comunicazione bidirezionale. Le SA attive sono memorizzate nel **SAD (SA Database)**, mentre le politiche di sicurezza sono nel **SPD (Security Policy Database)**. L'elaborazione dei pacchetti distingue il **traffico in uscita (outbound)** da quello **in entrata (inbound)**:
- **Outbound**: si verifica lo SPD, si associa il pacchetto a una SA esistente (o si crea con IKE), si applica IPsec e si inoltra;
- **Inbound**: si ricompone il datagramma IP (se frammentato), si identifica il pacchetto tramite il campo protocollo e il valore **SPI**, si eseguono le operazioni IPsec, si controlla lo SPD e si inoltra il pacchetto alla destinazione o al livello superiore;

Ora andiamo a dare uno sguardo più specifico ai 3 protocolli principali dell’IPsec:
- AH: fornisce servizi di autenticazione, integrità e protezione da attacchi di tipo replay, in cui un intruso immette nella rete un pacchetto autentico precedentemente intercettato. Il campo più interessante dell'AH è Security Parameters Index SPI, che contiene un valore numerico che insieme all'indirizzo IP di destinazione e il protocollo, identifica l'SA utilizzata;
- ESP: fornisce servizi di confidenzialità, autenticazione, integrità e protezione da attacchi di tipo replay. È possibile utilizzare solo alcuni servizi o tutti i servizi insieme. Per quanto riguarda la confidenzialità differisce dall'AH in quanto essa non copre l'header esterno. ESP aggiunge anche un campo Authentication che contiene i dati usati per autenticare il pacchetto;
- IKE: realizza un collegamento peer-to-peer in due fasi, in primis i due host creano una Security Association per IKE stesso, ovvero un canale sicuro per la condivisione dei messaggi. In secundis, utilizzano l'SA appena creata per negoziare Security Association per altri protocolli (IPsec SA);