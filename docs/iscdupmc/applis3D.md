# Applications 3D et autres pages html
Il est possible d'héberger d'autres pages ou services sur le site iscd.upmc.fr.
Cependant, pour héberger un serveur avec un service associé (gitlab, comex, wordpress de test...), le mieux est de encore de créer une machine virtuelle via proxmox (voir avec les admin sys) et de lui assigner une IP fixe afin de pouvoir s'y connecter depuis l'extérieur.

En revanche, il est possible de stocker des pages au format html ou applications Javascript par exemple sur le même serveur que l'installation du site iscd.upmc.fr.

Pour ce faire, créer un répertoire dans le dossier **/var/www/html**, et y copier la totalité contenu (html, js, css, assets divers...). Pour que l'accès soit possible par défaut sur la page html correspondante, il faudra créer un lien symbolique nommé __index.html__ dans ce dossier.

Pour une page appelée __mapage.html__ (pouvant faire appel à d'autres ressources dans le même dossier) transférée dans le dossier __/var/www/html/monApp__ par exemple, le lien se fera ainsi:
```
sudo ln -s /var/www/html/monApp/mapage.html /var/www/html/monApp/index.html
```
Cette méthode permettra alors d'accéder directement au contenu de __mapage.html__ depuis l'adresse iscd.upmc.fr/monApp

### Applications 3D avec blend4web
Un de ces cas d'application peut être le deploiement d'applications [blend4web](https://www.blend4web.com/en/), qui permet facilement d'exporter une scène 3D au format html, et éventuellement d'y lier une application basée sur Javascript pour y ajouter de l'interactivité.

**Resources**:
* [Documentation du processus de développement dans blend4web](https://www.blend4web.com/doc/en/developers.html)
* Documentation du [Project Manager](https://www.blend4web.com/doc/en/project_manager.html).

Des exemples de telles applications (peut être encore en développement) sont:
* [Visualisation de fichiers .mesh en ligne](http://iscd.upmc.fr/medit)
* [Théâtre d'orange interactif](http://iscd.upmc.fr/orange)
* [Ebauche de validation pour la reconstruction faciale](http://iscd.upmc.fr/facile)

Bien que la visualisation d'une scène au format .html peut se faire en copiant simplement cette page dans un dossier, la procédure à suivre pour déployer une application est un peu plus complexe, mais rien d'infaisable compte tenu du potentiel et de la (relative) facilité d'usage de blend4web:
1. Créer la scène et l'application grâce à blender (pour les matériaux, lumières, objets...) et javascript via le "Project Manager" de Blend4Web. Toutes les infos sont présentes dans la documentation de blend4web).
2. Dans le project Manager, une fois l'application validée ( dans le Project Manager, la version dev de la page est fonctionnelle), il faut **build** le projet, puis **deploy** pour télécharger une archive au format **.zip**.
3. Transférer cette archive sur le serveur du site, puis l'extraire dans un répertoire de /var/www/html.
4. Créer le lien symbolique vers la page html.
```
#Depuis votre ordinateur:
scp monProject.zip icsadm@134.157.15.2:~
#Depuis le serveur web:
sudo unzip ~/monProjet.zip -d /var/www/html/monProjet
cd /var/www/html/monProjet
sudo ln -s monProjet.html index.html
```
