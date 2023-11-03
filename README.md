Exemples de clés étrangères
============================

Pour rappel une clé primaire d'une table désigne une information unique d'une ligne.
la table "conctats" a une colonne "customer_id" qui référentie la colonne "customer_id" de la table customer
cette colonne est une clé primaire de la table "customers" mais pour "contacts" elle désigne une clé étrangère. 

le formalisme est le suivant :

>  CONSTRAINT fk_customer
>      FOREIGN KEY(customer_id) 
>	  REFERENCES customers(customer_id)

Avec ce type de paramétrage la suppression nécessite une suppression en cascade pour tenir compte des relations.

en ajout 


