le barometre c'est un endroit dans le code qui roule aboslument le plus souvent 


void triSelection(std::vector& x) { 
	for (int i = x.size() - 1; i > 0; i--) { 
		int pMax = i; 
		for (int j = 0; j < i; j++) {
			if (x.at(j) > x.at(pMax)) { 
				pMax = j; } } 
		int temp = x.at(i); x.at(i) = x.at(pMax); x.at(pMax)

dans ce code le for j et le if sont deux operatioon barometre puisque le code doit toujours passer par la 
