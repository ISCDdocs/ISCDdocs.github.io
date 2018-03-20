# Thème wordpress pour hpcave.upmc.fr
Le thème utilisé est une (très légère) adaptation du thème [Education base](https://fr.wordpress.org/themes/education-base/).

Les fichiers du thème sont sauvegardés dans [ce dépot](https://github.com/ISCDdocs/wordpressHPCAVE).

### 1 - Réinstallation
Pour réinstaller ce thème, il "suffit" de se déplacer sur l'installation wordpress dans le dossier **/var/www/html/wp-content/themes** et de taper la commande:
```
git clone https://github.com/ISCDdocs/wordpressHPCAVE.git
```
Dans le cas ou l'on souhaiterait d'abord installer le thème (depuis wordpress), avant d'y ajouter les modifications, il faudra modifier les fichiers de la section suivante.


### 2 - Modifications
Peu de modifications ont été apportées dans le thème:
* **style.css**: utilisé pour modifier certains éléments CSS, en début de fichier.
* **scripts/***: les fichiers javascript permettant de modifier le comportement de certains éléments du site (toggle de paragraphes, changement des headers)
* **header.php**: les scripts à utiliser sur la page sont ajoutés sous la section __do_action( 'education_base_action_before_head' );__

### 3 - statistiques
A noter que pour réincorporer les [statistiques d'utilisation des serveurs](http://hpcave.upmc.fr/index.php/resources/status/), il faudra suivre les [instructions dédiées](statistics.md)
