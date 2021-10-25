---
layout: page
title: Unités CSS
permalink: units.html
---

Il existe diverses unités de mesure disponibles en CSS. Elles peuvent être classées en trois catégories:

- **Unités absolues:** mm (millimètres), cm (centimètres), in (pouces), pt (point), pc (pica)
- **Unités relatives:** %, em, ex, rem, ch, vh, vw
- **Unités dépendantes de l'interface:** px

Les unités *absolues* correspondent à ce que l'on connaît de la mise en page "papier". Elles sont à éviter sur le web, sauf pour les styles d’impression (p.ex. pour spécifier les marges des pages). Comme l'indiquent les inventeurs du CSS, Håkon Wium Lie et Bert Bos (dans *Cascading Style Sheets: Designing for the Web*): 

- Utilisez les unités *ems* pour créer des feuilles de styles s'adaptant à différentes échelles.
- Utilisez les *ems* pour définir les tailles de fonte.
- Utilisez des unités relatives pour définir la longueur des éléments de mise en page.
- N'utilisez les longueurs absolues uniquement si les caractéristiques physiques du medium de sortie sont connues.

## Unités relatives:

- **Les pourcentages** (%): Définit une mesure en % par rapport à la taille de l'élément parent. Utile pour créer des mises en page flexibles, et pour définir des tailles de fonte.

### Unités relatives à la fonte - em, ex, ch, rem

- **em**: Unité typographique ancienne, correspondant historiquement à la largeur de la lettre "m". Par défaut, 1em est équivalent à 16px. Voici les équivalences par défaut du em: `1em = 16px = 0.17in = 12pt = 1pc = 4.2mm = 0.42cm`.
- **rem**: Unité relative, qui fonctionne comme le **em**, mais la taille est relative à la taille de fonte à la racine du document (attribuée à l'élément `html`).
- **ex**: Unité verticale, correspondant à la *x-height*, càd. la hauteur de la lettre x. Contrairement au **em**, cette unité varie en fonction de la fonte. 
- **ch**: Unité correspondant à la largeur du charactère "0". 

### Unités relatives au viewport - vw, vh, vmin, vmax 

- **vh** et **vw**: Unités relatives à la surface d’affichage. Ces unités sont relatives à la taille de la fenêtre de navigateur. Cela permet p.ex. de spécifier une taille de fonte qui s'adapte à la taille du navigateur. Un **vh** ou **vw** est équivalent à 1% de la taille de fenêtre. Donc un élément avec `height: 100vh` occupera toute la hauteur de la fenêtre.
- **vmin**: correspond à la plus petite valeur de vh ou vw.

#### Les pixels (px)

Les **pixels** ont été pendant longtemps l'unité la plus utilisée en webdesign, autant pour définir des mises en page que pour les tailles de fontes. 

Le postulat était que tous les écrans avaient la même résolution (72 dpi) et la même taille (1024 x 768px). On préfère actuellement utiliser des unités relatives comme les **em** ou les **pourcentages**, car les résolutions et les dimensions des écrans sont très variables.

## Ressources et références

Articles:

- *[Dimensionner ses fontes avec rem](http://www.pompage.net/traduction/dimensionner-ses-fontes-avec-rem)*, par Jonathan Snook, 2011
- *[Quelles mesures CSS, pour quel usage ?](http://www.pompage.net/traduction/css-unites-et-usages)*, par Dudley Storey, 2013

Ressources d'apprentissage:

Quelques bonnes ressources pour assimiler les bases du CSS, en trois chapitres:

- *[Getting to Know CSS](http://learn.shayhowe.com/html-css/getting-to-know-css/)*
- *[Opening the Box Model](http://learn.shayhowe.com/html-css/opening-the-box-model/)*
- *[Positioning Content](http://learn.shayhowe.com/html-css/positioning-content/)*


