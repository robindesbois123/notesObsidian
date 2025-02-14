### **Gestion de la mémoire dans ton projet en C++**

La gestion de la mémoire est un aspect crucial en C++, particulièrement dans des projets comme le tien impliquant des hiérarchies de classes, des objets polymorphiques, et des structures de données dynamiques (listes, vecteurs, etc.). Voici comment elle s'applique à ton projet et les bonnes pratiques que tu dois respecter.

---

### **1. Pourquoi la gestion de la mémoire est importante ?**

1. **Éviter les fuites de mémoire** : Si un objet est créé dynamiquement mais jamais libéré, la mémoire reste allouée jusqu’à la fin du programme.
2. **Assurer la destruction correcte** : Dans des hiérarchies de classes, les destructeurs des classes enfants doivent être appelés pour libérer toutes les ressources.
3. **Optimiser les performances** : Une gestion incorrecte de la mémoire peut ralentir le programme ou consommer inutilement des ressources.

---

### **2. Cas spécifiques à ton projet**

#### a. **Hiérarchies de classes (`Personne`, `Electeur`, `Candidat`)**

Dans ton projet, tu manipules des objets polymorphiques via des pointeurs à la classe parent (`Personne`). Cela introduit deux défis :

- **Appeler le bon destructeur** : Si le destructeur de la classe parent n'est pas déclaré comme virtuel, seul celui-ci sera appelé, ce qui peut causer des fuites de mémoire.
- **Gestion des pointeurs dynamiques** : Les objets créés avec `new` doivent être libérés manuellement ou gérés avec des pointeurs intelligents.

#### b. **Structure de données dynamique dans `Circonscription`**

Ta classe `Circonscription` contient une liste d’objets polymorphiques (`Electeur`, `Candidat`). Si tu utilises des vecteurs ou des listes avec des pointeurs bruts (`Personne*`), tu dois t’assurer de libérer correctement chaque pointeur lorsque la `Circonscription` est détruite.

---

### **3. Bonnes pratiques pour la gestion de la mémoire**

#### a. **Utiliser des destructeurs virtuels**

Les destructeurs virtuels garantissent que lorsque tu détruis un objet via un pointeur à la classe parent, le destructeur de la classe enfant est également appelé.

Exemple dans `Personne` :

cpp

Copy code

`class Personne { public:     virtual ~Personne() = default; // Assure la destruction correcte des objets dérivés };`

---

#### b. **Utiliser des pointeurs intelligents**

Les pointeurs intelligents (`std::unique_ptr`, `std::shared_ptr`) automatisent la gestion de la mémoire en détruisant automatiquement les objets lorsque le pointeur sort de portée. Cela évite les fuites de mémoire.

Exemple pour la gestion des électeurs dans `Circonscription` :

cpp

Copy code

`#include <memory> #include <vector>  class Circonscription { private:     std::vector<std::unique_ptr<Personne>> m_personnes; // Liste polymorphique avec pointeurs intelligents  public:     void ajouterPersonne(std::unique_ptr<Personne> p_personne) {         m_personnes.push_back(std::move(p_personne));     } };`

#### Comment ajouter une personne :

cpp

Copy code

`std::unique_ptr<Personne> electeur = std::make_unique<Electeur>("Martin", "Sophie", "123456789", "Montreal"); circonscription.ajouterPersonne(std::move(electeur));`

Avantages :

1. Tu n’as plus besoin d’appeler `delete` manuellement.
2. Les objets sont automatiquement détruits quand ils sortent du vecteur ou que la `Circonscription` est détruite.

---

#### c. **Éviter les pointeurs bruts**

Les pointeurs bruts (`Personne*`) nécessitent une gestion manuelle de la mémoire avec `new` et `delete`. Cela augmente le risque de fuites de mémoire.

Exemple à éviter :

cpp

Copy code

`Personne* personne = new Electeur("Martin", "Sophie", "123456789", "Montreal"); // Ne pas oublier de faire delete plus tard ! delete personne;`

---

#### d. **RAII (Resource Acquisition Is Initialization)**

Le principe de RAII consiste à associer la durée de vie des objets à la portée. Cela signifie que les ressources (mémoire, fichiers, etc.) sont automatiquement libérées à la fin de leur portée.

Exemple avec `std::unique_ptr` :

cpp

Copy code

``{     std::unique_ptr<Electeur> electeur = std::make_unique<Electeur>("Martin", "Sophie", "123456789", "Montreal");     // L'objet `Electeur` sera automatiquement détruit ici. }``

---

### **4. Gestion des objets dans `Circonscription`**

#### Scénario avec une liste polymorphique

Si tu dois gérer une liste d’objets `Personne` (polymorphiques), utilise des pointeurs intelligents pour automatiser la mémoire.

Exemple complet :

cpp

Copy code

`#include <memory> #include <vector> #include <iostream>  class Circonscription { private:     std::vector<std::unique_ptr<Personne>> m_personnes;  public:     void ajouterPersonne(std::unique_ptr<Personne> p_personne) {         m_personnes.push_back(std::move(p_personne));     }      void afficherPersonnes() const {         for (const auto& personne : m_personnes) {             std::cout << personne->afficher() << std::endl;         }     } };  int main() {     Circonscription circonscription;      circonscription.ajouterPersonne(std::make_unique<Electeur>("Martin", "Sophie", "123456789", "Montreal"));     circonscription.ajouterPersonne(std::make_unique<Candidat>("Dupont", "Jean", "987654321", "Économie verte"));      circonscription.afficherPersonnes(); // Affiche les informations des personnes      // Pas besoin de delete, la mémoire est automatiquement libérée.     return 0; }`

---

### **5. Résumé des points clés**

1. **Déclare un destructeur virtuel dans la classe parent (`Personne`)** :
    
    cpp
    
    Copy code
    
    `virtual ~Personne() = default;`
    
2. **Utilise des pointeurs intelligents (`std::unique_ptr` ou `std::shared_ptr`)** pour automatiser la destruction des objets.
    
3. **Évite les pointeurs bruts (`Personne*`)** autant que possible. Ils nécessitent une gestion manuelle avec `delete`.
    
4. **Libère les ressources dans le destructeur des classes** si tu utilises des allocations dynamiques.
    
5. **RAII (Resource Acquisition Is Initialization)** : Fais en sorte que les ressources soient associées à des objets dont la durée de vie est bien gérée.