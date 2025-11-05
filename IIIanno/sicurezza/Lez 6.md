# Lez 6

## The buffer overflow attack via smashing the stack techinique 

Robert Morris una notte scrive un programma C che sfrutta il buffer overflow su sunOS. Nel giro di un'ora il suo internet warn ha messo fuori uso il 10% di internet. C'era un bug nel codice, ovvero non controllava se la macchina infettata non fosse già infettata. 

Il warn funziona in questo modo: infetta la macchina e prova a infettare tutte le macchina connesse e presente nell'elenco dei contatti.

Smashing the stack, viene spiegato a tutti come funziona. 

Su sistemi IoT questi tipi di attacchi sono abbastanza frequenti. 

#### Funzione Buffer Overflow 

Il processore non controlla il contenuto del PC, per raggiungere il "sacro grall" del exploiting devo prendere il controllo del Program Counter. 

Questo tipo di attacco funziona solo su C e derivati. 

- **CALL**: Fa un goto a un indirizzo, la prima istruzione eseguibile, fa una push sullo stack l'indirizzo alla prossima istruzione.
- **RET**: Carica l'indirizzo puntato da rsp in quel momento nel PC. 

> Nei sistemi a 64 bit i primi 6 argomenti vengono caricati nei registri e gli altri nello stack

```C
// programma scritto in C che mostra il funzionamento dello stack
#include<stdio.h>

int main() {
    int cookie;
    char buf[80];

    printf("buf: %08x cookie: %08x\n" &buf, &cookie);
	gets(buf);
    
    if (cookie == 0x41424344) {
        printf("Hai vinto!\n");
    }
}
```

Questo dimostra che possiamo modificare lo stack. 

Quindi modificando lo stack di esecuzione del programma possiamo modificare il return address, facendolo puntare ad un indirizzo randomico. 

---

Il codice che vogliamo eseguire va caricato in una zona particolare di memoria. Ma il processore non conosce il linguaggio C o altri linguaggi se non il linguaggio macchina. In gergo chiamato *shellcode*. 

Una volta pronto e testato lo shellcode si procede con l'exploit.

Per preparare l'exploit, devo conoscere:

- l'indirizzo dello shellcode
- l'indirizzo del return adress
- la versione del compilatore

Vengono molto utilizzate le NOP (dato che occupano un byte `90`). 

## Contromisure 

Il buffer overflow è stato un attacco molto diffuso. La sua realizzazione è stata resa molto più complessa. Gli approcci:

1. Insegnare ai programmatori di usare funzioni *safe*.
2. Sono state instrodotte tre misure:

### Principio ASLR

Questo principio randomizza l'allocazione dello stack. Questo rende impossibile costruire l'exploit. 

> Su linux la randomizzazione può essere disabilitata.

Resta comunque possibile fare l'attacco anche con indirizzi randomizzati. 

### Stack guard

Un altro meccanismo per prevenire il buffer overlflow. Vine messa una *guardia* se la guardia viene modificata allora il codice non viene eseguito. 

La guardia si chiama canary. Deriva dall'usanza che quando le miniere di zolfo cadevano mandavano un canarino nella miniera, se non tornava allora la miniera era ancora inagibile. 

Anche il canarino può essere bypassato. Se conosco il valore del canarino lo posso sovrascrivere, nello shellcode, con il suo valore reale, così nessuno lo sa. 

Esiste il canarino **terminator**, questo perchè contiene i simboli di terminazione della stringa (`\00\00\`). Questo termina l'esecuzione dello shellcode.

### Not executable stack

Il SO rende non eseguibili le zone di memoria legate allo stack. 

Questa è stata bypassata nel giro di tre mesi. Con l'attacco Ret-to-libc. 

### Data Execution Prevention

Estensione del non executable stack. Rende non eseguibili varie zone di memoria. Dato che lo stesso smashing che si fa sullo stack si può fare anche su heap. 