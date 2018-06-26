# Migration wordpress
Pour faire une migration (changement d'adresse ou de machine virtuelle) d'un site wordpress, plusieurs étapes sont nécessaires pour s'assurer du bon déroulement de l'opération:
1. Préparer le nouveau serveur et installer le thème
2. Exporter les données depuis l'ancien site wordpress
3. Création des utilisateurs
4. Importer ces données dans le nouveau site
5. Vérifier que les changements aient bien été répercutés
6. Changement d'alias

## 1 - Préparation du nouveau serveur - installation du thème
Il faut pour cela disposer installer un wordpress "vierge" dans le dossier /var/www/html, et configurer apache pour avoir accès à l'adresse IP de l'installation par http. Voir pour cela l'administrateur(trice) système.

Une fois un compte créé, s'assurer d'avoir accès à l'interface d'administration de wordpress (ip+/wp-admin).

Si le thème est un thème "fait maison", il faudra alors le réinstaller. Pour le site iscd.upmc.fr, se référer au [dépot github correspondant](https://github.com/ISCDdocs/wordpressISCD) et aux [instructions associées](https://iscddocs.github.io/docs/iscdupmc/theme.html).

Enfin, pour s'assurer qu'il n'y ait pas de pages en double et que les images, pdf, documents... uploadés via wordpress correspondent aux bonnes versions, il vaut mieux supprimer toutes les pages, tous les posts et tous les médias depuis l'espace d'administration de wordpress du *nouveau site*.

## 2 - Export des données depuis l'ancien site
Lorsque la migration est prête à être effectuée, il faut faire un export depuis l'installation wordpress de l'ancien site: menu -> tools -> Export -> Wordpress -> export all content:

![](https://www.elegantthemes.com/blog/wp-content/uploads/2014/01/screenshot7.jpg)

Un fichier .xml est alors téléchargé.

## 3 - Création des utilisateurs sur le nouveau site
Si ce n'est pas déjà fait, recréer les utilisateurs de la nouvelle installation de wordpress. Il faudra s'assurer que les mots de passe correspondent aux anciens en testant avec un utilisateur (voir avec l'administrateur système si la manip a été faite), ou dans le cas contraire regénérer un mot de passe pour chaque utilisateur, ce qui leur enverra un mail de mise à jour.

## 4 - Import du fichier .xml
Encore une fois, avant d'importer les données sur le nouveau serveur, mieux vaut s'assurer d'avoir supprimé posts, pages et médias de la nouvelle installation. Cela permettra d'éviter les doublons et d'éviter d'avoir des pages sur le nouveau site qui ont été supprimées sur l'ancien.

Sur la page d'administration du nouveau site, réimporter le fichier xml téléchargé à l'étape précédente: menu -> tools -> Import -> run wordpress importer:

![](https://www.elegantthemes.com/blog/wp-content/uploads/2014/01/screenshot3.jpg)

Les médias de l'ancien site devraient également être réimportés.

## 5 - Vérification
En plus de s'assurer du bon comportement du thème wordpress, plusieurs autres vérifications peuvent être à apporter:

1. Si le nouveau site est disponible à une autre adresse que le précédent, utiliser le plugin "Better search and replace" pour remplacer les occurences de l'ancienne adresse par la nouvelle (remplacer par exemple 'http://monsite.com' par "http://monnouveausite.com").
Cette étape permet de s'assurer que les adresses web "mises en dur" dans l'ancien site soient bien converties vers le nouveau site. 

2. Certains plugins ne transfèrent pas leurs données via la méthode d'import/export de wordpress. Il faudra alors s'assurer d'avoir les plugins utiles à l'ancien site installés sur le nouveau, et penser à migrer "manuellement" les fichiers stockés entre les deux installations (copie entre les répertoires /var/www/html/uploads/dossierduplugin des deux serveurs), ou à défaut s'assurer d'avoir bien téléchargé les fichiers de l'ancien site (pour les formulaires d'upload par exemple).

3. Dans le cadre du thème du site iscd, il faut modifier quelques lignes du fichier css dans la nouvelle installation, afin que le menu principal ait des couleurs. Se référer pour ça à la [doc du thème](https://iscddocs.github.io/docs/iscdupmc/theme.html).

## 6 - Changement d'alias
Une fois vérifié le bon fonctionnement du nouveau site, l'administrateur système peut procéder au changement de l'alias (c'est à dire faire correspondre une adresse de type http://monsite.com à l'adresse IP du serveur sur lequel est installé le nouveau site). Après cette étape, et avant de fermer le serveur de l'ancienne installation, penser à revérifier le comportement global du site, et éventuellement y changer d'anciens chemins ne redirigeant plus au bon endroit (Cf partie 5).
