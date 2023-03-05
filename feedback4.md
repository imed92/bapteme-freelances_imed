### FEEDBACK Apprenant 4 ###

La vue de la page d'accueil n'existe pas car le controller MainController n'existe pas, alors que dans public\index.php la route que tu as mis pour '/' correspond à une méthode home() dans le MainController. Tu devrais commencer par la création du Contrôleur CoreController car cans ça il peut y avoir des soucis dans le projet si le CoreController manque, le CoreController doit contenir des méthodes et des fonctionnalités comme la gestion des autorisations et des permissions d'accès, l'affichage de vues, la gestion des erreurs, etc. D'autant plus que dans ton projet tu étends ce controller (voir UserController par exemple) mais il n'existe pas encore. Tu devrais commencer par ça puis le MainController.

### Connexion ###

Ni l'authentification ni les permissions ne sont gérées car il n'y a pas de CoreController. Essaye de voir les sessions sur symfony, elles sont essentiels pour l'authentification des utilisateurs. Les sessions sont un mécanisme de PHP qui permet de stocker des informations utilisateur de manière persistante entre les différentes pages d'un site web.

Sans ça, il te sera impossible de mettre en place les permissions pour chaque utilisateur, car le système ne peut pas savoir qui est connecté et quel est son rôle.

Néanmoins je vois que public\index.php tu as quand même essayé de faire des trucs.

## Prof

Ici tu as une erreur de syntaxe que tu as dû louper : dans ton TeachersController dans ta méthode teachers() tu as oublié un ; à la fin de la ligne 19 dans l'instanciation. Après avoir reglé ça, tu verras que tu as toujours le même problème que tout à l'heure : pas de CoreController alors que tu l'étends. 

## Etudiants

Ici aussi tu as une erreur de syntaxe : dans public\index.php quand tu créer la route '/students/list' tu appelle le controller StudentController alors que toi ton contrôleur s'appelle StudentsController (avec un 's' à la fin de student).
Après avoir reglé ça, tu verras que tu as toujours le même problème que tout à l'heure : pas de CoreController alors que tu l'étends. 

## Utilisateur

Ici tu as toujours le même problème avec le CoreController que tu étends alors qu'il n'existe pas. 

### Ce qu'il faut revoir ###


ICIIIIII
Authentification, session, voir les permissions, methode get, methode post, un peu de css car dans les liste y a des caracteres qui debordent.