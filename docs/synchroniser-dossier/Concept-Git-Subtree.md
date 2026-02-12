# Concept : Comprendre Git Subtree

## C'est quoi ?
Git Subtree est une méthode pour inclure le code d'un autre dépôt Git dans un sous-dossier de votre propre projet.

Contrairement aux **Submodules** (qui ne sont que des "liens" vers un commit précis), **Subtree** copie physiquement le code et son historique dans votre arborescence.

---

## L'Analogie Clef : Le Raccourci vs La Photocopie

Pour bien comprendre la différence majeure avec les Submodules :

| Méthode           | Analogie                        | Comportement                                                                                                                                |
| :---------------- | :------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------ |
| **Git Submodule** | **Un Raccourci**                | C'est un pointeur vers une adresse. Si vous n'initialisez pas le lien (`init/update`), le dossier est vide.                                 |
| **Git Subtree**   | **Une Photocopie Intelligente** | Vous avez les documents physiquement dans votre classeur. Vous pouvez écrire dessus. Et vous pouvez renvoyer vos notes à l'auteur original. |

---

## Scénarios de Flux de Travail

Pour bien saisir la puissance du Subtree, voici comment cela se passe concrètement quand on modifie du code.

### Scénario 1 : La Bibliothèque Évolue (Pull)
Vous avez intégré `agent-skills` dans votre projet. Entre temps, un collègue (ou vous-même) a amélioré le skill `init-lab` sur le dépôt central.

1.  **Dépôt Central (`agent-skills`)** : Le code a changé (commit X).
2.  **Votre Projet Local** : Votre copie est en retard.
3.  **Action** : Vous faites un `git subtree pull`.
4.  **Résultat** : Git va chercher les modifs distantes et crée un **commit de fusion (Merge Commit)** dans votre historique local.
    *   *Notez bien* : C'est comme un `git pull` classique, sauf qu'il cible un dossier précis.

### Scénario 2 : Le Projet Local Évolue (Push)
Vous travaillez sur votre projet `lab-git` et vous trouvez un bug dans le dossier `skills/init-lab`. Vous le corrigez directement ici.

1.  **Votre Projet Local** : Vous modifiez le fichier et committez ("Fix bug in init-lab").
    *   Pour Git, c'est un commit normal dans votre projet.
2.  **Action** : Vous voulez partager ce fix. Vous faites un `git subtree push`.
3.  **Magie** : Git va scanner votre historique, isoler ce commit qui touche au dossier partagé, et l'envoyer vers le dépôt central `agent-skills`.
4.  **Résultat** : Le dépôt central reçoit votre correction comme si vous aviez travaillé dessus directement.

---

## Pourquoi choisir Subtree ?

### 1. La Transparence pour l'équipe
C'est son plus gros atout. Une fois le subtree en place :
*   Vos collaborateurs clonent le projet (`git clone`).
*   **C'est tout.** Ils n'ont aucune commande spéciale à lancer. Les fichiers sont là.
*   Ils n'ont même pas besoin de savoir que ce dossier vient d'ailleurs.

### 2. La Modification Bidirectionnelle
Avec un Submodule, modifier le code interne est pénible (tête détachée).
Avec **Subtree**, vous modifiez le code du dossier partagé comme n'importe quel autre fichier. Git détectera plus tard que ce changement appartient au "sous-projet" si vous décidez de le partager (`push`).

---

## La notion de "Squash" (Compression)

Vous verrez souvent le drapeau `--squash` dans les commandes Subtree. C'est essentiel.

*   **Sans Squash** : Git importe *tous* les commits de l'historique du projet externe. Votre historique local se retrouve pollué par 1000 commits qui ne vous concernent pas.
*   **Avec Squash** : Git compresse tout l'historique externe en **un seul commit** de fusion. C'est propre, net et lisible.

---

## En Résumé

Utilisez **Git Subtree** quand :
*   Vous voulez partager du code (librairies, skills, configs) entre plusieurs projets.
*   Vous voulez que la vie soit simple pour les utilisateurs du projet.
*   Vous acceptez d'avoir des commandes un peu plus longues (`git subtree check ...`) pour la maintenance.
