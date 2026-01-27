# IDS

**Intrusion Detection System**, sono dei sistemi che devono accorgersi se sta avvenendo in un determinato momento. Grazie al machine learning si sono diffusi e migliorati molto. Lo scopo è automatizzare la fase di detection.  

L'IDS per controllare il sistema utilizza i file di log. In precedenza l'IDS era un processo umano, gente che osservava per ore i file di log. 

Gli IDS sono stati aumentati si funzionalità, questi si chiamano IPS (Intruscion Prevention System). Questi sistemi rispondono alla intrusion detection. 

## Architetture

Si sono specializzati in vari ambiti: 

- Network based: basa la sua decisione dall'analisi del traffico di rete. In questo caso viene messo alla base di un firewall e si vede tutto il traffico che arriva.  
  - Questi hanno dei sensori fisici che sono messi in alcuni punti della rete, questi convogliano le richieste sul terminale che gestisce le informazioni acquista
- Host based: decisioni basate sui syslog di sistema. 
  - Gli host based hanno un agente su ogni macchina che va monitorata. 

Entrambi questi sistema si basano su:

- matching di pacchetti, per riconoscere pattern di attacco (signature based)

- Riconoscimento di nuove forme di attacco. Basato sul principio di anomalia. Si monitora il comportamento di un utente, se questo utente si comporta diversamente da come si comporta di solito viene riconosciuto come tentativo di attacco.

  Profilano il sistema e il comportamento degli utenti, tramite meccanismi di machine learning. 

### Error rates

Questi sistemi non bloccano i pacchetti ma li segnalano soltanto, sarà il security analist a decidere se quello che ha fatto l'IDS è un TP o un FP. L'errore di falso positivo è particolarmente elevato (<= 1%). 

I sistemi signature based sono quelli che hanno meno probabilità di sbagliare. 

## Security Information Event Managemnet

Sono piattaforme molto costose che fanno da IDS, che diventa un alimentatore  del database dei SIEM. 

Fanno un salto qualitativo, prendono input da: applicazioni, rete, firewall, database e da fonti esterne di analisi (i db dei vendor). Quello che fanno in particolare è real time monitoring. Inoltre aggiungono informazioni geolocali, di DNS, possono accedere al dark web e controllare se ci sono utenti compromessi. 

## CSOC (CyberSecurity Operation Center)

Sono dei posti dove viene fatto il monitoraggio in tempo reale dell'organizzazione. Ogni grande o piccola azneda o ente statale hanno il loro CSOC. È la risposta naturale dei meccanismi di protezione, come la SIEM. 

L'obiettivo della CSOC è: 

- prevention (limitatamentee indirettamente)

I SOC sono centralizzati (Telecom ne ha due ridondati in italia), sono cecntri relativamente grossi,  qui dentro operano gruppi di esperti (CERT, Computer Emergency Responce Team) che gestiscono gli incidenti. 

Il primo CERT nasce nel 1988 dopo l'attacco di internet WORM. Il primo in italia è stato fondato in UNIMI nel 1995 (terzi in europa). I CERT sono tutti collegati globalmente. 

Adesso non si chiamano CERT ma CSIRT, questo perchè CERT è stato brevettato.

Riprendendo il discorso, il CERT viene preso per rispondere ad un attacco, dopo la segnalazione data dai SOC analist. 

I SOC analyst si dividono in:

- Primo livello: quasi completamente sostituito da machine learning
- Secono livello
- Terzo livello 

I CIEM sono forniti di diversi strumenti per riconoscere i vari formati di file di log di diversi produttori. 