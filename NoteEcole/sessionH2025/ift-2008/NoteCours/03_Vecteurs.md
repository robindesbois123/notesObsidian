### Description
- Séquence ordonnée d'élément
- chaque élément à sa position (position 1,2,3 ...)
- Opération supportées 
	- Accès au K élément
	- Supression du k element
	- Insertion avant la position k
- Specificaiton 
	- Acces au k element se fait en temps O(1)
	- les autres O(n)
		- n = nombre element dans le vecteur
-

### Utilité 
- Accès au k élément se fait en O(1)
- Temps d'insertion/Supression O(n)
- Les vecteurs sont implanteé avec des tableaux dynamique
	- les elements sont dans des cases contigue en memoire 
	- le temps d'acces est rapide
	- Mais pour inserer ou supprimer un element au milieux du tableau, il faudra deplacer la moitié des elements contenu en memoire. Ce qui necessite un temps O(n)



### Code 


- `#include <vector>`
- ce tconteneur utilise des tableaux dynamique poru le stockage
- On peut modifier dynamiqument la taille 
	- implique une relocation de alam emoire<
	- Acces aléatoire O(1)
	- insertion et suppresion lente
	- Supression a la fin O(1)
	- insertion a la fin O(1)



#### Constructeur 
- vector () ; //construit un vecteur d e 0 elements
- vector (size_t n); // construit un vecteur de n element 
- vector (size_t n, const T& a); //chaque element est une copie de a 
#### operateur indexation 
- T& operator[](size_t); // retourne un élément de type T modifiable 
- const T& operator[](size_t) const; // non modifiable par l’appelant

#### 📌 Les méthodes les plus utilisées

- `void clear();` → détruit tous les éléments  
- `size_t size();` → donne le nombre d’éléments présents  
- `void resize(size_t n);` → change le nb d’éléments à `n`  
- `size_t capacity();` → donne la taille de l’espace mémoire allouée  
- `void reserve(size_t n);` → demande une capacité `>= n`  
- `void push_back(const T&);` → ajoute un élément à la fin  
- `void pop_back();` → détruit le dernier élément  
- `T& front();` → retourne le premier élément  
- `T& back();` → retourne le dernier élément  
- `T& at(size_t n);` → retourne l’élément en position `n` et lance une exception `out_of_range` si l’élément n’existe pas  
- `iterator begin();` → retourne un itérateur au début  
- `iterator end();` → retourne un itérateur à la fin  

#### 📌 Les opérateurs les plus utilisés

- `=`  
- `==`  
- `<`  
- `[]`
