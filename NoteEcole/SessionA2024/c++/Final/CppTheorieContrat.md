La théorie du contrat repose sur le concept qu'une classe ou une méthode définit des **attentes claires** pour ses utilisateurs, comme un contrat juridique. Ce contrat comprend :

- **Les préconditions** : Ce qui doit être vrai avant l'exécution d'une méthode.
- **Les postconditions** : Ce qui sera garanti après l'exécution de la méthode.
- **Les invariants** : Les propriétés qui doivent toujours être vraies pour un objet, quel que soit son état.
### **2. Pourquoi utiliser la théorie du contrat ?**

Elle est utile pour :

1. **Garantir la robustesse** : Elle évite des comportements imprévus en assurant que les données et les états restent cohérents.
2. **Rendre le code compréhensible** : Les préconditions et postconditions agissent comme une documentation implicite.
3. **Faciliter le débogage** : Quand un bug survient, il est plus facile de savoir quel contrat a été violé.
4. **Encourager la réutilisabilité** : En définissant des attentes claires, les méthodes et classes peuvent être réutilisées plus facilement.

#### a. **Classe `Personne`**

- **Préconditions** : Un `Personne` doit avoir un nom, un prénom, et un numéro d'assurance sociale (NAS) valides.
- **Postconditions** : Après l'instanciation, un objet `Personne` contient ces informations correctement.
- **Invariants** :
    - Le NAS doit toujours respecter un format spécifique.
    - Le nom et le prénom ne doivent jamais être vides.