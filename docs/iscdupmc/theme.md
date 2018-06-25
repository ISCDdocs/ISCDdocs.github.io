# Theme wordpress pour iscd.upmc.fr
Informations concernant le thème wordpress du site [iscd.upmc.fr](iscd.upmc.fr).

## 1 - Installation
Pour installer le thème sur un nouveau serveur (pour des tests ou pour migration), il suffit de cloner le contenu du [dépot associé](https://github.com/ISCDdocs/wordpressISCD) dans un répertoire de **/var/www/html/wp-content/themes**:
```
git clone https://github.com/ISCDdocs/wordpressISCD.git ISCD
```
Le thème apparaitra alors dans le menu Apparence->Thèmes du portail admin du site. Il suffit alors de l'activer pour enregistrer les modifications.

En cas de réinstallation, deux étapes supplémentaires sont nécessaires:
1. Grâce au plugin "better search and replace", rechercher le nom de l'extension de l'ancien domaine, et le remplacer par le nouveau. Normalement, peu de références y seront faites, mais mieux vaut vérifier cette étape.
2. Modifier dans le fichier [style.css](https://github.com/ISCDdocs/wordpressISCD/blob/master/style.css), aux alentours de la ligne 160, les identifiants de "menu-item-*", pour les faire correspondre à ceux de la page, modifiés par wordpress. Pour les connaitre, utiliser la fonction "inspecteur" du navigateur, permettant de connaitre les identifiants du menu:
<p align="center">
<img src="https://user-images.githubusercontent.com/11873158/41841712-4bc3030e-7869-11e8-910c-2e7be3229e6c.png"/>
</p>

## 2 - Développement
Le thème est développé "from scratch", c'est à dire qu'il ne s'agit pas d'un thème enfant au vu de wordpress, mais d'un thème indépendant. Toutes les pages sont donc gérées par l'ensemble des fichiers présents dans le dépot.

Pour apporter des modifications au thème, il est important d'en comprendre la structure. Plus d'informations sont disponibles sur la page [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) du site de Wordpress, mais voici dans l'ordre "logique" le fonctionnement des fichiers .php présents dans le thème:
* __header.php__ et __footer.php__: Ces fichiers sont appelés au début et à la fin de chaque page chargée sur le site, et contiennent les logo, raccourcis de navigation (news, contact...) et menu principal.
* __front-page.php__: la page d'accueil du site
* __page.php__ et __page_tertiary.php__: les "templates" de pages pour la navigation, avec notamment la prise en compte du niveau pour l'affichage du menu sur la gauche
* __index.php__: idem mais page par défaut?
* __search.php__: sera affiché lors d'une recherche sur le site
* __htmlTemplates/azlist.html__: Tableau du A-Z (présent dans la recherche), pour ne pas encombrer le fichier header.php
* __404.php__: la page 404
* __functions.php__: contient des définitions de shortcode, les limites d'upload, la définition de fonctions php réutilisées par ailleurs...
* __style.css__: le style principal du site

Des scripts javascript sont également présents dans le dossier **js**.

La meilleure manière d'apporter des modifications au site est de le faire sur le serveur web (avec nano ou emacs). Pas de version d'essai, toute modification est donc visible en ligne.

Il arrive que des erreurs dues au php rendent le site inaccessible. Il faudra alors revoir le fichier .php pour trouver l'origine de l'erreur (pas de retour dans la console Web malheureusement...), ou en dernier recours restaurer le thème à une version précédente via git.
