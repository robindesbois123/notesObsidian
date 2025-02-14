### **Le polymorphisme : explications, rôle et lien avec ton projet**

---

### **1. Qu'est-ce que le polymorphisme ?**

Le polymorphisme est une capacité en programmation orientée objet permettant à un objet de prendre différentes formes selon son type réel. En d'autres termes :

- Une méthode appelée sur un objet peut se comporter différemment selon la classe à laquelle appartient cet objet.
- C’est une extension naturelle de l’héritage, où une classe parent définit une interface commune que les classes enfants spécialisent.

---

### **2. Pourquoi utiliser le polymorphisme ?**

1. **Flexibilité** : Tu peux manipuler différents types d'objets (héritant d'une même classe parent) avec une seule interface commune.
2. **Extensibilité** : Ajouter de nouveaux comportements (en créant de nouvelles classes enfants) ne nécessite pas de modifier le code existant.
3. **Lisibilité** : Le code devient plus simple, car il repose sur une interface commune au lieu de vérifier manuellement les types des objets.

---

### **3. Types de polymorphisme en C++**

#### a. **Polymorphisme au moment de l'exécution (dynamique)**

C’est ce que tu utilises dans ton projet via les classes `Personne`, `Electeur` et `Candidat`.  
Il repose sur :

- **Héritage** : Les classes enfants héritent de la classe parent.
- **Méthodes virtuelles** : Définies dans la classe parent et redéfinies dans les classes enfants.

#### b. **Polymorphisme au moment de la compilation (statique)**

C’est le polymorphisme lié à la surcharge de fonctions ou d’opérateurs. Ce n'est pas directement lié à ton projet actuel.

---

### **4. Comment l'as-tu appliqué dans ton projet ?**

Dans ton projet, tu utilises le polymorphisme au moment de l'exécution via une hiérarchie de classes (`Personne`, `Electeur`, et `Candidat`). La méthode `afficher()` est définie comme **virtuelle** dans `Personne` et redéfinie dans `Electeur` et `Candidat`.

#### **Structure de base :**

- `Personne` : Classe parent qui définit une interface commune (`afficher()`).
- `Electeur` et `Candidat` : Classes enfants qui redéfinissent cette méthode pour inclure des détails spécifiques.

### **5. Exemple concret dans ton projet**

#### a. **Classe parent : `Personne`**

La méthode `afficher` est déclarée **virtuelle**, ce qui permet aux classes enfants de la redéfinir.

cpp

Copy code

`class Personne { public:     Personne(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas)         : m_nom(p_nom), m_prenom(p_prenom), m_nas(p_nas) {}      virtual ~Personne() = default;      virtual std::string afficher() const {         return "Nom: " + m_nom + ", Prénom: " + m_prenom + ", NAS: " + m_nas;     }  private:     std::string m_nom;     std::string m_prenom;     std::string m_nas; };`

---

#### b. **Classe enfant : `Electeur`**

Elle redéfinit `afficher()` pour inclure les informations spécifiques à un électeur.

cpp

Copy code

`class Electeur : public Personne { public:     Electeur(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas, const std::string& p_circonscription)         : Personne(p_nom, p_prenom, p_nas), m_circonscription(p_circonscription) {}      std::string afficher() const override {         return Personne::afficher() + ", Circonscription: " + m_circonscription;     }  private:     std::string m_circonscription; };`

---

#### c. **Classe enfant : `Candidat`**

Elle redéfinit également `afficher()` pour inclure des détails spécifiques aux candidats.

cpp

Copy code

`class Candidat : public Personne { public:     Candidat(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas, const std::string& p_programme)         : Personne(p_nom, p_prenom, p_nas), m_programme(p_programme) {}      std::string afficher() const override {         return Personne::afficher() + ", Programme: " + m_programme;     }  private:     std::string m_programme; };`

---

### **6. Exemple d’utilisation du polymorphisme**

Dans ta classe `Circonscription`, tu manipules une liste d'objets `Personne` qui peuvent être des `Electeur` ou des `Candidat`. Grâce au polymorphisme, tu peux appeler `afficher()` sur tous ces objets sans te soucier de leur type réel.

#### Exemple :

cpp

Copy code

`void Circonscription::afficherPersonnes() const {     for (const auto& personne : m_personnes) {         std::cout << personne->afficher() << std::endl; // Appelle la version correcte de afficher()     } }`

---

### **7. Écriture et gestion du polymorphisme**

#### a. **Méthodes virtuelles**

Pour que le polymorphisme fonctionne, les méthodes de la classe parent doivent être déclarées comme **virtuelles**.

cpp

Copy code

`virtual std::string afficher() const;`

#### b. **Utilisation de `override`**

Dans les classes enfants, utilise `override` pour indiquer que tu redéfinis une méthode virtuelle. Cela permet d’éviter les erreurs accidentelles (par exemple, si tu changes le nom ou la signature de la méthode).

cpp

Copy code

`std::string afficher() const override;`

#### c. **Destructeur virtuel**

Si tu utilises le polymorphisme, il est crucial de déclarer le destructeur de la classe parent comme **virtuel**, afin de garantir que le destructeur des classes enfants est correctement appelé.

cpp

Copy code

`virtual ~Personne() = default;`

#### d. **Utilisation des pointeurs intelligents**

Pour manipuler des objets polymorphiques, utilise des pointeurs intelligents (`std::unique_ptr` ou `std::shared_ptr`). Cela permet une gestion automatique de la mémoire.

---

### **8. Lien entre polymorphisme et théorie du contrat**

Le polymorphisme fonctionne en parallèle avec la **théorie du contrat** :

1. **Classe parent** : Définit les préconditions, postconditions et invariants communs pour toutes les classes enfants.
2. **Classe enfant** : Spécialise ces contrats en ajoutant des comportements spécifiques tout en respectant les attentes définies par la classe parent.

Par exemple :

- La classe `Personne` garantit que la méthode `afficher()` renvoie des informations sur la personne.
- Les classes `Electeur` et `Candidat` ajoutent des informations spécifiques, tout en respectant ce contrat.

---

### **9. Résumé simple**

- **Polymorphisme** : Permet d’appeler des méthodes sur des objets sans connaître leur type réel.
- **Ton projet** :
    - Classe parent `Personne` avec une méthode virtuelle `afficher()`.
    - Classes enfants `Electeur` et `Candidat` redéfinissant cette méthode.
    - Liste polymorphique dans `Circonscription` manipulant des `Personne`.
- **Éléments clés pour écrire un code polymorphique** :
    1. Déclare les méthodes de la classe parent comme `virtual`.
    2. Utilise `override` pour marquer les redéfinitions dans les classes enfants.
    3. Utilise un destructeur virtuel pour éviter les fuites de mémoire.