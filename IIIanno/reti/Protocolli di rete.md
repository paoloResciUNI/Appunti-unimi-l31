# Protocolli di rete

La scelta del protocollo di rete viene valutata in base a dei principi fondamentali della comunicazione in rete.

## Affidabilità

Detto in parole semplici, per affidabilità ci riferiamo a una rete che funziona correttamente, ovvero che invia i dati esattamente come sono stati trasmessi. Per fare ciò si implementano dei meccanismi di ricerca e correzione degli errori, che è comune avvengano durante la comunicazione in rete. Per implementare questi metodi è però necessario aggiungere informazioni al messaggio, accettando di avere informazioni ridondanti all'interno del messaggio inviato. Addirittura inviando più volte lo stesso messaggio se non vi è stata la conferma di arrivo del pacchetto.

### Correzione degli errori

Spesso accade che nei messaggi inviati vi siano errori di trasmissione, a questo punto sta al mittente decidere cosa fare, se buttare il messaggio e richiederne uno nuovo o se correggerlo e verificarne l'accuratezza (con i mezzi a sua disposizione).

Lo **schema** di controllo appena descritto si chiama **richiesta autonome di ripetizione**  (ARQ, Automatic Repeat Request), dove il destinatario invia un messaggio al mittente per confermare la ricezione del messaggio o per richiederne un'altra copia.  Lo schema di controllo ARQ lavora al livello di collegamento e si cura di dare al protocollo di tale livello una comunicazione che con molta probabilità è affidabile, ovvero senza errori e senza blocchi duplicati.

#### Idle RQ

È il principale protocollo basato sullo schema ARQ, si porta dietro una serie di problemi che ne hanno richiesto varie implementazioni e migliorie.

RQ funziona in questo modo: definisce dei frame di informazione, detti **I-frame**, che il **primaro**, mittente, manda al **secondario**, destinatario. Questo schema lavora in modalità half-duplex, infatti il primario dopo aver inviato il messaggio aspetta l'acknwoledge del secondario, per poi inviare il nuovo messaggio, se il secondario non manda l'ack allora il primario assumerà che il pacchetto sia stato perso e procederà con il rinviarlo finché non riceve l'ack. Il secondario potrebbe inviare un messaggio di mancata ricezione, ovvero se il messaggio che è stato inviato è corrotto o presenta errori di ricezione.

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

In particolare il protocollo idle RQ è adatto per trasmissione brevi e con moderato tasso trasmissivo.

#### RQ continuo

In questo protocollo viene utilizzato meglio il collegamento a fronte di un utilizzo maggiore del buffer di memoria. Si utilizza una comunicazione duplex.

Il nome di questo protocollo deriva dal fatto che continua a mandare in continuazione i messaggi senza attendere l'ack. Dato che ci sono più I-frame che necessitano di conferma, il primario conserva una lista FIFO di **ritrasmissione**. il secondario manda gli ack man mano che arrivano i messaggi. Se si verificano degli errori durante la trasmissione si possono applicare le seguenti strategie.

#### Ritrasmissione Selettiva

Il frame ACK  costituisce l'invio di tutti i frame nella lista di ritrasmissione, fintanto che il numero di sequenza del frame sia contenuto nel ACK stesso.

Se P (primario) comunica con S (secondario) viene perso un frame durante la comunicazione, allora S manda un NAK a P che entra nello *stato di ritrasmissione*, ovvero non può inviare altri messaggi al di fuori del frame mancante, finché non arriva il frame ACK.

Il frame mancante viene mandato in continuazione allo scadere di un timeout che attende l'acknowledge.

#### Go-back-N

Il go-back-n ha un funzionamento analogo a quello visto precedentemente (grazie al cazzo serve per fare la stessa cosa). L'approccio cambia nel fatto che P, nello stato di ritrasmissione, si metta a ritrasmettere dalla prima frame mancante, ritrasmettendo tutti i frame seguenti fino a quando non riceve gli ACK che aspetta. S scarta tutti i frame che già possiede fino a quando non arriva il/i frame mancante/i, a quale punto esce dallo stato di ritrasmissione.

#### Allocazione delle risorse

#### Evolability

#### Sicurezza
