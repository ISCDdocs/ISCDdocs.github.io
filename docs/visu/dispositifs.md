# Dispositifs matériels associés à la salle de visualisation
**Sur cette page:**
* 1 - Projecteurs
* 2 - Stéréoscopie / 3D
* 3 - Kinect
* 4 - LeapMotion
* 5 - Caméras infrarouges
* 6 - Souris 3D
* 7 - Tablette tactile

## 1 - Projecteurs

Les projecteurs sont des [F35 AS3D de Projection Design](https://www.barco.com/fr/product/f35-series).

Ils s'allument grâce aux deux télécommandes associées, normalement présentes dans la salle de visualisation. Il faut bien se situer à l'arrière du projecteur pour le manipuler avec la télécommande.

Un troisième projecteur est présent dans la salle de visu en cas de panne, et des lampes de rechange sont dans l'armoire de la salle.

Un souci d'écran s'est déjà produit (lignes verticales multicolores entrelacées). Il a suffi dans ce cas de sortir les lampes de leurs emplacements et de les y ré-insérer pour refaire fonctionner le projecteur.

## 2 - Stéréoscopie / 3D

La stéréoscopie est assez dure à configurer du point de vue logiciel (cf [configuration 3D](blendingNvidia.md)). Au niveau des projecteurs, la configuration est également particulière:
1. S'assurer que chaque GPU ait en entrée une sortie DVI de chaque projecteur (pour pouvoir synchroniser l'affichage). GPU-0 = VP0-DVI1 et VP1-DVI1 par exemple, GPU-1 = VP0-DVI2 et VP1-DVI2.
2. Sur les deux projecteurs, dans les paramètres 3D, s'assurer que la 3D est en mode **frame sequential** et les lunettes en **IR**. Laisser par défaut décochée l'option "intervertir les yeux":
![inversionyeux](https://user-images.githubusercontent.com/11873158/37649251-7d78794e-2c31-11e8-9a2f-4cdb215c1833.jpg)
3. Sur le projecteur de gauche (qui reçoit les informations de synchronisation et les envoie via BNC sync-out), dans Installation -> Synchronisation, copier les paramètres de la photo suivante:
![projogauche](https://user-images.githubusercontent.com/11873158/37649254-7daa7430-2c31-11e8-91fd-a95437311796.jpg)
4. Sur le projecteur de droite, qui reçoit les informations de synchronisation depuis "BNC sync-in":
![projodroit](https://user-images.githubusercontent.com/11873158/37649253-7d91c23c-2c31-11e8-8dba-3971f0c32509.jpg)

## 3 - Kinect
Pour 

## 4 - LeapMotion

## 5 - Caméras infrarouge

## 6 - Souris 3D

## 7 - Tablette tactile
