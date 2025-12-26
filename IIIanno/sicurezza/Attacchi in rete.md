# Attacchi in rete 

Sono attacchi che si basano su una profonda conoscenza dei protocolli di rete. La rete allarga la superfice di attacco, infatti si aggiungono: i canali, i dispositivi di rete, i protocolli di rete... .

Ci sono diversi ti pi di attacchi di rete:

-  **Passivi**: difficili da rilevare e prevenire. Ad esempio l'intercettazione del traffico di rete.
- **Attivi**: richiedono il coinvolgimento diretto di pacchetti e protocolli di attacco che influenzano il comportamento del sistema. Es il denial of service. 

## Spoofing

Tecnica di supporto negli attacchi di rete. È una tecnica di cammuffamento dell'idirizzo di un pacchetto.

Per esempio quello che vine modificato è il mittente di una certa comunicazione (*ip spoofing*). 

---

Ciò che si vule attaccare è il canale di comunicazione per intercettare il traffico. questo attacco si chiama, **sniffing**, **wiretopping**, **evasedropping**. 

### Packet sniffing

Per esempio su una lan, lo sniffing è facile. Essendo che i messaggi sono mandati in brodcast, si può fare in modo che il protocollo internet legga tutti i messaggi che viaggiano sulla rete. 

I programmi appositi per questo tipo di attività si chiamano packet-sniffet. 

### Radiation

Si possono intercettare i campi elettromagnetici dei cavi di rete. Si può fare sulle linee telefoniche, antenne wifi e, ovviamente, cavi di rame. 

Allora la fibra ottica qui diventa più sicura. Per intercettare la fibra bisogna per forza mettersi sui duplicatori di segnali. 

Altre tecniche per intercettare il traffico, sono: compromettere il server, il router o la tecnica di attacco del man in the middle.

Il packet sniffer può essere usato positivamente da un amministratore di sistema per capire il funzionamento della sua rete. Questo lo rende uno strumento ambivalente, e come molti di questi strumenti possono essere usati sia per difendere e amministrare che per attaccare. 

Un altro tool dopo wireshark per fare packet sniffing è `tcpdump`.

Il modo per rendere innocuo il packet sniffing è la cifratura del canale di comunicazione e dei pacchetti. Da sapere che tcp, udp e ip sono protocolli che nascono in chiaro, quindi tutto internet di default nasce con comunicazioni in chiaro. 

### TAP

Oggetto che duplica le porte del router per intercettare il traffico di rete. 

## DoS-DDoS

Il Denial of Service è un tipo di attacco molto semplice che non richiede particolari competenze. In sostanza si blocco l'uso legittimo di una risorsa degradandone le sue performance e le sue funzionalità. Questo fa sì che la risorsa diventi inutilizzabile.

Si può fare sfruttando vulnerabilità software o facendo fluding. Con fluding si intende fare richieste che richiedono un numero tale di risorse che ne consumano il sistema.  Per esempio 

```C
while true{
	fork();
}
```

Questo tipo di attacco può mandare in crash addirittura un firewall. 

### Motivi dell'attacco 

L'attacco DoS è un attacco istantaneo, ovvero non lascia tracce. Quindi i motivi possono essere:

- estorsione - In questo caso non si fa l'attacco ma si minaccia di farlo
- competizione commerciale
- attivismo

La forma più diffusa di denial of service è la distributed denial of service (DDoS) con fluding, tipicamente fatto con le botnet.  Vengono coordinati i bot per fare una quantità di richieste enormi al server. 

### Attacchi DoS Locali 

#### Ping of Death 

Sfrutta un errore di programmazione. Sfrutta il comando `ping` (tramite ICMP). Il pacchetto di `ping` può essere lungo 65236 byte.

In Windows c'era un bug dove non veniva fatto il controllo sulla quantità di byte che venivano ricevuti. Il buffer allocato era di 65236 byte e dopo c'erano dati di sistema. Se si mandava un pacchetto più lungo buttava giù la macchina

#### Smurf

Uno dei primi attacchi DoS, dove le botnet non esistevano ancora. Si inondava un pc di una quntità ingestibile di pacchetti. Si sfrutta la possibilità di IP di mandare messaggi in broadcast. 

#### Land Attack

È stupido. 

Si fa spoofing dove si manda un pacchetto alla vittima, dove il mittente è la vittima stessa. Così facendo la vittima entra in un loop di risposte. 

#### Syn Flooding 

Questo tipo di attacco sfrutta una criticità di treway and shake (syn, syn/ack, ack). 

Alcuni firewall utilizzano delle erustiche per riconoscere syn flooding. È un attacco molto diffuso e complicato da identificare. 

Il modo più diffuso per fare DDoS è utilizzando le botnet. L'attacco DDoS più grande ha generato traffico di 2,2 TB di dati. 

In questo momento sono più diffusi gli attacchi DDoS da 100Gb di traffico. 

Di solito è possibile identificare degli attacchi DoS buttando via dei pacchatti, a volte anche non dannosi. 

### Address Resolution attacks

Compromettere la fasae di lavoro svolta dal server dns. Questo può essere utile per implementare il Man In the Middle Attak (MITM). L'obbiettivo dell'attacente è quello di impersonare qualcun'altro. 

### Pharming Attack 

Si avvelena il mapping tra il nome simbolico e l'ip adress. Si anticipa la risposta del DNS e si manda un indirizzo ip malevolo. Questo si utilizza perchè DNS è assolutamente non protetto, ovvero le query vengono inviati in chiaro. 

#### Pharm Vector

Se si prende un malware sulla propria macchina, e sostitusice l'ip che c'è con un ip che vuole l'attaccante. 

### ARP Spoophing

ARP fa il mapping tra indirizzo Ip e MAC adress. ARP si costruisce una cache per gli indirizzi che ha costruito di recente. 

Se durante la request dell'ARP viene mandato un indirizzo fasullo, è possibile fare intercettazione del traffico.

Ogni PC ha una ARP cache, ARP è state less, quindi non si ricorda l'associazione MAC - IP. Di fatto questo protocollo si basa sulla fiducia che ogni host i fidi di tutti gli altri. 

Anche in questo caso CI potrebbe essere un **poisoning** (ARP poisoning). L'attacco consiste nel creare ARP reply finte in modo che ARP aggiorni la cache. Questo attacco è ancora utilizzato. 

Di solito il target di questo attacco è l'indirizzo del router. 

In questo modo siamo in un mezzo man in the middle. Ora bisogna fare poisoning anche dell'altro host.

A livello di rete locale il traffico non è cifrato. Può essere utilizzato per fare un attacco DoS.

Allora l'hacker può controllare i messaggi della conversazione, e inoltrarli ai legittimi destinatari per fare in modo che non si accorgano dell'attacco.

Questo tipo di attacco può essere fatto internamente (es. da dipendenti) o esternamente (es. da un hacker). 

L'unico modo per difendersi da questo attacco (che derive da un'*errore* di progettazione) è tramite le ARP statiche. Si fa un file di configurazione nel quale è locata la ARP cache. Solo root potrà cambiare quelle entry. 

### TCP hijacking

Storica tipologia di attacco, fatta per la prima volta nel natale del '95 da Kevin Mitnik. 

Si dirotta una connessione TCP già stabilita. Ovvero si "fa fuori" uno degli interlocutori. Viene fatto per la prima volta da Shino Mura, dato che Mitnic era ricercato dalla NSA, per il fatto che era molto conosciuto per social engeneering. Questo attacco sfrutta delle particolarità del protocollo di TCP. 

Nel treway and shacke, i due host si scambiano il SQN e il ACKN. Per effettuare questo attacco il SQN deve esser acquisito. Per farlo si può: o indovinare o attraverso lo sniffing. 

Prima è necessario conoscere `rsh`. Serve per eseguire comandi su di host remoto. Per poter fare remote shell si utilizzano due file di configurazione: `etc/host.equiv` e `.rhosts`. Se si mette ++ nel file .rhost tutti possono accedere a quell'host. 

Si utilizza il comando `finger` per prendere le informazioni sull'utente desiderato, poi si esegue il comando `showmount -e <IP di interesse>` dopo vengono mandati 20 SYN/ACK dopo aver preso il trusted host. 

Questo attacco è ormai impraticabile.

*the fugitive game*