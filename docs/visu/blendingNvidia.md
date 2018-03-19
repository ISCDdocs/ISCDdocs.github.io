# Installation et configuration des projecteurs de la salle de visualisation

Pour configurer l'affichage correct des projecteurs, il faut d'abord utiliser l'utilitaire correspondant à l'O.S. permettant de disposer les écrans logiques.

Le chiffre magique est **1128**. Il s'agit du décalage (approximatif) entre les deux projecteurs. C'est à dire que le premier pixel du projecteur de droite est situé au 1128ème pixel du projecteur de gauche.

Les codes présents dans le [dépot github]() prennent ce nombre en compte, mais peuvent évidemment être modifiés en cas de réinstallation des projecteurs (nouvelle salle ou copie du dispositif).

## Linux

Pour configurer les projecteurs sous ubuntu, la première étape est d'installer une version récente des pilotes nvidia (à partir de la version 390.12, les pilotes prennent en compte le blending + stéréo 3D, ce qui n'était pas possible avant). 

#### 1 - Mise en place des écrans
Plusieurs possibilités sont offertes pour disposer correctement les écrans. Il reste à déterminer celle qui est la bonne:
* /etc/X11/xorg.conf
* nvidia-settings
* script randr au démarrage (similaire à [ce script](https://github.com/ISCDdocs/blendingNvidia/blob/linux/randr.sh))
* [fichier monitors.xml](https://github.com/ISCDdocs/blendingNvidia/blob/linux/monitors.xml)

#### 2 - Installation des pilotes
Depuis la page [https://doc.ubuntu-fr.org/nvidia](https://doc.ubuntu-fr.org/nvidia)
```
sudo add-apt-repository ppa:graphics-drivers/ppa 
sudo apt-get update 
ubuntu-drivers devices  
sudo apt-get install nvidia-(numéro du pilote)
sudo reboot
```
**Note:** faire en sorte d'avoir au moins la version 390.12!

#### 3 - Téléchargement de nvidia-settings
L'application **nvidia-settings** est soit installée avec les pilotes (vérifier), soit à installer par les paquets.

Dans les deux cas, il faudra télécharger les sources de l'application afin de bénéficier de la librairie NVAPI, permettant de communiquer en C avec le pilote nvidia.

Le téléchargement se fait à [cette page](https://github.com/NVIDIA/nvidia-settings/releases). Choisir la version correspondant au pilote utilisé.

#### 4 - Compilation de l'application de blending
Une fois les sources de nvidia-settings téléchargées et extraites (dans **/opt** de préférence), il faudra rajouter le fichier  [nv-control-warpblend-own.c](https://github.com/ISCDdocs/blendingNvidia/blob/linux/nv-control-warpblend-own.c) dans le répertoire **samples**, et modifier le Makefile du répertoire **samples** pour prendre en compte le nouveau fichier (à l'image de [ce Makefile](https://github.com/ISCDdocs/blendingNvidia/blob/linux/Makefile)).

La compilation se lance en tapant la commande `make` depuis le répertoire racine de nvidia-settings, et le binaire effectuant le blending a ainsi été créé.

Ne reste plus qu'à créer un lien symbolique vers ce fichier depuis /usr/local/bin et éventuellement à l'ajouter dans les programmes lancés au démarrage, ce qui dépend de l'environnement de bureau utilisé.

#### 5 - Le problème Xinerama
Xinerama permet facilement d'avoir accès à un mode "plein écran" sur les deux projecteurs, mais peut perturber les performances de certains logiciels, voire empêcher le fonctionnement d'autres logiciels (Unreal Engine par exemple).

Pour utiliser des logiciels ayant un problême avec Xinerama, il faut désactiver ce dernier dans **/etc/X11/xorg.conf**, et redémarrer lightdm avec la commande `sudo service lightdm restart`. Ce point est gênant et reste à régler, car ce mode de fonctionnement est loin d'être évident, et ne permet pas d'utiliser le combo écran DELL + projecteurs de manière intuitive...

## Windows 

#### 1 - Téléchargement des pilotes
Le téléchargement et l'installation des pilotes nvidia se fait sur windows depuis la [page de téléchargement de Nvidia](http://www.nvidia.fr/Download/index.aspx?lang=fr).

#### 2 - Configuration des écrans
Une fois l'installation des pilotes effectuée, les écrans se configurent avec l'application NView, accessible avec un clic droit sur le bureau.

#### 3 - Installation du SDK NVAPI
Le téléchargement de NVAPI se fait depuis [cette page](https://developer.nvidia.com/nvapi). Il faut pour cela se créer un compte développeur sur nvidia.com.

#### 4 - Téléchargement et compilation du code de blending
Le code de blending pour windows (inspiré du [dépot d'errollw](https://github.com/errollw/Warp-and-Blend-Quadros)) est disponible dans [la branche "window" du dépot github](https://github.com/ISCDdocs/blendingNvidia/tree/window). Après avoir téléchargé et décompressé le contenu de la branche **window** dans un dossier (par exemple dans C://Programmes), il faut copier l'ensemble des fichiers du SDK Nvidia dans le dossier **include**, afin de prendre en compte une version valide de la librairie NVAPI.

Installer de quoi compiler sous windows.

La compilation se fait alors en ligne de commande, en ouvrant un Powershell (Windows + X -> Console):
```
gcc blending.cpp -link nvapi.lib ...
```

Un éxécutable est alors généré, qui peut être copié dans un autre dossier du PC.
