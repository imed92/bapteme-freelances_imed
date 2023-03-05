### FEEDBACK Apprenant 3 ###

### Connexion ###

Les sessions ne sont pas intégré : elles sont essentiels pour l'authentification des utilisateurs. Les sessions sont un mécanisme de PHP qui permet de stocker des informations utilisateur de manière persistante entre les différentes pages d'un site web.

Sans ça, il te sera impossible de mettre en place les permissions pour chaque utilisateur, car le système ne peut pas savoir qui est connecté et quel est son rôle.

Je te conseille de te renseigner sur les $_SESSION sur symfony, tu peux consulter la documentation de symfony pour plus d'informations.

De plus la majorité des CRUD ne sont pas codés.

Néanmoins je vois que la vue profs et students sont codés. Nous allons analyser ça.

#### Prof
Ici la navbar a disparu, car je vois qu'elle n'est pas integré dans chacune de tes vues, elle présentes uniquement sur la page d'accueil. Essaye de créer un dossier layout dans lequel tu créer un fichier header.tpl.php ou tu mets le code de la navbar qui t'as été fournit dans docs\integration-html-css\index.html, puis implémente ce fichier header dans toutes tes vues.

         Liste : Fonctionne
         Ajout : Le bouton "Ajouter" existe bien mais redirige vers la vue d'ajout d'étudiant. La vue pour ajouter un prof n'existe pas encore.
         Suppression : Ne fonctionne pas => Dans app\views\teacher\teacher_list.tpl.php ligne 52, redirige vers todo.
         Modification : Ne fonctionne pas => Dans app\views\teacher\teacher_list.tpl.php ligne 43, redirige vers todo.

#### Etudiants
         Liste : Fonctionne
         Ajout : La page d'ajout fonctionne bien, le post aussi. Le seul problème ici est que la liste déroulante de prof n'est pas récupéré depuis la bdd. Dans ta méthode studentAdd() dans app\Controllers\StudentController.php récupere la liste des profs dans la bdd, puis à l'affichage de la vue envoie les data récupérés (liste des profs).
         Suppression : Ne fonctionne pas => Dans app\views\student\student_list.tpl.php, redirige vers todo.
         Modification : Ne fonctionne pas => Dans app\views\student\student_list.tpl.php, redirige vers todo.

#### Utilisateur
         Liste : Ne fonctionne pas car pas de controller, ni de model.
         Ajout : Pas encore fait
         Suppression : Pas encore fait
         Modification : Pas encore fait

## Ce qu'il faut revoir

Authentification, session, voir les permissions, methode get, methode post, routes, intégrer un header dans toutes tes vues pour que ta navbar soit accessible n'importe ou sur le site, un peu de css car dans les liste y a des caracteres qui debordent.
Fais aussi attention à certaines routes que tu as codé comme '/home' qui donne accès à la page d'accueil alors que c'est censé être '/' (voir 'docs\routes.md' pour les routes attendues).