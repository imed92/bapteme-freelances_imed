### FEEDBACK Apprenant 2 ###

### Connexion ###

Je constate que les sessions ne sont pas intégré : elles sont essentiels pour gérer l'authentification des utilisateurs. Le système de session est un mécanisme de PHP qui permet de stocker des informations utilisateur de manière persistante entre les différentes pages d'un site web.

Sans ça, le projet ne permet pas aux utilisateurs et aux admins de se connecter pour accéder aux pages restreintes. En conséquence, il est impossible de mettre en place les permissions pour chaque utilisateur, car le système ne peut pas savoir qui est connecté et quel est son rôle.

Je te conseille de te renseigner sur les `$_SESSION` sur symfony 5, tu peux consulter la documentation de symfony pour plus d'informations.

Néanmoins je vois que certaines vues sont codé et les CRUD sont + ou - fonctionnels.

#### Prof
         Liste : Fonctionne
         Ajout : Pas de bouton mais la vue app\views\teachers\teachers_add.tpl.php existe bien mais ne fonctionne pas car dans ton controller tu n'as pas implémenter la méthode POST. La méthode POST est nécessaire pour envoyer les données du formulaire au serveur.
         Suppression : Ne fonctionne pas => Dans app\views\teachers\teachers_list.tpl.php ligne 29, redirige vers todo.
         Modification : Lors du clique sur le bouton modifier ca redirige vers la vue pour ajouter un prof.

#### Etudiants
         Liste : Fonctionne
         Ajout : Pas de bouton et la vue inexistante.
         Suppression : Ne fonctionne pas => Dans app\views\students\students_list.tpl.php ligne 27, redirige vers todo.
         Modification : Ne fonctionne pas => Dans app\views\students\students_list.tpl.php ligne 18 redirige vers todo.

#### Utilisateur
         Liste : Ne fonctionne pas
         Ajout : Ne fonctionne pas
         Suppression : Ne fonctionne pas
         Modification : Ne fonctionne pas

## Ce qu'il faut revoir

Authentification, session, voir les permissions, methode get, methode post, un peu de css car dans les liste y a des caracteres qui debordent mais sinon c'est pas si mal. Good luck !