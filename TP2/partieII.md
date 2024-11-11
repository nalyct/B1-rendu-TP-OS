# III. Programmes et paquets

Une partie qui s'intéresse aux *programmes* au sens large.

➜ **Quand on exécute un *programme* on dit qu'on lance un *processus*.**

Un *processus* c'est donc juste un *programme* en cours d'exécution.

Les "commandes" du terminal, c'est des *programmes* hein !

> *C'est à dire qu'il a été déplacé en RAM et que le kernel ordonne au CPU d'exécuter les instructions que le programme contient.*

➜ En tant qu'utilisateur on peut facilement, depuis le terminal :

- voir la liste des *processus*
- interagir avec eux (pour les stopper par exemple)
- lancer un *processus* en tâche de fond

➜ **De plus, tout système Linux vient avec un *gestionnaire de paquets*.**

C'est une commande qui permet d'ajouter des nouveaux trucs au système, notamment des nouveaux *programmes*. C'est un app store avant l'heure quoi ! Utilisable en ligne de commande !

> On bénéficie d'une bien meilleure sécurité qu'en téléchargeant des *programmes* sur des sites internet chelous qui nous donnent des `.exe` chelous.

## Sommaire

- [III. Programmes et paquets](#iii-programmes-et-paquets)
  - [Sommaire](#sommaire)
- [1. Programmes et processus](#1-programmes-et-processus)
  - [A. Run then kill](#a-run-then-kill)
  - [B. Tâche de fond](#b-tâche-de-fond)
  - [C. Find paths](#c-find-paths)
  - [D. La variable PATH](#d-la-variable-path)
- [2. Paquets](#2-paquets)

# 1. Programmes et processus

➜ Dans cette partie, afin d'avoir quelque chose à étudier, on va utiliser le programme `sleep`

- c'est une commande (= un *programme*) dispo sur tous les OS
- ça permet de... ne rien faire pendant X secondes
- la syntaxe c'est `sleep 90` pour attendre 90 secondes
- on s'en fout de `sleep` en doit, c'est une commande utile parmi plein d'autres, elle est pratique pour étudier les trucs que j'veux vous montrer

## A. Run then kill

🌞 **Lancer un processus `sleep`**
```
naly@TPOS:~$ sleep 1000
```

> Le *PID* pour *Process IDentifier* c'est un ID unique attribué à chaque process lancé. Chaque processus, on lui attribue un numéro quoi.

🌞 **Terminez le processus `sleep` depuis le deuxième terminal**
```
naly@TPOS:~$ ps -fe | grep sleep
naly        1977    1965  0 15:36 pts/1    00:00:00 sleep 1000
naly        2007    1993 40 15:38 pts/2    00:00:00 grep sleep
naly@TPOS:~$ kill
naly@TPOS:~$ kill 1977
```
**Dans l'autre terminal :** 

```

Terminated
naly@TPOS:~$
```


## B. Tâche de fond

🌞 **Lancer un nouveau processus `sleep`, mais en tâche de fond**
```
naly@TPOS:~$ sleep 1000 &
[1] 2161

```
🌞 **Visualisez la commande en tâche de fond**
```
naly@TPOS:~$ ps -fe | grep sleep
naly        2161    1965  0 15:43 pts/1    00:00:00 sleep 1000
naly        2163    1965 50 15:44 pts/1    00:00:00 grep sleep
```
Son PID : 2161


## C. Find paths

➜ La commande `sleep`, comme toutes les commandes, c'est un programme

- sous Linux, on met pas l'extension `.exe`, s'il y a pas d'extensions, c'est que c'est un exécutable généralement

🌞 **Trouver le chemin où est stocké le programme `sleep`**

```
root@TPOS:~#  find / -name "sleep"
/usr/bin/sleep
/usr/lib/klibc/bin/sleep
```

🌞 Tant qu'on est à chercher des chemins : **trouver les chemins vers tous les fichiers qui s'appellent `.bashrc`**
```
root@TPOS:~#  find / -name "*.bashrc"
/etc/skel/.bashrc
/etc/bash.bashrc
/usr/share/base-files/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/root/.bashrc
/home/naly/.bashrc
/home/marmotte/.bashrc
find: ‘/proc/2013’: No such file or directory
```


## D. La variable PATH

**Sur tous les OS (MacOS, Windows, Linux, et autres) il existe une variable `PATH` qui est définie quand l'OS démarre.** Elle est accessible par toutes les applications qui seront lancées sur cette machine.

**On dit que `PATH` est une variable d'environnement.** C'est une variable définie par l'OS, et accessible par tous les programmes.

> *Il existe plein de variables d'environnement définie dès que l'OS démarre, `PATH` n'est pas la seule. On peut aussi en créer autant qu'on veut. Attention, suivant avec quel utilisateur on se connecte à une machine, les variables peuvent être différentes : parfait pour avoir chacun sa configuration !*

**`PATH` contient la liste de tous les dossiers qui contiennent des commandes/programmes.**

Ainsi quand on tape une commande comme `ls /home`, il se passe les choses suivantes :

- votre terminal consulte la valeur de la variable `PATH`
- parmi tous les dossiers listés dans cette variable, il cherche s'il y en a un qui contient un programme nommé `ls`
- si oui, il l'exécute
- sinon : `command not found`

Démonstration :

```bash
# on peut afficher la valeur de la variable PATH à n'importe quel moment dans un terminal
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/bin:/bin
# ça contient bien une liste de dossiers, séparés par le caractère ":"

# si la commande ls fonctionne c'est forcément qu'elle se trouve dans l'un de ces dossiers
# on peut savoir lequel avec la commande which qui interroge aussi la variable PATH
$ which ls
/usr/bin/ls
```

🌞 **Vérifier que**
```
root@TPOS:~#  find / -name "sleep"
/usr/bin/sleep
/usr/lib/klibc/bin/sleep
root@TPOS:~#  find / -name "ssh"
/run/user/107/gcr/ssh
/run/user/1000/gcr/ssh
/etc/runit/runsvdir/default/ssh
/etc/sv/ssh
/etc/default/ssh
/etc/ssh
/etc/init.d/ssh
/usr/share/runit/meta/ssh
/usr/share/bash-completion/completions/ssh
/usr/bin/ssh
/usr/lib/apt/methods/ssh
/var/log/runit/ssh
root@TPOS:~#  find / -name "ping"
/usr/share/bash-completion/completions/ping
/usr/bin/ping
```
```
root@TPOS:~# echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
```


# 2. Paquets

➜ **Tous les OS Linux sont munis d'un store d'application**

- c'est natif
- quand tu fais `apt install` ou `dnf install`, ce genre de commandes, t'utilises ce store
- on dit que `apt` et `dnf` sont des gestionnaires de paquets
- ça permet aux utilisateurs de télécharger des nouveaux programmes (ou d'autres trucs) depuis un endroit safe

🌞 **Installer le paquet `firefox`**

```
root@TPOS:~# apt install git
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  git-man liberror-perl patch
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui gitk gitweb git-cvs git-mediawiki git-svn ed
  diffutils-doc
The following NEW packages will be installed:
  git git-man liberror-perl patch
0 upgraded, 4 newly installed, 0 to remove and 60 not upgraded.
Need to get 9,467 kB of archives.
After this operation, 48.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://deb.debian.org/debian bookworm/main amd64 liberror-perl all 0.17029-2 [29.0 kB]
Get:2 http://deb.debian.org/debian bookworm/main amd64 git-man all 1:2.39.5-0+deb12u1 [2,054 kB]
Get:3 http://deb.debian.org/debian bookworm/main amd64 git amd64 1:2.39.5-0+deb12u1 [7,256 kB]
Get:4 http://deb.debian.org/debian bookworm/main amd64 patch amd64 2.7.6-7 [128 kB]
Fetched 9,467 kB in 2s (4,264 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 113588 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17029-2_all.deb ...
Unpacking liberror-perl (0.17029-2) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.39.5-0+deb12u1_all.deb ...
Unpacking git-man (1:2.39.5-0+deb12u1) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.39.5-0+deb12u1_amd64.deb ...
Unpacking git (1:2.39.5-0+deb12u1) ...
Selecting previously unselected package patch.
Preparing to unpack .../patch_2.7.6-7_amd64.deb ...
Unpacking patch (2.7.6-7) ...
Setting up liberror-perl (0.17029-2) ...
Setting up patch (2.7.6-7) ...
Setting up git-man (1:2.39.5-0+deb12u1) ...
Setting up git (1:2.39.5-0+deb12u1) ...
Processing triggers for man-db (2.11.2-2) ...
```

🌞 **Utiliser une commande pour lancer Firefox**
```
root@TPOS:~# firefox
Running Firefox as root in a regular user's session is not supported.  ($XDG_RUNTIME_DIR is /run/user/1000 which is owned by naly.)
```


🌞 **Mais aussi déterminer...**

```
root@TPOS:~# /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
```
