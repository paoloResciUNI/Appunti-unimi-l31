# Principi della sicurezza informatica 

## Obbiettivi principali 

> [!TIp]
>
> Gli **agents** rappresentano: utenti, entità di comunicazione o processi di sistema. Questi sono anche chiamati *principals*, a cui sono associati certi *privilegi* riguardo a certe risorse al quale è in grado di accedere

1. *Confidenzialità*: Informazioni private che rimangono accessibili solo al legittimo proprietario o a entità autorizzate. Questa proprietà è garantita da un access control, integrato nella maggior parte dei sistemi operativi. Un'altra tecnica è la criptazione dei dati mediante degli algoritmi di crittografia tramite chiave. 
2. *Integrità*: la garanzia che i dati che abbiamo a disposizione non vengano modificati in maniera non autorizzata. Maligne violazioni di codice sono prevenute e combattute da codici di correzione di errori, controllo degli accessi e controlli di integrità crittografici. 
3. *Autorizzazione*: è la proprietà che ci garantisce che le informazioni da noi custodite siano utilizzate solo da entità autorizzate: dal proprietario della risorsa informativa o dall'amministratore del sistema.    
4. *Disponibilità*: garantire che le risorse del sistema siano sempre disponibili alle entità autorizzate (attacchi *denial of service*).
5. *Autenticazione*: serve ad assicurarsi che un agent che accede ad una determinata entità abbia i privilegi per farlo. Garantisce anche che l'identità di un principal sia confermata ad ogni transazione. *Data origin authentication* ci permette di assicurarci la provenienza della risorsa software, o informativa, sul quale stiamo operando. L'autenticazione e il controllo degli accessi permette di attribuire le responsabilità delle azioni con maggiore sicurezza. 
6. *Responsabilità*: questa è la nostra ultima spiaggia. Se non riusciamo a proteggere in maniera adeguata le risorse o se i threat agents riescono a penetrare il mio sistema e farmi un attacco, questo sistema riesce a capire chi e quando ha fatto cosa. Sembra banale ma da la conoscenza di dove è partito l'attacco e la capacità di bloccarlo o di limitarne i danni.  