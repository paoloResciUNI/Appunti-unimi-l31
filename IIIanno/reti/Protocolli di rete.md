# Protocolli di rete

La scelta del protocollo di rete viene valutata in base a dei principi fondamentali della comunicazione in rete. 

## Affidabilità 

Detto in parole semplici, per affidabilità ci riferiamo a una rete che funziona correttamente, ovvero che invia i dati esattamente come sono stati trasmessi. Per fare ciò si implementano dei meccanismi di ricerca e correzione degli errori, che è comune avvengano durante la comunicazione in rete. Per implementare questi metodi è però necessario aggiungere informazioni al messaggio, accettando di avere informazioni ridondanti all'interno del messaggio inviato. Addirittura inviando più volte lo stesso messaggio se non vi è stata la conferma di arrivo del pacchetto. 

### Correzione degli errori 

Spesso accade che nei messaggi inviati vi siano errori di trasmissione, a questo punto sta al mittente decidere cosa fare, se buttare il messaggio e richiederne uno nuovo o se correggerlo e verificarne l'accuratezza (con i mezzi a sua disposizione). 

Lo schema di controllo appena descritto si chiama **richiesta autonome di ripetizione**  (ARQ, Automatic Repeat Request), dove il destinatario invia un messaggio al mittente per confermare la ricezione del messaggio o per richiederne un'altra copia.  Lo schema di controllo ARQ lavora al livello di collegamento e si cura di dare al protocollo di tale livello una comunicazione che con molta probabilità è affidabile, ovvero senza errori e senza blocchi duplicati.

#### Idle RQ

È il principale schema ARQ, si porta dietro una serie di problemi che ne hanno richiesto varie implementazioni e migliorie. 

#### RQ continuo  

#### Allocazione delle risorse

#### Evolability 

#### Sicurezza 

