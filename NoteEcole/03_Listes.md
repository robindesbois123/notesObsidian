### But 
- Séquence ordonnées d'élément d'un certain type
	- l'ordre signifie que chaque élément possede une position dans la liste
	- Il y a aussi la position courante
- Operation à supporter
	- Suppression d'un element situé a la position courrante
	- Insertion d'un élément situé avant celui de la position courrante
	- acceder a l'élément suivant (++)
	- Accéder a l'élément précedent
- Specification 
	- Ces 4 operations se font en temps O(1)
- Reamrque : absence d'operation se rednre a tel élément de la liste
	- Pour se rendre a un tel element dans la liste il faut looper
-




### Utilité 
- Utile pour sa rapidité
- tres rapide vs un vecteur et un tableau 
- les element n'ont pas des places contigue dans la memoire 



### comparaison entre liste et [[03_Vecteurs]]

- Liste
	- Temps d'insertion/supression (à la position courrante) O(1)
	- temps d'acces a une postion arbitraire O(n)
- Pour vecteur
	- Temps d'accès a une position arbitraire en O(1)
	- Temps d'insertion /suppression en O(n)
- Liste pour inserer/supprimer souvenbt
- à l'inverse, Vecteur
- 


### Classe List
Une Liste a tjr trois parties
1. Une partie contenant l'élément stocké 
2. Une partie contenant un pointeur pointant le noeud suivant 
3. Une partie contenant un pointeur pointant le noeud précédent 
![[Pasted image 20250215212521.png]]


### Classe Interne de List pour les noeuds

# 📌 Implémentation d'une liste chaînée en C++

## Définition de la classe `List`

```cpp
template <typename Object>
class List
{
public:
    // ....

private:
    struct Node
    {
        Object data;  // la donnée stockée
        Node* prev;   // adresse du nœud précédent
        Node* next;   // adresse du nœud suivant

        Node(const Object& d = Object(), Node* p = 0, Node* n = 0)
            : data(d), prev(p), next(n) { } // constructeur
    };

    int theSize; // nb d’éléments contenus dans la liste
    Node* head;  // pointeur au nœud du début de la liste
    Node* tail;  // pointeur au nœud de fin de la liste

    // ..
};
```



### Les noeuds 

- OBjet unique aux liste
- accès facile au noeud suivant/precedant en utilisant next et prev de node
- le noeud de tete et de fin servent de sentinelle, il ny a pas de donnée utilisateur dedans
![[Pasted image 20250215214102.png]]

### Les sentinelle
- simplifie les methode d'insertion et de supresiion 
	- evite d'Avoir a mettre a jour les pointeur head et tail de List
- on utiliste un [[03_Iterateur]] pour se promener dans laz list
	- begin pointe sur sentinelle de debut
	- end l'inverse


### 📌 Constructeurs et destructeur de `List`

#### Constructeur et destructeur

```cpp
template <typename Object>
class List
{
public:
    List() { init(); }

    List(const List& rhs) // constructeur de copie
    {
        init();
        *this = rhs; // utilise la surcharge de l’opérateur = (défini plus loin)
    }

    ~List()
    {
        clear(); // méthode à définir : efface tous les nœuds non sentinelle
        delete head;
        delete tail;
    }

    // ... Suite prochaine page
};


template <typename Object>
class List
{
private:
    // ...
    void init()
    {
        // création des sentinelles
        theSize = 0;
        head = new Node;
        tail = new Node;
        head->next = tail;
        tail->prev = head;
        head->prev = tail->next = 0;
    }
};
````

![[Pasted image 20250215220355.png]]

![[Pasted image 20250215220408.png]]


![[Pasted image 20250215220428.png]]



### Remarques
- list fourni un itérateur const_iteratort qui permet d'acceder en lecture seul 
- Plusieurs autres methode
- on ne peut pas trouver d'élément il faut loop
- on peut faire une liste dans un tableau dynamique voir les notes
- 


### Autre liste 
- Liste simpoleemnt chainé
	- chaque noeud possède un seul pointeur: le noeud suivant
	- one way
	- cela simplifie les methodes
- Liste circulaire
	- liste simplemnt chainé mais que le pointeru next du last node pointe vers le first node
	- ni debut ni fin
	- maj du dernier pointeur lirs de supression du dernier noeud
	- 