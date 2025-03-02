comparaison avec une crais, un fil d'arianedans un labyrinthe
### methode 
l'algorythme utilise une variable bool par sommet et une pile
- le bool permet de marquer un sommet visité 
- la pile permet de revenir en arriere et d'explorer d'autre chemin


### l'algorythme 
1. Initialiser, mettre a faux la marque associée a chaque noeud
2. Empiler et marquer à vrai le noeud de depart
3. tant et aussi longtemps que la pile n'est pas vide : 
	1. Depiler un noeud, lui faire le traitement (ex cout )
	2. Pour chacun de ses voisin 
		1. le marquer 
		2. l'empiler

### remarques 
- On ne peut pas acceder aux noeud isolé 
	- ca peut marcher si on repete l'algo pour tous les noeuds non visité
- Quand on prend un cul de sac, ca fait un retour en arriere. On peut faire la meme chose de maniere recursive


![[Pasted image 20250225233600.png]]
![[Pasted image 20250225233807.png]]


temps dexecution O(n+m)
n = noeud 
m = arc



### Variante 

Si on veut prendre en compte le temps de recherche, on peut modifier l'algorythme. 
ca prend 2 vecteurs et une pile 

- `debut[v]
- `fin[v]` 
- `pile` contient les noeusds abandonné
- `clock` est la variable qui servira d<increment de 1 

![[Pasted image 20250226210530.png]]


### Kosaraju 
Permet de trouver les composants fortements connexes d'un graph orienté 

#### lkes grandes lignes 
- onbtenir l'inverse de G
- Faire un parcourt en profondeur de G^i
- Faire un parcourt de G 
- A chaque retour de explore de G, les noeuds visité depuyius le dernier appel coinstituent une comp fortement connexe de G 
- 


![[Pasted image 20250226213032.png]]

temps d'execution 
- chaque passage dans G donne O(n+m)
- selon la regle du maximum, le temps est donc de O(n+m)
- 