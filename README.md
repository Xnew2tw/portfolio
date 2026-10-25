# Portfolio de Xavier Ammar

Ce dépôt contient le code source et les ressources que j'ai utilisés dans l'élaboration de mon portfolio. Le site, inspiré de l'atmosphère des jeux Astro Bot et réalisé au cours de mon année de pré-master à Epitech, présente mes projets informatiques ainsi que mon parcours.

## Lien vers le site en ligne

[Voir le portfolio en ligne](https://xnew2tw.github.io/portfolio/)

## Langages et outils utilisés

- **HTML** : établit la structure des pages.
- **Sass** : compile `sass/style.scss` en `style.css` (CSS sans framework) ; enregistre les couleurs sous forme de variables.
- **BEM** : convention de nommage des classes CSS en trois parties : Bloc, Élément, Modificateur.
- **Node.js** : exécute du JavaScript en dehors du navigateur et permet l'utilisation de Sass.
- **npm** : télécharge Sass et l'inscrit dans `package.json` ; crée deux éléments : le dossier `node_modules`, qui contient le code de Sass et de ses dépendances, et le fichier `package-lock.json`, qui note la version exacte de chaque paquet installé.
- **Git** : conserve l'historique du travail sur mon ordinateur.
- **GitHub** : héberge une copie du travail en ligne, avec son historique.
- **GitHub Actions** : exécute un workflow à chaque `git push` pour compiler `sass/style.scss` en `style.css` ; range ensuite `style.css` avec les pages du site dans le dossier `_site`, qu'il transmet à GitHub Pages pour la mise en ligne.
- **GitHub Pages** : héberge et sert le site une fois celui-ci construit, à chaque nouvelle publication.

## Structure du dépôt

```
portfolio/
├── fonts/                         # les polices du site (WOFF2) et leurs licences
│   ├── baloo-2/
│   │   ├── baloo-2.woff2
│   │   └── OFL.txt
│   └── nunito/
│       ├── nunito-italic.woff2
│       ├── nunito.woff2
│       └── OFL.txt
├── cv/
│   └── cv-xavier-ammar.pdf        # le CV au format PDF
├── photo/
│   └── photo-xavier-ammar.jpg     # la photo de l'accueil
├── .github/
│   └── workflows/
│       └── deploy.yml             # la compilation du Sass et la publication sur GitHub Pages
├── .gitignore                     # les éléments ignorés par Git, car reconstructibles :
|                                  node_modules/, style.css, style.css.map
├── index.html                     # la page d'accueil
├── projets.html                   # la page des détails des projets
├── parcours.html                  # la page de présentation de mon parcours
├── contact.html                   # la page du formulaire de contact
├── package.json                   # la fiche d'identité du projet pour npm
├── package-lock.json              # les versions exactes des paquets installés
└── sass/
    └── style.scss                 # la feuille de style que j'écris
```

## Construire le site sur son ordinateur

Prérequis :
- Git (vérification : `git --version`).
- Node.js, avec npm (vérification : `npm --version`).

1. `git clone https://github.com/Xnew2tw/portfolio.git` : clone le dépôt GitHub dans le dossier courant.

2. `cd portfolio` : entre dans le dossier créé.

3. `npm install` : lit `package.json` et installe les paquets qu'il liste.

4. `npx sass --version` : vérifie que Sass fonctionne.

5. `npx sass sass/style.scss style.css` : compile le Sass en CSS.

6. - `xdg-open index.html` : ouvre la page d'accueil du site sous Linux.
   - `open index.html` : ouvre la page d'accueil du site sous macOS.
   - `start index.html` : ouvre la page d'accueil du site sous Windows.

## Publication

Le workflow reçoit l'autorisation de lire le dépôt, d'écrire sur GitHub Pages et de prouver son identité au déploiement. Voici les étapes de la publication du site par le workflow, à chaque `git push` sur la branche `main` du dépôt.

1. Construction du site, sur une machine virtuelle sous Linux :
   - récupère le contenu du dépôt.
   - installe Node.js (version 24).
   - installe, avec `npm ci`, les versions exactes notées dans `package-lock.json` et s'arrête en cas d'incohérence.
   - compile le Sass en CSS, sans produire de carte des correspondances (option `--no-source-map`).
   - crée un dossier `_site` destiné à recevoir le site.
   - copie dans ce dossier `index.html` et `style.css`, les seuls fichiers nécessaires au visiteur.
   - emballe le dossier `_site` sous forme d'artefact et le confie à GitHub pour que la tâche suivante le retrouve.

2. Publication du site, via une nouvelle machine virtuelle, elle aussi sous Linux :
   - démarre à condition que la construction ait réussi.
   - récupère `_site`, emballé lors de la dernière étape de construction, pour commencer son travail.
   - met en ligne le contenu de `_site` sur GitHub Pages, qui le sert ensuite au visiteur.

Cette publication du site est rendue possible par le réglage de "Pages" sur "GitHub Actions" ("Settings" > "Pages"). Une fois la publication faite, le workflow en garde la trace dans l'onglet "Actions" de GitHub et affiche l'adresse du site comme un lien cliquable sous la case de la tâche `publication`, située dans chaque résumé d'une exécution.

## Ressources utilisées

Baloo 2 :
- auteur : Copyright 2019 The Baloo 2 Project Authors ([voir le dépôt des auteurs](https://github.com/EkType/Baloo2)).
- licence : SIL Open Font License 1.1 ([voir le site officiel de la licence](https://openfontlicense.org)).
- emplacement : `portfolio/fonts/baloo-2/OFL.txt`.
- source : [voir la police sur Google Fonts](https://fonts.google.com/specimen/Baloo+2).

Nunito :
- auteur : Copyright 2014 The Nunito Project Authors ([voir le dépôt des auteurs](https://github.com/googlefonts/nunito)).
- licence : SIL Open Font License 1.1 ([voir le site officiel de la licence](https://openfontlicense.org)).
- emplacement : `portfolio/fonts/nunito/OFL.txt`.
- source : [voir la police sur Google Fonts](https://fonts.google.com/specimen/Nunito).

Les fichiers des polices ont été convertis de `.ttf` en `.woff2`.

Les polices ne sont pas chargées depuis Google mais hébergées dans le dépôt, afin que l'adresse IP du visiteur ne soit pas transmise à un tiers.