# Guide Complet : Maîtriser Git Subtree pour vos Skills Agent

Ce guide est votre référence unique pour gérer la bibliothèque de compétences de votre agent via **Git Subtree**.

---

## 🏗️ 1. Comprendre le Concept

### Le Problème
Vous avez un agent IA qui doit posséder des compétences spécifiques (`init-lab`, `init-agent`) dans plusieurs projets différents (`lab-git`, `lab-laravel`).
Copier-coller ces dossiers est une erreur (désynchronisation, historique perdu).

### La Solution : Git Subtree
Imaginez **Git Subtree** comme une **"Photocopie Intelligente"**.
*   **Intelligente** : Elle garde le lien avec l'auteur original.
*   **Photocopie** : Le code est physiquement présent dans votre classeur (projet local).

| Submodule (Non)                | Subtree (Oui)                      |
| :----------------------------- | :--------------------------------- |
| Simple lien symbolique         | Copie réelle du code               |
| Complexe à gérer pour l'équipe | Transparent (juste un `git clone`) |
| Fragile                        | Robuste                            |

---

## 🚀 2. Cas d'Usage Principal : Importer "À la Carte" (Split)

Votre besoin : Vous avez une bibliothèque géante (`agent-skills`) mais vous ne voulez injecter **QUE** le dossier `init-lab` dans votre projet actuel.

### Étape A : Préparer la Source (Une seule fois)
*Sur le dépôt central `agent-skills`*

Nous devons isoler le dossier voulu dans une branche dédiée.

```bash
# 1. Créer une branche 'branch-init-lab' contenant UNIQUEMENT le dossier 'init-lab'
git subtree split --prefix=init-lab -b branch-init-lab

# 2. Publier cette branche sur GitHub
git push origin branch-init-lab
```

### Étape B : Importer dans votre Lab (Projet Cible)
*Sur votre projet local `lab-git`*

```bash
# 1. Ajouter le lien vers la bibliothèque (si pas déjà fait)
git remote add -f skills-lib https://github.com/votre-user/agent-skills.git

# 2. Injecter le skill spécifique
# --prefix : où le mettre chez vous
# --squash : pour garder un historique propre (1 seul commit)
git subtree add --prefix .agent/skills/init-lab skills-lib branch-init-lab --squash
```

### Étape C : Cycle de Vie (Workflow)

**Mettre à jour (Pull)** : La bibliothèque a évolué.
```bash
git subtree pull --prefix .agent/skills/init-lab skills-lib branch-init-lab --squash
```

**Contribuer (Push)** : Vous avez corrigé un bug localement.
```bash
git subtree push --prefix .agent/skills/init-lab skills-lib branch-init-lab
```

---

## ⚡ 3. Optimisation : Les Alias Git

Taper ces commandes est fastidieux. Créez des raccourcis pour votre projet.

### Créer les raccourcis
```bash
# Alias pour PULL (Mise à jour)
git config alias.pull-init-lab "subtree pull --prefix .agent/skills/init-lab skills-lib branch-init-lab --squash"

# Alias pour PUSH (Contribution)
git config alias.push-init-lab "subtree push --prefix .agent/skills/init-lab skills-lib branch-init-lab"
```

### Utiliser les raccourcis
```bash
git pull-init-lab
git push-init-lab
```

---

## 📝 4. Antisèche (Cheat Sheet)

| Action             | Commande                                                     | Alias suggéré    |
| :----------------- | :----------------------------------------------------------- | :--------------- |
| **Setup Remote**   | `git remote add -f skills-lib <URL>`                         | -                |
| **Split (Source)** | `git subtree split --prefix=<DIR> -b <BRANCH>`               | -                |
| **Add (Cible)**    | `git subtree add --prefix <DIR> <REMOTE> <BRANCH> --squash`  | -                |
| **Pull (Update)**  | `git subtree pull --prefix <DIR> <REMOTE> <BRANCH> --squash` | `git pull-skill` |
| **Push (Fix)**     | `git subtree push --prefix <DIR> <REMOTE> <BRANCH>`          | `git push-skill` |

> **Astuce** : Pour mettre à jour tous vos skills d'un coup, créez un script `update-skills.ps1` qui appelle vos alias en séquence.
