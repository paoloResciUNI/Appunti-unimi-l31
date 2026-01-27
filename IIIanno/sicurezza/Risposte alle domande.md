# Risposte

> [!TIp]
>
> Questo file contiene delle domande e delle risposte per la parte orale di Sicurezza e Privatezza

# Domande orale Bruschi

[ToC]

## Giovedì 2 febbraio 2023

### Primo
- Definizione di _sistema sicuro_ "canonica"
    - _un sistema è _sicuro_ quando..._
    - non vuole sentire le regole auree
    - confidenzialità, integrità, disponibilità: cap. 1 del libro di testo
- Cosa sono le capability lists? [nell'ambito dell'access control]

__Bocciato__ (10 min): non ha risposto a nessuna domanda.

>### Riposte 1
>
>- Sicuro è un termine ambiguo che può portare ad ambiguità. Ciò nonostante un sistema si definisce sicuro se raggiunge 6 principi fondamentali:
>
>  1. Integrità: gli assets all’interno del sistema non subiscono alterazioni, se non dalle parti autorizzate.
>  2. Disponibilità: gli asset sono sempre disponibili alle parti autorizzate.
>  3. Confidenzialità: gli asset sono disponibili solo a coloro che ne hanno l’autorizzazione e da nessun altro.
>  4. Autenticazione: chiunque voglia eseguire delle operazioni sugli asset di deve prima autenticare per verificare la sua identità.
>  5. Autorizzazione: tutte le operazioni sugli asset vanno prima di tutto autorizzare.
>  6. Audithing/Non repudiabilità: tutte le operazioni fatte nel sistema sono tracciate e memorizzate. 
>
>  > [!Note]
>  >
>  > Le ultime tre sono le così dette **regole auree**.
>
>- Le capability-lists sono un sistema che implementa il modello del reference monitor, ovvero un modello soggetto-oggetto che si occupa di garantire che le risorse e gli assets del sistema siano accessibili solo a chi ne ha effettivamente il permesso. Nello specifico le capability lists sono una lista delle azioni che un soggetto può compiere all’interno del sistema. 
>
>  > [!TIp]
>  >
>  > Le CL derivano dalla ACM (Access Control Matrix) un modello troppo *costoso da implementare effettivamente*, di fatti sulle righe ci sono i soggetti e sulle colonne gli oggetti. La CL si ottiene fissando una determinata riga $i$ della matrice.
>
>  Non vengono effettivamente utilizzate nell’ambito dei sistemai operativi (come *Unix* almeno) se non in soluzioni ibride in contesti molto specifici, insieme alle ACL (largamente utilizzate in *Unix*). 

### Secondo

- Cosa sono le capability lists? 
    - Follow up: una capability a cosa serve?
    - Follow up: fammi un esempio
- Come implementa il controllo degli accessi UNIX?
    - (ACL)
- Come si chiama il device che rappresenta la memoria in UNIX?
    - `/dev/mem`
- Supponendo di avere due filesystem uno implementato con ACL e uno con CL, quale operazione viene meglio con cosa?
- Quali tecniche utilizza un malware per uscire dalle sandbox?
    - Come _"fregano"_ l'analisi dinamica?
    - Che tipo di protezione riescono a "scavalcare" con il metamorfismo?

Domanda tutor:
- Che cosa è un worm? 

__Promosso__ (25 + 4 = 29)

> ### Risposte 2
>
> 

### Terzo 

- Cosa è l'ARP poisoning? 
- Che limite ha l'ARP poisoning? 
- Cos'è un IDS?
- ...

__Promosso__ (25)

### Quarto

- Quali sono le componenti fondamentali di un sistema di protezione informatico? 
- Sicurezza del Wi-Fi
    - Quale è il problema di sicurezza delle reti Wi-Fi? ...la principale debolezza
    - Quale è l'attacco più facile da fare alle reti Wi-Fi?
- ...

__Promosso__ (28)

### Quinto 

- Come si risolve il problema dello scambio chiavi?
    - Se bisogna comunicare con una persona senza avere la sua chiave pubblica, come si fa lo scambio chiavi?
- Come funziona la crittografia asimmetrica?
    - Quale è il problema della crittografia assimmetrica?
- Cosa è SYN-flood?
- Come si prevede un DOS?

Domanda tutor:
- Cosa sono i cookie e cosa c'entra con la sicurezza?

__Promosso__ (24)

### Sesto 
- Firma digitale
- Descrivimi l'HMAC
- Controlled Invocation (setuid o syscall?)
- Esempio di syscall?
- Come funziona il setuid?

Domanda tutor:
- Come sono gestite le password su Linux e che permessi bisogna avere per accedervi?
- Perché dovrei fare un bruteforce a /etc/shadow per scoprire la password quando in realtà potrei cambiarla?

__Promosso__ (30 e lode)

### Settimo
- Tre regole auree
- Cos'è l'autenticazione?
    - A cosa serve l'autenticazione?
    - Tecniche di autenticazione
        - Lei ce l'ha Instagram? (l'interrogata è una ragazza)
- Cosa è l'end to end encryption? 
    - Quali altri modi ci sono per comunicare in modo cifrato che non siano E2E? 
    - Perché TLS non è E2E?
        - Chi usa TLS?
    - _Lei ce l'ha WhatsApp?_ è E2E?

Domande tutor:
- Come funziona il protocollo Tor?
    - In che senso _"ogni nodo fa un pezzo di cifratura"_? Come funziona?
    - Ogni chiave è scambiata tra chi e chi? 

__Promossa__ (25)

### Ottavo 
- Differenza tra TLS e IPSec
    - Possono andare insieme?
    - Dal punto di vista dell'efficienza, ci sono indicazioni con l'uso di TLS e IPSec?
    - Quale è la "granularità" di TLS e IPSec? 
      Nel senso, che tipo di traffico cifra (livello ISO/OSI)?
- Che cosa si intende per rootkit?

Domande tutor:
- Differenza tra le varianti di XSS (stored e reflective), con particolare attenzione alla capabilities di ognuna
    - Quale dei due è più facile da rivelare?

__Promosso__ (23+3)

### Nono 
- Esempio di MAC visto a lezione (ring architecture?)
- Cosa è un honeypot? (lezione 1 dicembre 2022)

__Bocciato/Ritirato__

## Venerdì 3 febbraio 2023

### Primo 

- TCP hijacking
- Modello protezione MAC: come è implementato a livello hardware? (Ring architecture)
    - CPL <= o >= di DLP?
    - Chi determina le specifiche di sicurezza?

Domande tutor:
- Web of trust: come funziona? Differenze con CA?

__Promosso__ (30 e lode) 

### Secondo 

- TLS: cos'é?
    - Esiste una specifica di TLS in cui né il client né il server si autentica? (Sì, il client non chiede il certificato al server)
    - Come funziona l'handshake/key exchange?
    - Quale è la dimensione della cyphersuite, in bit? (?????)
    - Quali presupposti devono valere purché il meccanismo di key exchange funzioni? Quale è un attacco plausibile?
- È più facile scrivere un virus o un worm? Quale delle due è più efficace? 

Domande tutor:
- Cosa è il rainbow table attack e come funziona?

__Promosso__ (25+4)

### Terzo

- Cos'è PET? (Privacy Enabling Technology - stronzissima senza sapere l'acronimo)
- Tor
    - Cos'è?
    - Spiega alla lavagna la struttura dei nodi
    - Disegni alla lavagna il pacchetto con i vari strati
    - L'ultimo nodo può leggere il contenuto del pacchetto?
    - Cosa garantisce con il protocollo?
- Smurf attack
    - Cos'è
    - Che tipo di attacco è (DoS)

Domande tutor:
- In una LAN, quali attacchi si potrebbero fare?
- Quali metodi di scansione ha nmap?
    - Come fare per non essere rilevati?

__Promosso__ (28)

### Quarto
- Altri esempi di PET? (GPG)
    - Che tipo di attacco si può fare a un gruppo di persone che usa GPG? (con traffic analysis si può comunque vedere chi comunica con chi)
- Cosa è ASLR (Address Space Layout Randomization - altro acronimo molto stronzo)
    - Cosa fa?
    - Come viene assegnato lo stesso indirizzo di memoria a più processi (con la memoria virtuale)
- Come funziona il buffer overflow?

Domande tutor:
- Cosa è il CSRF?
    - Cosa sfrutta in particolare?

__Promosso__ (24+4)

### Quinto

- Quali sono le criticità della crittografia asimmetrica?
    - Quanta più lenta è in ordine di grandezza rispetto alla crittografia simmetrica? (2 ordini di grandezza)
    - A quale problema matematico è legato RSA?
- Quali metodi esistono per contrastare il buffer overflow?
    - Come funziona il canarino? Chi lo inserisce? Come deve essere? Elimina il rischio buffer overflow?
- IDS
    - Cosa sono e come funzionano?
    - Quali tipologie ci sono?
    - Che differenza c'è tra un firewall e un IDS?

Domande tutor:
- SQL injection
    - Cosa sono?
    - Come ci si può difendere?

__Promosso__ (25)

### Sesto

- Regole auree
    - A cosa servono? 
- ...
- Come si accorge un sistemista di una privilege escalation?
    - Come evitare che root cancelli i file di log?
- Quali sono le tipologie di firewall che conosce?
- Quale è la caratteristica della DMZ? Definizione di DMZ? Dove si trova?

Domande tutor:
- Quali tipi di attacchi XSS esistono?

__Promosso__ (30L)

### Settimo
- Wi-Fi security
    - Come si chiama l'attacco ...
    - Quale errore c'era nell'implementazione di RC4 che consentiva la costruzione dei dizionari?
    - Quale era il principale attacco fatto sulle reti Wi-Fi?
- Quali sono le tecniche che usano gli antivirus per rilevare i malware?
    - Come riconosce il binario? Cosa sono le signatures?
    - Come si rilevano i malware che si offuscano?

Domande tutor:
- Cosa sono i cookie?

__Promosso__ (26)

### Ottavo

- Come si esegue un attacco MITM?
- ARP poisoning
    - In quali contesti è utilizzato?
    - Come funziona?
- IPSec
    - Quali sono le criticità di IP che intende migliorare?

__Bocciato__

### Nono

- Quali sono le criticità lato sicurezza di IP?
- IPSec
    - Cosa è?
    - Confronti tra le due modalità
    - Che differenze ci sono tra TLS e IPSec?
    - Come fa IPSec a decidere se il traffico in uscita debba essere cifrato o meno?
- Come si fa un SYN-flood?
    - Per quali altri motivi si fa spoofing?

Domande tutor:
- Cosa sono gli honeypot?

__Promosso__ (27)

## Lunedì 13 febbraio 2023

### Primo

- Quale è la differenza fra shellcode ed eseguibile?
    - Quale è la differenza tra formato oggetto ed eseguibile?
- IDS behaviour-based vs knowledge-based

__Bocciato__

### Secondo

- Meccanismo usato dalle syscall per proteggere il SO dagli abusi? (ring architecture)
    - _Chi_ cambia il CPL?
    - Come funziona un interrupt hardware?
- Quali sono gli aspetti critici nella predisposizione di uno shell code per un buffer overflow? (Dimensione e dove saltare)
- Come si definisce un codice _position independent_? (RIP addressing)

Domande tutor:
- Cosa si può fare per evitare che lo shellcode venga eseguito? (Canary, rendere stack non eseguibile, ASLR)
    - Quali parti di codice possono essere randomizzate?

__Promosso__ (23+5+6=28)

### Terzo 

- Differenza dal punto di vista realizzativo tra virus e worm?
- Quali sono le 5 fasi che caratterizzano un virus?
- Disegna uno schema di TCP hijacking
- Attacco di Micnick

__Bocciato__

### Quarto

- ARP-Cache poisoning
    - Per cosa sta ARP (Address Resolution Protocol)
    - Disegna alla lavagna lo schema
- Quali servizi di sicurezza offre TLS?
    - Come viene garantita l'integrità?

Domande tutor:
    - Come funziona TOR?
    
__Promosso__ (21+5+1=22)

### Quinto

- Dictionary attack
    - Come viene protetta la passwordi in `/etc/shadow`?
    - Quali sono i limiti di John the Ripper?
    - Quali metodologie si usano per proteggere una password oltre all'hash?
    - Quali sono i permessi di `/etc/passwd`?
- Che cos'è un attacco smurf?

Domande tutor:
    - SQL injection

__Promosso__ (27+?=30)

### Sesto 

- Cos'è ANGR?
- Cosa sono le tre regole auree?
    - Cosa definiscono le regole auree? (___NON___ un sistema sicuro)
      Quale è il loro scopo / cosa rappresentano? (Controllo degli accessi)
      

__Bocciato__

### Settimo

- Cos'è un firewall?
    - Sono di strumenti di prevention, detection o audit? (Prevention)
    - Che tipi di attacchi evitano?
    - Il NAT è una misura di sicurezza?
- Cos'è una ACL?
    - Quale opzione è scomoda per le ACL?

Domande tutor:
- Cosa sono i cookie?

__Promosso__ (24+4+6=?)

### Ottavo 

- Controllo degli accessi in Linux
- Cosa è e a cosa serve SET-UID
- L'UID come viene determinato?
- Cos'è il SYN-flood?
- In cosa consinste l'IP spoofing?

Domande tutor:
- Quale è la differenza tra i concetti di _trust_ e _validity_ nelle chiavi GPG?

__Promosso__ (?=22)

### Nono

- Cosa è un file in formato ELF?
    - Perché lo shellcode non lo scriviamo in ELF?
- Quale è il problema della crittografia assimetrica?

Domande tutor:
- Contromisure buffer overflow

__Promosso__ (21+?=21)

### Decimo

- IPSec vs TLS
    - Quale è la granularità di IPSec?
    - Cosa definisce una SA?
    - Cosa c'è scritto nel SAD?
- Che differenza c'è tra virus e worm?
    - È più facile da scrivere un virus o un worm?
    - Assumendo un sistema sicuro, lo può attaccare un virus o un worm?
- Cos'è un sistema sicuro?
- Quale è la prima cosa che deve fare un worm quando arriva?
- Dato un sistema sicuro, quale principio bisogna estendere per far sì che un worm possa diffondersi? (?)

Domande tutor:
- Reflective vs stored XSS

__Promosso__ (26+3+6=28)

## Martedì 14 febbraio 

### Primo

- Sicurezza Wi-Fi
    - Per cosa sta WEP?
- Reference Monitor
    - Come avviene un processo di autorizzazione?

Domande tutor:
- Quali azioni si possono fare nelle reti locali prima di attaccare? (nmap)

__Bocciato__

### Secondo

- Aspetti negativi crittografica assimetrica
    - Quando sono grosse le chiavi pubbliche?
- Come fai a fidarti di _Google_ nell'ambito dei certificati? (Ti fidi del root CA)
- Come attaccherebbe la comunicazione tra un cliente e la sua banca?
- Cosa è una capability?
    - Esempio di capability

Domande tutor:
- CSRF 

__Promosso__ (25+5+5=29)

### Terzo

- IDS
    - Quale _signature_ si può impostare per rilevare i buffer overflow?
- Smurf

Domande tutor:
- SQL injection

__Promosso__

### Quarto

- Come vengono generati i processi in Linux?
    - EUID / RUID
- ...

Domande tutor:
- Rainbow attack

__Promosso__ (20+?=24)

### Quinto

- Shellcode
    - Come si fa a renderlo PIE senza RIP addressing? (articolo di coso)
- Società della sorveglianza

Domande tutor:
- Cookie

__Promosso__ (30+?=30L)

### Sesto

...

__Promosso__ (18+?=24)

### Settimo
- TCP hijacking e attacco mitnik
- ...

__Promosso__

### Ottavo 
- Cos'è il GDPR?

## Orali 2025/01/27:

1. (30L)
- STRIDE; come lo spiegherebbe a un amico che ha appena sviluppato un'app?
- Come protegge un'app da spoofing? Controindicazioni multi-factor?
- POW
- Tutor: Pen testing; qual è la prima operazione? (port scan, cosa fa?)

2. (28)
- SUID; come lo implementa? se in un programma con suid faccio fork che uid ha il programma forkato?
- cos'è l'autorizzazione
- Tutor: XSS

3. (Bocciato) 
- Auditing; come si chiamano in windows i file di log? problematiche dei file di log? dove vanno? chi fa l'analisi?
- TLS
- TOCTOU
- Tutor: john the ripper; come funziona senza fare bruteforce?

4.
- Mitnick Attack su lavagna
- E2E encryption; protocolli (mtproto, signal); alternativa a DH usata e perchè (i due host nelle app di messaggistica non sono per forza online contemporaneamente)
- Tutor: TOR

5. (25)
- Cosa significa approcio risk-based? (risk management)
- proprietà di un sistema sicuro (le 6)
- data origin authentication
- accountability
- difese da bufferoverflow
- Tutor: SQL Injection; contromisure; esempio semplice ed esempio complicato

6. (26)
- Repudiation
- Firma digitale
- MAC
- Integer overflow, perchè succede, come evitarlo, esempio di codice
- Tutor: come fare uno shell code con buffer overflow se vi è stack/heap non eseguibile

## Orali 17 Gennaio

### Orali mattino
#### Primo orale (Andrea)

1. Come garantire l’integrità dell’informazione?
  a. Cosa vuol dire integrità? → Definizione
  b. Cosa vuol dire confidenzialità? → Definizione
  c. Come so se un file è integro? → Valore di hash
  i. Che cos’è un valore di hash?
  ii. Che cos’è una funzione hash?
  iii. Per cosa usiamo la funzione di hash? → Per verificare l’integrità del messaggio)
2. Cosa sono le race condition?
  a. Creano problemi di sicurezza? → Sì, TOCTOU attack
  b. Come funziona l’attacco TOCTOU?
  i. Perchè viene usata la cartella dev/null nell’esempio visto a lezione, e come la
  usiamo?
3. Che metodi abbiamo visto per capire che porte sono aperte in un host remoto?
  a. Perchè cerchiamo di capire che porte sono aperte?
  b. Che valori ritorna la scansione?
  c. Nome del programma che usiamo? → Nmap

#### Secondo orale

1. Che cos’è una blockchain?
a. Come si chiama l’albero? → Merkel tree
b. Come sono collegati i blocchi? → In che modo il blocco n si collega al blocco n+1
c. Cosa devo fare per modificare una transazione? E cosa comporta la modifica?
d. Come so se la transazione è in un blocco?
i. Come usare gli hash per velocizzare la ricerca?
2. Cosa sono i frewall?
a. Proprietà firewall packet-filter? → In base a cosa filtrano il traffico?
b. Che tipi di firewall ci sono?
c. Firewall che migliora il packet-filter? → Statefull inspection
3. Rainbow attack? (in generale attacchi alle password)
a. Salting per permette di avere la stessa password a più utenti

#### Terzo orale

1. Cosa si intende per autenticazione e autorizzazione? (solo autenticazione)?
  a. Chi implementa il processo di autorizzazione? → reference monitor
  i. Chi definisce l’access control matrix?
  ii. Dove sono memorizzate le ACL? Chi le mette? → DAC e MAC
2. Che cos’è un ransomware?
  a. Come cifra i file?
  i. Dove salva la chiave?
  ii. Qual è il problema di usare la chiave simmetrica?
3. In che contesto parliamo di attacchi XSS?
  a. Differenza tra stored e reflected?

#### Quarto orale 

1. Che cos’è uno stack frame?
  a. Che cosa c’è all’interno?

  b. Come facciamo un buffer overflow?
  c. Chi decide quali dati vanno sullo stack e quali no?
  d. Come si alloca spazio nello stack?
  e. Come funziona un buffer overflow?
  f. Dove viene messa la porzione di codice da eseguire?
  g. Che vulnerabilità si usano per fare un buffer overflow?

2. Cos’è una SIEM?
  a. Quali sono gli input?
  b. Dispostivi che usano i loro log?

3. Come funziona il protocollo TOR?

4. Differenza tra trust e validity?

### Orali pomeriggio
#### Primo orale

1. Paralre di attacchi di rete
a. Che cos’è il DoS e come si fa?
i. Come satura il processore? → Non è un attacco che abbiamo visto
b. Come si fa un IP spoofing?
c. Altro attacco di tipo DoS? (ping of death, ma complesso che venga fatto ora)
i. Che cos’è il ping?
d. Dimensione massima di un pacchetto internet?
e. Smurf
f. Quanti messaggi gestisce un server? E da cosa dipende?
g. Come proteggere la rete da un attacco di tipo smurf?
h. Come sono fatti gli indirizzi broadcast? (risposta alla domanda “dove punta un
attacco smurf?”)
2. Dato un hash di può risalire alla password messa?
a. Rainbow table, differenza con attacchi dizionario

#### Secondo orale

1. Che cos’è una PKI?
  a. Come avviene la verifica di una firma digitale?
  b. Chi garantisce la validità delle chiavi pubbliche rilasciate dalle certification autority?
  c. Perchè si firma l’hash e non il documento?
2. Tecniche di evasion usate dai creatori di malware per sfuggire agli antivirus?
  a. Qual è il problema di criptare l’intero virus?
3. Come funziona TOR?
  a. Come avviene lo scambio di chiavi?
  b. Ci sono problematiche con TOR? → Nell’uso quotidiano è più lento

#### Terzo orale

1. he cos’è l’integer overflow?
  a. Come generiamo un integer overflow?
  b. Quale vulnerabilità viene sfruttata per questo attacco?
  i. Perchè non viene fatto il controllo di questa vulnerabilità?
2. Contromisure per il memory errors? → Ad esempio canarino o stack non eseguibile
  a. Come rendere lo stack non eseguibile? → Read to libc (?)
  b. Dove l’attaccante mette il codice da usare?
  c. Come so se ho sovrascritto il codice da usare?
3. Attacco di Mitnick
  a. Perchè è importante non far rispondere il server?
  b. In che altro contesto ci serve capire come cambiamo i casi (?)?

#### Quarto orale

1. Cosa si intende per privilege escalation?
  a. In che modo garantiamo che l’utente non faccia cose che non vogliamo?
  b. Come si esegue un codice con setUID? → Come lo si ottiene
  c. Chi setta il setUID?

  d. I rischi legati all’uso
  e. Per cosa usiamo RUID?

2. Contromisure adottate da bitcoin contro il double spending?
a. Che meccanismo usa bitcoin per nascondere l’identità dell’utente?
b. Cosa viene usato come identificativo del wallet?
c. Quando si parla di anonimato? È sempre vero nei bitcoin?
d. Il wallet è un meccanismo di anonimato o pseudo anonimato?
i. Differenze tra i due anonimati?
3. In che contesto abbiamo visto gpg?
a. Che cosa ci permette di fare? → Dove reperiamo le chiavi di una persona?
b. Concetto di trust e validity