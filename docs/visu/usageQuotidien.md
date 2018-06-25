# Salle de visualisation: Utilisation "quotidienne"

**Sur cette page:**
* Mise en marche
* Connexion - types de sessions
* Logiciels installés
* Usages de présentations/bureautique
* Visualisation scientifique
* Support pour la stéréoscopie 3D

La station de travail de la salle de visualisation est installée sous **Ubuntu** et **Windows**. Il s'agit d'une machine équipée de 128go de RAM, de 32 coeurs et de 2 cartes graphiques Quadro K5200. 

**A noter:** A l'heure actuelle, Windows ne supporte pas l'affichage en 3D (avec les lunettes).

## Mise en marche
1. Allumer l'ordinateur
2. Allumer les deux vidéoprojecteurs à l'aide de la télécommande, en visant l'arrière des projecteurs. Les voyants d'alimentation se mettront à clignoter en vert.
3. La station de travail est longue à démarrer (environ 2 minutes).

## Connexion - types de session

L'ordinateur boote sans intervention de l'utilisateur sous linux. Pour booter sous Windows, il faudra faire attention à allumer les projecteurs **avant** l'ordinateur, de manière à pouvoir sélectionner **Windows boot manager** dans le menu de boot (grub).

#### Linux
Plusieurs types de sessions sont accessibles sur Ubuntu:
* **Les sessions classiques** des utilisateurs de la station de travail, créées localement par l'administrateur système: typiquement pour les membres de l'ISCD qui ont un besoin fréquent d'utiliser la machine, et d'y stocker des fichiers de développement, des objets 3D...
* **La session "invité"**: cette session permet à n'importe qui de se connecter, mais ne permet ni d'effectuer des modifications sur les logiciels existants, ni de sauvegarder des données pour une prochaine utilisation: tout travil effectué doit donc être sauvegardé ou sera perdu.
* **Les sessions des utilisateurs de HPCaVe**: tout utilisateur ayant un compte sur les machines de calcul peut se connecter à sa session depuis la salle de visualisation, et y monter un espace de stockage situé sur les serveurs. Ceci permet par exemple de visualiser des données situées sur les serveurs HPCaVe avec des logiciels installés sur la station de travail, sans avoir à y transférer de données. 

#### Windows
Sur windows, seules les sessions des utilisateurs enregistrés et d'invité sont disponibles.

## Utilisation en présentation/bureautique (Ubuntu)

#### Présentations (.pdf, .ppt)
* **qpdfview** est le logiciel le plus pratique pour des présentations en plein écran. Une fois le fichier ouvert, F12 permet de passer en plein écran avec la touche **F12**, et de zoomer/dézoomer en mode présentation avec **Ctrl+molette**.
* **libreoffice** permet de lire des fichiers .ppt, mais la compatibilité n'est pas parfaite, en particulier sur des points comme les animations, les vidéos, transitions... Le mode présentation s'active avec **F5**.
Une télécommande équipée d'un pointeur laser utile pour les présentations est également disponible dans la salle. Il faut brancher l'adaptateur USB sur la station de travail pour pouvoir l'utiliser, et la reconnaissance se fait sans étape supplémentaire.

#### Partage de bureau
Pour le partage de bureau, deux possibilités sont offertes et faciles à utiliser/configurer:
* **TeamViewer** permet de prendre le contrôle d'un PC à distance, mais nécessite l'installation du logiciel sur l'ordinateur cible.
* **Chrome remote desktop**, fonctionnant avec le navigateur google chrome, permet également la prise de contrôle à distance, mais se désactive au bout de 20 minutes environ. Pour une présentation dans la salle de visualisation, il faudra par exemple se déplacer vers l'ordinateur ciblé régulièrement...

## Visualisation scientifique
Divers logiciels de visualisation sont installés sur la station de travail, parmi lesquels **Visit** et **Paraview** qui sont connectés aux machines de calcul, et permettent donc de visualiser des données stockées sur les serveurs. Voir la [page dédiée](/docs/visu/mesuVisu.md) pour plus d'informations.

## Stéréoscopie 3D
La salle de visualisation est équipée de lunettes 3D actives. Le support pour la 3D n'est pas automatique dans tous les logiciels, mais voici quelques logiciels la supportant:
* **blender** : logiciel de modélisation polygonale 3D, permettant le rendu réaliste en temps réel de nombreux formats de fichiers (fbx, ply, stl, x3D, obj...).
* **bino** : lecture de vidéos 3D.
* **medit**: utilitaire de visualisation de fichiers 3D au format **.mesh**
* **pymol**: visualisation de molécules 3D
* **visit**: visualisation scientifique générale
* **paraview**: visualisation scientifique générale
