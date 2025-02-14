![[Pasted image 20250208224844.png]]![[Pasted image 20250208224858.png]]


### Comparaison dss vs diagrame de sequqnce (de conception)

#### [[DiagrammeSequenceSysteme]] 
- documente un scénario et un use-case 
- interaction entre utilisateur et système
- les fleches ne représente pas de message au sens du language de prog
- le message sur les fleches correspond a un evenement/action/echange de donnée

#### DiagrammeSequence conception 
- Usage plus informatique
- PErmet de représenter les interactions entre les objets 
- Representation des structures de controle
- 


![[Pasted image 20250208230543.png]]


![[Pasted image 20250208230557.png]]


uun objet peut appeler ses propres methodes 



specification d'un appel/message

return = msgName(param:paramType1, …) : returnType


*nous n'avons pas a toujours utiliiser la signature complete


### Notation simplifié

![[Pasted image 20250208230718.png]]



voir le cours pour plus de detail sur les éléments du diagramme comme : 
- barre de specification d'execution/activation (p.20) 
	- Quand l'objet recoit un message, il peut
		- executer son propre code
		- Attendre les resultats retournés âs uin autre objet 
- Structure de controles
	- creation d'un objet
	- condition
	- boucle
	- 


*Les diagramme de séquences peuvent etre utilisé sous deux formes:
- forme générique
	- decrit tous les deroulements possible
	- peut contenir des branchemnt
	- des conditions
	- des boucles
- forme s'instanciation
	- decrit le comportement du systeme pour *une seule situation specifique*
	- contient aucun branchement
	- aucune condition 
	- aucune boucle

![[Pasted image 20250209105505.png]]
