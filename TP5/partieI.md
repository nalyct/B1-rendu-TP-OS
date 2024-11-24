# TP5 : Le compilateur ton pire meilleur ami

🌞 **Créer un répertoire de travail dans votre répertoire personnel**

```
abc@abc:~$ pwd
/home/abc
abc@abc:~$ mkdir work
abc@abc:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  work
abc@abc:~$ cd work
abc@abc:~/work$ pwd
/home/abc/work
```

## PARTIE I 

## 1. Compilation

## 2. Analyse du programme compilé


🌞 **Retrouvez à l'aide de `readelf` l'architecture pour laquelle le programme est compilé**
```
abc@abc:~/work$ readelf -h hello1
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              DYN (Position-Independent Executable file)
  Machine:                           Intel 80386
  Version:                           0x1
  Entry point address:               0x1000
  Start of program headers:          52 (bytes into file)
  Start of section headers:          13304 (bytes into file)
  Flags:                             0x0
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         11
  Size of section headers:           40 (bytes)
  Number of section headers:         21
  Section header string table index: 20
  ```


🌞 **Afficher la liste des *sections* contenues dans le *programme***
```
abc@abc:~/work$ readelf -S hello1
There are 21 section headers, starting at offset 0x33f8:

Section Headers:
  [Nr] Name              Type            Addr     Off    Size   ES Flg Lk Inf Al
  [ 0]                   NULL            00000000 000000 000000 00      0   0  0
  [ 1] .interp           PROGBITS        00000194 000194 000013 00   A  0   0  1
  [ 2] .note.gnu.bu[...] NOTE            000001a8 0001a8 000024 00   A  0   0  4
  [ 3] .gnu.hash         GNU_HASH        000001cc 0001cc 000018 04   A  4   0  4
  [ 4] .dynsym           DYNSYM          000001e4 0001e4 000010 10   A  5   1  4
  [ 5] .dynstr           STRTAB          000001f4 0001f4 000001 00   A  0   0  1
  [ 6] .text             PROGBITS        00001000 001000 00005d 00  AX  0   0  1
  [ 7] .eh_frame_hdr     PROGBITS        00002000 002000 00001c 00   A  0   0  4
  [ 8] .eh_frame         PROGBITS        0000201c 00201c 000058 00   A  0   0  4
  [ 9] .dynamic          DYNAMIC         00003f8c 002f8c 000068 08  WA  5   0  4
  [10] .got.plt          PROGBITS        00003ff4 002ff4 00000c 04  WA  0   0  4
  [11] .comment          PROGBITS        00000000 003000 00001f 01  MS  0   0  1
  [12] .debug_aranges    PROGBITS        00000000 00301f 000020 00      0   0  1
  [13] .debug_info       PROGBITS        00000000 00303f 000070 00      0   0  1
  [14] .debug_abbrev     PROGBITS        00000000 0030af 000062 00      0   0  1
  [15] .debug_line       PROGBITS        00000000 003111 000054 00      0   0  1
  [16] .debug_str        PROGBITS        00000000 003165 000085 01  MS  0   0  1
  [17] .debug_line_str   PROGBITS        00000000 0031ea 000018 01  MS  0   0  1
  [18] .symtab           SYMTAB          00000000 003204 0000b0 10     19   6  4
  [19] .strtab           STRTAB          00000000 0032b4 00006a 00      0   0  1
  [20] .shstrtab         STRTAB          00000000 00331e 0000d9 00      0   0  1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  D (mbind), p (processor specific)
  ```

🌞 **Affichez le code *assembleur* de la section `.text` à l'aide d'`objdump`**
```
abc@abc:~/work$ objdump -M intel -j .text -s hello1

hello1:     file format elf32-i386

Contents of section .text:
 1000 5589e557 565383ec 10e84b00 000005e6  U..WVS....K.....
 1010 2f0000c7 45e54865 6c6cc745 e96f2c20  /...E.Hell.E.o,
 1020 57c745ed 6f726c64 c745f064 210a008d  W.E.orld.E.d!...
 1030 75e5bf0e 000000b8 04000000 bb010000  u...............
 1040 0089f189 facd80b8 01000000 31dbcd80  ............1...
 1050 9083c410 5b5e5f5d c38b0424 c3        ....[^_]...$.
```

## 2. Librairie et compilation dynamique

### A. Intro lib

### B. Intro compilation dynamique


### C. Tracer les appels à des librairies

🌞 **Tracez à l'aide de la commande `ldd` les *librairies* appelées par...**
```
abc@abc:~/work$ ldd hello2
        linux-gate.so.1 (0xf7f81000)
        libc.so.6 => /lib32/libc.so.6 (0xf7d3d000)
        /lib/ld-linux.so.2 (0xf7f83000)
abc@abc:~/work$ file hello2
hello2: ELF 32-bit LSB pie executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=4d5bd5d79d0192184edef4b18b818126c7707932, for GNU/Linux 3.2.0, with debug_info, not stripped
abc@abc:~/work$ ldd hello1
        statically linked
abc@abc:~/work$ file hello1
hello1: ELF 32-bit LSB pie executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=10162ce5e895f70350cd1b628258d88a65e2ee64, with debug_info, not stripped
abc@abc:~/work$ ldd /bin/ls
        linux-vdso.so.1 (0x00007ffdc97d2000)
        libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007fae8a44c000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fae8a26b000)
        libpcre2-8.so.0 => /lib/x86_64-linux-gnu/libpcre2-8.so.0 (0x00007fae8a1d1000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fae8a4b3000)
abc@abc:~/work$ file /bin/ls
/bin/ls: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=15dfff3239aa7c3b16a71e6b2e3b6e4009dab998, for GNU/Linux 3.2.0, stripped
abc@abc:~/work$ which firefox
/usr/bin/firefox
abc@abc:~/work$ ldd $(which firefox)
        not a dynamic executable
abc@abc:~/work$ file $(which firefox)
/usr/bin/firefox: POSIX shell script, ASCII text executable
```

🌞 **Parmi les *librairies* appelées par *hello2*, déterminer le type du fichier nommé `libc.so.X`**
```
abc@abc:~$ file /usr/lib/x86_64-linux-gnu/libc.so.6
/usr/lib/x86_64-linux-gnu/libc.so.6: ELF 64-bit LSB shared object, x86-64, version 1 (GNU/Linux), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=c047672cae7964324658491e7dee26748ae5d2f8, for GNU/Linux 3.2.0, stripped
```

## 3. Compilation statique


🌞 **Affichez le type des fichiers `hello2` et `hello3`**
```
abc@abc:~/work$ cp hello2.c hello3.c
abc@abc:~/work$ gcc -static -fno-stack-protector -g -m32 -o hello3 hello3.c
abc@abc:~/work$ ls -l hello3
-rwxr-xr-x 1 abc abc 742172 Nov 24 15:14 hello3
abc@abc:~/work$ ./hello3
Hello, World!
```
```
abc@abc:~/work$ file hello2
hello2: ELF 32-bit LSB pie executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=4d5bd5d79d0192184edef4b18b818126c7707932, for GNU/Linux 3.2.0, with debug_info, not stripped
abc@abc:~/work$ file hello3
hello3: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, BuildID[sha1]=c267c46254603d9c1b2455874234c632bf7ba311, for GNU/Linux 3.2.0, with debug_info, not stripped
abc@abc:~/work$ ls -lh hello2 hello3
-rwxr-xr-x 1 abc abc  16K Nov 18 18:08 hello2
-rwxr-xr-x 1 abc abc 725K Nov 24 15:14 hello3
```

🌞 **Affichez leurs tailles**
```
abc@abc:~/work$ du -h hello2 hello3
16K     hello2
728K    hello3
```


## 4. Compilation cross-platform

🌞 **Affichez l'*architecture* de votre *CPU***
```
abc@abc:~/work$ lscpu
Architecture:             x86_64
  CPU op-mode(s):         32-bit, 64-bit
  Address sizes:          39 bits physical, 48 bits virtual
  Byte Order:             Little Endian
CPU(s):                   1
  On-line CPU(s) list:    0
Vendor ID:                GenuineIntel
  Model name:             Intel(R) N100
    CPU family:           6
    Model:                190
    Thread(s) per core:   1
    Core(s) per socket:   1
    Socket(s):            1
    Stepping:             0
    BogoMIPS:             1612.79
    Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36
                          clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good
                          nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 cx16
                           sse4_1 sse4_2 movbe popcnt aes rdrand hypervisor lahf_lm abm 3dnowprefe
                          tch ibrs_enhanced fsgsbase bmi1 bmi2 invpcid rdseed adx clflushopt sha_n
                          i arat md_clear flush_l1d arch_capabilities
Virtualization features:
  Hypervisor vendor:      KVM
  Virtualization type:    full
Caches (sum of all):
  L1d:                    32 KiB (1 instance)
  L1i:                    64 KiB (1 instance)
  L2:                     2 MiB (1 instance)
  L3:                     6 MiB (1 instance)
NUMA:
  NUMA node(s):           1
  NUMA node0 CPU(s):      0
Vulnerabilities:
  Gather data sampling:   Not affected
  Itlb multihit:          Not affected
  L1tf:                   Not affected
  Mds:                    Not affected
  Meltdown:               Not affected
  Mmio stale data:        Not affected
  Reg file data sampling: Mitigation; Clear Register File
  Retbleed:               Mitigation; Enhanced IBRS
  Spec rstack overflow:   Not affected
  Spec store bypass:      Vulnerable
  Spectre v1:             Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:             Mitigation; Enhanced / Automatic IBRS; RSB filling; PBRSB-eIBRS SW seque
                          nce; BHI SW loop, KVM SW loop
  Srbds:                  Not affected
  Tsx async abort:        Not affected
abc@abc:~/work$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 190
model name      : Intel(R) N100
stepping        : 0
microcode       : 0xffffffff
cpu MHz         : 806.399
cache size      : 6144 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 22
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
bogomips        : 1612.79
clflush size    : 64
cache_alignment : 64
address sizes   : 39 bits physical, 48 bits virtual
power management:

abc@abc:~/work$ which x86_64-linux-gnu-gcc
/usr/bin/x86_64-linux-gnu-gcc

```


🌞 **Vérifiez que vous avez la commande `x86-64-linux-gnu-gcc`**
```
abc@abc:~/work$ which x86_64-linux-gnu-gcc
/usr/bin/x86_64-linux-gnu-gcc
```


🌞 **Compilez votre fichier `hello3.c` dans un fichier cible nommé `hello4` vers une autre *architecture* que la vôtre**
```
abc@abc:~/work$ arm-linux-gnueabihf-gcc -o hello4 hello3.c
```


🌞 **[Désassemblez](../../cours/memo/glossary.md#désassembler) `hello3` et `hello4` à l'aide d'`objdump`**
```
objdump -dS hello3
objdump -dS hello4

```


🌞 **Essayez d'exécuter le *programme* `hello4`**   
```
abc@abc:~/work$ ./hello4
-bash: ./hello4: cannot execute binary file: Exec format error
```