- LIFO, last in last out 
- DAPS dernier arrivé dernier sorti

- Example
	- Assiette
	- livres
	- factures


pile = liste + gestion avancé 

### Objectif: 
- sert a mettre la mise en attente d'info pour l'utilisaer plus tard
- Operation supportée
	- ajouter un nouvel élément (empiler,push) 
	- oter lelement au sommet (depiler,pop)
- Specification
	- doit se faire en O(1)
- implementation
	- liste




# 📌 Implémentation de la classe `Pile`

## Définition de la classe `Pile`

```cpp
#include <list>

template <typename Objet>
class Pile
{
public:
    Pile() { } // Équivalent à celui par défaut

    ~Pile()
    {
        laPile.clear();
    }

    void empiler(const Objet& x)
    {
        laPile.push_front(x); // empilement au début de la liste
    }

    // Suite prochaine diapo

private:
    std::list<Objet> laPile;
};
#include <list>

template <typename Objet>
class Pile
{
public:
    unsigned int taille() const
    {
        return laPile.size();
    }

    Objet depiler() // dépilement au début de la liste
    {
        if (taille() == 0) throw std::logic_error("La pile est vide");

        Objet ret = laPile.front(); // retourne le premier élément
        laPile.pop_front(); // enlève cet élément de la liste
        return ret;
    }
};
````



# 📌 Utilisation de la classe `Pile`

## Exemple de programme utilisant `Pile`

```cpp
#include "Pile.h"
using namespace std;

int main()
{
    Pile<int> maPile;

    for(int i = 1; i <= 10; i++)
    {
        maPile.empiler(i);
    }

    cout << "taille = " << maPile.taille() << endl;

    unsigned int n = maPile.taille();
    for(unsigned int i = 0; i < n; i++)
    {
        cout << maPile.depiler() << " ";
    }

    cout << endl;
    cout << "taille = " << maPile.taille() << endl;

    return 0;
}
````


### remarques 
- Avant d'empiler, on doit tester si la pile est vide
- Pas necessaire en ajoutenat parce que c'est dynamique




