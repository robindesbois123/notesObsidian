### Les package

- Un package est représenté par un dossier 
- Les packages ont des niveaux de visibilité et des relations qui sont 
	- la dependance 
	- le raffinement
	- la generalisation


#### En java
- Quand il y a plusieurs classes, on regroupe en entité logique, les package 
- Un package est un ensemble de classe et de package
- Chaque package comporte des classes publiques qui lui permet de communiquer sa fonctionnalité aux auitres package
Voir chapitre 12 et 14 

### L'architecture logique
c'est l'organisation des classe logicielle en package
On l'appel architecture logique puisqu'ellle ne demande aucune decision quant a savoir comment les elements eront deployé physiquement


### Architecture en couche 
- une couche est un regroupement à très forte granularité de classe, package et sous-classe. 
- Elle a une responsabilité de cohésion 
- Architecture en couche : 
	- organiser pour que les couche aient accès au couche inferieur mais pas inversed


#### Avantage 
- Reduction des dependance et du couplage 
- Maintenance facile
- Remplacement de couche facile 
- les couches les plus basses contiennent des fonctionnalité reustilibal;e
- segmentation = facile de travailler en equipe 

![[Pasted image 20250208214619.png]]



### Séparation modele-Vue

![[Pasted image 20250208215128.png]]


l'inverse de ca c'est un interface-moteur
ca veut dire que la logique applicative et l'interface sont mélasngé. 
- Button1.onClick() fait des traitement
Ce n'est pas reutilisable