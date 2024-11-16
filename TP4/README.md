# TP4 : Safé d partission

**TP autour du partitionnement !**
## Sommaire

- [TP4 : Safé d partission](#tp4--safé-d-partission)
  - [Sommaire](#sommaire)
  - [3. Vérification](#3-vérification)
  - [4. Taille et inodes](#4-taille-et-inodes)
- [II. Partitioning](#ii-partitioning)
  - [1. d disk partou](#1-d-disk-partou)
  - [2. Grow !](#2-grow-)
  - [3. Montage automatique](#3-montage-automatique)
  - [4. Bonus : options de montage](#4-bonus--options-de-montage)

## 3. Vérification

🌞 **Lister les périphériques de stockage branchés à la machine**



🌞 **Lister les partitions en cours d'utilisation**



## 4. Taille et inodes

🌞 **Lister la quantité d'*inodes* disponibles sur chaque partition**


🌞 **Déterminer la taille (avec `du`) et l'*inode* (avec `ls`) de chacun des fichiers suivants :**


# II. Partitioning

## 1. d disk partou


🌞 **Repérer le nom des nouveaux disques**


🌞 **Ajouter ces deux disques comme des PV LVM**

🌞 **Créer un VG nommé `cat`**



🌞 **Créer un LV nommé `meoooow`**



🌞 **Formater la partition (le LV) en autre chose que ext4**


🌞 **Créer le *point de montage* `/mnt/meow`**



🌞 **Monter la partition `meoooow` sur le point de montage que vous avez créé**

🌞 **Vérifier avec la commande adaptée que la partition est utilisable et qu'elle fait 3G**

## 2. Grow !

🌞 **Il reste 2G sur le disque dur principal**



🌞 **Prouvez en affichant la liste des partitions que la partition fait désormais 2G de plus**



🌞 **Agrandir la partition `meoooow` pour qu'elle occupe tout l'espace libre de son VG**

🌞 **Déterminer la taille de la nouvelle partition**



## 3. Montage automatique


🌞 **Modifier le fichier `/etc/fstab` pour que la partition soit montée `/mnt/meow` automatiquement**



## 4. Bonus : options de montage



⭐ **Déterminer quelles options de montage permettrait d'améliorer le niveau de sécurité des données contenues sur une partition.**
