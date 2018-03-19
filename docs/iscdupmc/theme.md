# Theme wordpress pour iscd.upmc.fr
Informations concernant le thème wordpress du site [iscd.upmc.fr](iscd.upmc.fr).

## 1 - Installation
Pour installer le thème sur un nouveau serveur (pour des tests ou pour migration), il suffit de cloner le contenu du [dépot associé]() dans un répertoire de **/var/www/html/wp-content/themes**:
```
git clone https://github.com/ISCDdocs/wordpressISCD.git ISCD
```
Le thème apparaitra alors dans le menu Apparence->Thèmes du portail admin du site. Il suffit alors de l'activer pour enregistrer les modifications.

## 2 - Développement
Le thème est développé "from scratch", c'est à dire qu'il ne s'agit pas d'un thème enfant au vu de wordpress, mais d'un thème indépendant. Toutes les pages sont donc gérées par l'ensemble des fichiers présents dans le dépot.
