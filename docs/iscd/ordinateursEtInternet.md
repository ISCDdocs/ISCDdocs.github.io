# PCs, wifi et ethernet 
**Sur cette page:**
* Les PCs/ordinateurs de l'ISCD
* Le wifi
* Ethernet et IP fixes

## 1 - PCs à l'ISCD
En plus des ordinateurs portables des membres de l'ISCD, plusieurs ordinateurs fixes (à performances variables) sont disponibles à l'ISCD, et dédiés à différents usages:

#### La station de travail de la salle visu
En dehors des serveurs de calcul, il s'agit de l'ordinateur le plus "costaud" de l'institut. En plus de ses 32 coeurs et 128Go de RAM, il dispose de 2 cartes graphiques Nvidia Quadro K5200, et peut donc être utilisé (ponctuellement) pour ses performances brutes. Ubuntu et Windows 8.1.

#### "Bertha"
Ce PC (Dell T7910) est le second plus performant de l'institut, et a vocation à être partagé par plusieurs utilisateurs (photogrammétrie, modélisation et rendus 3D, calculs ponctuels pour éviter de passer par MeSU...).
Il dispose également de 32 coeurs et de 128Go de RAM, mais n'a "qu'une" K5200. Ce PC est de plus installé sous Windows, Ubuntu 16.04 et Oracle Server, et devrait donc répondre à la majorité des besoins de développement.

#### Les stations d'accueil DELL tout-en-un
Cinq ordinateurs DELL (optiplex 3030) tout-en-un (sans tour centrale) sont destinés à des usages plus légers. Quatre de ces orinateurs sont installés sous Ubuntu, le cinquième sous windows.

L'idée est que les ordinateurs sous Ubuntu puissent facilement être réinstallés pour subvenir aux besoins de post-doc, stagiaires, profs invités...

Une de ces stations de travail est installée dans la salle de réunion 204, et a vocation a servir principalement en session invité, c'est à dire pour vérifier des mails, montrer des données en l'absence de PC portable, se connecter via ssh ou TeamViewer à d'autres ordinateurs...

#### Le PC de l'ancienne salle de visualisation
Sous le format d'une tour horizontale, ce DELL (peu puissant) est installé sous Windows 7 et peut servir en appoint.

#### Les stations de travail "individualisées"
Plusieurs autres ordinateurs puissants (moins que Bertha) sont "privatisées" et utilisées par une seule personne:
* 2 HP de 16 coeurs (xeon) et 32go de RAM avec K5000.
* 4 Dell de 8 coeurs (i7) avec gtx 1080 et 16Go de RAM.

## 2 - Wifi
Le wifi est disponible de deux manières à l'ISCD:
#### wifi ICS_UPMC
Une capsule Apple sert de modem wifi et diffuse un réseau appelé "ICS_UPMC", dont le mot de passe est ics:wifi!
Le débit est assez bon, mais des problèmes peuvent survenir lorsque de nombreuses personnes y sont connectées. On préférera garder ce wifi pour les personnes n'ayant pas de compte eduroam.
#### eduroam
Le mieux est d'utiliser sur le campus, et dans les locaux de l'ISCD, le wifi **eduroam** qui fonctionne désormais très bien.

## 3 - Ethernet et IP fixes
De nombreuses prises sont disponibles dans les locaux, mais toutes ne sont pas activées. Si la connexion échoue, il faut ouvrir un ticket sur [la hotline de la DSI](https://hotline.sorbonne-universite.fr/), catégorie __FACULTE DES SCIENCES ET INGENIERIE -> Réseau__, en spécifiant le numéro de la prise incriminée (de la forme ROT33 22#012).

De plus, en fixant son adresse IP (dépend de l'OS utilisé), il est possible de demander l'ouverture de certains ports afin de pouvoir par exemple se connecter en ssh depuis l'extérieur du campus, ou utiliser un ordinateur comme serveur web.
