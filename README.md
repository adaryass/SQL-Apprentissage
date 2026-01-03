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

### A) Table todos:

1) Créer un tableau qui porte le nom `tableau` :

```sql
CREATE TABLE tableau (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  text TEXT NOT NULL,
  done BOOL NOT NULL DEFAULT 0
);
```
2) Je veux inserer un todos : ID est gérer automatiquement

```sql
INSERT INTO tableau (text) VALUES
('Faire la vaisselle'),
('La deuxième tableau'),
('Dernière tableau');
```

- Pour voir *text*: 
```sql 
SELECT text  FROM tableau 
SELECT done, text FROM tableau
```
- Pour voir toutes les colonnes
```sql
SELECT * FROM tableau
```

- Pour voir la dernière tableau:
```sql
SELECT * FROM tableau where id = 3
```

3) Ordonner mon todos selon un ordre alphabetique ou ordre id

- Ordre Alphabétique:
```sql
SELECT * FROM tableau ORDER BY text
```
- Ordre Descendant: 
```sql
 SELECT * FROM tableau ORDER BY text DESC
```
- Ordre id :
```sql
SELECT * FROM tabelau ORDER BY id
```
Ordre Descendant :
```sql
SELECT * FROM tableau ORDER BY id DESC
```
On a réussi à faire une insertion , une sélection. 


4) On  veut maintenant faire une supression: 
```sql
DELETE FROM tableau WHERE id = 3
```
```sql
SELECT * from tableau (Voir si j'ai réussi à supprimer id = 3)
```

5) Je veux faire une insert de nouveau:
   
```sql
INSERT INTO tableau (text, done) VALUES
       ('Quatième tableau', 1),
       ('5 ème tableau', 0)

 SELECT * from tableau
```
4) Il manque une mise à jour, une modification : 
```sql
UPDATE tableau SET text = 'Cinquième tableau' where id = 5;
```
- Faire 2 modifications d'un seul coups
```sql
UPDATE todos SET text = 'Deuxième todo', done = 1 where id = 2;
```
5) Supprimer dans la table tableau ou done = 1: 
```sql
DELETE FROM tableau where done = 1;
```
B) Création table categories


1) Table categories:

CREATE TABLE categories (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL
  );


2)Insérer des valeurs :

INSERT INTO categories (name) VALUES
('TEST 1'),
('TEST 2');


3) Liaison d'un todos à une catégorie

   --> ALTER TABLE todos
       ADD category_id INTEGER NOT NULL DEFAULT 1


   --> SELECT * FROM todos


4) Contrainte de clé etranger
 Lier id de la table categories avec la table todos 

- C'est impossible, on va donc supprimmer la table todos et la recréer.

   --> DROP TABLE todos

- la recréer

create table todos (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  text TEXT NOT NULL,
  done BOOL NOT NULL DEFAULT 0,
  category_id INT NOT NULL DEFAULT 1,
  FOREIGN KEY (category_id) REFERENCES categories(id)
  );


   --> SELECT * FROM todos
  

  --> INSERT into todos (text) VALUES ('coucou');
  --> INSERT INTO todos (text, category_id) VALUES ('TODO 2', 2);


5) Je veux dans la tableau todos avoir fait au lieu de done, avec AS j'ai renomée la colonne:
  --> SELECT done AS 'Fait ? ', text AS Contenu, category_id AS Catégorie FROM todos

6) Ici , qu'on va apprendre à faire une jointure; une clé étrangère pour associer des données entre elles.

  --> SELECT * from todos INNER JOIN categories ON todos.category_id = categories.id;
  --> SELECT todos.done AS 'Fait ?', todos.text AS Contenu, categories.name AS Catégorie  from todos INNER JOIN categories ON todos.category_id = categories.id;
     --> Si je veux que des todos de categorie 2: 
SELECT todos.done AS 'Fait ?', todos.text AS Contenu, categories.name AS Catégorie  from todos INNER JOIN categories ON todos.category_id = categories.id where categories.id = 1;



C) Utiliser Claude pour designer votre base de données:






