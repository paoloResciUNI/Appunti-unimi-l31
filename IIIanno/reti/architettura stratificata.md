# Architettura stratificata *layering*
I protocolli di rete vengono formalizzati con una divisione in strati suddivisi in livelli gerarchici. 
Ogni strato prende pacchetti dallo strato sottostante mediante code ad accesso FIFO.
A loro volta, anche i protocolli di rete sono divisi in strati, ognuno di essi permette di formalizzare un'interfaccia ben definita fra i vari livelli. 