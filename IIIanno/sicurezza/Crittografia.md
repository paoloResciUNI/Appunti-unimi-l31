# Crittografia

Non facile utilizzarla in un utilizzo di massa. 

Nata nell'epoca degli assiri e babilonesi. Nasce per comunicare sui campi di battaglia e per evitare che il nemico riuscisse ad anticipare le mosse prendendo i messaggi. 

La crittografia moderna ha una nascita simile. 

Ci si occupa di nascondere i messaggi facendo in modo che solo i destinatari possano leggere i messaggi indirizzati a loro. 

I cripto analisti si occupano di decifrare messaggi criptati. Si possono considerare come gli hacker della crittografia. 

Nell'ambito della cyber security la crittografia ci consente di avere 4 proprietà dei sistemi sicuri. 

## Modello di riferimento 

Il sender manda il plain text e lo encripta rendendolo ciphertext. L'attaccante cerca di prendere e decifrare il messaggio. 

Per passare da cipher a plain si utilizzano algoritmi parametrizzati. Si assume , in genere che l'intrusore sappia con quale algoritmo è stato ricavato il cipher text. Se non lo conosce allora si parala di security by obscurity.   

Si assume che la robustezza di un algoritmo non sia la sua diffusione ma i meccanismo che utilizza per criptare il testo. 

Funzione di encription (biettiva) che va dall'insieme di tutti i plain text ($P$) con tutte le chiavi ($K$) fino al messaggio cifrato ($C$)

$E:P \times K \to C$ 

$D: C\times K \to P$

$E$ funzione di ecription e $D$ funzione di decription. 

## Metodi di ricerca della chiave 

### Exhaustive search/Brute force

È un modo per cercare iterativamente la chiave giusta. Si cerca di capire quanto tempo un algoritmo riesca a capire quanto sia solido l'algoritmo utilizzato. 

Per chiavi lunghe la ricerca esaustiva non può funzionare. 

Ci sono altri metodo per verificare la robustezza di un algoritmo di criptazione (ciphertext only, known plain text, chosen-plaintext, choosen-ciphertext).

### Protocolli crittografici 

A chiave privata (simmetrica) o a chiave pubblica (asimmetrica).

La crittografia a chiave simmetrica mi consente di criptare e decriptare il messaggio con la stessa chiave. 

**stream  cipher**: criptano un solo bit alla volta. La funzione più usata è lo XOR. Si usa lo XOR poiché come funzione di criptazione che data la chiave restituisce il testo in chiaro. Il problema di questo metodo è che la chiave deve essere lunga come il testo cifrato. 

La crittografia simmetrica si basa su protocolli estremamente efficienti in termini di tempi e di implementazione in hardware. La lunghezza della chiave molto piccola. Il problema è la gestione di un numero molto grande di chiavi. E lo scambio di chiavi diventa complicato dato che se non mando la chiave in chiaro non posso comunicare (per esempio). 

> Diffie, W. and Hellman, M. *New Directions in Cryptography*. Vincitori del turing award.

**Block cipher**: prendono il testo e lo dividono in blocchi e lo criptano un pezzo alla volta. DES (Data Encription Standard) sviluppato da IBM, era lo standard per cifrare le comunicazione in ambiente bancario e finanziario. Divide il testo in otto caratteri. Con 3500 macchine in parallelo venne rotto nel 1997. Per rafforzare il DES se ne creano altri basati su DES ma più sicuri (come il triple DES, ovvero tre DES con tre chiavi diverse). 

Visto la criticità del DES si cerca un sostituto al DES. Alla fine Joan Deamen e Vincent Rijmen creano Rijndael. Viene poi usato come standard per le comunicazioni e la crittografia simmetrica. Questo algoritmo viene integrato in AES (Advance Encription Standard)

Elecronic Code Book: i blocchi vengono dati in pasto ad un algoritmo di crittografia.

Cipher Block Chaining: in questo caso la criptazione non può essere parallelizzata. CBC si dimostra estremamente più efficace di ECB.

La **public key criptography** funziona così, ognuno ha due chiavi: una pubblica e una segreta. Questa coppia di chiavi vengono generate insieme. La chiave pubblica cifra, quella privata decifra, per questo è asimmetrica. 

Un utente che vuole comunicare in modo riservato pubblica la sua chiave pubblica in modo che i messaggi che vengono mandati sono cifrati con la chiave pubblica e chi la legge deve per forza avere la chiave privata (quindi non deve essere rivelata).  

Il problema degli algoritmi di crittografia simmetrici ci si impiega 10000 volte il tempo che ci si impiega con un metodo simmetrico. Allora si usa una chiave asimmetrica per scambiarsi la chiave pubblica e si comunica in questo modo. 

## Digital Signature

Sicurezza dell'originalità dei dati, integrità dei dati, non reputiabilità.

## Computational security 

Si intende il fatto che per decifrare un algoritmo ci si impiega un tempo infinitamente lungo. 

## Funzioni Hash

Prendono in input una qualunque stringa binaria e restituiscono un output di dimensione fissata. 

Le funzioni di hash per essere implementate in ambito di sicurezza devono:

- essere a senso unico: $h (s) \to e \not \Leftrightarrow h(e) \to s$.
- impossibile trovare un input che mi stia data la funzione di hash lo stesso output
- impossibile trovare collisioni

Le funzioni di hash si utilizzano anche per verificare l'integrità del file system. 

Le funzioni hash più utilizzate:

- MD5 -> deprecata
- SHA-1 -> deprecata
- SHA-2
- SHA-3

### MAC (Message Authentication Code)

Come facciamo a garantire l'integrità di un messaggio in comunicazione? 

Non basta l'hash. Il MAC garantisce che i dati siano integri e originali. Serve anche per capire la veriditicità dell'utente con il quale sto comunicando. 

## Man in the middle 

Si basa a mandare una chiave pubblica a un interlocutore che parla con qualcunaltro e lo faccio parlare con me invece. 

Per evitare questo tipo di attacchi bisogna usare un certificato digitale, con vari approcci.

- Un documento digitale fornito da un organo statale o un autorità riconosciuta.
- La chiave pubblica non viene garantita da un'autorità pubblica o riconosciuta ma dalla rete. 

## Certificati 

- PKI e X.509

  Si basa sull'esistenza di una parte fidata a cui viene affidata l'identità dell'utente. 

  Es. SPID

- CA

