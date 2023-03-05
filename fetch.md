# FETCH 

Salut à toi l'apprenant 1, tout d'abord je tiens à te féliciter pour ton travail tu t'en es très bien sorti.
Pour t'éxpliquer la méthode fetch en Javascript, je vais d'abord t'expliquer en théorie comment fonctionne la méthode, puis je te ferais un exemple de cas d'utilisation de la méthode dans ton projet.

### 1 - THEORIE

La méthode Fetch en JavaScript permet de récupérer des données depuis un serveur distant en utilisant des requêtes HTTP*.

Le fetch est une méthode asynchrone*, ce qui signifie qu'il ne bloque pas l'exécution du reste du code pendant qu'il attend une réponse du serveur.

Pour utiliser fetch, il suffit d'appeler la méthode avec l'URL de la ressource que tu souhaite récupérer. Fetch retourne une promesse qui contiendra la réponse du serveur lorsqu'elle sera disponible. Pas besoin d'appeler de bibliothèque pour utiliser la méthode Fetch en JavaScript, c'est une méthode native du navigateur qui est prise en charge par la plupart des navigateurs modernes.


*Requête Http : Une requête HTTP (HyperText Transfer Protocol) est une méthode qui permet d'envoyer des data entre un client et un serveur sur Internet. Elle permet de demander des ressources (contenus HTML, fichiers, etc) depuis un serveur et de recevoir une réponse en retour.

*Méthode asynchrone : C'est une méthode qui ne bloque pas l'exécution du programme et ne renvoie pas immédiatement de résultat. Dans le contexte du développement web, les méthodes asynchrones sont utilisées pour effectuer des tâches comme la récupération de données à partir d'une API ou l'envoi de données à un serveur sans bloquer l'interface utilisateur (les vues). Pourquoi les utiliser ? Car les méthodes asynchrones permettent d'améliorer la performance et la réactivité des applications en évitant de bloquer le fil d'exécution principal.

### 2 - EXEMPLE

Pour mieux comprendre la notion de detch en js, je vais l'implémenter dans ton projet, plus précisément dans la suppression d'un étudiant (/student/[i:studentid]/delete).

##### 1ere étape #####
On va dans app\Views\layout\header.tpl.php pour y intégrer le fichier .js (de manière propre) que l'on va créer dans l'étape suivante.
On mets la ligne suivante :
    `<script src="<?= $assetsBaseUri ?>js/fetch.js"></script>`
Ici on concatène la variable $assetsBaseUri (variable qui contient l'URI de base des fichiers statiques) avec le chemin du fichier fetch.js qu'on va créer.

##### 2eme étape #####
On créer un dossier assets dans le dossier public.
Dans le dossier assets on créer un dossier js et dans ce dossier js on créer le fichier fetch.js.
Voilà le chemin qu'il faut :
public\assets\js\fetch.js
Maintenant on a bien intégrer le fichier js.

ATTENTION : Ici on voit comment intégrer un fichier js pour tous les fichiers qui vont implémenter le header, mais on aurait pu insérer la ligne `<script src="<?= $assetsBaseUri ?>js/fetch.js"></script>` directement dans la vue qu'on veut.

##### 3eme étape #####
Tu l'auras compris, ici on va implémenter la méthode fetch pour la suppression d'étudiant.
Dans le fichier fetch.js, on ajoute ce code :
`function deleteStudent(studentId) {                     // prototype de la fonction js qui va supprimer l'etudiant
    fetch('/student/' + studentId + '/delete', {        //utilisationde la methode fetch = 1er parametre la route via laquelle on va effectuer notre requete (ici /student/{id}/delete), 2eme parametre le type de methode : ici GET.
        method: 'GET'
    })
    .then(response => {                                 // ici on est a la fin de la requete
        if (!response.ok) {                             // ici gestion d'erreur, si ca s'est mal passé, on génère une erreur avec le message "Error deleting student"
            throw new Error('Error deleting student');
        }
        location.reload();                              // on actualise la page une fois la suppression terminée
    })
    .catch(error => console.error(error));              // si pas d'actualisation afficher l'erreur dans la console
}`

Maintenant dans la vue ou on liste tous les étudiants, on va implémenter cette méthode Javascript.
On va ligne 29 et on remplace cette ligne :

<a class="dropdown-item" href="<?= $router->generate('student_delete', [ "studentid" => $student->getId() ]) ?>">Oui, je veux supprimer</a>

Par cette ligne :
<a href="#" class="btn btn-sm btn-danger" onclick="deleteStudent(<?= $student->getId() ?>)"><i class="fa fa-trash-o" aria-hidden="true"></i>supprimer</a>

Maintenant on rafraîchit la page, on va sur la liste des étudiants et on voit que au clic du bouton supprimer, la méthode Javascript deleteStudent(studentId) fonctionne bien.

L'ancienne ligne de code crée un lien qui redirige l'utilisateur vers la page de suppression, tandis que la nouvelle utilise une fonction JavaScript pour effectuer la suppression en arrière-plan.

J'éspère que mon explication a été claire et qu'elle t'a été utile, n'hésites pas à me solliciter si tu as d'autres incompréhensions.