
### **Les hiérarchies de classes : explications, rôle et lien avec ton projet**

---

### **1. Qu'est-ce qu'une hiérarchie de classe ?**

Une hiérarchie de classe est une structure en programmation orientée objet où les classes sont organisées selon une relation parent-enfant (héritage). Cela permet de :

- Partager du code commun dans une classe parent.
- Spécialiser ou personnaliser certaines fonctionnalités dans les classes enfants.

---

### **2. Pourquoi utiliser une hiérarchie de classe ?**

1. **Réutilisation du code** : Les classes enfants héritent des méthodes et attributs communs de la classe parent, ce qui évite de dupliquer le code.
2. **Clarté** : L’héritage aide à structurer le code en groupes logiques (général -> spécifique).
3. **Extensibilité** : Il est facile d’ajouter de nouvelles classes en s’appuyant sur une base commune.
4. **Polymorphisme** : Les classes enfants peuvent être utilisées de manière interchangeable avec la classe parent, ce qui simplifie le code.

---

### **3. Comment les as-tu appliquées dans ton projet ?**

Dans ton projet, tu as une hiérarchie de classes basée sur une classe de base `Personne`. Elle est ensuite spécialisée en `Electeur` et `Candidat`. Ces deux dernières sont ensuite utilisées dans la classe `Circonscription`.

#### **Structure de la hiérarchie**

- **Classe parent** : `Personne`
    - Contient les attributs et méthodes communs à toutes les personnes (nom, prénom, NAS).
- **Classe enfant 1** : `Electeur`
    - Spécialise `Personne` en ajoutant des informations spécifiques aux électeurs, comme leur circonscription.
- **Classe enfant 2** : `Candidat`
    - Spécialise `Personne` en ajoutant des informations spécifiques aux candidats, comme leur programme électoral.

---

### **4. Exemple concret**

#### a. **Classe de base : `Personne`**

Elle sert de base pour toutes les entités humaines. Elle contient :

- Les attributs partagés : nom, prénom, NAS.
- Les méthodes communes : getters, setters, affichage.

cpp

Copy code

`class Personne { public:     Personne(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas)         : m_nom(p_nom), m_prenom(p_prenom), m_nas(p_nas) {         verifierInvariant();     }      virtual ~Personne() = default; // Virtual pour un polymorphisme correct      std::string getNom() const { return m_nom; }     std::string getNas() const { return m_nas; }      virtual std::string afficher() const {         return "Nom: " + m_nom + ", Prénom: " + m_prenom + ", NAS: " + m_nas;     }  protected:     void verifierInvariant() const {         assert(m_nas.size() == 9 && std::all_of(m_nas.begin(), m_nas.end(), ::isdigit) && "NAS invalide !");     }  private:     std::string m_nom;     std::string m_prenom;     std::string m_nas; };`

#### b. **Classe dérivée : `Electeur`**

Elle hérite de `Personne` et ajoute des attributs spécifiques aux électeurs.

cpp

Copy code

`class Electeur : public Personne { public:     Electeur(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas, const std::string& p_circonscription)         : Personne(p_nom, p_prenom, p_nas), m_circonscription(p_circonscription) {}      std::string afficher() const override {         return Personne::afficher() + ", Circonscription: " + m_circonscription;     }  private:     std::string m_circonscription; };`

#### c. **Classe dérivée : `Candidat`**

Elle hérite de `Personne` et ajoute des attributs spécifiques aux candidats.

cpp

Copy code

`class Candidat : public Personne { public:     Candidat(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas, const std::string& p_programme)         : Personne(p_nom, p_prenom, p_nas), m_programme(p_programme) {}      std::string afficher() const override {         return Personne::afficher() + ", Programme: " + m_programme;     }  private:     std::string m_programme; };`




### **6. Écriture et gestion des hiérarchies de classes**

#### a. **Principes à respecter**

1. **Favoriser l’héritage public** : Permet aux classes enfants de partager les comportements de la classe parent.
2. **Prévoir les destructeurs virtuels** : Pour assurer une destruction correcte des objets dans une hiérarchie polymorphique.
3. **Utiliser `override`** : Marque les méthodes redéfinies pour éviter des erreurs accidentelles.

#### b. **Privilégier la composition au lieu de l’héritage si nécessaire**

Si deux classes partagent des comportements similaires sans relation parent-enfant, préfère la **composition**. Par exemple, une classe `Adresse` pourrait être incluse dans `Personne` pour gérer des adresses.

---

### **7. Résumé simple**

- **Hiérarchie de classes** : Structure en parent-enfant pour partager des comportements communs tout en permettant la spécialisation.
- **Ton projet** :
    - Classe `Personne` pour les attributs communs.
    - `Electeur` et `Candidat` pour les spécialisations.
    - Utilisation du polymorphisme pour manipuler `Electeur` et `Candidat` de manière uniforme.
- **Points importants pour écrire les hiérarchies** :
    1. Identifier les comportements communs pour les classes parent.
    2. Spécialiser les classes enfants sans dupliquer de code.
    3. Utiliser le polymorphisme pour une manipulation flexible des objets.