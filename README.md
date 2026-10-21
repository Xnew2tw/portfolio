# Portfolio de Xavier Ammar

Ce dépôt contient le code source et les ressources que j'ai utilisés dans l'élaboration de mon portfolio. Le site, inspiré de l'atmosphère des jeux Astro Bot et réalisé au cours de mon année de pré-master à Epitech, présente mes projets informatiques ainsi que mon parcours.

## Lien vers le site en ligne

[Voir le portfolio en ligne](https://xnew2tw.github.io/portfolio/)

## Langages et outils utilisés

- **HTML** : établit la structure des pages.
- **Sass** : compile `sass/style.scss` en `style.css` (CSS sans framework) ; enregistre les couleurs sous forme de variables.
- **Node.js** : exécute du JavaScript en dehors du navigateur et permet l'utilisation de Sass.
- **npm** : télécharge Sass et l'inscrit dans `package.json` ; crée deux éléments : le dossier `node_modules`, qui contient le code de Sass et de ses dépendances, et le fichier `package-lock.json`, qui note la version exacte de chaque paquet installé.
- **Git** : conserve l'historique du travail sur mon ordinateur.
- **GitHub** : héberge une copie du travail en ligne, avec son historique.
- **GitHub Actions** : exécute un workflow à chaque `git push` pour compiler `sass/style.scss` en `style.css` ; range ensuite `style.css` avec `index.html` dans le dossier `_site`, qu'il transmet à GitHub Pages pour la mise en ligne.
- **GitHub Pages** : héberge et sert le site une fois celui-ci construit, à chaque nouvelle publication.