# TP5 : Le compilateur ton pire meilleur ami

🌞 **Créer un répertoire de travail dans votre répertoire personnel**

```

```

## PARTIE I 

## 1. Compilation

## 2. Analyse du programme compilé


🌞 **Retrouvez à l'aide de `readelf` l'architecture pour laquelle le programme est compilé**



🌞 **Afficher la liste des *sections* contenues dans le *programme***


🌞 **Affichez le code *assembleur* de la section `.text` à l'aide d'`objdump`**

## 2. Librairie et compilation dynamique

### A. Intro lib

### B. Intro compilation dynamique


### C. Tracer les appels à des librairies

🌞 **Tracez à l'aide de la commande `ldd` les *librairies* appelées par...**


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