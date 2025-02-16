Un itérateur permet de for each element in elements

- Begin() iterateur pointant le premier leement 
- End() derneire element 


### exemple [[03_Vecteurs]]

#### 📌 Le type `vector<int>` et son itérateur

###### Utilisation d'un itérateur avec `vector<int>`

```cpp
void exempleIteratorVector(vector<int>& x)
{
    int sum = 0;
    for(vector<int>::iterator i = x.begin(); i != x.end(); ++i)
    {
        sum += *i; // déréférenciation de l’itérateur donne l’élément pointé
    }
}

```



deux type d'itérateur 
- `container::iterator//mode lecture et ecriture`
- `container::const_iterator//mode lecture seulement
Les operatuer principaux sont 
- `*` donnant acces a la valuer
- ++ et -- pour aller a l'elément suivant 
- surchage de == et != pour comparer les iterateur





## List iterator


Cette classe interne est un membre public de list

### 📌 Implémentation de la classe `iterator` pour `List`

### Définition de la classe `iterator`

```cpp
class iterator
{
public:
    iterator() : current(0) {}; // constructeur sans paramètre

    Object& operator* () // permet à l’appelant de modifier `current->data`
    {
        return current->data;
    }

    // ... (suite page suivante)

private:
    // On ne veut pas permettre aux utilisateurs de `List` d’accéder à ces éléments
    Node* current;

    iterator(Node* p) : current(p) { } // constructeur appelé par des méthodes de `List`

    Friend class List<Object>; // rend accessible cette section aux membres de `List`
};
```


### Opérateurs d'incrémentation et de décrémentation (préfixe)

```cpp
class iterator
{
public:
    iterator& operator++ () // version préfixe
    {
        current = current->next;
        return *this;
    }

    iterator& operator-- () // version préfixe
    {
        current = current->prev;
        return *this;
    }

    // ... (suite page suivante)
};


### Autre utilisation
- surchage de operator 
class iterator
{
public:
    // ...

    iterator operator++ (int) // version postfixe
    {
        iterator old = *this;
        ++(*this); // version préfixe de ++ utilisée ici
        return old;
    }

    iterator operator-- (int) // version postfixe
    {
        iterator old = *this;
        --(*this); // version préfixe de -- utilisée ici
        return old;
    }

private:
    // ...
};
class iterator
{
public:
    // ...

    bool operator==(const iterator& rhs) const
    {
        return current == rhs.current;
    }

    bool operator!=(const iterator& rhs) const
    {
        return current != rhs.current;
    }

private:
    // ...
};


````

### Autre methode de list 
- Surchage operator= (constructeur de copie) 
- `clear()` (destructeur) 
- `erase(const iterator & itr)` pour detruire le noeud pointé par itr
- `insert(const iterator &itr,const Object & x)` pour inserer un objet x à la qposition précédent le noeud pointé par itr
- `begin()` et `end()` permettant aux utilisateur de List d'obtenir un itérateur (pour parcourir la liste)


