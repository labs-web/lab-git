---
layout: default
chapitre : Git-log
order: 5
---
# Git log


## Git Log Command Overview

The `git log` command affiche committed snapshots,Il vous permet de répertorier l'historique du projet, de le filtrer et de rechercher des modifications spécifiques. git log ne fonctionne que sur l'historique validé.


### Basic Usage

- `git log`: Display entire commit history with default formatting.
- `git log -n <limit>`: Limit number of displayed commits (e.g., `git log -n 3` for 3 commits).

### Formatting Options

- `git log --oneline`: Condense each commit to a single line.
- `git log --stat`: Include files altered and lines added/deleted.
- `git log -p`: Display patch (or "diff") representing each commit.

### Filtering and Searching

- `git log --author="<pattern>"`: Search commits by author.
    - `git log --format='%aN <%aE>' | Sort-Object -Unique ` :  to see a list of all unique authors who have contributed to the repositor

- `git log --grep="<pattern>"`: Search commits by commit message.
    - `git log --format="%h %s"` : will output a list of commit hashes and their corresponding commit subjects

- `git log <since>..<until>`: Show commits between specified range.
- `git log <file>`: Display commits related to a specific file.

### Additional Options

- `git log --graph --decorate --oneline`: Display commits with graph, branch/tag names, and on a single line.

### Discussion

The SHA-1 checksum after `commit` ensures commit integrity and serves as a unique ID. It can be used in commands like `git log <since>..<until>`. The `~` character enables relative references to commit parents.

### Example

Commands can be combined:
- `git log --author="John Smith" -p hello.py`: Display full diff of changes by John Smith in hello.py.
- `git log --oneline main..some-feature`: Display overview of commits in `some-feature` but not in `main`.





# git status vs git log

La commande git log affiche des instantanés validés. Il vous permet de répertorier l'historique du projet, de le filtrer et de rechercher des modifications spécifiques. Alors que git status vous permet d'inspecter le répertoire de travail et la zone de mise en scène, git log ne fonctionne que sur l'historique validé.

## Utilisation

- `git log`: Affiche l'historique des validations entier en utilisant le formatage par défaut. Si la sortie occupe plus d'un écran, vous pouvez utiliser la touche Espace pour faire défiler et q pour quitter.

- `git log -n <limit>`: Limite le nombre de validations à <limit>. Par exemple, `git log -n 3` affichera uniquement 3 validations.

- `git log --oneline`: Condense chaque validation sur une seule ligne. C'est utile pour obtenir un aperçu global de l'historique du projet.

- `git log --stat`: En plus des informations git log ordinaires, inclut les fichiers qui ont été modifiés et le nombre relatif de lignes qui ont été ajoutées ou supprimées dans chacun d'eux.

- `git log -p`: Affiche le patch représentant chaque validation. Cela montre la diff complète de chaque validation, ce qui est la vue la plus détaillée que vous puissiez avoir de l'historique de votre projet.

- `git log --author="<pattern>"`: Recherche les validations par un auteur particulier. L'argument ＜pattern＞ peut être une chaîne simple ou une expression régulière.

- `git log --grep="<pattern>"`: Recherche les validations avec un message de validation qui correspond à ＜pattern＞, qui peut être une chaîne simple ou une expression régulière.

- `git log <since>..<until>`: Affiche uniquement les validations qui se produisent entre < since > et < until >. Les deux arguments peuvent être soit un ID de validation, un nom de branche, HEAD, ou tout autre type de référence de révision.

- `git log <file>`: Affiche uniquement les validations qui incluent le fichier spécifié. C'est un moyen facile de voir l'historique d'un fichier particulier.

- `git log --graph --decorate --oneline`: Quelques options utiles à considérer. Le drapeau --graph qui dessinera un graphique basé sur du texte des validations du côté gauche des messages de validation. --decorate ajoute les noms des branches ou des tags des validations qui sont affichées. --oneline montre les informations de validation sur une seule ligne, ce qui facilite la navigation à travers les validations en un coup d'œil.

## Discussion

La plupart de cela est assez simple ; cependant, la première ligne mérite une certaine explication. La chaîne de 40 caractères après commit est une somme de contrôle SHA-1 du contenu de la validation. Cela sert à deux fins. Premièrement, il garantit l'intégrité de la validation - si elle était jamais corrompue, la validation générerait une somme de contrôle différente. Deuxièmement, il sert d'identifiant unique pour la validation.

Cet ID peut être utilisé dans des commandes comme git log .. pour faire référence à des validations spécifiques. Par exemple, git log 3157e..5ab91 affichera tout entre les validations avec les ID 3157e et 5ab91. Mis à part les sommes de contrôle, les noms de branches (discutés dans le module Branch) et le mot-clé HEAD sont d'autres méthodes courantes pour faire référence à des validations individuelles. HEAD fait toujours référence à la validation actuelle, qu'il s'agisse d'une branche ou d'une validation spécifique.

Le caractère ~ est utile pour faire des références relatives au parent d'une validation. Par exemple, 3157e~1 fait référence à la validation avant 3157e, et HEAD~3 est l'arrière-grand-parent de la validation actuelle.

## Exemple

La section Utilisation fournit de nombreux exemples de git log, mais gardez à l'esprit que plusieurs options peuvent être combinées en une seule commande :

