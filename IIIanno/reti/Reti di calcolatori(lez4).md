# Reti di calcolatori 

Livelli definiti da uno standard. Lo standard specifica, per ogni livello della gerarchia: 

[...]

Ad ogni livello ci può essere più di un protocollo. Al livello 4 ho un protocollo per le comunicazione affidabile e un altro per la comunicazione non affidabile. Analogamente, a livello fisico, al livello 2. 

Il messaggio deve passare tutti i livelli per poter essere trasmesso. Ogni livello aggiunge un header al messaggio. 

> [!TIP]
>
> Il livello 1 e 2 lavorano esclusivamente al livello hardware. 

## Il livello Data Link 

Due topologie di rete:

- Punto Punto (P2P) - Comunicazione unidirezionale
- Broadcast - Tutti i nodi sono collegati ad un centro stella e lo propaga su tutto ciò che conosce in uscita. Tecnologia che funziona anche sui satelliti e sugli hub. 

### Peer to Peer

Utilizziamo un data link per collegare una sorgente $A$ a una destinazione $B$. 

Consideriamo un'unità dati $F$ che vogliamo che viaggi in maniera *affidabile* sul link che collega $A$ a $B$. Aggiungo a $F$ un header e una coda. A livello 2 l'unità dati è definta *frame*. Le due sezioni inserite all'inizio e alla fine del frame sono chiamate "flag di inizio" e "flag di fine" (una sequenza di bit predefinita, sia per frame di inizio che di fine). Il flag è come una bolla che ingloba il messaggio e poi viene buttata.  

Perchè? Per poter dire al ricevitore che la frame sta iniziando e che sta finendo. Insomma consentono al ricevitore a preparasi al messaggio. 

Il trasmettitore fa in modo che all'interno della sequenza di 1 e 0 simili a quelle della flag venga inserito uno 0 in mezzo a un'insieme di uni (*bit stuffing*). Il ricevitore deve essere pronto a rimuovere lo zero del bit stuffing. 

##### Ora la frame viene mandata dal livello 3 al livello 2 e viene passata. Viene mandato da $B$ l'hacknowladge per indicare che il messaggio è arrivato. Il Round Trip Time/Delay (RTT/RTD) è il tempo nel quale arriva l'hack da parte del ricevitore, nel nostro caso $B$.  Come fa il destinatario a sapere che la frame che gli arriva è la frame giusta o è di nuovo la frame precedente (magari per un fallimento di ricezione dell'hack)? Con un numero di sequenza per ogni frame trasmessa, allora se viene ricevuto un duplicato allora il ricevitore la valida e manda nuovamente l'hack. 

##### Il numero di sequenza della frame trasmessa viene indicato con $V(S)$ per il *sender* e $V(R)$ per il *reciver*. Il trasmettitore incrementa la variabile di trasmissione, che parte da 0, e il ricevitore incrementa la variabile di ricezione, anche questa parte da 0. In questo modo il messaggio viene trasmesso in modo ordinato e senza perdite. 

$$
RTT = t_X+2\cdot t_P \to \text{Influenzato dalla lunghezza del cavo}
$$

L'efficienza della rete è molto influenzata dal $RTT$. Per misurare l'efficienza devo calcolare $t_X\over RTT$ dove $t_X$ è il tempo di trasmissione. 

##### Per ovviare il problema della poca efficienza della rete per via della lunghezza del cavo di trasmissione si mandano semplicemente più frame nell'arco di tempo di attesa del RTT. 

##### Questo protocollo si chiama *Coontinuos RT* o *protocollo a finestra*.

##### Goddeam 

#####  







#####  