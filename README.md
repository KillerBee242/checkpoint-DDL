# checkpoint-DDL

**1. Création des tables avec SQL :**

```sql
-- Table Product
CREATE TABLE Product (
    Product_id VARCHAR2(20) PRIMARY KEY,
    Product_Name VARCHAR2(20) NOT NULL,
    Price NUMBER
);

-- Table Customer
CREATE TABLE Customer (
    Customer_id VARCHAR2(20) PRIMARY KEY,
    Customer_Name VARCHAR2(20) NOT NULL,
    Customer_Tel NUMBER
);

-- Table Orders
CREATE TABLE Orders (
    Customer_id VARCHAR2(20) REFERENCES Customer(Customer_id),
    Product_id VARCHAR2(20) REFERENCES Product(Product_id),
    Quantity NUMBER,
    Total_amount NUMBER,
    PRIMARY KEY (Customer_id, Product_id) -- Clé primaire composée
);
```

**Explication :**

*   **`CREATE TABLE` :**  Commande SQL pour créer une table.
*   **`VARCHAR2(20)` :** Type de données pour les chaînes de caractères de longueur maximale 20.
*   **`NUMBER` :** Type de données numérique.
*   **`PRIMARY KEY` :** Définit la clé primaire de la table.
*   **`NOT NULL` :** Contrainte pour indiquer qu'un champ ne peut pas être vide.
*   **`FOREIGN KEY` :** Définit une clé étrangère, qui référence la clé primaire d'une autre table.
*   **`REFERENCES` :** Utilisé avec `FOREIGN KEY` pour spécifier la table et la colonne référencées.
*   **Clé primaire composée :** Dans la table `Orders`, la clé primaire est composée de `Customer_id` et `Product_id`. Cela signifie que la combinaison de ces deux valeurs doit être unique pour chaque enregistrement.

**2. Ajout de la colonne Category à la table Product :**

```sql
ALTER TABLE Product
ADD Category VARCHAR2(20);
```

**Explication :**

*   **`ALTER TABLE` :** Commande SQL pour modifier la structure d'une table existante.
*   **`ADD` :** Utilisé pour ajouter une nouvelle colonne.

**3. Ajout de la colonne OrderDate à la table Orders avec valeur par défaut SYSDATE :**

```sql
ALTER TABLE Orders
ADD OrderDate DATE DEFAULT SYSDATE;
```

**Explication :**

*   **`DATE` :** Type de données pour les dates.
*   **`DEFAULT SYSDATE` :**  Spécifie que la valeur par défaut pour `OrderDate` est la date et l'heure actuelles du système au moment de l'insertion d'un nouvel enregistrement.
