# Classification d'images à l'aide du deeplearning

## contexte
Ce projet a été réalisé dans le cadre de la formation [machine learning proposé par Openclassroom](https://openclassrooms.com/fr/paths/794-machine-learning-engineer).
Cette étude a pour but de classifier des races de chiens à partir de photographies. Deux approches ont été testées, une from scratch et une autre par transfert learning. 
**Ce projet a été réalisé sur GPU**

## Les données
La base de données utilisée pour entrainer les algorithmes est la [Stanford dogs dataset](http://vision.stanford.edu/aditya86/ImageNetDogs/). Elle indexe 120 races de chiens et possède 20,580 images.


## Déroulement du projet:

### Notebook d'exploration:
- Exploration des données 
- Traitement des Images avec le package Pillow
	- whitening
	-  auto contrast 
	-  equalizing
	-  transpose 
	-  rotation
	-  resize

### Notebook modèle
- Modélisation avec prétraitement de Pillow:
	- Teste un modèle from scratch (3 couches de convolution, une couche dense) avec activation ReLu.
	- Mise en place de différentes variations du modèle de base.

 -  Modélisation avec prétraitement de Keras  (rotation, zoom, flip):
	- Teste un modèle from scratch (3 couche de convolution, une couche dense) avec activation ReLu.
	- Mise en place de différentes variations du modèle de base.  
	- Mise en place du transfert learning avec MobileNet.
 
## conclusion

Dans le but de tester nos modèles en optimisant le temps de calcul, on a gardé uniquement les **10 races les plus représentées du dataset**.
Dans le cas des modèles dit from scratch, les résultats avec le prétraitement Pillow ne donnent pas des résultats satisfaisants. Les fonctions de pertes sont toutes des fonctions croissantes en fonction du nombre d'epochs. Cependant avec le prétraitement de keras le le meilleur modèle obtient un résultat d'environ **35% de précision sur l'ensemble de validation**.  le modèle de transfert learning MobileNet donne un résultat de **92% après réentrainement** sur le jeu de données de validation. Malgré ce résultat, le modèle MobileNet est en situation d'overfiting dû au  nombre de races qui a été utilisé.

