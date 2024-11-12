# II. Files and users

## Sommaire

- [II. Files and users](#ii-files-and-users)
  - [Sommaire](#sommaire)
- [1. Fichiers](#1-fichiers)
  - [A. Find me](#a-find-me)
- [2. Users](#2-users)
  - [A. Nouveau user](#a-nouveau-user)
  - [B. Infos enregistrées par le système](#b-infos-enregistrées-par-le-système)
  - [C. Hint sur la ligne de commande](#c-hint-sur-la-ligne-de-commande)
  - [D. Connexion sur le nouvel utilisateur](#d-connexion-sur-le-nouvel-utilisateur)

# 1. Fichiers

## A. Find me

🌞 **Trouver le chemin vers le répertoire personnel de votre utilisateur**
```
naly@TPOS:~$ cd /home/

```

> N'hésitez pas à le chercher d'abord avec un explorateur de fichier, en utilisant l'interface graphique si vous en avez une. Si ça vous aide au début ! Appelez-moi, faites des recherches Google, mais pas de chatGPT si vous voulez progresser !

🌞 **Vérifier les permissions du répertoire personnel de votre utilisateurs**

```
naly@TPOS:/home$ ls -l
total 4
drwx------ 16 naly naly 4096 Nov 11 13:24 naly

```



🌞 **Trouver le chemin du fichier de configuration du serveur SSH**
```
naly@TPOS:~$ find / -name "sshd_config" 2</dev/null
/etc/ssh/sshd_config
/usr/share/openssh/sshd_config
```



# 2. Users

## A. Nouveau user

🌞 **Créer un nouvel utilisateur**
```
naly@TPOS:~$ sudo useradd -m marmotte -s /bin/bash
[sudo] password for naly:
naly@TPOS:~$ cd /
naly@TPOS:/$ cd home/
naly@TPOS:/home$ ls
marmotte  naly
naly@TPOS:/home$ sudo passwd marmotte
New password:
Retype new password:
passwd: password updated successfully

```

## B. Infos enregistrées par le système


🌞 **Prouver que cet utilisateur a été créé**
```
naly@TPOS:/home$ su marmotte
Password:
marmotte@TPOS:/home$
```

🌞 **Déterminer le *hash* du password de l'utilisateur `marmotte`**
```
naly@TPOS:/$ sudo cat /etc/shadow | grep marmotte
marmotte:$y$j9T$hXspIf4S50X2jfOsHk6Oi1$USE7iLKUXJshA6dL2Lw.n67yzLXG.AxfVNzufBUvcD9:20038:0:99999:7:::

```

> **On ne stocke JAMAIS le mot de passe des utilisateurs** (sous Linux, ou ailleurs) mais **on stocke les *hash* des mots de passe des users.** Un *hash* c'est un dérivé d'un mot de passe utilisateur : il permet de vérifier à l'avenir que le user tape le bon password, mais sans l'avoir stocké ! On verra peut-être ça une autre fois en détails.

![File ?](./img/file.jpg)

## C. Hint sur la ligne de commande

> *Ce qui est dit dans cette partie est valable pour tous les OS.*

**Quand on donne le chemin d'un fichier à une commande, on peut utiliser soit un *chemin relatif*, soit un *chemin absolu* :**

➜ **chemin absolu**

- c'est le chemin complet vers le fichier
  - il commence forcément par `/` sous Linux ou MacOS
  - il commence forcément par `C:/` (ou une autre lettre) sous Windows
- peu importe où on l'utilise, ça marche tout le temps
- par exemple :
  - `/etc/ssh/sshd_config` est un chemin absolu
  - *et c'est le chemin vers le fichier de conf du serveur SSH sous Linux en l'occurrence*
- mais parfois c'est super long et chiant à taper/utiliser donc on peut utiliser...

➜ ... un **chemin relatif**

- on écrit pas le chemin en entier, mais uniquement le chemin depuis le dossier où se trouve
- par exemple :
  - si on se trouve dans le dossier `/etc/ssh/`
  - on peut utiliser `./sshd_config` : c'est le chemin relatif de `sshd_config` quand on se trouve dans `/etc/ssh/`
  - un chemin relatif commence toujours par un `.`
  - `.` c'est "le dossier actuel"

➜ **Exemples :**

```bash
# on se déplace dans un répertoire spécifique, ici le répertoire personnel du user it4
$ cd /home/it4

# on affiche (parce que pourquoi pas) le fichier de conf du serveur SSH
# en utilisant le chemin absolu du fichier
$ cat /etc/ssh/sshd_config
[...] # ça fonctionne

# cette fois chemin relatif ???
$ cat ./sshd_config
cat: sshd_config: No such file or directory
# on a une erreur car le fichier "sshd_config" n'existe pas dans "/home/it4"

# on se déplace dans le bon dossier
$ cd /etc/ssh

# et là
$ cat ./sshd_config
[...] # ça fonctionne

# en vrai pour permettre d'aller plus vite, ça marche aussi si on met pas le ./ au début
$ cat sshd_config
[...] # ça fonctionne
```

## D. Connexion sur le nouvel utilisateur

🌞 **Tapez une commande pour vous déconnecter : fermer votre session utilisateur**
```
naly@TPOS:/$ exit
exit
```
🌞 **Assurez-vous que vous pouvez vous connecter en tant que l'utilisateur 
```
root@TPOS:/# su marmotte
marmotte@TPOS:/$ ls /home/naly
ls: cannot open directory '/home/naly': Permission denied
```
> **On verra en détails la gestion des droits très vite.**


