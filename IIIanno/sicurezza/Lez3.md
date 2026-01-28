# Sistemi “Sicuri”

## Design Secure Systems 

> [!tip]
>
> L'unico oggetto che esegue i programmi è il processore.

Il processore si alterna tra i programmi per eseguire più programmi contemporaneamente. Da qui nascono i sistemi multiprogrammati. I sistemi multiprogrammati contengono tutti i programmi in memoria, dato che li eseguono contemporaneamente. Il SO crea code di processi per poter eseguire tutti i programmi in modo che simulino l'esecuzione in parallelo.

Un attaccante cerca di inserire codice maligno nella coda dei processi del calcolatore. Una volta che il codice maligno si trova nella coda dei processi, deve solo aspettare il suo turno. Si può convincere l'utente a mettere il processo maligno in coda o sfruttare vulnerabilità dei processi in coda per iniettare il processo maligno.

Ci sono modi per rendere queste azioni più complicate e rendere il sistema più sicuro.

Il primo punto è pensare a scrivere bene i programmi, inserendo meccanismi di protezione.

*Cyber security is a process* (inteso all'interno di un'organizzazione)

### Costruire un sistema sicuro 

Non esiste una metodologia unica per costruire un sistema sicuro. Per prima cosa bisogna fare un sistema "piccolo" e semplice: meno codice scriviamo, meno errori potenziali introduciamo. 

> Quando un programmatore lascia un'azienda, il codice fatto da lui viene spesso abbandonato. L'importante nel mondo enterprise è consegnare il codice in tempo. 

Un altro meccanismo è lasciare nelle impostazioni di default l'opzione più sicura. Per esempio, nei firewall è meglio scegliere l'opzione del sistema chiuso, ovvero il sistema a whitelist (entra solo se esplicitamente permesso).

La complete mediation dice che quando un'applicazione accede a un oggetto, non può accedere direttamente ma tramite il controllo di un altro oggetto che verifica che abbia i permessi adeguati per lavorare con quell'oggetto (che può essere un file, processo, I/O, ecc.). Se le applicazioni potessero accedere direttamente alle risorse, basterebbe corrompere l'applicazione.

L'open design rende le applicazioni più sicure: le applicazioni open source sono generalmente più sicure. C'è anche il concetto della security by obscurity, ma è sostanzialmente sbagliato dato che dà una sicurezza illusoria. Gli algoritmi di crittografia, per esempio, devono essere open source.

La politica del *least privilege* è una buona pratica per mantenere il sistema sicuro: dare al minor numero di persone i privilegi da super user. Si integra con un'altra buona pratica, il modular design. Facciamo in modo di separare i vari privilegi e non avere un sistema monolitico: ogni componente del sistema compie la sua funzionalità e si autogestisce. Vi sono anche sistemi nei quali più entità hanno la responsabilità: tutte le componenti devono essere d'accordo per eseguire alcune operazioni (separation of duty).

Un meccanismo emergente è un'altra cosa che può rendere un programma più sicuro. L'accettazione psicologica è un meccanismo di accettazione di una tecnologia, perché complicata da usare. L'usabilità tenta di superare questo ostacolo.

> **B. Lampson**
>
> Tre meccanismi per implementare un'applicazione sicura.
>
> Golden rules:
>
> - Authenticating principals 
> - Authorizing access
> - Auditing the decisions of the guard

Esempio del Night Club 

- Authentication - controllo ID 
- Access Control
  - < 18 non può entrare 
  - < 21 non può bere
- Enforcement Mechanisms - Muri, porte, serrature...
- Accountability - Telecamere

Entità attive = quelli che fanno cose 

Entità passive = le cose su cui si possono fare azioni (es. RAM)

Ogni soggetto (attivo) ha dei diritti su un oggetto (passivo). 

### Access Control 

La prevenzione dell'uso non autorizzato di una risorsa, incluso l'uso della risorsa in una maniera non autorizzata.

Il controllo degli accessi viene effettuato dal reference monitor, che non è un oggetto ma un concetto, composto da più componenti. È l'insieme di meccanismi che svolge questo compito.  

### Identificazione e Autenticazione 

Per riconoscere una persona si procede tramite:

- Identificazione - una persona dichiara la sua identità
- Autenticazione - si verifica che l'utente sia effettivamente chi dice di essere

Di base sui computer si utilizza una password. La password si basa sul principio di fiducia che solo la persona interessata conosca quella password. Le password sono memorizzate insieme agli user id su un file. 

In Unix il meccanismo è separato. Il file `/etc/passwd` contiene tutti gli utenti (di sistema e non). Le password sono nel file `/etc/shadow`, la password non viene salvata in chiaro ma viene cifrata. 

Il problema di questo sistema è l'utente che sceglie password facili da indovinare. Forzare gli utenti a scegliere password difficili da indovinare è estremamente controproducente. 

#### Rompere una password

1. Indovinarla  
2. WordList - presuppone di avere un file `shadow`, allora si prova a indovinare le password. Viene costruita una lista di password possibili e viene confrontata con il file `shadow` per vedere se è stata trovata. Questo attacco è chiamato dictionary attack.  
3. Brute force - è sicuro che prima o poi trova la password giusta. 

### Categorie di meccanismi di identificazione 

- **What you know** (password)
- **What you are** (sistemi biometrici)
- **What you have** (chiave di autenticazione fisica)
- **Where you are** 

La multifactor authentication è definita quando almeno due di queste categorie sono utilizzate contemporaneamente per identificare un soggetto. 

> **OTP** (One Time Password)
>
> Nei primi anni 2000 tutti i dati su Internet erano in chiaro. 
>
> Nasce l'idea della password utilizzabile una sola volta.
>
> Se la password viene mandata sul telefono allora è un'autenticazione a più fattori.

### Dati biometrici 

La biometria nasce per affrontare la debolezza delle password. Vengono utilizzati più tratti biometrici: quelli fisici e quelli comportamentali. 

#### Problemi della biometria 

Può essere: intrusiva, costosa, single point of failure (non è rimpiazzabile), falsi positivi, lenta, può essere contraffatta. 

Il punto a favore della biometria è l'**usabilità**. 

Ci sono due fasi nella biometria: **enrollment** e **recognition**. L'impronta viene processata e memorizzata. I lettori possono sbagliare: se sbagliano in fase di lettura, l'accesso è negato. C'è un limite teorico sotto il quale i lettori non possono andare. 

**Threshold** = valore che indica se l'impronta è corretta o no; se sopra lo 0.5 è TP, se sotto lo 0.5 invece è TN. Il problema è che non sempre funziona: se aumento il threshold aumento i false negative, altrimenti aumento i false positive. 

Questo diventa un sistema di autenticazione probabilistico, non più deterministico (come la password).















