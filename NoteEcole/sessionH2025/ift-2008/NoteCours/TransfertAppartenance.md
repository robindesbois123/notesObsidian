### Ivalue,Rvalue

lvalue a une adresse
rvalue n'en a pas 

a = a2 + a3

a est une lvalue et (a2+a3 ) sont des rvalue

### Transfert d'appartenance : move()

- std :: move() retourne une ref rvalue sur l'objet passé en arguemnt 
- fonciton de service pour utiliser la notion de deplacement
- Idée : 
	- transfert de ressourvce 
	- optimise le code pour eviter les copies inutile



vouir les exemples dans le pdf



regle des 5 coplien

- constructeur de copie
- constructeur de deplacement
- surchage de operator=
- surchage de operator = de deplacement
- Destructeur si pointeur natif
- 