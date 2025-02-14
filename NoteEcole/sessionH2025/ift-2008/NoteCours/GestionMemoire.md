
- operateur new
	- X* p = new X (constructeur)
	- On doit recuperer l'espace sinon ca fait une memory leak
- operator delete, 
	- recuperation de l'estpace 
	- Appel de l'operatuer delete sur le pointeur obtenu a partir de new
	- delete p

Copie 
- Copie Surface
	- Par defaut en cpp
- Copie en profondeur 
	- On doit l'implementer![[Pasted image 20250213193115.png]]


les 3 copliens
- contructeur de copie
- surchage de operator =
- destructeur



Memory leak 
- 1 new, 1 delete 
- Qui libère
- Solutions : 

### Unique_ptr

- Un emplacement mémoire = un pointeur 
	- un unique_ptr est propriétaire de l'emplacement pointé 
		- ex : unique_ptr Employe ptEmploye(make_unique Employe("harry")); 
la seule donnée dans unique_ptr

On ne peut pas le copier ou le modifier, on peut seulement le transferer vers un autre pointeur 

### Shared_ptr
un meme emplacement référencé par plusieurs pointeur
- Compteur de ref, quand le dernier est detriut, l'objet est detruit
- Pas de notion de proptiété 

### weak_ptr
- as utiliser pour observer un objet sans impacter son compteur de references 
	- à utiliser pour observer un objet sans qu'il demeure actif
	- Obligatoire pour interrompre les ref circulaire dans les shared_ptr



![[Pasted image 20250213221215.png]]
