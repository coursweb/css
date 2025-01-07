---
layout: page
title: CSS - bonnes pratiques
permalink: bonnes-pratiques.html
---

# Bonnes pratiques - écrire du bon CSS

Quelques articles:

- [Principes à connaître pour améliorer vos feuilles de styles](http://www.pompage.net/traduction/ameliorer-vos-feuilles-de-styles), par Hugo Giraudel, 2012
- [Pour des sélecteurs CSS raccourcis](http://www.pompage.net/traduction/pour-des-selecteurs-css-raccourcis), par Harry Roberts, 2012

Comment organiser ses feuilles de style? Un exemple: [la méthode Daisy](http://daisy.tetue.net/), proposée par Romy Duhem-Verdière.

Deux expertes qui ont donné d'excellentes conférences sur les bonnes pratiques en CSS:

* Nicole Sullivan.
* Nathalie Downe, l'une des premières à parler de systèmes de design : voir les slides de ses présentations *[CSS Systems](http://fr.slideshare.net/nataliedowne/css-systems-presentation/2-WRITING_MAINTAINABLE_CSSNatalie_Downe_Barcamp)* (2008) et *Practical, maintainable CSS* (2009).

## Outils et méthodes

Des principes pour nommer les classes CSS, et structurer les feuilles de styles. Voici des méthodes parmi les plus connues:

- la méthode BEM: “Block, Element, Modifier” - [https://en.bem.info/methodology/](https://en.bem.info/methodology/)
- ITCSS - "[Inverted Triangle CSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/)", par Harry Roberts de CSSwizardry.com
- [SMACSS](http://smacss.com/) - "Scalable and Modular Architecture for CSS", par Jonathan Snook

### Frameworks CSS

Quelques frameworks CSS en utilisation:

* [ZURB Foundation](http://foundation.zurb.com/) - lancé en 2011 par ZURB, une agence de design californienne.
* [Bootstrap](http://getbootstrap.com/) - lancé en 2011 par Mark Otto et Jacob Thornton, développeurs chez Twitter.
* [Röcssti](https://rocssti.net/), un micro-framework CSS, par Nicolas Hoffmann.

Anciens frameworks (aperçu historique):

* Yahoo User Interface Library (YUI) - lancé en 2006, abandonné en 2014.
* [Blueprint](http://www.blueprintcss.org/) - lancé en 2007, comme alternative à la Yahoo UI Library, abandonné en 2011.
* [960 grid system](http://sonspring.com/journal/960-grid-system), lancé en 2008 par Nathan Smith (le chiffre 960 fait référence à la largeur d'écran de 960px couramment utilisée vers 2008).
* [pure.css](http://purecss.io/) - par Yahoo, lancé en 2013, abandonné en 2015.

Une [liste de frameworks CSS](https://en.wikipedia.org/wiki/CSS_frameworks) sur Wikipédia.

L'utilisation d'un Framework n'est pas forcément une bonne pratique: lire l'article de Belén Albeza, *[You might not need a CSS framework](https://hacks.mozilla.org/2016/04/you-might-not-need-a-css-framework/)*.

En 2012, Jacob Thornton, co-auteur de Bootstrap, [écrivait](http://byfat.xxx/deep-emo-shit):

> For me, Bootstrap is very fun, not serious – nearly every line is a joke. It’s trying to provoke you. Taking shortcuts. Demanding that you reread it. Reread it again. It’s very pop. Very optimistic. Forward. Playful.

En 2017, avec l'arrivée du module **CSS Grids** dans les navigateurs, il n'est plus très pertinent d'utiliser une grille préconçue par un framework - il est tout aussi facile de la créer directement en CSS.

Afin d'illustrer cela, Jen Simmons a créé un framework parodique, [960 Grid Grid Grid](https://github.com/jensimmons/960gridgridgridme/blob/gh-pages/css/960gridgridgrid.css) : "a silly project from someone who is starting to hate 12-column symmetrical grid frameworks"

### Préprocesseurs (Less, Sass...)

Autoprefixer:    
[https://github.com/postcss/autoprefixer](https://github.com/postcss/autoprefixer)

[SMACSS](https://smacss.com/) - "Scalable and Modular Architecture for CSS", par Jonathan Snook, est une méthodologie pour la construction des feuilles de style.

[http://cssguidelin.es/](http://cssguidelin.es/) - High-level advice and guidelines for writing sane, manageable, scalable CSS - par Harry Roberts.

[Enduring CSS](http://ecss.io/) - A guide to writing style sheets for large scale, rapidly changing, long-lived web projects - par Ben Frain. 

[http://tympanus.net/codrops/2013/07/17/troubleshooting-css/](http://tympanus.net/codrops/2013/07/17/troubleshooting-css/)