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
* script randr au démarrage (similaire à )
* fichier monitors.xml

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
Une fois les sources de nvidia-settings téléchargées et extraites (dans **/opt** de préférence), il faudra rajouter le fichier dans le répertoire **samples**, et modifier le Makefile du répertoire **samples** pour prendre en compte le nouveau fichier (à l'image de )

## Windows
