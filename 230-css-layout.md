---
layout: page
title: CSS Layout
permalink: /css/layout
---

Méthodes de positionnement et mise en page
----------

![](/cours-web/cours-css/img/stores-css.gif)

Deux bonnes introductions à la mise en page et au positionnement CSS:

* *[Introduction au positionnement CSS](http://www.pompage.net/traduction/introduction-au-positionnement-css)*, par Noah Stokes, 2010 (aussi [en anglais](http://alistapart.com/article/css-positioning-101)).
* *[Apprendre les mises en page CSS](http://fr.learnlayout.com/)*, par Greg Smith.

Le modèle de boîte
------------------

Le modèle de mise en page du HTML / CSS repose sur un principe de "boîtes" (en anglais: box-model). Ces boîtes sont définies géométriquement par les paramètres suivants:

- **Largeur** (width)
- **Hauteur** (heigth)
- **Bordure** (border)
- **Marge intérieure** (padding)
- **Marge extérieure** (margin)

La propriété box-sizing: border-box
-----------------------------------

La propriété **box-sizing**, ajoutée en CSS3, permet de définir la manière dont la largeur d'un élément est calculée.

La valeur par défaut est "content-box", elle signifie que la **largeur** est celle du **contenu** uniquement. Le padding (marge intérieure), la bordure et la marge extérieure vont s'ajouter.

Imaginons un élément auquel on donne ces règles:

```css
.element {
	width: 200px;
	padding: 10px;
	border: 2px;
	margin: 10px;
}
```

Cet élément aura une largeur effective de 200+(2x10)+(2x2)+(2x10) = 244 pixels. Tout s'additionne, y compris le padding, la bordure, la marge.

Si on utilise `box-sizing: border-box`, alors la **marge intérieure** et la **bordure** sont compris dans la largeur (width). Un paragraphe situé dans cet élément de 200px n'aura donc que 176px de large (on soustrait aux 200px les 2x10px de padding et 2x2px de bordure). Il n'y a que la **marge extérieure** (2x10px) qui s'additionne. L'élément fait donc 220px de large. 

Le mode `box-sizing: border-box` est bien supporté par les navigateurs actuels (état mai 2016):
[http://caniuse.com/#feat=css3-boxsizing](http://caniuse.com/#feat=css3-boxsizing)

De nombreux designers ont commencé à appliquer le mode `box-sizing: border-box` sur tous leurs éléments de mise en page, jugeant ce comportement plus intuitif. Le framework *Boostrap* suit cette pratique.

**Références:**

Article de Paul Irish, membre de l'équipe Google Chrome:
[http://www.paulirish.com/2012/box-sizing-border-box-ftw/](http://www.paulirish.com/2012/box-sizing-border-box-ftw/)

L'auteur se prononce en faveur de l'utilisation d'un "reset" global pour appliquer le mode *border-box* à tous les éléments:

```css
/* apply a natural box layout model to all elements, 
 * but allowing components to change */
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}
```

Utilisation dans Bootstrap, depuis 2013:

- [http://blog.getbootstrap.com/2013/08/19/bootstrap-3-released/](http://blog.getbootstrap.com/2013/08/19/bootstrap-3-released/)
- [https://github.com/twbs/bootstrap/issues/12351](https://github.com/twbs/bootstrap/issues/12351)

En 2014, le site CSS Tricks déclare le 1er février comme étant la Journée Internationale du box-sizing (*International box-sizing Awareness Day*):    
[https://css-tricks.com/international-box-sizing-awareness-day/](https://css-tricks.com/international-box-sizing-awareness-day/)

Un article (en français) qui résume tout cela:    
[https://la-cascade.io/controler-le-modele-de-boite/](https://la-cascade.io/controler-le-modele-de-boite/)

Mise en page CSS
----------

Depuis le lancement du CSS en 1996, diverses techniques ont été développées pour créer des mises en page avec ce langage.

Pendant longtemps, des mises en page ont été créées avec le positionnement **"Float"**. Depuis l'introduction du CSS3, on peut utiliser le module **CSS Flexbox**. Pour l'avenir, le module **CSS Grid Layout** propose des solutions intéressantes.

![](/cours-web/cours-css/img/Strips-Vieux-coder-VS-jeune-codeur.jpg)

Positionnement avec Float
===

"En octobre 2002, le site du magazine wired.com a bénéficié d'une refonte qui n'utilisait aucune table", déclare Eric Meyer (alors employé de Netscape) dans un discours[^1] à la conférence TODCON (*The Other Dreamweaver Conference*) en 2003. Meyer démontre que l'utilisation du CSS pour la mise mise en page (au lieu des tableaux) permet de gagner du temps de développement, et de réduire le temps de chargement d'un site.

[^1]: "In October 2002, wired.com redesigned using no tables at all. (...) Basically [Eric Meyer] presented proof of how much bandwidth and time CSS layouts can save you" - http://meyerweb.com/eric/talks/2003/todcon/payoff/keynote.html

En 2004, des designers web font une véritable campagne pour pousser leur profession à abandonner les mises en page construites avec des tableaux HTML. 

- Dans son livre *More Eric Meyer on CSS* (2004), Eric Meyer décrit comment convertir des tableaux en mises en page CSS.
- Douglas Bowman donne la présentation *No More Tables, CSS Layout Techniques*[^2] à la conférence Digital Design World à Seattle, durant laquelle il "reconstruit" le site actuel de Microsoft.

[^2]: http://stopdesign.com/archive/2004/07/27/throwing-tables.html

Pour maîtriser la méthode de mise en page CSS préconisée, il est essentiel de comprendre les propriétés CSS suivantes:

- **float** (valeurs possibles: left, right)
- **clear** (valeurs possibles: left, right, both)

![Un exemple d'utilisation de {float: left}](/cours-web/cours-css/img/layout-float2p.png)

Cette méthode présente toutefois des difficultés, quand il s'agit de créer une mise en page flexible (avec des largeurs de colonnes exprimées en pourcentage). Dans le jargon, on parle du "Holy Grail Layout" (le *Saint Graal* de la mise en page), qui comprend deux colonnes à largeur fixe (les barres latérales), et un contenu central à largeur flexible (qui augmentera avec la taille de l'écran).

![Holy Grail Layout](/cours-web/cours-css/img/holy-grail-div-structure.png)    
*Une structure HTML complexe pour obtenir le Holy Grail Layout*

Une nouvelle approche: Flexbox
===

Flexbox est un module CSS récent, qui propose une manière novatrice de définir des mises en page extrêmement "flexibles". Ce module est récemment passé du statut de "Working Draft" (depuis 2009) à "Candidate Recommendation". 

Dans la pratique, le module Flexbox est déjà bien supporté par les navigateurs. On peut donc envisager son utilisation pour des projets réels. Le framework *Bootstrap* a récemment modifié son système de grille de mise en page pour utiliser Flexbox.

![Flexbox support](/cours-web/cours-css/img/flexbox-caniuse.png)
*Support des navigateurs pour Flexbox (source: [Can I Use](http://caniuse.com/#feat=flexbox), mars 2016)*

#### Ressources Flexbox

Quelques bonnes ressources pour maîtriser ce module CSS:

- Une démonstration: [https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/](https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/)
- Un article: [http://fr.learnlayout.com/flexbox.html](http://fr.learnlayout.com/flexbox.html)
- Un autre article sur Alsa Créations:
[http://www.alsacreations.com/tuto/lire/1493-css3-flexbox-layout-module.html](http://www.alsacreations.com/tuto/lire/1493-css3-flexbox-layout-module.html)
- Un article (en anglais): 
[https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- Des exemples d'usages typiques:
[http://philipwalton.github.io/solved-by-flexbox/](http://philipwalton.github.io/solved-by-flexbox/)
- [Un exemple de Holy Grail layout](https://jsfiddle.net/n7nk0hac/79/), par Belén Albeza

Musique d'avenir: CSS Grid Layout
===

Le *CSS Grid Layout* est une nouvelle spécification CSS, en cours d'implémentation, qui a le potentiel de révolutionner la mise en page CSS. Comme son nom l'indique, il s'agit d'un modèle de mise en page basé sur une *grille* à deux dimensions, sur laquelle viennent se placer des blocs de contenu.

Cette fonctionalité CSS a été proposée en 2011 par Microsoft, et implémentée à fins de test dans Internet Explorer 10 et 11. Le projet a été repris par le W3C, et est en cours de développement.

Les navigateurs actuels offrent la possiblité aux développeurs de tester ce module CSS, mais il est nécessaire d'activer la fonctionalité. Voici des informations sur la manière de l'activer: [http://igalia.github.io/css-grid-layout/enable.html](http://igalia.github.io/css-grid-layout/enable.html)

#### Ressources CSS Grid Module

* Support actuel des navigateurs: [http://caniuse.com/#feat=css-grid](http://caniuse.com/#feat=css-grid)
* Un tutoriel (le site de référence de Rachel Andrew): [http://gridbyexample.com/what/](http://gridbyexample.com/what/)
* Un autre tutoriel (par Alsa Créations):
[http://www.alsacreations.com/article/lire/1388-css3-grid-layout.html](http://www.alsacreations.com/article/lire/1388-css3-grid-layout.html)
* Un livre publié en début 2016 par Rachel Andrew: *Get Ready For CSS Grid Layout*, A Book Apart, 2016

Références - mise en page CSS:
===

**En français:**

- *[Le tournant des CSS vers le Layout](http://www.paris-web.fr/2012/conferences/le-tournant-des-css-vers-le-layout.php)* - conférence de Daniel Glazman, à Paris Web 2012. Présente diverses nouveautés: CSS Variables, CSS Flexbox, CSS Regions, CSS Exclusions and Shapes, CSS Grids, Blending & Compositing, Web Fonts, CSS Filter Effects.
- [Learn CSS Layout](http://fr.learnlayout.com/) - un tutoriel très complet pour apprendre la mise en page CSS. Ecrit par Greg Smith, traduction par Joël Matelli.

**En anglais:**

- *[An Introduction to CSS Grid Layout](http://www.paris-web.fr/2015/conferences/an-introduction-to-css-grid-layout.php)* - conférence de Rachel Andrew, à Paris Web 2015, Présente le module CSS Grid Layout.
- *[The Magic of CSS](http://adamschwartz.co/magic-of-css/)*, par Adam Schwartz, un tutoriel en six chapitres. Introduction basique, il n'aborde pas Flexbox ou Grid Layout.
- [Learn HTML & CSS](http://www.frontendhandbook.com/learning/html-css.html), liste de références et tutoriels sur le développement frontend.

