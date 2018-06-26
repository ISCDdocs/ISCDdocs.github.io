# Moteurs de jeu et Frameworks graphiques pour la 3D

Pour aller plus loin que l'OpenGL basique et pouvoir proposer "rapidement" des applications interactives (et éventuellement interfacées avec d'autres applications ou des dispositifs matériels), plusieurs solutions sont envisageables, et peuvent se révéler intéressantes.

Parmi celles ci, deux grandes catégories émergent:
* Les moteurs de jeu, à savoir les logiciels permettant de créer des jeux vidéos
* Les frameworks graphiques (en ligne ou non)

Les moteurs de jeu permettent, en un temps réduit, d'atteindre des niveaux de rendus très réalistes, et s'interfacent parfaitement avec des objets matériels/physiques (scans archéologiques, éléments d'architecture, pièces mécaniques...), à l'aide de programmes de modélisation 3D type blender, 3Ds Max, Rhino, Maya... S'il est possible d'imaginer l'application à développer comme un jeu vidéo (mouvements de type First Person, modifications de l'environnement, navigation dans un environnement réel...), ces moteurs seront à privilégier.

Les "frameworks graphiques" quant à eux permettront des rendus moins poussés graphiquement, mais sont plus légers, plus faciles à mettre en place, et souvent plus facilement interfaçables (car orientés programmation...), et sont donc idéaux pour développer des prototypes, ou des applications dont la partie visuelle n'est pas privilégiée, ou devant intégrer des programmes tiers.

## 1 - Moteurs de jeu vidéo

Les "leaders" sont Unity3D et Unreal Engine, qui sont des moteurs standards dans le jeu vidéo, et fonctionnent sur de nombreuses plateformes (Unreal étant encore assez instable sur linux). Les deux moteurs sont finalement assez équivalents, et le choix entre l'un ou l'autre pour une application développée de zéro se fera en fonction de critères assez arbitraires:

Unreal dispose de fonctionnalités graphiques plus développées intégrées par défaut, alors qu'il faudra souvent installer des plugins extérieurs pour Unity. L'API d'unreal est accessible en C++, celle d'Unity en C#. Unity est aussi en général légèrement plus simple à utiliser, et donne accès à de très bonnes fonctionnalités d'import/export nativement (fichiers blender directement copiés dans le répertoire du projet par exemple...).

Sur des petits projets ou prototypes et sans contrainte forte, l'utilisation de l'un ou l'autre est donc presque une affaire de préférence personnelle.

### Unity

### Unreal

## 2 - Frameworks graphiques

Pour développer une application 3D rapidement, le plus simple est encore d'utiliser un framework graphique, venant se substituer à l'utilisation "brute" d'OpenGL et rendant les taches de développement plus faciles en proposant des APIs très riches. 
Parmi ces frameworks, deux catégories se distinguent:
* Frameworks OpenGL
* Frameworks Web

### 2.1 - Frameworks OpenGL

#### vtk
[vtk](https://www.vtk.org/) (sur lequel est basé le logiciel Paraview) est la solution se prétant le mieux (et presque exclusivement) au traitement de données scientifiques. En Python ou C++ par exemple, il est assez facile de charger un résultat de simulation, et de lui appliquer une série de filtres permettant des opérations comme des coupes, tracés de streamlines, visualisation de vecteurs en 3D... en quelques lignes de code. De nombreux exemples sont également disponibles.

#### OpenFrameworks
[OpenFrameworks](https://openframeworks.cc/) est un ensemble de librairies C++ dédié aux applications "créatives", et permet facilement d'interfacer via son API de nombreuses librairies (assimp pour le chargement d'objets, OpenCV pour l'analyse d'images, librairies gérant les kinect comme capteur de mouvement, bullet pour la physique en temps réel...) dans un même programme, tout en pouvant intégrer des codes développés en dehors de ce framework. Très utile pour éviter des étapes fastidieuses de compilation par exemple. Les performances 3D sont de plus très bonnes, et une [bonne docmentation](https://openframeworks.cc/learning/) ainsi que de [nombreux exemples](https://github.com/openframeworks/openFrameworks/tree/master/examples) sont disponibles, ainsi qu'un système d'[addons](https://openframeworks.cc/learning/01_basics/how_to_add_addon_to_project/), permettant soit d'intégrer des fonctionnalités extérieures dans son projet, soit de packager les fonctionnalités développées.

#### Processing
[Processing](https://processing.org/) est à la fois un logiciel est un langage de programmation basé sur Java, facile à apprendre, et premettant de développer des applications interactives très facilement en 2D, un peu moins en 3D. Son utilisation dans la communauté des "makers" fait que de nombreux exemples sont disponibles sur internet.
Son avantage principal réside dans sa facilté d'installation et d'utilisation, et même si ses performances sont moins bonnes que vtk ou Openframeworks par exemple, il est possible de remplacer les fonctions disponibles par défaut par de l'OpenGL depuis Java. Avis aux amateurs!
Une grande librairie d'exemples en OpenSource est disponible [ici](https://www.openprocessing.org/).

#### Ogre3D et Irrlicht
Même si des moteurs OpenGL comme [Ogre3D](https://www.ogre3d.org/) ou [Irrlicht](http://irrlicht.sourceforge.net/) peuvent parfois se substituer à des moteurs de jeu, leurs fonctionnalités sont quasi-systématiquement moins abouties, et leurs utilisation "déconseillée" sauf pour des besoins très spécifiques. Dans le doute, à éviter donc.

### 2.2 - Frameworks Web
Openframeworks et Processing permettent tous les deux des exports vers le web grâce à EmScriptem et p5.js (Openframeworks étant plus optimisé à ce niveau-ci). Cependant, leur utilisation n'est pas des plus simples, et d'autres librairies et modules permettent de mettre en place rapidement des applications 3D dans le navigateur (et donc accessibles sans installation), et interfacées avec toutes les fonctionnalités propres à Javascript et HTML.

Il est à noter qu'Unreal Engine et Unity permettent également des exports au format html, mais ne sont pas les plus pertinents pour des applications "légères".

#### three.js et babylon.js
Deux librairies basées purement sur Javascript, mais qui peuvent permettre des rendus web très rapides, légers, et complètement intégrés à des pages html. Solution "native" donc.

#### Blend4Web
Blend4Web est un SDK basé sur blender et javascript, et permet très facilement d'exporter une scène depuis blender vers un format html (en "un clic"), et de lui rajouter une couche d'interaction grâce à son API javascript. Solution idéale pour passer rapidement d'une scène 3D à une application en ligne, le déploiement étant également très facile.

