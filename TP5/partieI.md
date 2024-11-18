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

## 3. Compilation statique


🌞 **Affichez le type des fichiers `hello2` et `hello3`**


🌞 **Affichez leurs tailles**


## 4. Compilation cross-platform

🌞 **Affichez l'*architecture* de votre *CPU***



🌞 **Vérifiez que vous avez la commande `x86-64-linux-gnu-gcc`**



🌞 **Compilez votre fichier `hello3.c` dans un fichier cible nommé `hello4` vers une autre *architecture* que la vôtre**



🌞 **[Désassemblez](../../cours/memo/glossary.md#désassembler) `hello3` et `hello4` à l'aide d'`objdump`**



🌞 **Essayez d'exécuter le *programme* `hello4`**