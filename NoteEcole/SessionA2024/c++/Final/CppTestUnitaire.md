### **1. Qu'est-ce qu'un test unitaire ?**

Un **test unitaire** est une méthode qui teste une unité minimale de ton code (généralement une fonction ou une méthode) de manière isolée. Cela signifie que :

- On vérifie que cette unité se comporte comme attendu pour un ensemble donné d'entrées.
- On teste chaque unité **indépendamment** du reste du système.

---

### **2. Pourquoi faire des tests unitaires ?**

1. **Détecter les bugs rapidement** : En isolant chaque composant, les tests unitaires t’aident à trouver des erreurs dans des fonctions spécifiques.
2. **Garantir la robustesse** : Si ton code évolue, tu peux exécuter les tests pour vérifier que tout fonctionne encore correctement.
3. **Documenter le code** : Les tests montrent comment utiliser tes méthodes et classes.
4. **Réduire les régressions** : Lors d'ajouts ou modifications, ils assurent que tu n'as pas cassé quelque chose.

---

### **3. Comment les as-tu appliqués dans ton projet ?**

#### a. **Exemple pour la classe `Personne`**

Tu veux vérifier que la création d’un objet `Personne` respecte les préconditions et invariants.

##### **Cas testés :**

- La création d’une personne avec des données valides.
- La création d’une personne avec un NAS invalide (9 caractères numériques requis).
- La modification du NAS pour garantir l’invariant.