# Status and statistics sur hpcave.upmc.fr

Pour afficher les statistiques présentes sur la page [status and statistics](http://hpcave.upmc.fr/index.php/resources/status/) du site hpcave.upmc.fr, un ensemble de scripts sont à installer sur le serveur web associé au site. Ces fichiers, lancés régulièrement grâce à **crontab**, exécuteront différentes commandes sur une frontale de MeSU, et en stockeront le résultat dans des fichiers .txt, ensuite mis à disposition du serveur apache à l'aide de liens symboliques.

## 1 - Configuration existante

### 1.1 - Téléchargement des scripts
Pour installer les scripts de la branche **serveurWeb** il faut:
```
cd /home/icsadm
git clone https://github.com/ISCDdocs/statisticsHPCAVE.git --branch serveurWeb --single-branch
cd statisticsHPCAVE
```
Dans le dossier sont présents plusieurs scripts, lançant des commandes sur les frontales de MeSU à partir de l'utilisateur présent dans les fichiers (qu'il faudra donc changer en accordance).

Créer un dossier **results** dans lequel seront stockés les résultats des commandes:
```
mkdir results
```

### 1.2 - Configuration de la connexion en ssh vers les frontales
L'utilisateur **root** du serveur web doit pouvoir se connecter en ssh sans mot de passe vers les frontales, avec l'utilisateur spécifié (norgeot dans les exemples). Il faut pour cela enregistrer les clés ssh de part et d'autre, et faire en sorte que la commande `ssh utilisateur@mesu.dsi.upmc.fr` ne requière pas le mot de passe.
Ceci permettra d'envoyer les fichiers de manière régulière.

**Note:** l'utilisateur utilisé pour lancer les commandes doit également avoir un accès en lecture sur le fichier `/opt/dev/pbs/spool/server_priv/bdd.pbs.sqlite3` (fichier de la base de données PBS). Ceci peut se vérifier en essayant d'accéder à ce fichier via la commande:
```
sqlite3 /opt/dev/pbs/spool/server_priv/bdd.pbs.sqlite3
```

### 1.3 - Test des scripts
Pour s'assurer que les scripts fonctionnent et avant de les programmer grâce à crontab, il faut les tester en les lançant un par un (en tant que root):
```
sudo sh /home/icsadm/statisticsHPCAVE/getCurrentStatus.sh  /home/icsadm/statisticsHPCAVE/results norgeot
sudo sh /home/icsadm/statisticsHPCAVE/getLastMonthUsage.sh /home/icsadm/statisticsHPCAVE/results norgeot
sudo sh /home/icsadm/statisticsHPCAVE/getLastYearUsage.sh  /home/icsadm/statisticsHPCAVE/results norgeot
sudo sh /home/icsadm/statisticsHPCAVE/getWeeklyUsage.sh    /home/icsadm/statisticsHPCAVE/results norgeot
sudo sh /home/icsadm/statisticsHPCAVE/getUptime.sh         /home/icsadm/statisticsHPCAVE/results norgeot
```
Certaines de ces commandes prennent un peu de temps à s'éxécuter, il faudra donc s'armer de patience (quelques minutes au plus...).
A noter que les arguments sont le dossier dans lequel écrire les résultats et le nom d'utilisateur sur MeSU.

Si les scripts ont fonctionné, plusieurs fichiers seront présents dans le répertoire **results**.


### 1.4 - Création des liens symboliques

Pour que les résultats des commandes précédentes soient visibles depuis le serveur web, il faut que les fichiers soient présents (ou visibles) dans le répertoire **/var/www/html** (dossier public pour apache).
Pour ce faire, créer un dossier appelé "statisticsHPCAVE" dans le répertoire **/var/www/html**, et y créer les liens symboliques pointant vers les fichiers présents dans le répertoire **results**:
```
sudo mkdir /var/www/html/statisticsHPCAVE
sudo ln -s /home/icsadm/statisticsHPCAVE/results/*.txt /var/www/html/statisticsHPCAVE/
```

### 1.5 - Configuration de la page web
Un fichier javascript, [stats.js](https://github.com/ISCDdocs/statisticsHPCAVE/blob/serveurWeb/stats.js), permet d'actualiser différents éléments de la page [Status and statistics](http://hpcave.upmc.fr/index.php/resources/status/).

#### Lien symbolique
Pour pouvoir actualiser facilement ce fichier, créer un lien symbolique pointant vers stats.js depuis le dossier **/var/www/html/statisticsHPCAVE/**:
```
sudo ln -s /home/icsadm/statisticsHPCAVE/stats.js /var/www/html/statisticsHPCAVE/stats.js
```
Le fichier sera ainsi lisible depuis le site.

#### Configuration sur la page web
Sur la [page web](http://hpcave.upmc.fr/index.php/resources/status/), s'assurer qu'en bas de page les balises suivantes soient bien présentes:
```
<script src="http://d3js.org/d3.v4.min.js"></script>
<script src="https://rawgit.com/susielu/d3-annotation/master/d3-annotation.min.js"></script>
<script src="http://hpcave.upmc.fr/statisticsHPCAVE/stats.js"></script>
```
La dernière balise en particulier référence le lien symbolique créé auparavant.

Mettre à jour la page si nécessaire: les statistiques devraient s'afficher sur le site web.

### 1.6 - Configuration des crontab
* [Exemples de crontab](https://devhints.io/cron)

Si les étapes précédentes ont réussi, il ne reste plus qu'à configurer le crontab sur le serveur pour faire en sorte de lancer les scripts régulièrement:
```
sudo crontab -e
```

Puis rajouter les lignes suivantes à crontab:
```
*/15 * * * *  sh /home/icsadm/statisticsHPCAVE/getCurrentStatus.sh  /home/icsadm/statisticsHPCAVE/results norgeot > /dev/null
*/15 * * * *  sh /home/icsadm/statisticsHPCAVE/getUptime.sh         /home/icsadm/statisticsHPCAVE/results norgeot > /dev/null
15 */6 * * *  sh /home/icsadm/statisticsHPCAVE/getLastMonthUsage.sh /home/icsadm/statisticsHPCAVE/results norgeot > /dev/null
15 */24 * * * sh /home/icsadm/statisticsHPCAVE/getLastYearUsage.sh  /home/icsadm/statisticsHPCAVE/results norgeot > /dev/null
15 */24 * * * sh /home/icsadm/statisticsHPCAVE/getWeeklyUsage.sh    /home/icsadm/statisticsHPCAVE/results norgeot > /dev/null
```

Les fichiers seront ainsi mis à jour régulièrement.



## 2 - Nouvelles statistiques

La méthode présentée au dessus permet "facilement" d'ajouter de nouvelles visualisations ou d'obtenir de nouvelles données. 

#### 2.1 - Exemple du "uptime" (simple)

Pour rajouter le temps depuis le dernier redémarrage sur la page j'ai:
1. identifié la commande à lancer sur les frontales renvoyant le résultat attendu, ici **uptime**
2. créé un script [getUptime.sh](https://github.com/ISCDdocs/statisticsHPCAVE/blob/serveurWeb/getUptime.sh), qui lance la commande en ssh
3. lancé le script une première fois pour vérifier que le résultat était celui attendu
4. rajouté le code suivant en html, en y incluant un attribut "id" pour facilement modifier le contenu depuis Javascript et en vérifiant que l'apparence soit satisfaisante:
```
<b>Time since last reboot (uptime): </b>
<span id="uptime">unknown</span>
```
5. créé un lien symbolique entre /var/www/html/statisticsHPCAVE et le fichier results/uptime.txt
6. modifié le fichier Javascript pour lire le fichier .txt et remplacer le contenu de la balise créée en 4 par le temps d'uptime:
```
//Display the uptime
function uptime(text){jQuery("#uptime").html(text);}
jQuery.ajax({type:"GET", url:"/statisticsHPCAVE/uptime.txt",success: uptime});
```

La forme utilisée est une requête AJAX: on essaie de lire un fichier, et si on y arrive, on execute une fonction.

#### 2.2 Nouvelle visualisation d3.js (plus dur)
