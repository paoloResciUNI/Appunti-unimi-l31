# Protocolli di rete

La scelta del protocollo di rete viene valutata in base a principi fondamentali della comunicazione in rete.

La comunicazione passa per vari livelli e ognuno di loro ha bisogno di un determinato protocollo per effettuare la comunicazione.

> ## Affidabilità

> Detto in parole semplici, per affidabilità ci riferiamo a una rete che funziona correttamente, ovvero che invia i dati esattamente come sono stati trasmessi. Per fare ciò si implementano dei meccanismi di ricerca e correzione degli errori, che è comune avvengano durante la comunicazione in rete. Per implementare questi metodi è però necessario aggiungere informazioni al messaggio, accettando di avere informazioni ridondanti all'interno del messaggio inviato. Addirittura inviando più volte lo stesso messaggio se non vi è stata la conferma di arrivo del pacchetto.

> ### Correzione degli errori

Spesso accade che nei messaggi inviati vi siano errori di trasmissione. A questo punto, spetta al mittente decidere cosa fare: buttare il messaggio e richiederne uno nuovo oppure correggerlo e verificarne l'accuratezza (con i mezzi a sua disposizione).

> Lo **schema** di controllo appena descritto si chiama **richiesta autonome di ripetizione**  (ARQ, Automatic Repeat Request), dove il destinatario invia un messaggio al mittente per confermare la ricezione del messaggio o per richiederne un'altra copia.  Lo schema di controllo ARQ lavora al livello di collegamento e si cura di dare al protocollo di tale livello una comunicazione che con molta probabilità è affidabile, ovvero senza errori e senza blocchi duplicati.

## Livello Data Link

### Idle RQ

È il principale protocollo basato sullo schema ARQ, si porta dietro una serie di problemi che ne hanno richiesto varie implementazioni e migliorie.

RQ funziona in questo modo: definisce dei frame di informazione, detti **I-frame**, che il **primario**, mittente, manda al **secondario**, destinatario. Questo schema lavora in modalità half-duplex. Infatti, il primario, dopo aver inviato il messaggio, aspetta l'acknowledge del secondario per poi inviare il nuovo messaggio. Se il secondario non manda l'ack, allora il primario assumerà che il pacchetto sia stato perso e procederà con il rinviarlo finché non riceve l'ack. Il secondario potrebbe inviare un messaggio di mancata ricezione, ovvero se il messaggio inviato è corrotto o presenta errori di ricezione.

Se il primario non riceve il messaggio di ack o nak nel tempo previsto, rinvia l'ultimo messaggio che è stato mandato.

Ogni pacchetto ha un identificatore in modo che, se vengono inviati duplicati, essi vengano scartati. Questo tipo di schema si chiama **stop-and-wait**. Dato che vengono mandati un solo bit alla volta, di solito si utilizza un bit che oscilla tra 0 e 1, per questo motivo questo protocollo viene anche chiamato protocollo del **bit alternato**.

#### Utilizzo della banda/collegamento
$$
U = \frac{T_{ix}}{T_t}
$$
Dove $T_{ix}$ è il tempo che il mittente impiega per inviare una frame e $T_t$ è uguale al tempo $T_{ix}$ sommato al tempo nel quale il trasmittente si mette in attesa di ricevere il messaggio. Può anche essere approssimata come segue:
$$
U = {T_{ix}\over T_{ix}+2T_p} \text{ oppure } {1 \over 1+2a}: a = {T_p\over T_ix}
$$
Dove $T_p$ è il tempo del ritardo di propagazione nel canale di trasmissione.
In particolare, il protocollo Idle RQ è adatto per trasmissioni brevi e con un moderato tasso trasmissivo.
### RQ continuo
In questo protocollo viene utilizzato meglio il collegamento a fronte di un utilizzo maggiore del buffer di memoria. Si utilizza una comunicazione duplex.
Il nome di questo protocollo deriva dal fatto che continua a mandare in continuazione i messaggi senza attendere l'ack. Dato che ci sono più I-frame che necessitano di conferma, il primario conserva una lista FIFO di **ritrasmissione**. il secondario manda gli ack man mano che arrivano i messaggi. Se si verificano degli errori durante la trasmissione si possono applicare le seguenti strategie.
#### Ritrasmissione Selettiva
Il frame ACK  costituisce l'invio di tutti i frame nella lista di ritrasmissione, fintanto che il numero di sequenza del frame sia contenuto nel ACK stesso.
Se P (primario) comunica con S (secondario) viene perso un frame durante la comunicazione, allora S manda un NAK a P che entra nello *stato di ritrasmissione*, ovvero non può inviare altri messaggi al di fuori del frame mancante, finché non arriva il frame ACK.
Il frame mancante viene mandato in continuazione allo scadere di un timeout che attende l'acknowledge.
#### Go-back-N
Il Go-Back-N ha un funzionamento analogo a quello visto precedentemente. L'approccio cambia nel fatto che P, nello stato di ritrasmissione, si metta a ritrasmettere dalla prima frame mancante, ritrasmettendo tutti i frame seguenti fino a quando non riceve gli ACK che aspetta. S scarta tutti i frame che già possiede fino a quando non arriva il/i frame mancante/i, a quel punto esce dallo stato di ritrasmissione.

---
Un'altra questione importante nei protocolli Data link è il **controllo degli errori** e il **Controllo del flusso**, qust'ultimo in particolare permette al ricevente di prendere avere abbastanza memoria per i prossimi messaggi in arrivo.
### Finestra a scorrimento/*sliding window*
Questo meccanismo è necessario per il controllo di flusso dei frame. L'approccio ricorda molto quello di Idle RQ: si pone un limite al numero di richieste/frame che possono essere inviate fino a che non arriva una conferma.
Si prepara una lista di frame, già inviati, grande $K$. Quella lista sarà la lista di ritrasmissione del primario. Se il secondario non manda ACK per confermare che gli sono arrivati i frame nella lista, allora P smette di inviare frame. La grandezza $K$, che rappresenta il numero di frame che possono essere ritrasmessi, si chiamerà **finestra di invio**. Se la finestra vale 1 ($K=1$), allora ci troviamo in uno schema Idle RQ, rischiando di perdere efficienza nella trasmissione. Per questo motivo, sono molto numerosi i criteri con cui scegliere $K$.
##### Funzionamento
Per ogni frame inviata aumenta di 1 il bordo superiore della finestra di invio (UWE, *upper window edge*), analogamente quando viene ricevuta la conferma di ricezione per una frame si riduce di 1 il limite inferiore della finestra di invio (LWE, *lower window edge*).
Quando la differenza fra UWE e LWE raggiunge il valore di $K$, allora P entra nello stato di ritrasmissione.

> #### Gli identificatori
> Per poter identificare correttamente le frame inviate in una determinata finestra di grandezza $K$ si procede, in base alla stradegia utilizzata, come segue:
> - **Go-back-N**: si utilizzano almeno $K+1$ identificatori. Per spiegarlo immaginiamo che il secondario mandi solo ACK danneggiate, in questo modo può "capire" meglio se arrivano frame duplicati o nuovi.
> - **ripetizione selettiva**: in questo caso si devono usare non meno di $2K$ identificatori. Come prima supponiamo che il secondario mandi solo frame danneggiate, lìunico modo che ha per capirlo è ricevere nuovi frame con nuovi identificatori (la nuova finestra).
