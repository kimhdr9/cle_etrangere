Exemples de cl�s �trang�res
============================

Pour rappel une cl� primaire d'une table d�signe une information unique d'une ligne.
la table "conctats" a une colonne "customer_id" qui r�f�rentie la colonne "customer_id" de la table customer
cette colonne est une cl� primaire de la table "customers" mais pour "contacts" elle d�signe une cl� �trang�re. 

le formalisme est le suivant :

>  CONSTRAINT fk_customer
>      FOREIGN KEY(customer_id) 
>	  REFERENCES customers(customer_id)

Avec ce type de param�trage la suppression n�cessite une suppression en cascade pour tenir compte des relations.

en ajout 


