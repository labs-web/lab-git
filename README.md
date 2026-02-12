# 🧪 Lab Git - Maîtrise des commandes avancées

## 1. Contexte du Lab

### Objectif
Explorer **Git Avancé**.
L'objectif est de maîtriser les commandes complexes (revert, log, diff), la gestion des conflits et les sous-modules.

### Localisation dans le Cursus
*   **Compétence validée** : `C4` - Organiser le travail et collaborer.
*   **Compétence secondaire** : `M` - Veille technologique et labs.
*   **Stack Technique** : Niveau **N2** - Versioning Avancé.

---

## 2. Travail à faire

### Instructions Générales
- **Livrables** : Un dossier `/docs` contenant un fichier Markdown pour chaque atelier.
- **Approche** : Recherches autonomes, compréhension avant exécution.

---

### Atelier 1 : Initialisation & Histoire
#### Travail à faire
1.  **Initialisation** : Créez un nouveau dépôt Git local.
2.  **Exploration du stockage** :
    -   Ajoutez quelques fichiers et committez-les.
    -   Recherchez comment Git stocke les données pour optimiser l'espace disque (notion de snapshot vs delta, compression).
    -   Documentez vos trouvailles (explication succincte).
#### Livrable
-   `/docs/initialisation.md` : Explication sur l'économie d'espace disque par Git.

### Atelier 2 : GitHub CLI & Pull Requests
#### Travail à faire
1.  **Installation** : Installez `GitHub CLI` (gh) sur votre machine si ce n'est pas déjà fait.
2.  **Authentification** : Connectez-vous à votre compte GitHub via le CLI.
3.  **Pull Request** :
    -   Créez une branche `feature-cli`.
    -   Faites une modification et poussez la branche.
    -   Créez une Pull Request (PR) vers `main` uniquement en utilisant la ligne de commande.
    -   Fusionnez la PR via le CLI.
#### Livrable
-   `/docs/github-cli.md` : Commandes utilisées pour créer et fusionner la PR.

### Atelier 3 : Git Log
#### Travail à faire
1.  **Exploration de l'historique** :
    -   Utilisez la commande `git log` pour visualiser l'historique de votre dépôt.
    -   Expérimentez avec différentes options pour afficher le graphe, les modifications par fichier, ou filtrer par auteur/date.
#### Livrable
-   `/docs/git-log.md` : Liste des 3 options de `git log` que vous trouvez les plus utiles avec un exemple de sortie pour chacune.

### Atelier 4 : Git Diff
#### Travail à faire
1.  **Comparaison** : Utilisez `git diff` pour comprendre les changements entre :
    -   Votre répertoire de travail et l'index (staging area).
    -   L'index et le dernier commit (`HEAD`).
    -   Deux branches distinctes.
2.  **Problème d'encodage** :
    -   Supposons que vous ayez des fichiers avec des noms comportant des caractères spéciaux.
    -   Trouvez comment configurer ou utiliser `git diff` (ex: `--name-only`) pour gérer correctement l'affichage des noms de fichiers (problème d'UTF-8 souvent rencontré sous Windows).
#### Livrable
-   `/docs/git-diff/git-diff.md` : Explications sur les différentes portées de `git diff` et solution pour l'affichage UTF-8.

### Atelier 5 : Résolution de Conflits
#### Travail à faire
1.  **Création du conflit** :
    -   Créez deux branches à partir du même commit.
    -   Modifiez la *même ligne* du *même fichier* dans les deux branches différemment.
    -   Tentez de fusionner (merge) les deux branches.
2.  **Résolution** :
    -   Analysez le message de conflit.
    -   Résolvez le conflit manuellement dans le fichier.
    -   Terminez le merge.
#### Livrable
-   `/docs/conflits.md` : Capture d'écran ou copie du fichier contenant les marqueurs de conflit (`<<<<<<<`, `=======`, `>>>>>>>`) avant résolution, et explication de la démarche.

### Atelier 6 : Git Revert
#### Travail à faire
1.  **Annulation propre** :
    -   Faites un commit "indésirable".
    -   Utilisez `git revert` pour créer un *nouveau* commit qui inverse les changements.
#### Livrable
-   `/docs/GitRevert/git-revert.md` : Preuve que le commit de revert a été créé (sortie de `git log`).

### Atelier 7 : Git Submodules
#### Travail à faire
1.  **Ajout de dépendance** :
    -   Identifiez un dépôt public sur GitHub.
    -   Ajoutez ce dépôt comme sous-module (`submodule`) dans votre projet actuel.
    -   Initialisez et mettez à jour le sous-module.
#### Livrable
-   `/docs/submodules.md` : Commande utilisée et contenu du fichier `.gitmodules`.
