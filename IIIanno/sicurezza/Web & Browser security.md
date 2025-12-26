# Web & Browser security 

Funzionamento: 

Utente "onesto" e un attaccente. L'attaccante (uno specifico livello) sfrutta:

1. vulnerabilità o bug del sistema
2. attacchi network utilizzando la conoscenza dei protocolli di rete

## Web Security

La rete è indipendente dai sistemi operativi. Gli attacchi di fatti sono sempre gli stessi, non importa il SO da attaccare. 

Tipicamente si attacca il server web o il borwser. Questi tipi di attacchi sono i più semplici da fare e infatti sono più diffusi, ma fanno meno male degli attacchi a livello di sistema operativo. 

### DNS

Traduce indirizzi logici in indirizzi ip. 

In DNS ci sono i top level domain (.com, .it ...) e i low level domain (www.unimi.it). 

Questa è la **gerarchia DNS**. Quindi tutto si basa sul root, finchè funziona va tutto bene. Esistono 13 root server, poi ci sono diversi global top level domain. Ci sono 1750 repliche di questi 13 top server. Durante gli aggiornamenti priva si aggiornano gli originali e poi le  repliche. La comunicazione funziona per livelli. Il client chiede l'indirizzo di un particolare web server. La richiesta viene fatta a un server DNS che se non conoscono l'indirizzo chiede a livello superiore fino ad arrivare alla root. 

In alcuni attacchi è possibile modificare l'inidrizzo del DNS server nel browser. Questi attacchi si chiamano DNS poisoning. 

#### Nomenclature varie

**URI**: <u>Unic Resource Identifier</u>. Composto da URL e da URN 

**URL**: Composto dal protocollo, sottodominio, dominio e top level domain, la porta la root e poi i parametri della query. 

Hypertxt: testo di testi, ovvero testo che si collega ad un altro. 

web form: particolarmente importanti per ottenere dati in input da parte dell'utente. I dati vengono mandati con GET o POST.

### Script web

Tutto quello che viene messo nel tag `script` inizia l'esecuzione del codice. Il codice può essere anche remoto. Gli script vengono eseguiti a seconda ci certi eventi che triggerano l'esecuzione del codice.  

##### HTTP

Protocollo che sta su TCP/IP, quindi connection oriented. Dopo la connessione ci sono due messaggi che possono essere mandati: GET, senza payload e, POST, con payload. 

#### Proxy

La connessione ad un web server può essere proxata. Si mette un server intermedio che risponde al posto del server a cui è stata fatta una richiesta. Questo permette al browser di fare meno strada rispetta a cercare il server di origine. La connessione HTTPS non è possibile fare questo dato che la chiave pubblica e privata è condivisa solo fra client e server. In alcune aziende le richieste devono essere controllate allora vengono fatte in chiaro per un certo tratto e poi cifrate dal proxy. 

Il browser può essere rediretto, automaticamente o in base ad eventi. 

#### Il browser

Interpreta le pagine HTML all'interno del frame. In `js` la frame è una window object.

**DOM**(Document Object Method)

**COOKIE**: Essendo http stateless, serve un modo per mantenere i dati e le variabili di sessione, in modo da riconoscere le sessioni di lavoro e mantenere le variabili per più connessioni. I cookie sono memorizzati in un file apposito. ogni server che viene visitato rilascia dei cookie. I coockie hanno degli attributi che li distinguono, come il dominio. L'attributo `HttpOnly` dice che il cookie con quel parametro può essere usato solo tramite connessione http. 

Per evitare il furto dei cookie attraverso `js`. I cookie non possono essere letti, dato che sono cifrati. Di solito anche a livello server vengono utilizzati dei mezzi di crittografia per proteggere i cookie degli utenti.   

In alcuni casi svolgono addirittura una funzione di autenticazione. Ciò fa in modo che il server sappia chi siamo in base al cookie.

Same Origin Policy (SOP): è un meccanismo di isolamento. Ogni pagina viene eseguita nella sua sandbox, e non può sbirciare o accedere ad altre pagine aperte nel browser. Solo le pagine che hanno la stessa origine possono condividere dati. L'origine è data da: protocollo, nome host, e (eventualmente) porta. Questo comporta che si potrebbe annullare l'effetto del web. 

I cookie sono stati considerati dati personali. Di fatto grazie i cookie si può profilare l'attività dell'utente sul web. La SOP sui cookie non controlla la porta nell'origine dei cookie. 

## Web Attacks

### Cross Site Request Forgery

Attacco che si basa sulla fiducia che il server ha nei cookie di autenticazione. In questi attacchi la vittima clicca su di un link che fa scaricare una pagina dell'attaccante. Essa contiene un reindirizzamento del browser che fa eseguire delle operazioni alla vittima da parte dell'attaccante. 

Per evitare questo attacco è stato aggiunto ai cookie l'attributo SameSite. Questo evita che i cookie siano mandati da richieste che arrivano cross site. Questo parametro ha tre livelli: strict, lax, none. In questo modo l'attacco non funziona. 

È stato uno degli attacchi più usati negli anni 2010-2012.

### XSS (Cross-Site Scripting)

Nato da un errore di programmazione. Consente ad un attaccante di far eseguire ad un sito del codice `js` maligno. Questo codice rube i cookie di sessione. 

Ci sono tre tipologie per questo attacco:

- Persistente: Tipico dei siti dove vengono postati pareri note (forum). Viene scritto un codice malevolo all'interno del sito (che viene violato), la vittima va sul sito e gli vengono rubate tutte le informazioni della pagina. Come errore di programmazione in questo caso c'è evitare la sanitizzazione dell'input. Un altro modo per ovviare questo attacco è utilizzare http cookie.   
- Riflessa: in questo caso ci sono tre attori, web server, vittima e attaccante. In questo caso viene attaccato il web server. L'attaccante deve disporre di un web server per rubare le informazioni alla vittima. L'attaccante deve trovare un server con un sito che fa reflection. L'attaccante tenta di forzare l'utente a cliccare sul suo link per rubargli i cookie di sessione. 
- DOM-based

Per prevenire un XSS è molto banale, si può fare:

- Via proxy
- Via firewall a livello applicazione: La più usata.
- con auditing

Queste soluzioni sono efficaci solo con HTTP, se si usa HTTPS allora diventa tutto più complicato perché il traffico è cifrato.

### SQL injection

Anche questa basata su errori di programmazione. In questo caso si mettono delle query da un form html. 

Consente di leggere in maniera non autorizzata le informazioni presenti sul DB. 

Il problema in questo caso risiede nell'input che non viene controllato a livello applicazione. Per prevenirla bisogna fare sanitizzazione dell'input in SQL. Per evitare questo tipo di attacco si utilizza il (WAF)