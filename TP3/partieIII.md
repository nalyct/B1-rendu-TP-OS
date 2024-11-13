# III. Services

- [III. Services](#iii-services)
  - [1. Intro](#1-intro)
  - [2. Analyser un service existant](#2-analyser-un-service-existant)
  - [3. Modification du service](#3-modification-du-service)
    - [A. Configuration du service SSH](#a-configuration-du-service-ssh)
    - [B. Le service en lui-même](#b-le-service-en-lui-même)
  - [4. Créez votre propre service](#4-créez-votre-propre-service)

## 1. Intro

Dernière partie du TP pour s'attarder un peu sur la notion de *service*.

Un *service* c'est juste un [*programme*](../../cours/memo/glossary.md#programme) lancé par l'OS. C'est à dire que c'est un *programme* que l'utilisateur n'a pas besoin de lancer à la main.

Parfois certains *programmes* sont juste chiants à lancer à la main (de longues lignes de commande), parfois c'est juste pratique d'avoir tel ou tel *programme* que l'OS s'occupe de lancer automatiquement quand la [*machine*](../../cours/memo/glossary.md#machine) s'allume. Parfois aussi on aimerait bien qu'un *programme* soit automatiquement relancé s'il s'arrête, peu importe la raison.

Créer un *service* permet de résoudre ce genre de problèmes : on demande à l'OS de lancer un *programme*.

Sur les systèmes Linux, la commande pour interagir avec les services c'est `systemctl`, et `journalctl` pour voir les logs :

```bash
# obtenir l'état d'un service
systemctl status <SERVICE>
# par exemple, pour obtenir l'état du service SSH
systemctl status ssh

# démarrer un service
systemctl start <SERVICE>

# stopper un service
systemctl stop <SERVICE>

# voir tous les logs d'un service
journalctl -xe -u <SERVICE>
```

> Les *logs* c'est un fichier texte dans lequel un *programme* écrit tout ce qu'il fait. Il écrit la date et l'heure de chaque action qu'il fait. Ainsi on peut retracer toutes les actions qui ont été faites par un *programme* donné en regardant dans ses *logs*. Si le programme produit un erreur, on peut obtenir les détails de ce qui a cause l'erreur en lisant les *logs*.

## 2. Analyser un service existant


🌞 **S'assurer que le service `ssh` est démarré**
```
naly@TPOS:~$ systemctl status
● TPOS
    State: running
    Units: 273 loaded (incl. loaded aliases)
     Jobs: 0 queued
   Failed: 0 units
    Since: Mon 2024-11-11 13:21:03 CET; 1 day 19h ago
  systemd: 252.31-1~deb12u1
   CGroup: /
           ├─init.scope
           │ └─1 /lib/systemd/systemd --system --deserialize=35
           ├─system.slice
           │ ├─ModemManager.service
           │ │ └─459 /usr/sbin/ModemManager
           │ ├─NetworkManager.service
           │ │ └─447 /usr/sbin/NetworkManager --no-daemon
           │ ├─avahi-daemon.service
           │ │ ├─415 "avahi-daemon: running [TPOS.local]"
           │ │ └─440 "avahi-daemon: chroot helper"
           │ ├─colord.service
           │ │ └─913 /usr/libexec/colord
           │ ├─cron.service
           │ │ └─418 /usr/sbin/cron -f
           │ ├─cups-browsed.service
           │ │ └─609 /usr/sbin/cups-browsed
           │ ├─cups.service
           │ │ └─593 /usr/sbin/cupsd -l
           │ ├─dbus.service
           │ │ └─419 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslo>
           │ ├─lightdm.service
lines 1-29
```
```
naly@TPOS:~$ sudo systemctl list-units -t service -a
[sudo] password for naly:
  UNIT                                  LOAD      ACTIVE   SUB     DESCRIPTION                                         >
  anacron.service                       loaded    inactive dead    Run anacron jobs
  apparmor.service                      loaded    active   exited  Load AppArmor profiles
  apt-daily-upgrade.service             loaded    inactive dead    Daily apt upgrade and clean activities
  apt-daily.service                     loaded    inactive dead    Daily apt download activities
● auditd.service                        not-found inactive dead    auditd.service
  avahi-daemon.service                  loaded    active   running Avahi mDNS/DNS-SD Stack
  colord.service                        loaded    active   running Manage, Install and Generate Color Profiles
● connman.service                       not-found inactive dead    connman.service
● console-screen.service                not-found inactive dead    console-screen.service
  console-setup.service                 loaded    active   exited  Set console font and keymap
  cron.service                          loaded    active   running Regular background program processing daemon
  cups-browsed.service                  loaded    active   running Make remote CUPS printers available locally
  cups.service                          loaded    active   running CUPS Scheduler
  dbus.service                          loaded    active   running D-Bus System Message Bus
  dpkg-db-backup.service                loaded    inactive dead    Daily dpkg database backup service
  e2scrub_all.service                   loaded    inactive dead    Online ext4 Metadata Check for All Filesystems
  e2scrub_reap.service                  loaded    inactive dead    Remove Stale Online ext4 Metadata Check Snapshots
  emergency.service                     loaded    inactive dead    Emergency Shell
  fstrim.service                        loaded    inactive dead    Discard unused blocks on filesystems from /etc/fstab
  getty-static.service                  loaded    inactive dead    getty on tty2-tty6 if dbus and logind are not availa>
  getty@tty1.service                    loaded    active   running Getty on tty1
  ifupdown-pre.service                  loaded    active   exited  Helper to synchronize boot up for ifupdown
  initrd-cleanup.service                loaded    inactive dead    Cleaning Up and Shutting Down Daemons
  initrd-parse-etc.service              loaded    inactive dead    Mountpoints Configured in the Real Root
  initrd-switch-root.service            loaded    inactive dead    Switch Root
  initrd-udevadm-cleanup-db.service     loaded    inactive dead    Cleanup udev Database
● kbd.service                           not-found inactive dead    kbd.service
  keyboard-setup.service                loaded    active   exited  Set the console keyboard layout
lines 1-29
```

🌞 **Isolez la ligne qui indique le nom du programme lancé**
```
naly@TPOS:~$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Mon 2024-11-11 13:21:16 CET; 1 day 19h ago
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 616 (sshd)
      Tasks: 1 (limit: 1982)
     Memory: 8.2M
        CPU: 8.287s
     CGroup: /system.slice/ssh.service
             └─616 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

Warning: some journal files were not opened due to insufficient permissions.
naly@TPOS:~$ systemctl status ssh | grep "Main PID"
   Main PID: 616 (sshd)
   ```

🌞 **Déterminer le port sur lequel écoute le service SSH**
```
naly@TPOS:~$ sudo ss -lnpt | grep 'sshd'
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=616,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=616,fd=4))
```
 

🌞 **Consulter les logs du service SSH**
```
naly@TPOS:~$ journalctl |grep "sshd"
Hint: You are currently not seeing messages from other users and the system.
      Users in groups 'adm', 'systemd-journal' can see all messages.
      Pass -q to turn off this notice.
Nov 11 13:32:28 TPOS sshd[1382]: Received disconnect from 192.168.29.1 port 64970:11: disconnected by user
Nov 11 13:32:28 TPOS sshd[1382]: Disconnected from user naly 192.168.29.1 port 64970
Nov 11 15:32:19 TPOS sshd[1588]: Received disconnect from 192.168.29.1 port 65072:11: disconnected by user
Nov 11 15:32:19 TPOS sshd[1588]: Disconnected from user naly 192.168.29.1 port 65072
Nov 11 15:42:36 TPOS sshd[1989]: Received disconnect from 192.168.29.1 port 49739:11: disconnected by user
Nov 11 15:42:36 TPOS sshd[1989]: Disconnected from user naly 192.168.29.1 port 49739
Nov 12 09:11:08 TPOS sshd[1961]: Received disconnect from 192.168.29.1 port 49715:11: disconnected by user
Nov 12 09:11:08 TPOS sshd[1961]: Disconnected from user naly 192.168.29.1 port 49715
Nov 12 10:32:21 TPOS sshd[33190]: Received disconnect from 192.168.29.1 port 62175:11: disconnected by user
Nov 12 10:32:21 TPOS sshd[33190]: Disconnected from user naly 192.168.29.1 port 62175
Nov 12 22:27:58 TPOS sshd[33771]: Received disconnect from 192.168.29.1 port 62627:11: disconnected by user
Nov 12 22:27:58 TPOS sshd[33771]: Disconnected from user naly 192.168.29.1 port 62627
Nov 13 09:15:07 TPOS sudo[35179]:     naly : TTY=pts/1 ; PWD=/home/naly ; USER=root ; COMMAND=/usr/bin/journalctl -u sshd
```

## 3. Modification du service


### A. Configuration du service SSH


🌞 **Identifier le fichier de configuration du serveur SSH**
```
naly@TPOS:~$ ls -l /etc/ssh/sshd_config
-rw-r--r-- 1 root root 3223 Jun 22 21:38 /etc/ssh/sshd_config
```
🌞 **Modifier le fichier de conf**
```
naly@TPOS:~$ echo $RANDOM
31056
naly@TPOS:~$ sudo nano /etc/ssh/sshd_config
naly@TPOS:~$ cat /etc/ssh/sshd_config | grep "Port"
Port 31056
#GatewayPorts no
```

🌞 **Redémarrer le service**
```
naly@TPOS:~$ systemctl restart sshd
```


🌞 **Effectuer une connexion SSH sur le nouveau port**
```
naly@TPOS:~$ sudo ss -lnpt | grep sshd
LISTEN 0      128          0.0.0.0:31056      0.0.0.0:*    users:(("sshd",pid=35220,fd=3))
LISTEN 0      128             [::]:31056         [::]:*    users:(("sshd",pid=35220,fd=4))
naly@TPOS:~$ ssh -p 31056 naly@192.168.29.2
The authenticity of host '[192.168.29.2]:31056 ([192.168.29.2]:31056)' can't be established.
ED25519 key fingerprint is SHA256:T7PaSD073glVen8lpUVH+Lbuhg1lF0ifzmK4XX4pWi8.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? YES
Warning: Permanently added '[192.168.29.2]:31056' (ED25519) to the list of known hosts.
naly@192.168.29.2's password:
Linux TPOS 6.1.0-26-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.112-1 (2024-09-30) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Wed Nov 13 08:51:27 2024 from 192.168.29.1
naly@TPOS:~$
```

✨ **Bonus : affiner la conf du serveur SSH**

- faites vos plus belles recherches internet pour améliorer la conf de SSH
- par "améliorer" on entend essentiellement ici : augmenter son niveau de sécurité
- le but c'est pas de me rendre 10000 lignes de conf que vous pompez sur internet pour le bonus, mais de vous éveiller à divers aspects de SSH, la sécu ou d'autres choses liées

![Such a hacker](./img/such_a_hacker.png)

### B. Le service en lui-même


🌞 **Trouver le fichier `ssh.service`**
```
naly@TPOS:~$ systemctl show -p FragmentPath ssh.service
FragmentPath=/lib/systemd/system/ssh.service
```

🌞 **Déterminer quel est le programme lancé**
```
naly@TPOS:~$ systemctl show ssh.service -p ExecStart
ExecStart={ path=/usr/sbin/sshd ; argv[]=/usr/sbin/sshd -D $SSHD_OPTS ; ignore_errors=no ; start_time=[Wed 2024-11-13 0>
lines 1-1/1 (END)
```


## 4. Créez votre propre service

➜ On va se servir d'une petite commande pratique pour mettre ça en oeuvre, faites un petit test d'abord :
```
naly@TPOS:~$ echo "meow" > meow
naly@TPOS:~$ python3 -m http.server 8888
Serving HTTP on 0.0.0.0 port 8888 (http://0.0.0.0:8888/) ...
192.168.29.1 - - [13/Nov/2024 09:38:46] "GET / HTTP/1.1" 200 -
192.168.29.1 - - [13/Nov/2024 09:38:46] code 404, message File not found
192.168.29.1 - - [13/Nov/2024 09:38:46] "GET /favicon.ico HTTP/1.1" 404 -

```



🌞 **Déterminer le dossier qui contient la commande `python3`**
```
naly@TPOS:~$ which python3
/usr/bin/python3
```


🌞 **Créez un fichier `/etc/systemd/system/meow_web.service`**
```
naly@TPOS:~$ sudo nano /etc/systemd/system/meow_web.service
naly@TPOS:~$ sudo systemctl start meow_web
naly@TPOS:~$ sudo systemctl enable meow_web
Created symlink /etc/systemd/system/multi-user.target.wants/meow_web.service → /etc/systemd/system/meow_web.service.
```



🌞 **Indiquez à l'OS que vous avez modifié les *services***
```
naly@TPOS:~$ sudo systemctl daemon-reload
```


🌞 **Démarrez votre service**
```
naly@TPOS:~$ systemctl start meow_web
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ====
Authentication is required to start 'meow_web.service'.
Multiple identities can be used for authentication:
 1.  naly,,, (naly)
 2.  imnotbobsorry
Choose identity to authenticate as (1-2): 1
Password:
==== AUTHENTICATION COMPLETE ====
```

🌞 **Assurez-vous que le service `meow_web` est actif**
```
naly@TPOS:~$ systemctl status meow_web
● meow_web.service - Super serveur web MEOW
     Loaded: loaded (/etc/systemd/system/meow_web.service; enabled; preset: enabled)
     Active: active (running) since Wed 2024-11-13 09:44:00 CET; 4min 40s ago
   Main PID: 35310 (python3)
      Tasks: 1 (limit: 1982)
     Memory: 9.0M
        CPU: 599ms
     CGroup: /system.slice/meow_web.service
             └─35310 /usr/bin/python3 -m http.server 8888
 ```

🌞 **Déterminer le PID du *processus* Python en cours d'exécution**
```
naly@TPOS:~$ ps -ef | grep '[p]ython3 -m http.server 8888'
root       35310       1  0 09:44 ?        00:00:02 /usr/bin/python3 -m http.server 8888
```


🌞 **Prouvez que le *programme* écoute derrière le port 8888**
```
naly@TPOS:~$ sudo ss -lnpt | grep 'python3' | grep ':8888'
LISTEN 0      5            0.0.0.0:8888       0.0.0.0:*    users:(("python3",pid=35310,fd=3))
```


🌞 **Faire en sote que le *service* se lance automatiquement au démarrage de la machine**
```
naly@TPOS:~$ sudo systemctl enable meow_web
```



