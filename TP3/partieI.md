# I. Utilisateurs

- [I. Utilisateurs](#i-utilisateurs)
  - [1. Liste des users](#1-liste-des-users)
  - [2. Hash des passwords](#2-hash-des-passwords)
  - [3. Sudo](#3-sudo)
    - [A. Intro](#a-intro)
    - [B. Practice](#b-practice)

## 1. Liste des users

La liste des utilisateurs qui existent sur le système est contenue dans un fichier : le fichier `/etc/passwd`.

Le fichier `/etc/passwd` est structuré comme suit :

- chaque ligne concerne un utilisateur
- chaque ligne contient plusieurs informations
  - c'est comme un tableau la structure de ce fichier
  - les colonnes de chaque ligne sont indiquées par le caractère `:`

🌞 **Afficher la ligne du fichier qui concerne votre utilisateur**
```
naly@TPOS:~$ cat /etc/passwd | grep naly
naly:x:1000:1000:naly,,,:/home/naly:/bin/bash
```


🌞 **Afficher la ligne du fichier qui concerne votre utilisateur ET celle de `root` en même temps**
```
naly@TPOS:~$ cat /etc/passwd | grep -E "naly|root"
root:x:0:0:root:/root:/bin/bash
naly:x:1000:1000:naly,,,:/home/naly:/bin/bash
```


🌞 **Afficher la liste des groupes d'utilisateurs de la *machine***

```
naly@TPOS:~$ cat /etc/passwd |cut -d":" -f1
root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
proxy
www-data
backup
list
irc
_apt
nobody
systemd-network
systemd-timesync
messagebus
avahi-autoipd
dnsmasq
avahi
speech-dispatcher
pulse
saned
lightdm
polkitd
rtkit
colord
naly
sshd
marmotte
```

🌞 **Afficher la ligne du fichier qui concerne votre utilisateur ET celle de `root` en même temps**

```
naly@TPOS:~$ cut -d":" -f1,6 | grep -E "naly|root" /etc/passwd
root:x:0:0:root:/root:/bin/bash
naly:x:1000:1000:naly,,,:/home/naly:/bin/bash
```

## 2. Hash des passwords

Le *hash* des mots de passe des utilisateurs est stocké dans un fichier aussi : le fichier `/etc/shadow`.

🌞 **Afficher la ligne qui contient le hash du mot de passe de votre utilisateur**
```
naly@TPOS:~$ sudo cat /etc/shadow | grep naly
naly:$y$j9T$wBNvzilIsFv6PUFnqdqHk/$P/LoTmPgTeBRbX2Bw9Nl6pr.AKsLZItXLlpKcu5it78:20033:0:99999:7:::
```


## 3. Sudo

### A. Intro

**La *commande* `sudo` (*switch user do*) permet d'exécuter une *commande* en tant qu'un autre utilisateur** (c'est dans le nom *switch user do* pour "changer d'utilisateur et faire un truc").

La syntaxe :

```bash
# la tête de la ligne c'est
sudo -u USER COMMAND

# pour qu'on exécute la commande COMMANDE
# sous l'identité de l'utilisateur USER

# par exemple
sudo -u toto ls /etc
# exécute la commande ls /etc en tant que toto
```

On l'utilise généralement pour exécuter une *commande* en tant que `root` sans se connecter directement en tant que `root`, ce qui est utile pour faire des tâches d'administration qui demandent les droits de `root`.

> *Par exemple, installer des paquets avec une comande `apt install`, ça demande les privilèges de `root`.*

On l'utilise tellement souvent pour exécuter une commande en tant que  `root` (et pas quelqu'un d'autre) que si on précise pas d'utilisateur avec `-u`, c'est `root`  par défaut qui sera utilisé !

> *Donc taper `sudo ls` c'est pareil que `sudo -u root ls` et ça fait économiser pas mal de caractères à taper vu que c'est quasiment tout le temps ce qu'on veut faire ! (quasiment)*

**Le fichier `/etc/sudoers` contient la configuration de la commande `sudo`.**

On y définit quel utilisateur a le droit d'utiliser `sudo` pour devenir quel autre utilisateur afin de taper quelle commande.

> *On peut par exemple dire que `it4` n'a le droit de taper que la commande `echo meow` en tant que l'utilisateur `toto`. Autrement dit, la seule commande `sudo` que `it4` peut taper sans avoir d'erreur ce serait : `sudo -u toto echo meow`.*

### B. Practice

🌞 **Créer un groupe d'utilisateurs**
```
naly@TPOS:~$ sudo -u root groupadd stronk_admins
```


🌞 **Créer un utilisateur**
```
naly@TPOS:~$ sudo useradd -m imbob
naly@TPOS:~$ sudo usermod -aG imbob,stronk_admins imbob
naly@TPOS:~$ sudo passwd imbob
New password:
Retype new password:
passwd: password updated successfully
```

🌞 **Prouver que l'utilisateur `imbob` est créé**
```
naly@TPOS:~$ cat /etc/passwd |grep imbob
imbob:x:1002:1003::/home/imbob:/bin/sh
```


🌞 **Prouver que l'utilisateur `imbob` a un password défini**
```
naly@TPOS:~$ sudo cat /etc/shadow |grep imbob
imbob:$y$j9T$ArovoG/sTaOvhajMNBCkP1$3VZgIwnIL..CNtZNnFiuuW4Lk3yZFJC6lbPvGDulNZ9:20039:0:99999:7:::
```



🌞 **Prouver que l'utilisateur `imbob` appartient au groupe `stronk_admins`**
```
naly@TPOS:~$ sudo cat /etc/group | grep "stronk_admins"
stronk_admins:x:1002:imbob
```


🌞 **Créer un deuxième utilisateur**
```
naly@TPOS:~$ sudo useradd -m imnotbobsorry
naly@TPOS:~$ sudo passwd imnotbobsorry
New password:
Retype new password:
passwd: password updated successfully
naly@TPOS:~$ sudo usermod -aG imnotbobsorry imnotbobsorry
```


🌞 **Modifier la configuration de `sudo` pour que**

```
naly@TPOS:~$ sudo usermod -aG imnotbobsorry imnotbobsorry
naly@TPOS:~$ echo "%stronk_admins ALL=(ALL) NOPASSWD: /usr/bin/apt, /usr/bin/apt-get" | sudo tee -a /etc/sudoers
%stronk_admins ALL=(ALL) NOPASSWD: /usr/bin/apt, /usr/bin/apt-get
naly@TPOS:~$ echo "imbob ALL=(ALL) NOPASSWD: ALL" | sudo tee -a /etc/sudoers
imbob ALL=(ALL) NOPASSWD: ALL
```



🌞 **Créer le dossier `/home/goodguy`** (avec une commande)
```
naly@TPOS:~$ sudo mkdir /home/goodguy
```

🌞 **Changer le répertoire personnel de `imbob`**
```
naly@TPOS:~$ sudo usermod -d /home/goodguy imbob
[sudo] password for naly:
naly@TPOS:~$ cat /etc/passwd | grep imbob
imbob:x:1002:1003::/home/goodguy:/bin/sh
```
🌞 **Créer le dossier `/home/badguy`**
```
naly@TPOS:~$ sudo mkdir /home/badguy
```
🌞 **Changer le répertoire personnel de `imnotbobsorry`**
```
naly@TPOS:~$ sudo mkdir /home/badguy
naly@TPOS:~$ sudo usermod -d /home/badguy imnotbobsorry
naly@TPOS:~$ cat /etc/passwd | grep imnotbobsorry
imnotbobsorry:x:1003:1004::/home/badguy:/bin/sh
```
**Prouvez que les permissions sont incohérentes**

```
naly@TPOS:~$ ls -ld /home/goodguy
drwxr-xr-x 2 root root 4096 Nov 12 10:26 /home/goodguy
naly@TPOS:~$ grep imbob /etc/passwd
imbob:x:1002:1003::/home/goodguy:/bin/sh
naly@TPOS:~$ sudo chown imbob:imbob /home/goodguy
naly@TPOS:~$ sudo su - imbob
touch /home/goodguy/testfile
$ $
```

🌞 **Modifier les permissions de `/home/goodguy`**
```
naly@TPOS:/home/goodguy$ ls -l /home/goodguy
total 0
-rw-r--r-- 1 imbob imbob 0 Nov 12 10:43 testfile
```



🌞 **Modifier les permissions de `/home/badguy`**
```
naly@TPOS:~$ sudo chown -R imnotbobsorry:imnotbobsorry /home/badguy
naly@TPOS:~$ ls -l /home/badguy
total 0
-rw-r--r-- 1 imnotbobsorry imnotbobsorry 0 Nov 12 10:51 testfile
```


🌞 **Connectez-vous sur l'utilisateur `imbob`**
```
naly@TPOS:~$ sudo su - imbob
$ pwd
/home/goodguy
$ sudo echo meow
meow
```
🌞 **Connectez-vous sur l'utilisateur `imnotbobsorry`**
```
naly@TPOS:/home/badguy$ su - imnotbobsorry
Password:
$ bash
imnotbobsorry@TPOS:~$ pwd
/home/badguy
imnotbobsorry@TPOS:~$ sudo apt update
[sudo] password for imnotbobsorry:
Hit:1 http://security.debian.org/debian-security bookworm-security InRelease
Hit:2 http://deb.debian.org/debian bookworm InRelease
Hit:3 http://deb.debian.org/debian bookworm-updates InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
```



