Un serveur de fichiers (d'utilisation similaire à Dropbox ou Google Drive) est disponible à l'ISCD à l'adresse IP **134.157.66.205**.


# Les différents espaces de stockage
Une fois connecté, différents espaces de stockage sont accessibles, les principaux étant:
* **home**: il s'agit de votre espace de stockage privé, dans lequel vous pouvez stocker des fichiers que vous seuls pourrez consulter et éditer, à la manière d'une Dropbox personnelle.
* **iscd**: dans ce dossier figurent des documents accessibles à tous. Parmi ceux là les fichiers des différents séminaires comme les mardi de l'ISCD par exemple.
* **projets**: c'est dans ce répertoire que se situent les dossiers contenant les données à partager entre plusieurs utilisateurs, mais qui n'ont pas vocation à être accessibles à tous. Un répertoire accessible à un nombre restreint d'utilisateurs peut y être créé sur une simple demande à l'administrateur système.

# Connexion au serveur de fichier
Bien que la connexion soit possible via ftp (pour une sauvegarde automatique, un accès via des scripts ou pour utiliser un logiciel similaire à Filezilla par exemple), la méthode recommandée est de se connecter via l'utilitaire natif de son O.S:

## Windows 10
Depuis l'explorateur de fichiers windows, cliquer sur **ce PC** dans le menu de gauche.

Dans l'onglet **Ordinateur**, sélectionner **Ajouter un emplacement réseau**. 

![windowsconnect](https://user-images.githubusercontent.com/11873158/37348988-b0f094c0-26d5-11e8-9664-423967ed86fb.jpg)

Un utilitaire s'ouvre alors, et l'adresse à rentrer est alors: `\\134.157.66.205\home`.

![windowsadress](https://user-images.githubusercontent.com/11873158/37348987-b0d7a816-26d5-11e8-853a-b488b4932248.jpg)

Après avoir rentré ses identifiants, le disque est alors monté, et les différents espaces de stockage deviennent accessibles depuis les **emplacements réseau** de l'explorateur de fichiers.
![windowsconnected](https://user-images.githubusercontent.com/11873158/37348785-42809454-26d5-11e8-9ec9-2bb439efb451.jpg)


## Ubuntu
Le disque partagé est disponible via le navigateur de fichiers **nautilus**, soit par le menu **Network**, dans lequel il est désigné comme **ISCDS1517 (File sharing)**, soit par l'option **Connect to a server**.

Dans ce cas, il faudra se connecter en rentrant lorsque l'adresse du serveur est demandée:
`smb://134.157.66.205`

![connecttoserver](https://user-images.githubusercontent.com/11873158/37298265-17489490-2620-11e8-8ae6-961a653c3052.jpg)

Après avoir rentré ses identifiants dans la fenêtre qui s'est ouverte, la connexion est établie et l'ouverture/édition de fichiers rendue possible.

![enterpassword](https://user-images.githubusercontent.com/11873158/37298268-17be7354-2620-11e8-9894-47ef6ddd2be3.jpg)

![connected](https://user-images.githubusercontent.com/11873158/37298261-16dd6e04-2620-11e8-85aa-56b6306e85c0.jpg)


## MacOS

Depuis un ordinateur sous MacOS, le serveur de fichiers est visible dans le menu de gauche du **Finder**, menu **Réseau**, sous le nom **ISCDS1517**. En le sélectionnant, un bouton **Connect as** apparait alors:

![connectas](https://user-images.githubusercontent.com/11873158/37298442-98790298-2620-11e8-8897-571bc743adbc.jpg)

Après avoir rentré ses identifiants, la connexion est possible et les différents espaces disponibles dans le Finder.

![ids](https://user-images.githubusercontent.com/11873158/37298444-98cc8b84-2620-11e8-9773-b3c7070f8b9a.jpg)

![connected](https://user-images.githubusercontent.com/11873158/37298443-98ab06c6-2620-11e8-87ef-3a69c2407c87.jpg)