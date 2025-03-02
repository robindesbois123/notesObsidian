structure auxilière parce qu'utilisé par d'autre structure



- Files 
	- FIFO:First in first out
	- PAPS : premier arrivé presmiier sorti
ex : 
- file d'attente cinema
- file pour impresison
- Processsus d'execution dans un systeme dexploitation

File = lites + gestion adaptée 


### Objetctif
- mettre en attente d'information dans le but de les recuperer plus tard
- Operation a supporter 
	- ajouter un nouvel element (enfiler,push)
	- oter l'élément le plkus ancien (defiler, pop)
- Specification
	- opération en O(1)
- Implementation 
	- implementation a l'aide d'une liste


## Définition de la classe `File`

```cpp
#include <list>

template <typename Objet>
class File
{
public:
    File() { } // Équivalent à celui par défaut

    ~File()
    {
        laFile.clear();
    }

    void enfiler(const Objet& x)
    {
        laFile.push_front(x); // enfilement au début de la liste
    }

    // Suite prochaine diapo

private:
    std::list<Objet> laFile;
};

#include <list>

template <typename Objet>
class File
{
public:
    Objet defiler() // défilement à la fin de la liste
    {
        if (taille() == 0) throw std::logic_error("La file est vide");

        Objet ret = laFile.back(); // retourne le dernier élément
        laFile.pop_back(); // enlève cet élément de la liste
        return ret;
    }

    unsigned int taille() const
    {
        return laFile.size();
    }
};
````

- remarques 
	- Avant de defiler, on doit tester si elle est vide
	- On ne doit pas tester si c'est pour enfiler
		- l'ajout d'un nouvel element est dynamique du à l'utilisation de la list


exemple dans le cours sur le triage de donnée