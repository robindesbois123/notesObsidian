Étape d'évaluation d'une fonction: 
1. Évaluation des paramètre effectif
2. Appel de la fonction : 
	1. les variables locales et les parametre formels sont créés 
	2. Les parametre formel prennent la valeur résultante de l'évalution
	3. Évaluation du corps de la fonction
	4. Execution du corp de la fonctiuon
	5. Retour d'une valeur en resultat
	6. Les variables du pt 1 sont detruites
3. Affectation de la valeur de retour a une variable 
4. On reprend le code


passer une variable par reference permet de modifier la variable passé en parametre
Si on met const devant, on prend la variable mais on ne fait pas une copie donc ca amméliore les performances.


exemple: 
void maFonction(int& x) {
	x = x + 1 
}
x sera incremente de 1 dans le prog principal

exemple const 
void maFonction(const int& x ){
	cout<<x<< endl 
}
ici, const permet d'afficher x sans en fire une copie dans la fonction.