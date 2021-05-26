---
layout: page
title: RWD
permalink: responsive.html
---

Le "responsive web design" est un terme popularisé par Ethan Marcotte en 2010, d'abord lors de sa conférence "A Dao of Flexibility" (An Event Apart, Seattle, avril 2010), puis [dans un article](http://alistapart.com/article/responsive-web-design) (mai 2010), puis [dans un livre](https://abookapart.com/products/responsive-web-design) (2011).

Media Queries et RWD (Responsive Web Design)
---------

L'élément-clé qui est au coeur de cette approche "responsive" du web design sont les **Media Queries**, un propriété introduite avec le CSS3.

L'ancêtre des Media Queries: les styles CSS pour l'impression
===

Depuis le standard HTML4/CSS2, introduit en 1997, un attribut `media` est disponible, permettant de réserver des styles CSS à un certain type de médias. Voici leur liste:

`all` `aural` `braille` `embossed` `handheld` `print` `projection` `screen` `tty` `tv`

En théorie, le CSS peut donc définir des styles particuliers pour des "médias" spécifiques – ces médias pouvant être des écrans (`screen`), moniteurs de télévision (`tv`), projecteurs (`projection`), mais aussi des systèmes de synthèse vocale (`aural`), voire des appareils rendant les contenus de manière tactile (`braille`, `embossed`). 

Cependant, dans la pratique réelle, les seuls medias qui soient supportés par les navigateurs sont `screen` et `print`.

On utilise souvent l'attribut media `print` pour charger des styles CSS spécifiques pour l'impression d'une page web:

```html
<link rel="stylesheet" media="print" href="impression.css">
```

Ou à l'intérieur d'une feuille de styles CSS, avec la syntaxe suivante:

```css
@media screen {
  * { font-family: sans-serif }
}
```

Pour un bon exemple de styles destinés à optimiser une page web pour l'impression, on peut se référer au [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate/blob/master/dist/css/main.css#L205). Lire également [cet article](https://medium.com/@matuzo/i-totally-forgot-about-print-style-sheets-f1e6604cfd6#.npcr2tohy) de Manuel Matuzovic.

<h4>Références concernant @print:</h4> 

- *[Faites bonne impression avec les CSS](http://www.pompage.net/traduction/impression)*, par Eric A. Meyer, 2002
- *[Maîtriser l’impression CSS](http://openweb.eu.org/articles/maitriser_impression_css)*, par Nicolas Hoffmann, 2010
- [La spécification CSS 2.1](https://www.w3.org/TR/CSS21/media.html)
- [Les styles @print](https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css#L197) du HTML5Boilerplate - ces styles sont aussi utilisés [dans Bootstrap](https://github.com/twbs/bootstrap/blob/master/dist/css/bootstrap.css#L190).

Les Media Queries du CSS3
===

Avec l'évolution du HTML5 et CSS3, les possibilités de l'attribut "media" sont étendues: on peut maintenant charger des styles selon le format de la fenêtre du navigateur, la largeur, la hauteur, la densité des pixels...

Cela a rendu possible le "Responsive Web Design" (RWD).

RWD (Responsive Web Design)
-----

TODO: explicatif et exemples...

Un exemple de media query:

```css
@media screen and (min-width: 20em) {
  .member-list {
    column-count: 2;	
  }
}
```

Références:

- *[Responsive Web Design](http://alistapart.com/article/responsive-web-design)*, par Ethan Marcotte, alistapart, 2010
(aussi [en français](http://gobanclub.net/2010/11/17/responsive_webdesign_ethan_marcotte_trad_fr/))
- *[Responsive Webdesign – présent et futur de l’adaptation mobile](http://openweb.eu.org/articles/responsive-webdesign-present-et-futur-de-l-adaptation)*, par Stéphanie Walter, openweb, 2013. Sujets abordés: images responsives, `<picture>`, srcset, image-set(), WebP, flexbox, CSS columns, Grid Layout, iframes, navigation...

Questions de détail
=== 

Faut-il les écrire les Media Queries en pixels ou en EM?

Un article qui préconise l'usage des EM:    
[http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/](http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/)

