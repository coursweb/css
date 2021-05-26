---
layout: page
title: CSS Layout - Flexbox
permalink: flexbox.html
---


Flexbox est un module CSS qui propose une manière novatrice de définir des mises en page "flexibles". Il s'agit d'un modèle de mise en page optimisé pour le design d'interfaces.

> In the flex layout model, the children of a flex container can be laid out in any direction, and can “flex” their sizes, either growing to fill unused space or shrinking to avoid overflowing the parent. Both horizontal and vertical alignment of the children can be easily manipulated. Nesting of these boxes (horizontal inside vertical, or vertical inside horizontal) can be used to build layouts in two dimensions.

Il s'agit d'un module, composé de tout un ensemble de propriétés.

## La liste de toutes les propriétés introduites avec Flexbox:

En premier, pour appliquer la  mise en page flexbox, il faut donner cette propriété à l'élément parent:

```
display: flex;
```

À présent, on a accès à toute une série de nouvelles propriétés qui peuvent être appliqués à l'élément parent, ou à un élément enfant.

## Pour l'élément parent

* flex-direction : la direction, horizontale ou verticale (row / column).
* flex-wrap : permettre ou non aux éléments de se mettre sur plusieurs lignes (nowrap / wrap / wrap-reverse)
* flex-flow : cette propriété combine flex-direction et flex-wrap.

### Alignement:

* justify-content : alignement sur l'axe principal. Valeurs possibles: flex-start, flex-end, center, space-between, space-around.
* align-items: alignement perpendiculaire. Valeurs possibles: stretch, flex-start, flex-end, center, baseline.
* align-content: comportement si on a plusieurs lignes de flex-items. Mêmes valeurs que justify-content, ainsi que stretch.

## Pour les éléments enfants

* order: permet de donner un chiffre, indiquant sa place.
* flex-grow: chiffre sans unité, permettant de donner son facteur de taille comparé aux autres éléments.
* flex-shrink: indique si on autorise l'élément à rétrécir.
* flex-basis: taille par défaut de l'élément.
* flex: propriété qui regroupe flex-grow, flex-shrink et flex-basis. La valeur par défaut est: 0 1 auto.

* align-self: Alignement. Similaire au "align-items" de l'élément parent. Valeurs possibles: auto, flex-start, flex-end, center, baseline, stretch.

#### Ressources Flexbox

Quelques bonnes ressources pour maîtriser ce module CSS:

- La référence officielle du W3C: [https://www.w3.org/TR/css-flexbox/](https://www.w3.org/TR/css-flexbox/)
- Une démonstration: [https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/](https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/)
- Un article: [http://fr.learnlayout.com/flexbox.html](http://fr.learnlayout.com/flexbox.html)
- Un autre article sur Alsa Créations (Tutoriel par Raphael Goetter, auteur du livre "CSS Flexbox"):
[http://www.alsacreations.com/tuto/lire/1493-css3-flexbox-layout-module.html](http://www.alsacreations.com/tuto/lire/1493-css3-flexbox-layout-module.html)
- Un article (en anglais): 
[https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- Des exemples d'usages typiques:
[http://philipwalton.github.io/solved-by-flexbox/](http://philipwalton.github.io/solved-by-flexbox/)
- [Un exemple de Holy Grail layout](https://jsfiddle.net/n7nk0hac/79/), par Belén Albeza

