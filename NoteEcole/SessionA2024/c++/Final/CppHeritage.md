### **L’héritage : explications, rôle et lien avec ton projet**

---

### **1. Qu'est-ce que l'héritage ?**

L’héritage est un mécanisme de la programmation orientée objet qui permet à une classe (appelée **classe enfant** ou **dérivée**) d’hériter des propriétés et des méthodes d’une autre classe (appelée **classe parent** ou **de base**). Il permet :

- De partager du code commun entre plusieurs classes.
- D’établir une relation hiérarchique entre des classes.

---

### **2. Pourquoi utiliser l’héritage ?**

1. **Réduction de la duplication de code** : Les méthodes et attributs communs sont définis dans une seule classe parent.
2. **Organisation claire** : Les relations parent-enfant structurent le code et rendent les comportements réutilisables.
3. **Extensibilité** : Les classes enfants peuvent **spécialiser** ou **redéfinir** certains comportements de la classe parent.
4. **Polymorphisme** : Grâce à l’héritage, les classes enfants peuvent être manipulées via des références ou des pointeurs à la classe parent.

---

### **3. Comment l'as-tu appliqué dans ton projet ?**

Dans ton projet, l’héritage est central pour organiser les entités liées aux personnes (`Personne`, `Electeur`, `Candidat`) :

- **Classe parent : `Personne`**  
    Contient les attributs et comportements communs à toutes les personnes (nom, prénom, NAS).
- **Classe enfant 1 : `Electeur`**  
    Spécialise `Personne` pour ajouter des informations propres aux électeurs, comme leur circonscription.
- **Classe enfant 2 : `Candidat`**  
    Spécialise `Personne` pour inclure des informations spécifiques aux candidats, comme leur programme électoral.

#### **Structure de l’héritage :**

plaintext

Copy code

`Personne ├── Electeur └── Candidat`

---

### **4. Exemple concret d’héritage dans ton projet**

#### **Classe parent : `Personne`**

La classe parent `Personne` contient les attributs communs à toutes les personnes et des méthodes génériques.

cpp

Copy code

`class Personne { public:     Personne(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas)         : m_nom(p_nom), m_prenom(p_prenom), m_nas(p_nas) {         verifierInvariant();     }      virtual ~Personne() = default;      std::string getNom() const { return m_nom; }     std::string getNas() const { return m_nas; }      virtual std::string afficher() const {         return "Nom: " + m_nom + ", Prénom: " + m_prenom + ", NAS: " + m_nas;     }  protected:     void verifierInvariant() const {         assert(m_nas.size() == 9 && std::all_of(m_nas.begin(), m_nas.end(), ::isdigit) && "NAS invalide !");     }  private:     std::string m_nom;     std::string m_prenom;     std::string m_nas; };`

---

#### **Classe enfant : `Electeur`**

La classe `Electeur` hérite de `Personne` et ajoute des attributs et des comportements spécifiques aux électeurs.

cpp

Copy code

`class Electeur : public Personne { public:     Electeur(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas, const std::string& p_circonscription)         : Personne(p_nom, p_prenom, p_nas), m_circonscription(p_circonscription) {}      std::string afficher() const override {         return Personne::afficher() + ", Circonscription: " + m_circonscription;     }  private:     std::string m_circonscription; };`

---

#### **Classe enfant : `Candidat`**

La classe `Candidat` hérite de `Personne` et ajoute des attributs spécifiques, comme le programme électoral.

cpp

Copy code

`class Candidat : public Personne { public:     Candidat(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas, const std::string& p_programme)         : Personne(p_nom, p_prenom, p_nas), m_programme(p_programme) {}      std::string afficher() const override {         return Personne::afficher() + ", Programme: " + m_programme;     }  private:     std::string m_programme; };`

---

### **5. Lien entre héritage et polymorphisme**

Grâce à l’héritage, le polymorphisme devient possible. Par exemple, tu peux manipuler une liste d’objets `Personne` contenant à la fois des `Electeur` et des `Candidat`. La méthode `afficher` appellera automatiquement la version correcte en fonction du type réel de l’objet.

#### Exemple :

cpp

Copy code

`std::vector<std::unique_ptr<Personne>> personnes;  personnes.push_back(std::make_unique<Electeur>("Martin", "Sophie", "123456789", "Montreal")); personnes.push_back(std::make_unique<Candidat>("Dupont", "Jean", "987654321", "Économie verte"));  for (const auto& personne : personnes) {     std::cout << personne->afficher() << std::endl; // Affiche les détails spécifiques à chaque classe }`

---

### **6. Points importants pour écrire un code utilisant l’héritage**

#### a. **Constructeurs**

- Les classes enfants doivent appeler explicitement le constructeur de la classe parent pour initialiser les attributs hérités.

Exemple :

cpp

Copy code

`Electeur(const std::string& p_nom, const std::string& p_prenom, const std::string& p_nas, const std::string& p_circonscription)     : Personne(p_nom, p_prenom, p_nas), m_circonscription(p_circonscription) {}`

#### b. **Destructeurs virtuels**

Si une classe parent est utilisée polymorphiquement (avec des pointeurs ou références), son destructeur doit être déclaré comme **virtuel** pour assurer la destruction correcte des objets enfants.

cpp

Copy code

`virtual ~Personne() = default;`

#### c. **Spécialisation des méthodes**

Les classes enfants peuvent redéfinir les méthodes de la classe parent à l’aide de `override`.

cpp

Copy code

`std::string afficher() const override;`

#### d. **Protéger les données sensibles**

Les attributs de la classe parent doivent être déclarés comme `protected` ou `private` pour éviter un accès direct non contrôlé depuis les classes enfants.

---

### **7. Lien entre héritage et la théorie du contrat**

L’héritage respecte la **théorie du contrat**, car :

- La classe parent définit le **contrat** (préconditions, postconditions, invariants) que les classes enfants doivent respecter.
- Les classes enfants peuvent ajouter des comportements spécifiques tout en maintenant ce contrat.

Exemple :

- La méthode `afficher` dans `Personne` garantit que les informations de base d’une personne sont affichées.
- `Electeur` et `Candidat` étendent ce contrat en ajoutant des informations supplémentaires (circonscription ou programme).

---

### **8. Limites de l’héritage**

Bien que l’héritage soit puissant, il a des limites :

1. **Couplage fort** : Les classes enfants dépendent fortement de la classe parent. Un changement dans le parent peut affecter tous les enfants.
2. **Pas toujours approprié** : Si les classes n’ont pas de relation naturelle de parent-enfant, préfère la composition.
### **9. Résumé simple**

- **Héritage** : Permet à une classe enfant de réutiliser et spécialiser le comportement d’une classe parent.
- **Ton projet** :
    - `Personne` : Classe parent avec les attributs et méthodes communs.
    - `Electeur` et `Candidat` : Spécialisent `Personne` pour inclure des comportements spécifiques.
    - Utilisation du polymorphisme pour manipuler des objets `Personne` sans connaître leur type réel.
- **Éléments clés pour écrire du code avec héritage** :
    1. Appelle explicitement le constructeur parent.
    2. Utilise des destructeurs virtuels.
    3. Spécialise les comportements avec `override`.
    4. Protège les données sensibles dans le parent.
