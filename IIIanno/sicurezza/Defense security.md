# Defense security 

Costituita da strumenti e tecnologie per implementare detection e aiutare questa attività. Ci sono strumenti per facilitare la prevention. 

L'anello della catena più debole in un sistema informatico è il fattore umano. Uno degli strumenti migliori può essere l'istruzione del personale e strumenti che facilitano l'istruzione degli **standard di sicurezza**. 

Ciò che si cerca di fare con la defense security è difendersi dagli script kiddie, ovvero coloro che fanno attacchi solo per divertimento e per denaro. <u>Non</u> difende da intelligence militari o da gruppi di hacker organizzati. 

## Defence strategy

Ogni qualvolta che si utilizzano sistemi informatici è necessario essere consapevoli di dover utilizzare strategie di difesa. 

I momenti che definiscono una strategia di cyber security sono:

- **Identify**
- **Protect**
- **Detect**
- **Respond**
- **Recover**

Prima di tutto bisonga identificare gli asset da difendere su un sistema informatico. Dopo cercare di trovare il meccanismo migliore per proteggere quella determinata risorsa/asset. Dobbiamo essere pronti a identificare eventiali tentativi di intrusione. Dopo aver identificato l'attacco bisogna rispondere in maniera adeguata. Il piano di risposta e la strategia di risposta va definita in precedenza. Dopo aver risposto all'attacco bisogna risistemare il sistema dopo l'attacco. 

Chi difende deve essere competente in ambiti differenti rispetto a chi attacca. 

Un metodo per avere confidenzialità e integrità sono:

- crittografia 
- protocolli di crittografia
- antivirus
- ...

### Firewall

È un oggetto che lavora a livello di rete. Lavora filtrando i pacchetti di rete. Attraverso alla configurazione del firewall si identificano pacchetti da fonti sospetti che vengono droppati da esso. 

Nel corso degli anni si è complicato sempre di più. Di base è un getway, tutto il traffico in entrata nella rete passa dal firewall. È un meccanismo di difesa **perimetrale**. 

> Traffico che entra = inbound
>
> Traffico che esce = outbound

A volte può essere necessario non far uscire alcuni pacchetti malevoli che vogliono attaccare altre reti.

I firewall possono essere hardware o software o entrambi (spesso lo sono). Vengono definiti **screening router**. 

#### Hybrid

Sono pacchetti software che sostanzialmente fungono da firewall. Sono firewall abbastanza diffusi. In sostanza i firewall, per evitare problemi di compromissione del sistema operativo, fanno hardening ovvero rimuovono parti del sistema operativo che non servono al firewall. 

Inannzitutto si sipezione il traffico che arriva e decide chi può passare e chi no. Inoltre logga (tiene traccia di tutto il traffico che passa per il firewall) e notifica (avverte dell'arrivo di certi pacchetti).

#### Types of firewall

1. Packet filter: Effettua le sue decisioni in base ai singoli pacchetti.

   1. Questo firewall ha un database di regole. Queste regole consentono di fare tre azioni distinte: allow, block, reject.
   2. Questo tipo di firewall viene definito *stateless*.  

2. statefull inspection: questi tipi di firewall possono riconoscere i pacchetti che fanno parte della singola applicazione.

   1. SI tiene aperta una tabella delle connessioni, per identificare le connessioni. Se la conessione è già stabilita viene fatto passate. 

3. Proxy firewall: in questi firewall si aprono due connessioni tcp diverese, il firewall fa man in the middle fra la rete e internet.

   1. **Circuit level proxy**: sdoppia la comunicazione. Questi tipi di firewall di recente sono tornati in voga dato che permettono di controllare i pacchetti, facendo in modo che il traffico interno all'azienda o alla rete sia in chiaro.

      1. Questo ci protegge da: TCP syn flood, Ip spoofing, TCP session hijecking, port scanning, blind injection, ACK flooding e i fragment packet attacks.  

   2. **Apllication level filter**: questo è efficace sopratutto sugli application firewall (firewall che hanno accesso al payload dei pacchetti). Lavorano a livello 7. 

      > WAF: Web Aplication Firewall -> hanno scopo di capire gli attacchi di cross site scripting. 

      L'uso di questi tipi di firewall richiedono che le applicazioni siano proxy over getway. Di solito si usano delle soket particolari (SOCKS, le socket sicure).  

4. personal firewall:

   1. Sono dei firewall implementati all'interno dei sistemi operativi. C'è un software che funge da firewall. Controllando traffico in ingrasso, in uscite e applicando regole di filtraggio. 



I vantaggi di utilizzare un proxy firewall rispetto ad un packet filter sono: 

- La facilità nel logging

Gli svantaggi sono:

- complessità di configurazione
- rallentamento della connessione

Per i proxy firewall, **deve** essere abilità la regola DEFAULT DENY. 

##### NGFW (Next Generation FireWall)

Mette in sieme diverse tipologie di strumenti che inizialmente erano *sparse*. Aggiunge la capacità di intrusione detection e prevention. 

A differenza dei firewall precedenti il NGFW è un tipo di controllo più profondo. 

Pilastri:

- Application Awareness
- Native Integration
- User Identify

Questi tipi di firewall sono molto pesanti e quindi per grandi retti sono ancora usati i firewall classici. 

>  perimetro: L'insieme dei server da proteggere
>
> Di solito un'azienda il numero di firewall dipende dagli amministratori della rete. 
>
> In molte aziende ci sono delle zone isolate, queste zone contengono informazioni sensibili, come informazioni sui dirigenti e i brevetti. 

#### DMZ

Consideriamo un'azienda che si deve connettere a internet. Questo comporta molti rischi di sicurezza. Una parte del mio server web che deve esser pubblica. Questa sarà la rete demilitarizzata (DMZ), le macchine in questa zona sono isolate dalla rete intranet dell'azienda. 

Per implementarla si utilizzano degli stratagemmi. Dato che le macchine in quella rete hanno delle altissime probablità di essere attaccati ci metto dei *bastioni*, ovvero macchine hardenizzata. Ovvero una macchina con delle verioni di software di sistema modificate in modo da renderle più complicate da attaccare. Questo significa diminuisco la superfice di attacco ovvero prendo un sistema molto minimale. 

Bisogna limitare al massimo l'interazione fra la intranet e la DMZ.  