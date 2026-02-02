# Sistemi sicuri (pt.2)

Linux implementa di base un controllo degli accessi discrezionale. 

In ambiti più particolari, come quello militare, questo non va più bene. Allora si utilizzano i mandatory access control. Questo implementa delle politiche di controllo degli accessi. 

Ci sono vari livelli di security per i documenti (U.S. governament). Questa è la multilevel security. 

#### RBAC 

Un misto fra MAC e DAC. È una politica di controllo degli accessi basato sui ruoli. Ad ogni persona è associato un ruolo. In base al ruolo si decidono le azioni che possono essere fatte. Questo modo di fare viene implementato in ambito enterprice (o anche unimi). 

 #### Oauth

In un contesto distribuito (es. social media) la questione del controllo degli accessi alle risorse informative diventa complesso. In un sistema dinamico si può utilizzare il protocollo *Oauth*. Basato sull'idea del DAC. Viene chiesto all'utente quali azioni autorizzare e quali no. Questo scarica le responsabilità amministrative dall'azienda/organizzazione all'utente. È un protocollo di rete. 

L'access control list viene gestita direttamente dall'utente. 

## Sistema di protezione 

1. Prevention - (come l'autenticazione)
2. Detection 
3. Response 

### Detection & Response

Dopo che la prevention ha fallito, dato che prima o poi fallisce, vanno implementate queste due azioni. 

La prima fase è la detection per capire cosa e dove sta succedendo per indirizzare la response. Predisporre configuare e implementare un meccanismo che registri tutte le attività ce stanno venendo svolte all'interno del sistema è una buona pratica di detection. 

È il reference monitor a registrare tutte le azioni che vengono fatte nei file di log. Ogni tipo di informazione vine memorizzata sui file di log. Ci sono più  processi e applicazioni che generano più file di log. 

L'attività di *audit* verifica e convalida i file di logo all'interno del sistema (IT audit).

L'IT auditor si occupa di controllare tutto quello che succede all'interno del sistema. L'it securiry audit è l'audit della sicurezza del sistema.  

Vari sistemi utilizzano file di log anche servizi online e di rete. 

Un attacco di rete molto comune è continuare a mandare file al firewall che memorizza i file di log. Se si riempie l'hrd disk il firewall smette di funzionare. Un modo per evitare questo problema è sovrascrivere, ad un certo punto, i file di log precedenti. Questa è una perdita di informazioni importanti. 

Il formato dei file di log non è standardizzato. Quindi come si fa ad analizzando tutti i file di log? 

Esistono dei sistemi che fanno proprio questo, ovvero i log managmet system.

#### Detection

Due modi nel quale si può fare:

1. **In tempo reale**: Si analizza in tempo reale i file di log (intrusion detection system). 
2. **Post mortem**: Dopo che si è verificato il fattaccio. 

L'analisi può essere automatica o manuale. Quella manuale trova gli attacchi più articolati.

Security information Evet Managment. Contiene motori di machine lerning addestrato con file di log di attacchi avvenuti in passato. Raccoglie e analizza informazioni da tutto il mondo. Se ci sono pattern sospetti viene generato un allarme. 

Security Analist:

- Tier 1
- Tier 2
- Tier 3

L'entry poit è 1. Se 1 non capisce passa a 2 se anche lui non capisce allora lo passa al 3. SIEM esegue il tier 1. 

Dopo la detection c'è la response. 

#### Response 

[...]

---

Esiste un altro sistema la *retalietion*, tipo una vendetta. La SIEM rileva un attacco e contrattacca. 

## Software e Security 

Gli attaccanti sfruttano degli exploit di programmi e software per superare tutti i meccanismi di sicurezza visti fino ad ora. 

Il livello di conoscienza per eseguire questi tipi di attacco bisogna essere degli hecker (delle persone altamente informate). Di fatti le persone che riescono a costruire un exploit sono veramente poche, dato che il tipo di conoscenza necessaria è veramente alto. 

Il sistema di attacco del buffer overflow è stato usato e riusato varie volte. 

### TOCTOU (Time Of Checking Time Of Use)

Attacco che funziona su sistemi unix.

Il controllo degli accessi richiede la complite mediation con il reference monitor.

L'attacco si basa sui tempi di richiesta delle varie operazioni. Il consenso viene dato ad un tempo maggiore  del tempo di richiesta. 

Nel mentre che uso il tocken di superuser per fare delle azioni. 

Si utilizza la Race condition.

Viene invocata la syscall access(). Questa verifica che il real user id del processo che l'ha invocata può accedere al file. Questa syscall restituisce 0 se l'utente può accedere. La syscall open() verifica che l'effective user id ha il permesso di accedere al file.   

