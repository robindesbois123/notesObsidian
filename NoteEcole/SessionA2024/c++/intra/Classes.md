Classe représente un bojet
- l'interface : 
	defini ce qui est vu de l'exterieur, montre ce qui est necessaire contient principalement les declaration 

- l'implementation 
	est-ce que qui est à l'interieur et qui fait le code qui fait marcher l'interface



une classe ne permet pas l'accès à ses attributs 
	- Encapsulation 



structure d'une classe : 
- .h
	- Section privée
		- attribut
	- Section Publique
		- méthode
- .cpp
	- declaration des métohode

constructeur, sert a construire un bojet 
on peut surchager une classe en mettant plusieurs cfonstructuers. Le compilatweur decide lui-meme de quel constructeur al=ppeler selon les arguments 




constructeur
date::date(int p_jour, int p_mois, int p_annee){
	m_jour = p_jour
	m_mois = p_mois
	m_annee = p_annee
}
ca c'est pas bon, 
on est mieux avec : 
date::date(int p_jour, int p_mois, int p_annee): m_jour(p_jour), m_mois(p_mois),m_annee(p_annee){}



le destructeur fait le menage dans la classe avant la destruction. Il n'efface pas vraiment la memoire
~ maclasse(){}



### categorie de methode : 
- Acces
- Assignation
- comparaison 
- Utilitaire
- Statique
	- sert a faire une methode qui ne se sert pas des attribut de la classe 
