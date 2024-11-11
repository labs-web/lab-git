---
layout: default
chapitre : true
order: 90
---

# Sous-module git

## 1. Ajouter un Sous-module

Pour ajouter un sous-module dans votre dépôt Git principal, utilisez la commande suivante :

```bash
git submodule add <URL-du-référentiel> <chemin/facultatif>
```

Exemple :

```bash
git submodule add https://github.com/utilisateur/exemple-sous-module.git sous-module
```

Cela créera un dossier nommé `sous-module` dans votre dépôt principal et enregistrera l’URL du sous-module dans un fichier `.gitmodules`.

## 2. Mettre à Jour un Sous-module

Pour mettre à jour un sous-module, accédez au sous-module et récupérez les mises à jour :

```bash
cd sous-module
git pull origin main
```

Ensuite, pour engager cette mise à jour dans le dépôt principal :

```bash
cd ..
git add sous-module
git commit -m "Mise à jour du sous-module"
```

> **Remarque** : Utilisez `main` ou remplacez par la branche pertinente de votre sous-module.

Pour mettre à jour tous les sous-modules en même temps (depuis la racine du dépôt principal) :

```bash
git submodule update --remote
```

## 3. Supprimer un Sous-module

Pour supprimer un sous-module :

1. Supprimez l’entrée du sous-module du fichier `.gitmodules` :

   ```bash
   git config -f .gitmodules --remove-section submodule.<chemin-du-sous-module>
   ```

2. Supprimez la configuration du sous-module de `.git/config` :

   ```bash
   git config -f .git/config --remove-section submodule.<chemin-du-sous-module>
   ```

3. Supprimez le dossier physique et l'indexation du sous-module :

   ```bash
   git rm --cached <chemin-du-sous-module>
   rm -rf <chemin-du-sous-module>
   ```

4. Engagez les modifications :

   ```bash
   git commit -m "Supprimer le sous-module"
   ```

## 4. Cloner un Dépôt avec des Sous-modules

Si votre dépôt principal contient des sous-modules et que vous souhaitez cloner avec tous les sous-modules :

1. **Cloner avec les sous-modules** : Utilisez l’option `--recurse-submodules` pour cloner le dépôt principal et ses sous-modules en une seule commande :

   ```bash
   git clone --recurse-submodules <URL-du-dépôt>
   ```

2. **Initialiser les sous-modules après un clonage classique** : Si vous avez déjà cloné le dépôt sans sous-modules, vous pouvez les initialiser et les mettre à jour manuellement :

   ```bash
   git submodule init
   git submodule update
   ```

## 5. Cloner un Dépôt Sans Initialiser les Sous-modules

Si vous souhaitez cloner un dépôt sans récupérer les sous-modules immédiatement :

1. Clonez le dépôt sans sous-modules :

   ```bash
   git clone <URL-du-dépôt>
   ```

2. Plus tard, vous pouvez initialiser uniquement les sous-modules souhaités :

   ```bash
   git submodule update --init <chemin-du-sous-module>
   ```

## Résumé des Commandes Utiles

| Action                     | Commande                                                                                       |
|----------------------------|------------------------------------------------------------------------------------------------|
| Ajouter un sous-module     | `git submodule add <URL-du-référentiel> <chemin/facultatif>`                                   |
| Mettre à jour un sous-module | `git submodule update --remote`                                                              |
| Supprimer un sous-module   | `git rm --cached <chemin-du-sous-module> && rm -rf <chemin-du-sous-module>`                   |
| Cloner avec sous-modules   | `git clone --recurse-submodules <URL-du-dépôt>`                                               |
| Initialiser après clonage  | `git submodule init && git submodule update`