- objet de n'importe que type de classe implementant operator
	- aka operateur d'appel ou operateur d'application 
	- peuvent agir comme une fonction mais aussi comme arguemnt a une methode ou a une autre fct

Deux avantage p/r aux appel de fct direct
- un objet de fct peut contenir un etat
- obj fct est aussi un typwe et peut etre utilisé comme param de modele


Les foncteur sont des objet 
utilisent des attribut comme n'importe quelle autre classe
Exemeple: 
creer une fct avec une mem. Elle pourra effectuer une operation différente a chaque appel


les foncteurs de base servent normallement comme operateur de tri


vboir les exemples du cour

### Algo de la bibliotheque par defaut 
- La plupart ont deux dverison
	- Foncteur par defaut
	- avec un arg supp pour fournir un foncteur personnalisé
ex fct *sort*
- par defaut avec < 
- ou foncteur pserso
- 
### Predicat
- Expression qui retourne un bool 
	- Les algo n'utilisent pas tous < certain utilisent == 
std::sort(begin(v), end(v)); // foncteur par défaut
std::sort(begin(v), end(v), un_foncteur); // foncteur personnalisé