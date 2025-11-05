# Privilege escalation e Exploit

Fare privilege escalation permette all'attaccante di prendere accesso alle risorse del sistema come se fosse il proprietario di tali risorse. Per fare questo vengono utilizzati exploit, presenti nei sistemi operativi Windows o Unix like.

---

## Iteger-base vulnerabilità e problemi di C
Le Integer-based vulnerabilities sono exploit che utilizzano dei bug legati alla gestione degli interi in memoria centrale. Difatti l'obbiettivo di ogni attaccante è quello di mettere nella coda delle eseczioni il prorpio codice malevolo. Questi exploit sfruttano delle particolari vulnerabilità legate allo svolgimento di operazioni aritmetiche e nella conversione di numeri interi e tipi di differente grandezza o sneza segno (*signedness*)

### Problemi con C
I problemi di sicurezza legati a C sono molto pericolosi, causa il fatto che C sia il linguaggio di programmazione più utilizzato per le applicazioni legacy. Di fatti tutti i sistemi operativi sono scritti in C data la sua enorme diffusione e alte prestazioni. Quindi risulta fondamentale conoscere le vulnerabilità della gesione degli interi nella memoria centrale che questo linguaggio si porta dietro.

Consideriamo ora il tipo `char`.

---
