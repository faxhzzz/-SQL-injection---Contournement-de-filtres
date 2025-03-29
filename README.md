# -SQL-injection---Contournement-de-filtres
 SQL injection - Contournement de filtres (challenge root me 80pt)

Description courte : Nous allons injecter dans le paramètre id ici.

![image](https://github.com/user-attachments/assets/2f36be91-3947-4aa1-a9bf-ecb908886649)

Les caractères filtrés et leurs contournements :

    Espaces → remplacer par %09 (tabulation)

    "select" → remplacer par "SELECT" (majuscules)

    "union" → remplacer par "UNION" (majuscules)

    "join" → remplacer par "JOIN" (majuscules)

    "select 1,2" (virgule filtrée) → remplacer par :
    (SELECT 1) AS A JOIN (SELECT 2) AS B
    (Note : Sans alias pour les sous-requêtes, erreur "Every derived table must have its own alias")

    "where" → remplacer par limit et offset

Indice du code source : la table a 4 colonnes.


