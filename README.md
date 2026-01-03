# SQL-Apprentissage
Ce dépôt est destiné à l’apprentissage de SQL.



##### - Types de données principaux: 

 - *INT* : Integer
 - *VARCHAR(255)*: la taille du texte ou d'Integer (VARCHAR(255) variable il peut faire entre 0 et 255 caractères alors que CHAR(255) il fait 255 caractères).
   Parfait pour un Nom, une adresse mail, etc.
 - *ENUM('SMS' , 'email')* : peut avoir SMS ou email.
 - *TEXT* : Texte long. Adapté aux articles, commentaires, etc.
 - *BOOL* : Booléen.
 - *DATETIME* : Dates et heures. Pour les horodatages précis.
 - *JSON* : Objets JSON Complets. Flexible pour les données structurées. Exemple: {"id": 1, "nom": "IBRAHIM", "tags" : ["test1", "test2", "test3"]}


Lien entre tableau on utilise les relations : Une ligne dans un tableau est associée à un autre tableau.
4 tableaux : Utlisateurs, Conversations, Messages.

1) Créer un tableau qui porte le nom `todos` :

```sql
CREATE TABLE todos (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  text TEXT NOT NULL,
  done BOOL NOT NULL DEFAULT 0
);



