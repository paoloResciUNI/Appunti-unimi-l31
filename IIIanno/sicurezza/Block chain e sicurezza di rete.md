# Block chain e sicurezza di rete 

 ## MAC

Message Authentication  Code. È un protocollo di controllo e verifica dei pacchetti. Questo codice mi porta all'autenticità ma non la non reputiabilità. Non ci garantisce la non reputiablità per il fatto che la chiave è conosciuta da due individui, per avere la non repudiabilità è necessario che lo conosca uno solo. 

Bisogna fare una scelta sul tipo di algoritmo da utilizzare per cifrare la comunicazione, simmetrici per key exchange e asimmetrici per il traffico di rete. 

A quel livello dello stack ISO verrà cifrato il messaggio? Dipende dal tipo di comunicazione, possiamo cifrare a tutti i livelli ma dobbiamo considerare che il pacchetto verrà decriptato a quello stesso livello. Più si sta al livello più la comunicazione è "sicura". 

Consideriamo le conseguenze della cifratura ai vari livelli: 

- A livello di sistema operativo, ha il vantaggio che è tutto trasparente al programmatore, non si deve preoccupare della confidenzialità. È meno faticoso fare encription e decription per la CPU e per la banda di rete. Per questo motivo si può decidere su quali IP avere una comunicazione criptata.
- A livello applicazione, la situazione è più complicata per il programmatore che deve conoscere concetti di crittografia, dato che quel lavoro non è demandato al SO. La comunicazione può essere cifrata per le singole applicazioni. Questa è la crittografia End-To-End. Solo mittente e destinatario possono accedere al messaggio in chiaro.  

> Caso FBI vs Apple

## IPSEC

Standard costruito sopra IP (inizialmente per IPv6). Aggiunge 2 header al pacchetto IP. È utiliRzzato dalle VPN. IPSEC offre:

- confidenzialità 
- integrità 
- Authentication

Sono tutti servizi opzionali, dipendenti dalla configurazione. 

## HTTPS 

Fornisce servizi di cifratura a livello trasporto. Utilizza una parte di protocollo, TLS (Transporto Layer Security), montato sopra TCP. 

> TLS prima chiamato SSL. Una socket sicura che nasce nel '95 da netscape 
>
> TLS fa un sacco di belle cose. 

>  Trattatto di Wassenar, non mettere armi a disposizione di paesi nemici, inclusi gli algoritmi di crittografia. I browser europei non usavano RSA statunitense ma ne usavano una versione più debole. 

### Master Secret 

Contiene tutti i materiali crittografici che servono per eseguire una sessione TLS.

> Esempi di attacchi a TLS
>
> - BEAST 2011
> - Heartbleed 2014

## End to End

## Diffie Hellman algorithm 

Assume che i due interlocutori lavorino in campo finito. 

Ognuno genera un numero casuale sulla propria macchina. I due elevano il loro numero per $R_U$, quando uno dei due riceve il numero dell'altro lo eleva. 

Diffie Hellman è vulnerabile all'attacco man in the middle. La versione non vulnerabile presuppone l'utilizzo di certificati digitali. 

#### MTProto

#### Sygnal

Sygnal usa curve ellittiche e una versione modificata di diffie-hellman. Impleenta:

- End to end encription
- Perfect forward security 
- Deniable Authentication
- Asyncronius Communication



###  

