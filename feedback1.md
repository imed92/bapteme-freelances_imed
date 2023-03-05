### FEEDBACK Apprenant 1 ###

L'ensemble du projet est bon, mention pour les méthodes qui sont bien codées, les routes fonctionnent, l'authentification et les sessions fonctionnent ce qui est une très bonne chose, tu as aussi l'air d'avoir bien saisi le fonctionnement du design pattern MVC.
Cependant je remarque quelques soucis au niveau des routes/permissions.

### Connexion ###

Pour ce qui est de la connexion, que ce soit pour l'admin ou pour l'user ca fonctionne bien.
Seulement je remarque que même sans être connecté on a accès à la page d'accueil (app\Views\main\home.tpl.php) car ce n'est pas gérer dans ton tableau $acl dans le CoreController ligne 16 (app\Controllers\CoreController.php);

<ins>Connexion admin</ins>

Ici on va voir, pour chaque table de la base de donnée, quel CRUD ne fonctionne pas et ou est l'anomalie.

#### Prof
         Liste : Fonctionne
         Ajout : Fonctionne
         Suppression : Fonctionne
         Modification : Erreur lors du clique sur le bouton valider => Regarde dans le formulaire de la page ou tu POST les modifications (/app/Views/teacher/teacher_update.tpl.php). Ton formulaire est correct dans son ensemble mais le problème c'est que dans la balise form, dans action="..." il manque l'id de l'élément que tu cherche à modifier à la fin du lien. Essaye de trouver un moyen de récuperer l'id du prof que tu modifie actuellement, et concatène cet id à ce que tu as mis dans action="..." comme tu l'as très bien fait pour la suppression.

#### Etudiants
         Liste : Fonctionne
         Ajout : Fonctionne
         Suppression : Fonctionne
         Modification : Erreur lors du clique sur le bouton valider => Regarde dans le formulaire de la page ou tu POST les modifications (/app/Views/student/student_update.tpl.php). Ton formulaire est correct dans son ensemble mais le problème c'est que dans la balise form, dans action="..." il manque l'id de l'élément que tu cherche à modifier à la fin du lien. Essaye de trouver un moyen de récuperer l'id de l'étudiant que tu modifie actuellement, et concatène cet id à ce que tu as mis dans action="..." comme tu l'as très bien fait pour la suppression.

#### Utilisateur
         Liste : Fonctionne
         Ajout : Erreur => Ne fonctionne pas car dans la vue ou tu liste tous les utilisateurs (app\Views\user\user_list.tpl.php) au clic du bouton "ajouter" il n'y a aucune redirection (href="#"). De plus je vois que la vue ou on ajoute un utilisateur n'existe pas. J'imagine que tu as manquer de temps pour gérer cela mais pour t'aiguiller sache que c'est le même principe que pour l'ajout de professeur ou d'étudiant (seulement fais attention à la gestion d'erreur car tu as une nouveauté à gérer : le format adresse mail ;) ).
         
         Suppression : Erreur lors du clique sur le bouton supprimer => dans la vue ou tu liste tous les utilisateurs (app\Views\user\user_list.tpl.php) au clic du bouton "supprimer" la redirection est brut car dans le href (ligne 31) tu mets directement href="/appusers/1/delete", c-a-d que tu cherche à supprimer directement l'élément 1. De plus je vois que dans ton controller (app\Controllers\UserController.php) tu n'as pas créée de méthode pour supprimer un utilisateur, pour se faire aide toi de ce que tu as fais pour supprimer un étudiant ou un prof.

         Modification : Erreur => Ne fonctionne pas car dans la vue ou tu liste tous les utilisateurs (app\Views\user\user_list.tpl.php) au clic du bouton "modifier" il n'y a aucune redirection (href="#"). De plus je vois que la vue ou on modifie un utilisateur n'existe pas. Sache que c'est le même principe que pour la modification de professeurs ou d'étudiants.


###### Connexion user ######

#### Prof
        Liste : Erreur => Pas accès alors que je devrais y avoir accès
        Ajouter : Correct => Pas accès
        Supprimer : Correct => Pas accès
        Modifier : Correct => Pas accès

#### Etudiants
        Liste : Erreur => Pas accès alors que je devrais y avoir accès
        Ajouter : Correct => Pas accès
        Supprimer : Correct => Pas accès
        Modifier : Correct => Pas accès mais lors de la modification ne fonctionne pas pour la même raison que quand on est connecté en tant qu'admin (Voir plus haut ligne 24).


#### Utilisateur
        Liste : Correct => Pas accès
        Ajouter : Correct => Pas accès
        Supprimer : Correct => Pas accès
        Modifier : Correct => Pas accès
