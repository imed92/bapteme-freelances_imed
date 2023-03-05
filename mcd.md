### MCD ###

Pour déterminer les cardinalités, il faut se fier aux informations données dans la contextualisation.


La cardinalité entre Utilisateur et Adresse est la suivante : 
Un utilisateur peut avoir une ou plusieurs adresses de livraison
Une adresse ne peut appartenir qu'à un seul utilisateur
SOIT :
USER a ADRESS => 1 , N / ADRESS appartient à USER => 1 , 1


La cardinalité entre Utilisateur et Commande est la suivante :
Un utilisateur peut passer plusieurs commandes ou aucune
Une commande doit appartenir à un seul utilisateur

SOIT :
USER génere ORDER => 0 , N / ORDER est generé USER => 1 , 1


La cardinalité entre Commande et Produit est la suivante :
Une commande peut contenir un ou plusieurs produits
Un produit peut appartenir à 0 ou à plusieurs commande

SOIT :
ORDER contient PRODUCT => 1 , N / PRODUCT contenu ORDER => 0 , N


La cardinalité entre Utilisateur et Aime est la suivante :
Un utilisateur peut aimer plusieurs produits
Un produit peut être aimé par plusieurs utilisateurs

SOIT :   
USER like PRODUCT => 0 , N / PRODUCT liké USER => 0 , N


________________________________________________________________________________


OUTILS

Pour créer des modèles conceptuels de données (MCD) avec la méthode Merise, j'utilise principalement deux logiciels : PowerAMC et JMerise. 

- Jmerise : JMerise est également un logiciel de modélisation de données qui prend en charge la méthode Merise. Il est gratuit, open-source et facile à utiliser
- PowerAMC : logiciel de modélisation de données qui prend en charge la méthode Merise. PowerAMC est un outil professionnel de modélisation de données qui offre une large gamme de fonctionnalités, il est donc payant.
