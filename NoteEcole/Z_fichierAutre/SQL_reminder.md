# Commandes de base MySQL pour gérer des tables

## **1. Créer une table**

La commande de base pour créer une table dans MySQL est la suivante :

```sql
CREATE TABLE nom_table (
    colonne1 TYPE DONNEES [options],
    colonne2 TYPE DONNEES [options],
    ...
);
```

### Exemple :

```sql
CREATE TABLE utilisateurs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nom VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    date_creation TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## **2. Afficher la structure d'une table**

Pour voir la structure d'une table (colonnes et types de données) :

```sql
DESCRIBE nom_table;
```

### Exemple :

```sql
DESCRIBE utilisateurs;
```

---

## **3. Modifier une table**

### **Ajouter une colonne :**

```sql
ALTER TABLE nom_table ADD colonne TYPE DONNEES [options];
```

### Exemple :

```sql
ALTER TABLE utilisateurs ADD telephone VARCHAR(15);
```

### **Supprimer une colonne :**

```sql
ALTER TABLE nom_table DROP COLUMN colonne;
```

### Exemple :

```sql
ALTER TABLE utilisateurs DROP COLUMN telephone;
```

### **Modifier une colonne existante :**

```sql
ALTER TABLE nom_table MODIFY colonne TYPE DONNEES [options];
```

### Exemple :

```sql
ALTER TABLE utilisateurs MODIFY nom VARCHAR(200) NOT NULL;
```

### **Renommer une colonne :**

```sql
ALTER TABLE nom_table CHANGE ancienne_colonne nouvelle_colonne TYPE DONNEES [options];
```

### Exemple :

```sql
ALTER TABLE utilisateurs CHANGE email courriel VARCHAR(100) UNIQUE NOT NULL;
```

### **Renommer une table :**

```sql
RENAME TABLE ancienne_table TO nouvelle_table;
```

### Exemple :

```sql
RENAME TABLE utilisateurs TO clients;
```

---

## **4. Supprimer une table**

Pour supprimer une table et toutes ses données :

```sql
DROP TABLE nom_table;
```

### Exemple :

```sql
DROP TABLE utilisateurs;
```

---

## **5. Insérer des données**

Pour ajouter une ligne dans une table :

```sql
INSERT INTO nom_table (colonne1, colonne2, ...) VALUES (valeur1, valeur2, ...);
```

### Exemple :

```sql
INSERT INTO utilisateurs (nom, email) VALUES ('Alice', 'alice@example.com');
```

---

## **6. Mettre à jour des données**

Pour modifier des données existantes :

```sql
UPDATE nom_table SET colonne1 = nouvelle_valeur WHERE condition;
```

### Exemple :

```sql
UPDATE utilisateurs SET nom = 'Alice Dupont' WHERE id = 1;
```

---

## **7. Supprimer des données**

Pour supprimer des lignes spécifiques :

```sql
DELETE FROM nom_table WHERE condition;
```

### Exemple :

```sql
DELETE FROM utilisateurs WHERE id = 1;
```

Pour supprimer **toutes les lignes** d'une table (attention !) :

```sql
DELETE FROM nom_table;
```

---

## **8. Lire des données**

Pour récupérer des données d'une table :

```sql
SELECT colonne1, colonne2 FROM nom_table WHERE condition;
```

### Exemple :

```sql
SELECT * FROM utilisateurs;
SELECT nom, email FROM utilisateurs WHERE nom LIKE 'Alice%';
```

---

## **9. Sauvegarde de la structure ou des données**

Pour sauvegarder une table en SQL :

```bash
mysqldump -u utilisateur -p nom_base nom_table > sauvegarde.sql
```

---

## **10. Importer une table sauvegardée**

Pour réimporter une table depuis un fichier `.sql` :

```bash
mysql -u utilisateur -p nom_base < sauvegarde.sql
```