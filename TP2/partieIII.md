# IV. Poupée russe

Pour finir de vous exercer avec le terminal, je vous ai préparé une poupée russe :D

➜ **De mon côté, pour préparer l'exercice :**

- j'ai créé un dossier `dawa/`, qui a plein de sous-dossiers, sous-fichiers, etc
  - y'a des fichiers particuliers, les autres c'est juste du random
- je l'ai archivé/compressé plusieurs fois
- j'ai volontairement supprimé les extensions des fichiers compressés
  - comme ça tu peux pas savoir à l'aide du nom si c'est un `.zip` ou un autre format

➜ **Le but de l'exercice pour vous :**

- je vous file le fichier que j'ai compressé/archivé plusieurs fois, que vous téléchargez dans la VM
- vous devez :
  - déterminer le type du fichier
  - renommer le fichier correctement (si c'est une archive zip, il faut ajouter `.zip` à son nom)
  - extraire l'archive
  - répéter l'opération (car j'ai mis une archive, dans une archive, dans une archive... meow)
- bien sûr que c'est stupide
  - mais c'est pour vous faire pratiquer le terminal, et voir des commandes usuelles
- une fois que vous avez trouvé le dossier `dawa/`, vous avez fini le jeu de poupées russes
- vous allez devoir trouver les fichiers spécifiques que je vous demande à l'intérieur de ce dossier

🌞 **Récupérer le fichier `meow`**
```
root@TPOS:~# wget https://gitlab.com/it4lik/b1-os/-/blob/main/tp/é/meow
--2024-11-11 16:14:52--  https://gitlab.com/it4lik/b1-os/-/blob/main/tp/%C3%A9/meow
Resolving gitlab.com (gitlab.com)... 172.65.251.78, 2606:4700:90:0:f22e:fbec:5bed:a9b9
Connecting to gitlab.com (gitlab.com)|172.65.251.78|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://gitlab.com/it4lik/b1-os/-/tree/main [following]
--2024-11-11 16:14:53--  https://gitlab.com/it4lik/b1-os/-/tree/main
Reusing existing connection to gitlab.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 40775 (40K) [text/html]
Saving to: ‘meow’

meow                          100%[=================================================>]  39.82K  --.-KB/s    in 0.009s

2024-11-11 16:14:54 (4.45 MB/s) - ‘meow’ saved [40775/40775]
```


🌞 **Trouver le dossier `dawa/`**

```
root@TPOS:~# find . -name "meow"
./meow
root@TPOS:~# file ./meow
./meow: HTML document, Unicode text, UTF-8 text, with very long lines (11422)
```
```
root@TPOS:~# find / -name "meow.html"
/root/meow.html
root@TPOS:~# find / -name "dawa"
root@TPOS:~# find / -name "dawa/"
find: warning: ‘-name’ matches against basenames only, but the given pattern contains a directory separator (‘/’), thus the expression will evaluate to false all the time.  Did you mean ‘-wholename’?
```

🌞 **Dans le dossier `dawa/`, déterminer le chemin vers**



![Matryoshka](./img/dolls.png)
