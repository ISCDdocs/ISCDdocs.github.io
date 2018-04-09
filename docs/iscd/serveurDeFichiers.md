Un serveur de fichiers (d'utilisation similaire à Dropbox ou Google Drive) est disponible à l'ISCD à l'adresse IP **134.157.66.224**.


# Les différents espaces de stockage
Une fois connecté, différents espaces de stockage sont accessibles, les principaux étant:
* **home**: il s'agit de votre espace de stockage privé, dans lequel vous pouvez stocker des fichiers que vous seuls pourrez consulter et éditer, à la manière d'une Dropbox personnelle.
* **iscd**: dans ce dossier figurent des documents accessibles à tous. Parmi ceux là les fichiers des différents séminaires comme les mardi de l'ISCD par exemple.
* **projets**: c'est dans ce répertoire que se situent les dossiers contenant les données à partager entre plusieurs utilisateurs, mais qui n'ont pas vocation à être accessibles à tous. Un répertoire accessible à un nombre restreint d'utilisateurs peut y être créé sur une simple demande à l'administrateur système.

# Connexion au serveur de fichier
Bien que la connexion soit possible via ftp (pour une sauvegarde automatique, un accès via des scripts ou pour utiliser un logiciel similaire à Filezilla par exemple), la méthode recommandée est de se connecter via l'utilitaire natif de son O.S:

## 1. Interface web
Une interface est disponible à l'adresse [https://iscd1517quickconnect.fr1.quickconnect.to/](https://iscd1517quickconnect.fr1.quickconnect.to/). Son utilisation est relativement limitée (pas de modifications possibles sur les fichiers), et il est donc préférable d'utiliser les versions "natives" des systèmes d'exploitation, présentées après.

## 2. Windows 10
Depuis l'explorateur de fichiers windows, cliquer sur **ce PC** dans le menu de gauche.

Dans l'onglet **Ordinateur**, sélectionner **Ajouter un emplacement réseau**. 

![windowsconnect](https://user-images.githubusercontent.com/11873158/37348988-b0f094c0-26d5-11e8-9664-423967ed86fb.jpg)

Un utilitaire s'ouvre alors, et l'adresse à rentrer est alors: `\\134.157.66.224\home`.

![windowsconnect](https://user-images.githubusercontent.com/11873158/38487955-34424f00-3be2-11e8-9c3f-2a91b50f120a.jpg)

Après avoir rentré ses identifiants, le disque est alors monté, et les différents espaces de stockage deviennent accessibles depuis les **emplacements réseau** de l'explorateur de fichiers.
![windowsconnected](https://user-images.githubusercontent.com/11873158/37348785-42809454-26d5-11e8-9ec9-2bb439efb451.jpg)

## Ubuntu
Le disque partagé est disponible via le navigateur de fichiers **nautilus**, soit par le menu **Network**, dans lequel il est désigné comme **ISCDS1517 (File sharing)**, soit par l'option **Connect to a server**.

Dans ce cas, il faudra se connecter en rentrant lorsque l'adresse du serveur est demandée:
`smb://134.157.66.224`

![serveradress](https://user-images.githubusercontent.com/11873158/38487958-348a94e0-3be2-11e8-9012-e9b2f1ca60e8.jpg)

Après avoir rentré ses identifiants dans la fenêtre qui s'est ouverte, la connexion est établie et l'ouverture/édition de fichiers rendue possible.

![identification](https://user-images.githubusercontent.com/11873158/38487956-345ae330-3be2-11e8-8627-4d9dbb9b29da.jpg)

![connected](https://user-images.githubusercontent.com/11873158/38487957-34726244-3be2-11e8-95fc-2b5952052c62.jpg)

## MacOS

Depuis un ordinateur sous MacOS, le serveur de fichiers est visible dans le menu de gauche du **Finder**, menu **Réseau**, sous le nom **ISCDS1517**. En le sélectionnant, un bouton **Connect as** apparait alors:

![37298442-98790298-2620-11e8-8897-571bc743adbc](https://user-images.githubusercontent.com/11873158/37532388-2b4327c2-293f-11e8-88ed-37119110d2db.jpg)

Après avoir rentré ses identifiants, la connexion est possible et les différents espaces disponibles dans le Finder.

![37298444-98cc8b84-2620-11e8-9773-b3c7070f8b9a](https://user-images.githubusercontent.com/11873158/37532390-2b7a454a-293f-11e8-97cb-4957bb78f46e.jpg)

![37298443-98ab06c6-2620-11e8-87ef-3a69c2407c87](https://user-images.githubusercontent.com/11873158/37532389-2b5d6e20-293f-11e8-9ebb-be35c8444626.jpg)
