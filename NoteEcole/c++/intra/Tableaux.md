"#Include <Array>

std::array<int,5> monTableau;

opur acceder pour lire ou ecrire

monTableau[0] = maVariable
maVariable = monTableau[0]


un tableau commence a 0 
exemple un tableau de taille 10 

tableau 2d array<array<int,3>,5> monTableau

5 lignes 3 colonne 

pour acceder 

monTableau[0][1] = 5 
colonne 1 ligne 0 

initialisation : 

array<array<int,3>,5> matrice {
{1,2,3},
{5,6,7},
....,
....,
.....
}


### tableau avec des boucles for 
for(auto element: p_tableau1D)
	cout<< element << endl ;  

