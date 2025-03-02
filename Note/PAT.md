---
connections:
  - "[[NAT]]"
---
 Per il NAT vale il rapporto 1:1 tra IP del server di destinazione e IP del client. Il router NAT non è in grado di distinguere a quale dei due client locali sono destinati i pacchetti in arrivo dello stesso server remoto, ed è qui che entra in gioco la tecnica PAT.
 Il PAT è una tecnica che consente al router di utilizzare un singolo IP per gestire oltre 64.000 connessioni private contemporaneamente, ciò significa che può traslare più IP client per un medesimo IP destinazione cambiando solo la porta. Per il PAT vale il rapporto 1:1 tra IP del server di destinazione e IP del client.