# Lez 11

# Bitcoin	

È un protocollo di comunicazione peer-to-peer progettato per il trasporto di moneta virtuale. Non corrisponde a nessuna moneta fisica ma è virtuale. Sono mossi tramite le transazioni. 

Nasce nel 2008, teorizzato da un gruppo di persone sconosciute (satoshi inakamoto). 

## Funzionamento 

La transazione è estremamente semplice. La transazione viene mandata al gruppo che gestisce le transazioni. Dopo la transazione c'è un movimento di tali bitcoin. 

Si basa su una rete di nodi. 

- **full node**: nodi importanti, fanno la validazione delle transazioni e mantengono l'integrità del libromastro. 
- **light node**: Contengono le informazioni necessarie per la validazione delle transazioni. 

I **miner** sono dei nodi particolari. Ogni nodo deve avere una coppia di chiavi pubblica e privata. Il protocollo utilizzato è ECDSA. 

Ogni utente è individuato da un indirizzo. 

Non è vero che il Bitcoin garantisce l'anonimato. L'edger di Bitcoin è totalmente pubblico. 

### Hash pointer

Un puntatore che contiene l'idirizzo al dato e all'hash di quel dato. Questo è utile per garantirne l'integrità. 

Per garantire l'integrità dei bitcoin, e quindi che siano difficili da contraffare e che abbia una fonte sicura.

Per evitare che le monete siano contraffatte vengono firmate al momento della creazione, dal minatore. Quell'oggetto non potrà essere rigenerato da qualcun'altro.  Le transazioni che vengono poi fatte vengono registrate sul registro mastro. In questo modo si può verificare che le monete, i bitcoin, siano reali e non siano contraffatte. 

Per garantire di evitare il double spending, tutte le transazioni sono scritte sul **global ledger**.

### Transaction

Sono dei programmi che trasferiscono/prendono soldi.  

Le transazioni vengono salvate in blocchi dai miner. Ogni blocco contiene dalla 1000 alle 2500 transazioni che vengono verificate dai miner. 

La **coinbase transaction** è quella transazione che da origine ai bitcoin. Il miner per goni blocco creato e accettato dalla rete prende una percentuale di bitcoin che è il block reward. 

Nel 2009 il block reward era di 50 bitcoin. Ogni 21000 transazioni il block reward si dimezza. Non potranno essere generati più di 21.000.000 di bitcoin al mondo. 

### Registro mastro

È una sequenza di blocchi, una lista linkata di blocchi. 

C'è bisogno del blocco zero generato da satoshi. 

>  [!Note]
>
> Un problema gigantesco dei bitcoin è l'estrema volatilità. La merce non rispecchia il valore in termini di bitcoin. 

## Blockchain 

Le transazioni sono organizzate attraverso un merkel tree. 

> #### Merkel tree
>
> Le foglie dell'albero sono al livello superiore. Vengono concatenati gli hash di due trnsazioni e i genitori sono gli hash dell'hash. La root dell'albero viene chiamata Merkel root e viene posta nell'header del blocco. 

Il problema del **consenso** è un probelma struttura dei sistemi distribuiti. Bisonga controllare se alcuni miner non propongano dei blcchi con un double spending. Per raggiungere un'accordo si usano:

- block rewards 
- transactions fees
- per produrre blocchi spendi un sacco di soldi (**Proof Of Work**)

Questa cosa funziona se il 50+1% dei miner è onesto allora bitcoin funziona bene, altrimenti no.

Accordo Bizantini. 

---

Ricapitolando: ogni transazione viene mandato in broadcast ad ogni blocco, ogni nodo inserisce la transazione nel blocco. 

Il blocco viene pubblicato, per essere accettato deve essere accettato dall'intera rete.

### Proof of Work

Consiste nell'ivertire una fnzione hash, SHA256. 

Viene data una merkel root più un numero $x$ che deve dare, data la fuzione hash, un numero che sia minore uguale al *nonce* (un numero dopo una quantità prefissata di zeri).

##### Nonce 

La block chain forka, ovvero più miner lavorano su più block chain diverse. Dato questo problema ogni transazione viene convalidata dopo 6 blocchi (ogni blocco viene validato ogni 10 minuti). Questo perchè è dimostrato che la block chain converge