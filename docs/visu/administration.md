**Sur cette page**:
* Configuration existante de la machine
* Utilisateurs et droits
* Logiciels installés, et particularités
* Sauvegarde et réinstallation

## Configuration actuelle de la machine
La station de travail est configurée avec un dual boot Ubuntu 16.04 / windows 8.1.

#### linux

La distribution choisie est Ubuntu 16.04, par souci de facilité d'usage et pour pouvoir supporter la majorité des logiciels "grand public" de l'écosystème linux.

Adresse IP (qui doit être fixe pour le montage des serveurs de calcul): **134.157.66.205**

La principale difficulté concernant linux consiste en la gestion des deux projecteurs et de la 3D:

Depuis Janvier 2018, les pilotes nvidia supportent la combinaison du blending entre les projecteurs avec le support pour la 3D stéréoscopique. Cette partie est présentée dans le dépot correspondant. Une fois configurée, cette étape ne prend plus que la forme de lancer l'application de blending au démarrage.

La configuration avec lightdm (qui permet de gérer les connexion des différents utilisateurs), est aussi assez délicate, et mérite de ne pas trop y toucher une fois installée.

Le reste de la configuration est classique à linux: si on ne peut installer les logiciels via "sudo apt-get", on les installe à partir d'executables ou de sources dans **/opt/nomDuProgramme**, en créant un lien symbolique dans **/usr/local**.

#### windows

Rien de spécial à noter pour l'administration de windows, si ce n'est la gestion également des deux projecteurs et du blending entre écrans (dans le dépot correspondant). A noter qu'en ce jour, la 3D n'est pas supportée sous windows.

## Utilisateurs et droits

#### linux
Plusieurs catégories d'utilisateurs:
* les utilisateurs ayant un compte sur la machine, ajoutés par un administrateur depuis son compte, et dont les données et paramètres seront sauvegardés sur l'ordinateur: typiquement des personnes de l'ISCD ou ayant un besoin récurrent d'utiliser la machine.
* les utilisateurs des machines de calcul: grâce à la connexion (via lightdm) sur le ldap des serveurs de calcul, les utilisateurs de HPCaVe peuvent monter leur /home directement sur la station de travail de la salle de visualisation, et donc visualiser leurs données en live.
* utilisateur invité: lightdm propose d'avoir une session "invitée", idéale pour les utilisations ponctuelles de la machine. Cette session peut aussi être peatique pour tester la bonne installation des logiciels, car elle n'aura aucun paramètres utilisateur sauvegardés, autres que ceux par défaut.
* utilisateur **admin**: pour faciliter l'administration de la station de travail, un seul administrateur est présent sur la machine: compte **admin**. Il faudra donc l'utiliser pour installer des logiciels.
* utilisateur **demo**: sur le bureau de cet utilisateur, de nombreuses démos sont accessibles au double clic, afin de présenter les différentes possibilités/projets de visualisation à l'ISCD.

#### windows
Par défaut, les utilisateurs ne sont pas administrateurs, et il faudra donc se connecter en tant qu'un des utilisateurs ayant les droits requis. 

## Logiciels installés
#### linux
#### windows

## Sauvegarde et restauration

Cf. [page dédiée](sauvegarde.md)
