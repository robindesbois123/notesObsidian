garde certains aspect du [[DomaineDuModèle]]
Par contre certasines classes vont disparaitre

Dans le diagramme de classe, on defini certaine methode et certains attribut

![[Pasted image 20250208101125.png]]


on peut aussi transformer les relations entre les classes


### Composition (est constitué de)
- ligne avec losange plein 
- relation tout-partie avec inclusion physique

![[Pasted image 20250208102842.png]]

- le parent a pour seul role de creer et delete l'enfant
- Une instance peut faire partie d'un seul parent a la fois 
![[Pasted image 20250208102949.png]]



### Agregation ( à un)

- Relation tout-partie (moins forte que la composition)
- possède des role comme une association normale
- ligne avec losange vide
-  rien de plus qu'une relation normale mais tres utile en pratique pour la communication

![[Pasted image 20250208103431.png]]




#### représentation des attributs

Les annotations 


concept de clée je pense

| notation                                 | Description                             |
| ---------------------------------------- | --------------------------------------- |
| currentSale : Sale                       | Dit que currentSale a une instance Sale |
| Faire une fleche du parent vers l'enfant | Dit la meme chose                       |
|                                          |                                         |
![[Pasted image 20250208103906.png]]



#### Liste et vecteurs
![[Pasted image 20250208104235.png]]


#### Association qualifiées

un peu l'équivalent d'un id dans une BD qui relierait une table a une autre mais dans notre cas, c'est des objets
![[Pasted image 20250208105704.png]]


#### Contraintes

| **Type de Contrainte**                     | **Explication**                                                  | **Exemple**                                                 |
| ------------------------------------------ | ---------------------------------------------------------------- | ----------------------------------------------------------- |
| **Contrainte sur une classe**              | Règles applicables aux objets d’une classe.                      | `{age >= 18}` pour une classe `Personne`.                   |
| **Contrainte sur une association**         | Restrictions sur les relations entre objets.                     | `{chaque employé ne peut être associé qu'à un seul poste}`. |
| **Contrainte de multiplicité**             | Limite le nombre d'instances dans une relation.                  | `1..*` signifie qu’il doit y avoir **au moins 1** instance. |
| **Contrainte d’unicité**                   | Une propriété ou une combinaison de propriétés doit être unique. | `{numéroSécuritéSociale unique}` pour une classe `Employé`. |
| **Contrainte d’agrégation ou composition** | Spécifie qu'un élément ne peut pas exister sans son conteneur.   | Un `Moteur` **doit appartenir** à une `Voiture`.            |
| **Contrainte de dérivation**               | Une valeur est calculée à partir d'autres.                       | `{salaireTotal = salaireBase + primes}`.                    |
![[Pasted image 20250208105838.png]]




### Generalisation (héritage)
- représenté par une flèche qui va de la classe spécifique vers la classe generale
- il faut se dire cete chose "est un" autre qqc

exemeple
- une *voiture* est un *véhicule*

### Interfaces 

- une classe contient seulement des classes d'implementation 
- une classe Interface :
	- n'a pas d'atribut
	- contient des methodes que toutes sorte de classe peuvnt utiliser 
est not.é avec un socket


exemples: 
- Un *Avion* peut voler, un *Oiseau* aussi
 



## Recap 


|**Concept UML**|**Type de relation**|**Signification**|**Exemple**|
|---|---|---|---|
|**Héritage (Généralisation)**|"Est un" (`is-a`)|Une classe dérivée hérite des attributs/méthodes d’une classe mère.|`Voiture` **est un** `Véhicule`|
|**Composition**|"Fait partie de" (`has-a` fort)|Une partie **ne peut pas exister** sans son tout.|Un `Cœur` fait partie d'un `Humain`|
|**Agrégation**|"Fait partie de" (`has-a` faible)|Une partie **peut exister indépendamment** de son tout.|Une `Équipe` a des `Joueurs` (qui existent seuls)|



différence entre heritage et interface

|**Concept**|**Héritage (Classe Abstraite)**|**Interface**|
|---|---|---|
|**Type de relation**|"Est un" (`is-a`)|"Peut faire" (`can-do`)|
|**Peut contenir des attributs ?**|✅ Oui|❌ Non (uniquement des constantes)|
|**Peut contenir des méthodes avec implémentation ?**|✅ Oui (méthodes abstraites et concrètes)|❌ Non (seulement des signatures)|
|**Peut être implémentée par plusieurs classes ?**|❌ Non (héritage simple)|✅ Oui (une classe peut implémenter plusieurs interfaces)|
|**Utilisation typique**|**Modéliser une relation parent-enfant**|**Définir des capacités communes** à plusieurs classes non liées|
![[Pasted image 20250208111708.png]]






### A comprendre : 
faire la lecture de : Version anglaise: 12,16,13,34,35

- Anlayse, Design
- Diagramme des classe 
	- conceptuelle 
	- classe de conception 
- Architecture logique / logicielle
- Architecture en couche
- Architecture couche classique
