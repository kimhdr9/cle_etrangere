Exemples de clés étrangères
============================

Pour rappel une clé primaire d'une table désigne une information unique d'une ligne.
la table "contacts" a une colonne "customer_id" qui référencie la colonne "customer_id" de la table customer
cette colonne est une clé primaire de la table "customers" mais pour "contacts" elle désigne une clé étrangère.

le formalisme est le suivant :

>CONSTRAINT fk_customer
>FOREIGN KEY(customer_id)
>REFERENCES customers(customer_id)

Utilisation des codes sql joints :
bash>psql -U utilsateur -h serveur -d nom_base -p numero_port -W
psql>\i script.sql

on peut supprimer les tables

psql>\i drop_tables.sql

puis créer les tables

psql>\i create_tables.sql

puis l'alimenter

psql>\i insert_data.sql

psql> delete from customers where customer_id = 1 ;
ERREUR:  UPDATE ou DELETE sur la table « customers » viole la contrainte de clé étrangère « fk_customer » de la table « contacts »
DÉTAIL : La clé (customer_id)=(1) est toujours référencée à partir de la table « contacts ».

Rien n'a été modifié

Avec ce type de paramétrage la suppression nécessite une suppression en cascade pour tenir compte des relations.

en ajoutant

``PRIMARY KEY(contact_id),
CONSTRAINT fk_customer
FOREIGN KEY(customer_id)
REFERENCES customers(customer_id)
ON DELETE SET NULL``

``psql>\i drop_tables.sql``

puis créer les tables

``psql>\i create_tables_set_null.sql``

puis l'alimenter

``psql>\i insert_data.sql``
``psql>\i test_delete.sql``
| contact_id | customer_id | contact_name |     phone      |          email           
|:-----------|:------------|:-------------|:---------------|:------------------------
|          3 |           2 | David Wright | (408)-222-1234 | david.wright@dolphin.dev
|          1 |             | John Doe     | (408)-111-1234 | john.doe@bluebird.dev
|          2 |             | Jane Doe     | (408)-111-1235 | jane.doe@bluebird.dev
(3 lignes)

avec ON DELETE CASCADE

DELETE 1
| contact_id | customer_id | contact_name |     phone      |          email           
|:-----------|:------------|:-------------|:---------------|:------------------------
|          3 |           2 | David Wright | (408)-222-1234 | david.wright@dolphin.dev
(1 ligne)