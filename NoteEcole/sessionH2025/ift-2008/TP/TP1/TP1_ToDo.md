### 📌 **Dans `Bibliotheque.cpp`** :

1. **Constructeur de copie** `Bibliotheque::Bibliotheque(const Bibliotheque& p_autre)`
2. **Surcharge de l'opérateur d'affectation** `Bibliotheque& Bibliotheque::operator=(const Bibliotheque& p_autre)`
3. **`chargerDonnees(const std::string& p_nomFichier)`** → Charger les données depuis un fichier.
4. **`ajouterLivre(const Livre& p_livre)`** → Ajouter un livre à la bibliothèque.
5. **`ajouterEmprunteur(const Emprunteur& p_emprunteur)`** → Ajouter un emprunteur.
6. **`emprunterLivre(int p_idLivre, int p_matricule)`** → Un emprunteur emprunte un livre.
7. **`retournerLivre(int p_idLivre)`** → Un emprunteur retourne un livre.
8. **`reqLivreParId(int p_id)`** → Retourne une référence à un livre à partir de son ID.

---

### 📌 **Dans `Emprunteur.cpp`** :

1. **Constructeur** `Emprunteur::Emprunteur(int p_matricule, const std::string& p_prenom, const std::string& p_nom)`
2. **Constructeur de copie** `Emprunteur::Emprunteur(const Emprunteur& p_autre)`
3. **Surcharge de l'opérateur d'affectation** `Emprunteur& Emprunteur::operator=(const Emprunteur& p_autre)`
4. **`reqMatricule() const`** → Retourne le matricule de l'emprunteur.
5. **`reqPrenom() const`** → Retourne le prénom de l'emprunteur.
6. **`reqNom() const`** → Retourne le nom de l'emprunteur.
7. **`asgPrenom(const std::string& p_prenom)`** → Assigne un prénom à l'emprunteur.
8. **`asgNom(const std::string& p_nom)`** → Assigne un nom à l'emprunteur.
9. **`reqNombreLivresEmpruntes() const`** → Retourne le nombre de livres empruntés.
10. **`ajouterLivre(const Livre& p_livre)`** → Ajoute un livre à la liste des emprunts.
11. **`retirerLivre(int p_id)`** → Retire un livre de la liste des emprunts.

---

### 📌 **Dans `Livre.cpp`** :

1. **Constructeur** `Livre::Livre(int p_id, const std::string& p_titre, const std::string& p_auteur, bool p_estDisponible)` (Fait)
2. **Constructeur de copie** `Livre::Livre(const Livre& p_autre)` (Fait)
3. **Surcharge de l'opérateur d'affectation** `Livre& Livre::operator=(const Livre& p_autre)`
4. **`reqId() const`** → Retourne l'ID du livre. (FAIT)
5. **`reqTitre() const`** → Retourne le titre du livre. (FAIT)
6. **`reqAuteur() const`** → Retourne l'auteur du livre. (FAIT)
7. **`reqEstDisponible() const`** → Indique si le livre est disponible. (FAIT)
8. **`reqDateRetour() const`** → Retourne la date de retour sous forme de chaîne. (FAIT)
9. **`estRetourDepasse() const`** → Vérifie si la date de retour est dépassée. (fait)
10. **`emprunter(int p_matricule)`** → Permet à un emprunteur d’emprunter le livre.
11. **`retourner()`** → Permet de retourner un livre. (FAIT)
12. **`ajouterEmprunteurEnAttente(int p_matricule)`** → Ajoute un emprunteur à la file d'attente.
13. **`retirerEmprunteurEnAttente()`** → Retire et retourne le prochain emprunteur en attente. (FAIT)
14. **`estEnAttente() const`** → Vérifie si des emprunteurs sont en attente. (FAIT)