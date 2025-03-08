# To-Do List

## Description

L'objectif de ce projet est de créer une application simple de gestion de tâches.

## Fonctionnalités

- Affichage d'un message lorsque aucune tâche n'est disponible.
- Champ texte et bouton "Ajouter" en haut pour créer une nouvelle tâche.
- Chaque tâche dispose d'une case à cocher pour être marquée comme terminée.
- Une tâche terminée sera barrée.
- Les tâches à faire sont affichées en premier.
- Une case à cocher permet de masquer les tâches terminées.

## Format des Tâches

Les tâches sont représentées sous le format suivant :

```json
[
  {
    "title": "Tâche à faire",
    "completed": false,
    "date": 1020302103
  }
]
```

## Configuration Recommandée

Il est recommandé d'utiliser l'éditeur suivant :

- [VSCode](https://code.visualstudio.com/) avec l'extension [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (désactiver Vetur).

## Configuration du Projet

Installation des dépendances :

```sh
npm install
```

### Lancer l'application en mode développement

```sh
npm run dev
```

### Compiler et minifier pour la production

```sh
npm run build
```

## Configuration Personnalisée

Consulte la documentation de Vite pour plus de détails : [Vite Configuration Reference](https://vite.dev/config/).
