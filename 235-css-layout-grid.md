---
layout: page
title: CSS Layout - Grid
permalink: grid-layout.html
---

Le *CSS Grid Layout* est une nouvelle spécification CSS, en cours d'implémentation, qui a le potentiel de révolutionner la mise en page CSS. Comme son nom l'indique, il s'agit d'un modèle de mise en page basé sur une *grille* à deux dimensions, sur laquelle viennent se placer des blocs de contenu.

Cette fonctionalité CSS a été proposée en 2011 par Microsoft, et implémentée à fins de test dans Internet Explorer 10 et 11. Le projet a été repris par le W3C, où son développement se poursuit.

> En début 2017, le module CSS Grid Layout fait son entrée dans les navigateurs. Il est actif dans Firefox 52 (sorti le 7 mars 2017) et Chrome 57 (sorti le 9 mars 2017).

Il est donc désormais possible de l'utiliser. Une manière prudente de le faire est d'utiliser la méthode de chargement CSS optionnel @supports:

```css

// Styles sans la grille

@supports ( display: grid ) {
  .foo { display: grid; }
  // Styles avec la grille
}
```

### Exemples de grille

Ajouter une gouttière:

La propriété `column-gap` permet de définir l'espace entre les colonnes d'un élément.

```
column-gap: 2rem;
```

Voir: [Documentation MDN](https://developer.mozilla.org/fr/docs/Web/CSS/column-gap)

#### Ressources CSS Grid Module

* Support actuel des navigateurs: [http://caniuse.com/#feat=css-grid](http://caniuse.com/#feat=css-grid)
* Un tutoriel (le site de référence de Rachel Andrew): [http://gridbyexample.com/what/](http://gridbyexample.com/what/)
* Un autre tutoriel (par Alsa Créations):
[http://www.alsacreations.com/article/lire/1388-css3-grid-layout.html](http://www.alsacreations.com/article/lire/1388-css3-grid-layout.html)
* Un livre publié en début 2016 par Rachel Andrew: *Get Ready For CSS Grid Layout*, A Book Apart, 2016

**En anglais:**

- *[An Introduction to CSS Grid Layout](http://www.paris-web.fr/2015/conferences/an-introduction-to-css-grid-layout.php)* - conférence de Rachel Andrew, à Paris Web 2015, Présente le module CSS Grid Layout.
