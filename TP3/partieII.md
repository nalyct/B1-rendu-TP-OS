# II. Processes

- [II. Processes](#ii-processes)
  - [1. Jouer avec la commande ps](#1-jouer-avec-la-commande-ps)
  - [2. Parent, enfant, et meurtre](#2-parent-enfant-et-meurtre)

## 1. Jouer avec la commande ps

La commande `ps` permet de lister les *[processus](../../cours/memo/glossary.md#processus)* en cours d'exécution sur la machine. Elle possède plein d'options pour affiner l'affichage.

Quand on veut juste la liste de tout, on tape généralement `ps -ef`.

On va se servir de la commande `ps` pour faire mumuse avec le terminal, en affichant des trucs pouvant être utiles dans la vraie vie.

🌞 **Affichez les processus `bash`**

```
naly@TPOS:/$ ps -ef |grep bash
naly        1131    1106  0 01:00 pts/0    00:00:00 bash
naly        2464    1106  0 03:57 pts/2    00:00:00 bash
naly       33775   33771  0 10:32 pts/1    00:00:00 -bash
naly       33847   33846  0 10:44 pts/3    00:00:00 bash
naly       33923   33922  0 10:57 pts/5    00:00:00 bash
naly       34184   34183  0 11:00 pts/5    00:00:00 bash
naly       34196   34195  0 11:01 pts/5    00:00:00 bash
naly       34227   34226  0 11:19 pts/5    00:00:00 bash
imnotbo+   34298   34295  0 11:43 pts/5    00:00:00 bash
naly       34309   34308  0 11:45 pts/5    00:00:00 bash
imnotbo+   34322   34321  0 11:45 pts/5    00:00:00 bash
naly       34584   34583  0 11:50 pts/5    00:00:00 bash
naly       34593   34584 33 11:55 pts/5    00:00:00 grep bash
```

🌞 **Affichez tous les processus lancés par votre utilisateur**
```
naly@TPOS:/$ ps -ef |grep ^naly
naly         706       1  0 00:59 ?        00:00:00 /lib/systemd/systemd --user
naly         707     706  0 00:59 ?        00:00:00 (sd-pam)
naly         722     706  0 00:59 ?        00:00:00 /usr/bin/pulseaudio --daemonize=no --log-target=journal
naly         724     706  0 01:00 ?        00:00:00 /usr/bin/gnome-keyring-daemon --foreground --components=pkcs11,secrets --control-directory=/run/user/1000/keyring
naly         728     706  0 01:00 ?        00:00:14 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
naly         732     701  0 01:00 ?        00:00:00 xfce4-session
naly         780     732  0 01:00 ?        00:00:01 /usr/bin/ssh-agent x-session-manager
naly         790     706  0 01:00 ?        00:00:00 /usr/libexec/at-spi-bus-launcher
naly         796     790  0 01:00 ?        00:00:00 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 11 --address=unix:path=/run/user/1000/at-spi/bus_0
naly         806     706  0 01:00 ?        00:00:00 /usr/libexec/at-spi2-registryd --use-gnome-session
naly         816     706  0 01:00 ?        00:00:00 /usr/bin/gpg-agent --supervised
naly         818     732  0 01:00 ?        00:00:07 xfwm4
naly         821     706  0 01:00 ?        00:00:00 /usr/libexec/gvfsd
naly         833     732  0 01:00 ?        00:00:01 xfsettingsd
naly         842     732  0 01:00 ?        00:00:11 xfce4-panel
naly         846     732  0 01:00 ?        00:00:06 Thunar --daemon
naly         851     732  0 01:00 ?        00:00:03 xfdesktop
naly         854     842  0 01:00 ?        00:00:01 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 6 16777228 systray Status Tray Plugin Provides status notifier items (application indicators) and legacy systray items
naly         855     732  0 01:00 ?        00:00:01 light-locker
naly         857     842  0 01:00 ?        00:00:54 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libpulseaudio-plugin.so 8 16777229 pulseaudio PulseAudio Plugin Adjust the audio volume of the PulseAudio sound system
naly         859     842  0 01:00 ?        00:00:09 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libxfce4powermanager.so 9 16777230 power-manager-plugin Power Manager Plugin Display the battery levels of your devices and control the brightness of your display
naly         861     842  0 01:00 ?        00:00:01 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libnotification-plugin.so 10 16777231 notification-plugin Notification Plugin Notification plugin for the Xfce panel
naly         862     732  0 01:00 ?        00:00:02 xfce4-power-manager
naly         866     732  0 01:00 ?        00:00:03 /usr/lib/x86_64-linux-gnu/xfce4/notifyd/xfce4-notifyd
naly         867     732  0 01:00 ?        00:00:00 /usr/bin/python3 /usr/share/system-config-printer/applet.py
naly         869     732  0 01:00 ?        00:00:01 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
naly         871     732  0 01:00 ?        00:00:01 nm-applet
naly         873     732  0 01:00 ?        00:00:00 xiccd
naly         874     706  0 01:00 ?        00:00:00 /usr/libexec/gvfs-udisks2-volume-monitor
naly         885     821  0 01:00 ?        00:00:00 /usr/libexec/gvfsd-trash --spawner :1.14 /org/gtk/gvfs/exec_spaw/0
naly         892     706  0 01:00 ?        00:00:00 /usr/libexec/gvfsd-metadata
naly         899     706  0 01:00 ?        00:00:00 /usr/libexec/dconf-service
naly         922     842  0 01:00 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libactions.so 14 16777232 actions Action Buttons Log out, lock or other system actions
naly        1106       1  0 01:00 ?        00:00:03 xfce4-terminal
naly        1131    1106  0 01:00 pts/0    00:00:00 bash
naly        2452     821  0 03:56 ?        00:00:00 /usr/libexec/gvfsd-computer --spawner :1.14 /org/gtk/gvfs/exec_spaw/1
naly        2464    1106  0 03:57 pts/2    00:00:00 bash
naly       33771   33762  0 10:32 ?        00:00:04 sshd: naly@pts/1
naly       33775   33771  0 10:32 pts/1    00:00:00 -bash
naly       33847   33846  0 10:44 pts/3    00:00:00 bash
naly       33923   33922  0 10:57 pts/5    00:00:00 bash
naly       34184   34183  0 11:00 pts/5    00:00:00 bash
naly       34196   34195  0 11:01 pts/5    00:00:00 bash
naly       34227   34226  0 11:19 pts/5    00:00:00 bash
naly       34309   34308  0 11:45 pts/5    00:00:00 bash
naly       34584   34583  0 11:50 pts/5    00:00:00 bash
naly       34598     706  0 12:00 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
naly       34619   34584 99 12:03 pts/5    00:00:00 ps -ef
naly       34620   34584 33 12:03 pts/5    00:00:00 grep ^naly
```



🌞 **Affichez le top 5 des processus qui utilisent le plus de RAM**
```
naly@TPOS:/$ ps -ef --sort=-%mem | head -n 6
UID          PID    PPID  C STIME TTY          TIME CMD
root         612     598  0 00:59 tty7     00:00:34 /usr/lib/xorg/Xorg :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
lightdm     2553    2518  0 04:03 ?        00:00:25 /usr/sbin/lightdm-gtk-greeter
naly         818     732  0 01:00 ?        00:00:07 xfwm4
root        2493     598  0 04:03 tty8     00:00:06 /usr/lib/xorg/Xorg :1 -seat seat0 -auth /var/run/lightdm/root/:1 -nolisten tcp vt8 -novtswitch
naly         851     732  0 01:00 ?        00:00:03 xfdesktop
```



> Pour rappel, la ***[RAM](../../cours/memo/glossary.md#ram)*** ou *mémoire vive* joue un rôle crucial dans le fonctionnement d'une *[machine](../../cours/memo/glossary.md#machine)*. Si la *RAM* est complètement pleine, c'est simple : la *machine* freeze et il n'y aucune remédiation... à part la débrancher électriquement et la rebrancher... L'OS fait tout pour que ça n'arrive pas et n'hésitera pas à fermer arbitrairement des *processus* en cours d'exécution si la *RAM* s'apprête à être pleine et que ça met en danger la *machine* ! La fermeture de League of Legends sera priorisée par rapport à un *processus* nécessaire à l'OS évidemment !

🌞 **Affichez le *PID* du processus du service SSH**
```
naly@TPOS:/$ ps -C sshd |head -n 2
    PID TTY          TIME CMD
    616 ?        00:00:00 sshd
```


> Un *programme* un peu complexe fait souvent ça : il lance plusieurs *processus* plus ou moins indépendants pendant son fonctionnement. C'est le cas des navigateurs web par exemple : un *processus* est lancé pour chaque onglet ouvert ! Chaque onglet ouvert, utilisé ou non, c'est un peu de performances perdues... En *RAM*, en *[CPU](../../cours/memo/glossary.md#cpu)*, et aussi juste le fait de gérer un *processus* de +, ça fait perdre du temps !

🌞 **Affichez le nom du processus avec l'identifiant le plus petit**

```
naly@TPOS:/$ ps --sort=pid -eo pid | head -n 2
    PID
      1
```

> Rappelez-vous que les *processus* forment une arborescence : quand on lance un nouveau *programme*, on le fait toujours depuis un *[programme](../../cours/memo/glossary.md#programme)* existant, qui est déjà en cours d'exécution. Ainsi, le nouveau *programme* lancé devient un ***processus* *enfant*** du premier *programme* (qui lui est le ***processus* *parent***). Le *processus* qui a le plus petit identifiant est le père des premiers *programmes* lancés par l'OS !

## 2. Parent, enfant, et meurtre

Quand on lance un *programme* on le fait toujours depuis un *processus* déjà en cours d'exécution. Genre quand on double-clique sur l'icone de Firefox pour le lancer, on le fait depuis l'interface graphique de l'OS, qui est un *processus* en cours d'exécution.

On dit alors que le nouveau *processus* lancé est l'enfant du *programme* qui le lance (lui est le *processus parent*).

🌞 **Déterminer le *PID* de votre shell actuel**
```
naly@TPOS:/$ echo $$
34584
```


🌞 **Déterminer le *PPID* de votre shell actuel**
```
naly@TPOS:/$ ps -ef | grep $$ | head -n 1
naly       34584   34583  0 11:50 pts/5    00:00:00 b
```


🌞 **Déterminer le nom de ce *processus***
```
naly@TPOS:/$ ps -p $(ps -p $$ -o ppid=) -o comm=
su
```


🌞 **Lancer un *processus* `sleep 9999` en tâche de fond**
 ```
 naly@TPOS:/$ sleep 9999 &
[1] 35026
naly@TPOS:/$ ps -ef | grep sleep | head -n 1
naly       35026   34584  0 22:21 pts/5    00:00:00 sleep 9999
naly@TPOS:/$ echo $$
34584
 ```

🌞 **Fermez votre session SSH**
```
naly@TPOS:~$ ps -ef | grep sleep
naly       35026       1  0 08:42 ?        00:00:00 sleep 9999
naly       35121   35101 23 08:53 pts/1    00:00:00 grep sleep
```
-> le processus sleep lancé en tâche de fond s'éxécute toujours.


> Un *parent* ne laisserait quand même pas ses *enfants* seuls voyons ? Qui ferait ça ? Si un *parent* est amené à mourir, il fait ce que tout bon *parent* fait : il tue ses *enfants*.

![Process](./img/kill_process.png)

➜ **Pour les curieux, un ptit trick**

- si un *processus* n'a plus de parent, on dit qu'il est orphelin
- ça arrive parfois plus ou moins dans des cas légitimes, quand le *processus* parent crash par exemple
- un orphelin se fait immédiatement adopté ! Par l'OS lui-même (le ptit privilégié woaw)
- ptit trick bash pour créer un *processus* orphelin ('vais pas expliquer les détails de la syntaxe ici meow)

```bash
( ( sleep 9999) & )
```

- si tu fais un `ps` tu verras que le *processus* est bien orphelin car il a été adopté par un process qui porte un PID très élevé, et pas n'importe lequel hehe !
