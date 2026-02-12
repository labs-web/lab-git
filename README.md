# Lab Git - Maîtrise des commandes avancées

## Objectif du Lab
Ce laboratoire a pour but de vous familiariser avec les fonctionnalités avancées de Git. Vous apprendrez à manipuler l'historique, gérer les conflits, utiliser des sous-modules et interagir avec GitHub via la ligne de commande.

## Instructions Générales

- **Approche** : Pour chaque atelier, effectuez les recherches nécessaires pour trouver les commandes appropriées. Ne copiez-collez pas bêtement, comprenez ce que vous faites.

---

## Atelier 1 : Initialisation & Histoire
### Travail à faire
1.  **Initialisation** : Créez un nouveau dépôt Git local.
2.  **Exploration du stockage** :
    -   Ajoutez quelques fichiers et committez-les.
    -   Recherchez comment Git stocke les données pour optimiser l'espace disque (notion de snapshot vs delta, compression).
    -   Documentez vos trouvailles (explication succincte).

---

## Atelier 2 : GitHub CLI & Pull Requests
### Travail à faire
1.  **Installation** : Installez `GitHub CLI` (gh) sur votre machine si ce n'est pas déjà fait.
2.  **Authentification** : Connectez-vous à votre compte GitHub via le CLI.
3.  **Pull Request** :
    -   Créez une branche `feature-cli`.
    -   Faites une modification et poussez la branche.
    -   Créez une Pull Request (PR) vers `main` uniquement en utilisant la ligne de commande.
    -   Fusionnez la PR via le CLI.


## Atelier 3 : Git Log
### Travail à faire
1.  **Exploration de l'historique** :
    -   Utilisez la commande `git log` pour visualiser l'historique de votre dépôt.
    -   Expérimentez avec différentes options pour afficher le graphe, les modifications par fichier, ou filtrer par auteur/date.


## Atelier 4 : Git Diff
### Travail à faire
1.  **Comparaison** : Utilisez `git diff` pour comprendre les changements entre :
    -   Votre répertoire de travail et l'index (staging area).
    -   L'index et le dernier commit (`HEAD`).
    -   Deux branches distinctes.
2.  **Problème d'encodage** :
    -   Supposons que vous ayez des fichiers avec des noms comportant des caractères spéciaux.
    -   Trouvez comment configurer ou utiliser `git diff` (ex: `--name-only`) pour gérer correctement l'affichage des noms de fichiers (problème d'UTF-8 souvent rencontré sous Windows).


## Atelier 5 : Résolution de Conflits
### Travail à faire
1.  **Création du conflit** :
    -   Créez deux branches à partir du même commit.
    -   Modifiez la *même ligne* du *même fichier* dans les deux branches différemment.
    -   Tentez de fusionner (merge) les deux branches.
2.  **Résolution** :
    -   Analysez le message de conflit.
    -   Résolvez le conflit manuellement dans le fichier.
    -   Terminez le merge.


## Atelier 6 : Git Revert
### Travail à faire
1.  **Annulation propre** :
    -   Faites un commit "indésirable" (ex: suppression d'un fichier important ou ajout d'un bug).
    -   Utilisez `git revert` pour créer un *nouveau* commit qui inverse les changements du commit indésirable, sans modifier l'historique passé (contrairement à `reset`).


## Atelier 7 : Git Submodules
### Travail à faire
1.  **Ajout de dépendance** :
    -   Identifiez un dépôt public sur GitHub (ex: une librairie ou un thème).
    -   Ajoutez ce dépôt comme sous-module (`submodule`) dans votre projet actuel (par exemple dans un dossier `libs/`).
    -   Initialisez et mettez à jour le sous-module.
