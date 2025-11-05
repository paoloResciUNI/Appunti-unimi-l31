# ARP

Il DNS mappa un nome logico in un indirizzo.

ARP riesce a risolvere l'indirizzo IP destinazione in un indirizzo MAC adress. 



> LAN -> CL1 *ARP*
>
> |
>
> v
>
> CL2 *ARP*
>
> ARP manda in LAN una ARP request in broadcast. Tutte le stazioni la ricevono. Tutte quelle al quale non corrisponda l'IP la buttano, quella invece interessata risponde con una ARP reply. 
>
> Il MAC adress ricevuto viene tenuto in cache per un certo periodo di tempo.  

Il GetWay fa anche da porxy ARP. Esso associa l'IP della macchina destinazione alla porta del getway. 

 Consideriamo che un terminale nella rete voglia palare con un terminale in un altra rete collegata con un bridge alla rete. Il bridge essendo di livello 2, fa semplicemente forwarding su tutte le porte di uscita che conosce. Da considerare che su tutti gli apparati di livello 2 **non** gira ARP. 

## ARP request

Viene incapsulato in una frame ethernet. 

   6     6    2       46-1500      4

|DA|SA|Type|ARP/RARP|FCS

Consideriamo tipo:

- hardware: il tipo di scheda
- protoc type: ci dice il tipo di protocollo di livello 3 (nel nostro caso il protoccollo IP)

# DHCP

Dynamic Host Configuration Protocl

 

