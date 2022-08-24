# GUI-autonomous-car
GUI project for autonomous car simulation

### Prérequis
Configurer un interpréteur Python au sein de votre IDE si vous en utiliser un.

### Pour RUN le fichier modele-final.py, il est nécessaire d'installer les modules pyqt5 et numpy

##### Si ce n'est pas déjà fait installer les via les lignes de commandes ci-dessous :

pip install pyqt5

pip install pyqt5-tools 

pip install numpy

Attention ces commandes peuvent varier selon votre version de Python et/ou de pip.

## RVIZ

Afin d'utiliser le logiciel de simulation RVIZ, il est nécessaire d'installer une machine virtuelle.
il est fortement recommandé d'en installer une déjà prévue à cet effet. Il suffit de suivre ces deux tutos pour avoir l'environnement nécessaire.

https://mushr.io/tutorials/intro-to-ros/

https://mushr.io/tutorials/quickstart/

### Pour créer un nouveu circuit :

- Ajouter votre image (format pgm) dans le dossier catkin_ws/src/mushr_sim/maps
- Créer le fichier .yaml associé dans le même dossier, en spécifiant l'image utilisée, la résolution que vous souhaitez ainsi que la position de la carte.

Voici un exemple de format pour le fichier yaml :

image: circuitMIA.pgm  
resolution: 0.01  
origin: [0, 0, 0]  
occupied_thresh: 0.1  
free_thresh: 0.09  
negate: 0  


### Pour choisir le circuit lors de la simulation :

Aller dans le dossier catkin_ws/src/mushr_sim/launch/map_server.launch

### Pour créer un nouveau fichier de commande :

Ajouter votre fichier de commande (.txt) dans le dossier catkin_ws/src/mushr_ros_intro/plans

### Pour lancer ROS :

Exécuter dans un terminal séparé :

roslaunch mushr_sim teleop.launch

### Pour lancer RVIZ :

Exécuter dans un terminal séparé :

rosrun rviz rviz -d $HOME/catkin_ws/src/mushr/mushr_utils/rviz/default.rviz

### Pour lancer la simulation avec le fichier de commande choisi :

Exécuter dans un terminal séparé :

roslaunch mushr_ros_intro path_publisher.launch plan_file:='$(find mushr_ros_intro)/plans/fichier_choisi.txt'

## Utilisation de l'interface PyQT

 - Lancer le programme Python modele-final.py
 - Choisir votre couleur pour le tracé
 - Tracer une trajectoire (il est possible de s'arrêter pendant le tracé et de le reprendre ensuite)
 - Valider votre trajectoire à l'aide du bouton si elle vous convient
 - Si le tracé ne vous convient pas, effacer à l'aide du bouton "CLEAR CIRCUIT"
 - Si vous voulez redessiner le dernier tracé validé, cliquez sur "LOAD LAST TRAJECTORY"
 - Une fois le fichier de commande généré (appelé par défaut trajectoire.txt), copier-coller le contenu du fichier dans votre fichier de commande pour RVIZ.


