 AUTOMATISATION DES TACHES
----------------------------------------------------------------------
# TP6 - installation et mise a jour de logiciels sauvegardes distantes
-----------------------------------------------------------------------
SILLAH SANKOU 
11/03/2026
-------------------------
**EXERCICE 1 - Paquets Debian**

***étape 1*** : 
```code
sankou@p20221:~$ sudo apt update

Nous espérons que vous avez reçu de votre administrateur système local
les consignes traditionnelles. Généralement, elles se concentrent sur ces trois éléments :

    #1) Respectez la vie privée des autres.
    #2) Réfléchissez avant d'utiliser le clavier.
    #3) De grands pouvoirs confèrent de grandes responsabilités.

[sudo] Mot de passe de sankou : 
Atteint :1 http://download.virtualbox.org/virtualbox/debian bullseye InRelease
Atteint :2 https://download.docker.com/linux/debian bullseye InRelease         
Atteint :3 http://security.debian.org/debian-security bullseye-security InRelease
Atteint :4 http://deb.debian.org/debian bullseye InRelease                     
Atteint :5 http://deb.debian.org/debian bullseye-updates InRelease    
Atteint :6 http://ppa.launchpad.net/gns3/ppa/ubuntu bionic InRelease  
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
431 paquets peuvent être mis à jour. Exécutez « apt list --upgradable » pour les voir.
```

***étape 2*** : Installer un paquet, ici on va prendre comme exemple curl 
```code
sankou@p20221:~$ sudo apt-get install curl
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Les paquets supplémentaires suivants seront installés : 
  libcurl4
```

***1- Combien de paquets sont-ils installés sur votre système ?***

Pour savoir combien de paquets sont installés sur mon système Debian, j’utilise la commande suivante :
```code
sankou@p20221:~$ dpkg -l | wc -l
1749
```
**Explication** : 
dpkg -l liste tous les paquets installés sur le système.
wc -l compte le nombre de lignes, ce qui me donne le nombre total de paquets installés.
Cela m'indique combien de paquets sont actuellement installés sur mon système Debian.

***2- Votre syst`eme est-il à jour ? Si non, mettez-le `a jour. Listez les paquets mis `a jour dans votre compte rendu.***

Pour vérifier si mon système est à jour, j'utilise la commande suivante :
```code
sankou@p20221:~$ sudo apt-get update
sankou@p20221:~$ sudo apt-get upgrade
```
**Explication** :

sudo apt-get update va interroger les serveurs de la distribution et télécharger la liste des paquets disponibles.
Ensuite, sudo apt-get upgrade mettra à jour les paquets installés vers les dernières versions disponibles.
Cela m'assure que tous mes paquets sont bien à jour. Si des paquets sont mis à jour, ils s'affichent dans la sortie de la commande apt-get upgrade.

***3- Quel paquet (non installée) fourni le logiciel LibreOffice Writer ?***

Pour savoir quel paquet contient le logiciel LibreOffice Writer, je fais une recherche dans les dépôts avec la commande suivante :
```code
sankou@p20221:~$ apt-cache search libreoffice-writer
libreoffice-writer - suite de productivité bureautique - traitement de texte
libreoffice-writer2latex - extension de conversion de Writer ou Calc vers LaTeX pour LibreOffice
libreoffice-writer2xhtml - extension de conversion de Writer ou Calc vers XHTML pour LibreOffice
libreoffice - office productivity suite (metapackage)
libreoffice-nogui - office productivity suite (metapackage, no GUI)
libreoffice-writer-nogui - office productivity suite -- word processor (no GUI variant)
```
**Explication** :

Cette commande va chercher tous les paquets correspondant à libreoffice-writer dans les dépôts.
Elle renverra le nom exact du paquet qui contient ce logiciel.
Dans ce cas, le paquet correspondant sera probablement libreoffice-writer, mais je le vérifie avec cette commande.

***4- Quels sont les d´ependances de ce paquet ?***

Pour connaître les dépendances du paquet LibreOffice Writer, j’utilise la commande suivante :
```code
sankou@p20221:~$ apt-cache showpkg libreoffice-writer
Package: libreoffice-writer
Versions: 
1:7.0.4-4+deb11u13 (/var/lib/apt/lists/security.debian.org_debian-security_dists_bullseye-security_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/deb.debian.org_debian_dists_bullseye_main_binary-amd64_Packages
                  MD5: 7ddf1a7be67dc22b315f212f564325e8
 Description Language: fr
                 File: /var/lib/apt/lists/deb.debian.org_debian_dists_bullseye_main_i18n_Translation-fr
                  MD5: 7ddf1a7be67dc22b315f212f564325e8
 Description Language: en
                 File: /var/lib/apt/lists/deb.debian.org_debian_dists_bullseye_main_i18n_Translation-en
                  MD5: 7ddf1a7be67dc22b315f212f564325e8
 Description Language: 
                 File: /var/lib/apt/lists/security.debian.org_debian-security_dists_bullseye-security_main_binary-amd64_Packages
                  MD5: 7ddf1a7be67dc22b315f212f564325e8

1:7.0.4-4+deb11u10 (/var/lib/apt/lists/deb.debian.org_debian_dists_bullseye_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/deb.debian.org_debian_dists_bullseye_main_binary-amd64_Packages
                  MD5: 7ddf1a7be67dc22b315f212f564325e8
 Description Language: fr
                 File: /var/lib/apt/lists/deb.debian.org_debian_dists_bullseye_main_i18n_Translation-fr
                  MD5: 7ddf1a7be67dc22b315f212f564325e8
 Description Language: en
                 File: /var/lib/apt/lists/deb.debian.org_debian_dists_bullseye_main_i18n_Translation-en
                  MD5: 7ddf1a7be67dc22b315f212f564325e8
 Description Language: 
                 File: /var/lib/apt/lists/security.debian.org_debian-security_dists_bullseye-security_main_binary-amd64_Packages
                  MD5: 7ddf1a7be67dc22b315f212f564325e8


Reverse Depends: 
  libreoffice-core,libreoffice-writer 1:7.0.4-4+deb11u13
  tryton-server,libreoffice-writer
  tryton-client,libreoffice-writer
  libreoffice-writer-nogui,libreoffice-writer
  libreoffice-writer-nogui,libreoffice-writer
  libreoffice-wiki-publisher,libreoffice-writer
  libreoffice-librelogo,libreoffice-writer
  libreoffice-core-nogui,libreoffice-writer 1:7.0.4-4+deb11u13
  libreoffice-common,libreoffice-writer 1:7.0.0~alpha~
  libreoffice-core,libreoffice-writer 1:7.0.0~alpha~
  libreoffice-common,libreoffice-writer 1:7.0.0~alpha~
  libreoffice-base-nogui,libreoffice-writer
  libreoffice-base,libreoffice-writer
  libreoffice,libreoffice-writer
  parl-desktop,libreoffice-writer
  writer2latex,libreoffice-writer
  libreoffice-writer2xhtml,libreoffice-writer
  libreoffice-writer2latex,libreoffice-writer
  unoconv,libreoffice-writer
  tryton-server,libreoffice-writer
  tryton-client,libreoffice-writer
  todo.txt-base,libreoffice-writer
  task-xfce-desktop,libreoffice-writer
  task-mate-desktop,libreoffice-writer
  task-lxqt-desktop,libreoffice-writer
  task-lxde-desktop,libreoffice-writer
  task-kde-desktop,libreoffice-writer
  task-gnome-flashback-desktop,libreoffice-writer
  task-gnome-desktop,libreoffice-writer
  hunspell-en-ca,libreoffice-writer
  hunspell-en-au,libreoffice-writer
  libreoffice-parlatype,libreoffice-writer
  hyphen-pl,libreoffice-writer
  mythes-en-au,libreoffice-writer
  gnome,libreoffice-writer
  lloconv,libreoffice-writer
  libreoffice-voikko,libreoffice-writer
  libreoffice-texmaths,libreoffice-writer
  mythes-uk,libreoffice-writer
  mythes-sv,libreoffice-writer
  mythes-sl,libreoffice-writer
  mythes-sk,libreoffice-writer
  mythes-ru,libreoffice-writer
  mythes-ro,libreoffice-writer
  mythes-pt-pt,libreoffice-writer
  mythes-no,libreoffice-writer
  mythes-ne,libreoffice-writer
  mythes-lv,libreoffice-writer
  mythes-it,libreoffice-writer
  mythes-is,libreoffice-writer
  mythes-id,libreoffice-writer
  mythes-hu,libreoffice-writer
  mythes-gug,libreoffice-writer
  mythes-gl,libreoffice-writer
  mythes-fr,libreoffice-writer
  mythes-es,libreoffice-writer
  mythes-en-us,libreoffice-writer
  mythes-da,libreoffice-writer
  mythes-cs,libreoffice-writer
  mythes-ca,libreoffice-writer
  mythes-bg,libreoffice-writer
  mythes-ar,libreoffice-writer
  hyphen-zu,libreoffice-writer
  hyphen-uk,libreoffice-writer
  hyphen-sv,libreoffice-writer
  hyphen-sr,libreoffice-writer
  hyphen-sl,libreoffice-writer
  hyphen-sk,libreoffice-writer
  hyphen-ro,libreoffice-writer
  hyphen-pt-pt,libreoffice-writer
  hyphen-pt-br,libreoffice-writer
  hyphen-no,libreoffice-writer
  hyphen-nl,libreoffice-writer
  hyphen-lt,libreoffice-writer
  hyphen-it,libreoffice-writer
  hyphen-is,libreoffice-writer
  hyphen-id,libreoffice-writer
  hyphen-hu,libreoffice-writer
  hyphen-hr,libreoffice-writer
  hyphen-gl,libreoffice-writer
  hyphen-fr,libreoffice-writer
  hyphen-es,libreoffice-writer
  hyphen-en-gb,libreoffice-writer
  hyphen-el,libreoffice-writer
  hyphen-de,libreoffice-writer
  hyphen-da,libreoffice-writer
  hyphen-cs,libreoffice-writer
  hyphen-ca,libreoffice-writer
  hyphen-bg,libreoffice-writer
  hyphen-af,libreoffice-writer
  hunspell-vi,libreoffice-writer
  hunspell-uk,libreoffice-writer
  hunspell-tr,libreoffice-writer
  hunspell-th,libreoffice-writer
  hunspell-te,libreoffice-writer
  hunspell-sw,libreoffice-writer
  hunspell-sv,libreoffice-writer
  hunspell-sr,libreoffice-writer
  hunspell-sl,libreoffice-writer
  hunspell-sk,libreoffice-writer
  hunspell-si,libreoffice-writer
  hunspell-ru,libreoffice-writer
  hunspell-ro,libreoffice-writer
  hunspell-pt-pt,libreoffice-writer
  hunspell-pt-br,libreoffice-writer
  hunspell-pl,libreoffice-writer
  hunspell-oc,libreoffice-writer
  hunspell-no,libreoffice-writer
  hunspell-ne,libreoffice-writer
  hunspell-lt,libreoffice-writer
  hunspell-lo,libreoffice-writer
  hunspell-kmr,libreoffice-writer
  hunspell-it,libreoffice-writer
  hunspell-is,libreoffice-writer
  hunspell-id,libreoffice-writer
  hunspell-hu,libreoffice-writer
  hunspell-hr,libreoffice-writer
  hunspell-hi,libreoffice-writer
  hunspell-he,libreoffice-writer
  hunspell-gug,libreoffice-writer
  hunspell-gu,libreoffice-writer
  hunspell-gl,libreoffice-writer
  hunspell-gd,libreoffice-writer
  hunspell-es,libreoffice-writer
  hunspell-en-za,libreoffice-writer
  hunspell-en-gb,libreoffice-writer
  hunspell-el,libreoffice-writer
  hunspell-de-de-frami,libreoffice-writer
  hunspell-de-ch-frami,libreoffice-writer
  hunspell-de-at-frami,libreoffice-writer
  hunspell-da,libreoffice-writer
  hunspell-cs,libreoffice-writer
  hunspell-bs,libreoffice-writer
  hunspell-bn,libreoffice-writer
  hunspell-bg,libreoffice-writer
  hunspell-af,libreoffice-writer
  libreoffice-canzeley-client,libreoffice-writer
  libreoffice-writer-nogui,libreoffice-writer
  libreoffice-writer-nogui,libreoffice-writer
  libreoffice-wiki-publisher,libreoffice-writer
  libreoffice-librelogo,libreoffice-writer
  libreoffice-core-nogui,libreoffice-writer 1:7.0.4-4+deb11u10
  libreoffice-core,libreoffice-writer 1:7.0.4-4+deb11u10
  libreoffice-core,libreoffice-writer 1:7.0.0~alpha~
  libaccessodf-java,libreoffice-writer
  libreoffice-base-nogui,libreoffice-writer
  libreoffice-base,libreoffice-writer
  libreoffice,libreoffice-writer
  jabref,libreoffice-writer
  hunspell-de-de,libreoffice-writer
  hunspell-de-ch,libreoffice-writer
  hunspell-de-at,libreoffice-writer
  hyphen-ru,libreoffice-writer
  hyphen-en-us,libreoffice-writer
  hyphen-lv,libreoffice-writer
  myspell-de-de-1901,libreoffice-writer
  gnumed-client,libreoffice-writer
  ebook-speaker,libreoffice-writer
  libreoffice-dmaths,libreoffice-writer
  parl-desktop,libreoffice-writer
  design-desktop,libreoffice-writer
  cinnamon-desktop-environment,libreoffice-writer
Dependencies: 
1:7.0.4-4+deb11u13 - libreoffice-base-core (5 1:7.0.4-4+deb11u13) libreoffice-common (2 1:7.0.0~alpha~) libreoffice-core (5 1:7.0.4-4+deb11u13) ucf (2 0.8) libabw-0.1-1 (0 (null)) libc6 (2 2.29) libe-book-0.1-1 (0 (null)) libepubgen-0.1-1 (0 (null)) libetonyek-0.1-1 (0 (null)) libgcc-s1 (2 3.0) libicu67 (2 67.1-1~) libmwaw-0.3-3 (0 (null)) libodfgen-0.1-1 (0 (null)) librevenge-0.0-0 (0 (null)) libstaroffice-0.0-0 (0 (null)) libstdc++6 (2 9) libuno-cppu3 (2 4.4.0~alpha) libuno-cppuhelpergcc3-3 (2 5.3.0~alpha) libuno-sal3 (2 5.3.0~alpha) libuno-salhelpergcc3-3 (2 1.4.0) libwpd-0.10-10 (0 (null)) libwpg-0.3-3 (0 (null)) libwps-0.4-4 (0 (null)) libxml2 (2 2.8) uno-libs-private (0 (null)) zlib1g (2 1:1.1.4) libreoffice-common (3 1:6.4.2~rc1~) libreoffice-math (0 (null)) fonts-crosextra-caladea (0 (null)) fonts-crosextra-carlito (0 (null)) libreoffice-base (0 (null)) libreoffice-java-common (2 1:7.0.4~) default-jre (18 2:1.8) java8-runtime (16 (null)) jre (0 (null)) libreoffice-common (3 1:6.4.2~rc1~) 
1:7.0.4-4+deb11u10 - libreoffice-base-core (5 1:7.0.4-4+deb11u10) libreoffice-common (2 1:7.0.0~alpha~) libreoffice-core (5 1:7.0.4-4+deb11u10) ucf (2 0.8) libabw-0.1-1 (0 (null)) libc6 (2 2.29) libe-book-0.1-1 (0 (null)) libepubgen-0.1-1 (0 (null)) libetonyek-0.1-1 (0 (null)) libgcc-s1 (2 3.0) libicu67 (2 67.1-1~) libmwaw-0.3-3 (0 (null)) libodfgen-0.1-1 (0 (null)) librevenge-0.0-0 (0 (null)) libstaroffice-0.0-0 (0 (null)) libstdc++6 (2 9) libuno-cppu3 (2 4.4.0~alpha) libuno-cppuhelpergcc3-3 (2 5.3.0~alpha) libuno-sal3 (2 5.3.0~alpha) libuno-salhelpergcc3-3 (2 1.4.0) libwpd-0.10-10 (0 (null)) libwpg-0.3-3 (0 (null)) libwps-0.4-4 (0 (null)) libxml2 (2 2.8) uno-libs-private (0 (null)) zlib1g (2 1:1.1.4) libreoffice-common (3 1:6.4.2~rc1~) libreoffice-math (0 (null)) fonts-crosextra-caladea (0 (null)) fonts-crosextra-carlito (0 (null)) libreoffice-base (0 (null)) libreoffice-java-common (2 1:7.0.4~) default-jre (18 2:1.8) java8-runtime (16 (null)) jre (0 (null)) libreoffice-common (3 1:6.4.2~rc1~) 
Provides: 
1:7.0.4-4+deb11u13 - 
1:7.0.4-4+deb11u10 - 
Reverse Provides:
```
**Explication** :

Cette commande me montre toutes les informations relatives au paquet libreoffice-writer, y compris ses dépendances.
Les dépendances sont les autres paquets nécessaires pour que LibreOffice Writer fonctionne correctement.
Je peux ainsi voir quels autres paquets doivent être installés.


***5- Installer ce logiciel. Quels menus de votre environnement sont-ils modifiés ?***

Pour installer LibreOffice Writer, je lance la commande suivante :
```code
sankou@p20221:~$ sudo apt-get install libreoffice-writer
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
libreoffice-writer est déjà la version la plus récente (1:7.0.4-4+deb11u13).
libreoffice-writer passé en « installé manuellement ».
0 mis à jour, 0 nouvellement installés, 0 à enlever et 6 non mis à jour.
```
**Explication** :

Cette commande installe le paquet libreoffice-writer.
Après l'installation, LibreOffice Writer sera disponible dans le menu des applications, dans la section bureautique de mon environnement de bureau (par exemple, dans le menu "Applications" sous GNOME ou "Menu Principal" sous XFCE).
Le paquet va aussi intégrer une entrée dans le menu principal de LibreOffice, et ajouter un raccourci pour le traitement de texte Writer dans mon menu d'applications

__________________________________________________________________________________________

**EXERCICE 2 - Surveillance de l’espace disque**

***1- Quel est l’espace disponible sur le système de fichier qui contient votre répertoire de connexion ?***

Pour savoir combien d’espace est disponible sur le système de fichiers qui contient mon répertoire de connexion, j’utilise la commande suivante :
```code
sankou@p20221:~$ df -h ~
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
/dev/nvme0n1p2     123G    7,3G  110G   7% /
```
**Explication** :

La commande df affiche l’espace utilisé et disponible sur les systèmes de fichiers.
L'option -h permet de rendre les tailles plus lisibles (Go, Mo, etc.).
En utilisant ~, je cible mon répertoire de connexion (mon répertoire personnel).
Cela me donne directement l’espace disponible sur le disque qui contient mon répertoire de connexion.

***2- Quel espace occupe votre répertoire de connexion ? Et le répertoire /usr ?***

Pour vérifier l’espace occupé par mon répertoire de connexion et le répertoire /usr, je vais utiliser la commande du. 

*Commande pour mon répertoire de connexion :*
```code
sankou@p20221:~$ du -sh ~
226M	/home/sankou
```

*Commande pour le répertoire /usr :*
```code
sankou@p20221:~$ du -sh /usr
5,4G	/usr
```

**Explication** :

La commande du permet de calculer l’espace occupé par un fichier ou un répertoire.
L’option -s donne seulement un résumé total de l’espace utilisé, et -h affiche les résultats de manière lisible.
Avec ~, je vérifie l’espace utilisé par mon répertoire personnel.
Avec /usr, je peux voir l’espace utilisé par le répertoire /usr, qui contient de nombreux fichiers système et applications.


***3- Quel est le plus gros fichier dans /usr/bin ?***

Pour trouver le plus gros fichier dans /usr/bin, je vais utiliser du combiné avec sort pour trier les fichiers par taille et afficher le plus gros.

```code
sankou@p20221:~$ du -ah /usr/bin | sort -rh | head -n 1
463M	/usr/bin
```

**Explication** :

du -ah /usr/bin liste tous les fichiers et répertoires dans /usr/bin avec leur taille.
sort -rh trie les fichiers par taille de manière décroissante (-r pour inverser l’ordre, -h pour un format lisible).
head -n 1 affiche uniquement le fichier le plus gros.
Cela me permet de trouver et d’afficher le fichier le plus volumineux dans le répertoire /usr/bin.


________________________________________________________________________________________
**EXERCICE 3 - Sauvegardes de fichiers sur une machine distante**

****1- Rappels sur les copies de fichiers copier le fichier /etc/passwd dans mon répertoire de connexion***

Commande :
```code
sankou@p20221:~$ cp /etc/passwd ~/
```
**Explication** :

En tant qu'utilisateur ordinaire, je ne peux pas copier de fichiers systèmes comme /etc/passwd dans mon répertoire de connexion sans avoir les droits administrateur. Toutefois, si j'essaie de copier, les permissions, le propriétaire et les dates de modification ne seront pas identiques, car cp copie simplement le contenu sans conserver les attributs (sauf si l'option -p est utilisée).

***(Meme question en utilisant cp -p.)***

```code
sankou@p20221:~$ cp -p /etc/passwd ~/
```

**Explication** :

Avec l'option -p, cp conserve les permissions, le propriétaire, et les dates de modification. Cela garantit que la copie du fichier est exactement la même que l'original, y compris les métadonnées.

***Si on veut copier `a l’identique tout un r´epertoire (et ses sous-r´epertoires), quel(les) option(s) de cp utiliser ?***

```code
sankou@p20221:~$ sudo cp -r /etc /home/sankou/
[sudo] Mot de passe de sankou :
```

**Explication** :

L'option -r permet de copier un répertoire et tous ses sous-répertoires. Cela permet de réaliser une copie complète du contenu d’un répertoire, tout en préservant sa structure. Pour s'assurer que tout est copié à l'identique, l'option -p doit également être utilisée si l'on veut conserver les informations liées aux fichiers (permissions, dates, etc.).


***2- Rappels sur les connexions SSH
Se connecter à la machine distante avec SSH***

```code
sankou@p20221:~$ ssh arol@p20224
The authenticity of host 'p20224 (192.168.52.24)' can't be established.
ECDSA key fingerprint is SHA256:4UM3Y2Moxb6Ty6X0toMtOZu/XcD6ltMK+xLD5NAUNug.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'p20224,192.168.52.24' (ECDSA) to the list of known hosts.
arol@p20224's password: 
Linux p20224 5.10.0-25-amd64 #1 SMP Debian 5.10.191-1 (2023-08-16) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Mon Jan 31 13:55:40 2022 from 192.168.53.2
arol@p20224:~$ 
```

**Explication** :

Ici, je me connecte à la machine distante en utilisant ssh (Secure Shell). Lorsque je me connecte pour la première fois, il me sera demandé de valider la clé de la machine distante. Une fois connecté, je peux exécuter des commandes à distance. ici je me connecte à la machine de mon camarade arol. 


*Vérification de la connexion SSH*

Pour vérifier que je suis bien connecté à la machine distante, je peux utiliser la commande hostname pour obtenir le nom de la machine distante.
```code
arol@p20224:~$ hostname
p20224
```
Cela me permet de m’assurer que je suis bien connecté à la machine que je voulais atteindre.

***Créer une clé DSA pour SSH et l'utiliser sans mot de passe***
```code
arol@p20224:~$ ssh-keygen -t dsa
Generating public/private dsa key pair.
Enter file in which to save the key (/home/arol/.ssh/id_dsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/arol/.ssh/id_dsa
Your public key has been saved in /home/arol/.ssh/id_dsa.pub
The key fingerprint is:
SHA256:qyyk4T9pwtj7DIg12F9NdjAX64FQ/YwjT3gO2tTAo2c arol@p20224
The key's randomart image is:
+---[DSA 1024]----+
|      .o+.o.     |
|       .+=..     |
|       .+=++     |
| o    .+Eo*.o    |
|. +   .*SB..     |
|.o.o... ..o      |
|o=.+..  .        |
|. *o=. .         |
|  .*+oo          |
+----[SHA256]-----+
```

**Explication** :

Cette commande génère une paire de clés DSA. La clé publique sera copiée sur la machine distante pour permettre une connexion sans avoir à entrer de mot de passe à chaque fois.

***Quatre premiers et derniers octets de la clé publique :***
```code
arol@p20224:~$ head -n 1 ~/.ssh/id_dsa.pub
ssh-dss AAAAB3NzaC1kc3MAAACBAIQSh2DAAt3d4IO9ItNO28acqfIO14YrJJOcvUQFLtaUfr3jwiy882dGBPDR7u4KCdvYiWospmWchgW0sFI9EtGryIhlBklDK0eMCEU3zOwH7h7hkqQDp2OwcRixTGgI7YfiBMM7fMNUEmODzsqb/Thd7P/uYyhz76sEYzwI6tHTAAAAFQDWtCzd2SZHX+PZFM0KlEFp6jnK8wAAAH9p4+ywYD9B3BObPLftKNTROYVs28l8GY5LwSQpssuCAnyn+YmFllwtnCZ0q2SdcP0sm1fxFtTanfzv8pLj3cwbHp/pGaY1a1jY2JWXZe4JQDsAOccz+NCiE51vhTIiZCAfk2ROa++iEuadn5Go6YQ0qUQoy+qCkyVDUz7+wFnoAAAAgBux/2/VIcG8ADVDa2ObO94zo7/nNmYlIQoDVdzrdTZDZkU6VceaTM5aH0ywpe8mpfrky440vxCjz2MmV9KlxlMqS6oGExrHB4Qi2V3R5R70yGfVSn8Neags04iuur+55L8BOKoz0FmTAFYxD2t1N7lmIW49fu1W3XXvMIzOmfq0 arol@p20224
arol@p20224:~$ tail -n 1 ~/.ssh/id_dsa.pub
ssh-dss AAAAB3NzaC1kc3MAAACBAIQSh2DAAt3d4IO9ItNO28acqfIO14YrJJOcvUQFLtaUfr3jwiy882dGBPDR7u4KCdvYiWospmWchgW0sFI9EtGryIhlBklDK0eMCEU3zOwH7h7hkqQDp2OwcRixTGgI7YfiBMM7fMNUEmODzsqb/Thd7P/uYyhz76sEYzwI6tHTAAAAFQDWtCzd2SZHX+PZFM0KlEFp6jnK8wAAAH9p4+ywYD9B3BObPLftKNTROYVs28l8GY5LwSQpssuCAnyn+YmFllwtnCZ0q2SdcP0sm1fxFtTanfzv8pLj3cwbHp/pGaY1a1jY2JWXZe4JQDsAOccz+NCiE51vhTIiZCAfk2ROa++iEuadn5Go6YQ0qUQoy+qCkyVDUz7+wFnoAAAAgBux/2/VIcG8ADVDa2ObO94zo7/nNmYlIQoDVdzrdTZDZkU6VceaTM5aH0ywpe8mpfrky440vxCjz2MmV9KlxlMqS6oGExrHB4Qi2V3R5R70yGfVSn8Neags04iuur+55L8BOKoz0FmTAFYxD2t1N7lmIW49fu1W3XXvMIzOmfq0 arol@p20224
```















