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

On utilise l'attribut media `print` pour charger des styles CSS spécifiques pour l'impression d'une page web:

```html
<link rel="stylesheet" media="print" href="impression.css">
```

Ou à l'intérieur d'une feuille de styles CSS, avec la syntaxe suivante:

```css
@media print {
  * { 
      background: #fff;
      color: #000;
    }
}
```

Pour un bon exemple de styles destinés à optimiser une page web pour l'impression, on peut se référer au [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate/blob/main/dist/css/style.css#L182). Lire également [cet article](https://medium.com/@matuzo/i-totally-forgot-about-print-style-sheets-f1e6604cfd6#.npcr2tohy) de Manuel Matuzovic.

#### Références concernant @print 

- *[Faites bonne impression avec les CSS](http://www.pompage.net/traduction/impression)*, par Eric A. Meyer, 2002
- *[Maîtriser l’impression CSS](http://openweb.eu.org/articles/maitriser_impression_css)*, par Nicolas Hoffmann, 2010
- [La spécification CSS 2.1](https://www.w3.org/TR/CSS21/media.html)
- [Les styles @print](https://github.com/h5bp/html5-boilerplate/blob/main/dist/css/style.css#L182) du HTML5Boilerplate - ces styles étaient aussi utilisés [dans Bootstrap 4](https://github.com/twbs/bootstrap/blob/6ffb0b48e455430f8a5359ed689ad64c1143fac2/dist/css/bootstrap.css#L10220) (mais plus depuis la version 5).

## Les Media Queries du CSS3


Avec l'évolution du HTML5 et CSS3, les possibilités de l'attribut "media" sont étendues: on peut charger des styles selon le format de la fenêtre du navigateur, la largeur, la hauteur, la densité des pixels...

Cela a rendu possible le "Responsive Web Design" (RWD).

Un exemple de Media Query:

```css
@media screen and (min-width: 20em) {
  .member-list {
    column-count: 2;	
  }
}
```

On peut aussi omettre le mot-clé `screen` si on souhaite que les styles s'appliquent sur tous les supports:

```css
@media (min-width: 20em) {
  /* Déclarations */
}
```

On peut cumuler différents critères avec le mot-clé `and`:

```css
@media (orientation: portrait) and (min-width: 20em) {
  /* Déclarations */
}

@media (min-width: 30em) and (max-width: 50em) {
  /* … */
}
```

Ce qu'on peut détecter avec des Media Queries:

- Les **dimensions** - `width` et `height` - avec les préfixes `min-` et `max-`.
- L’**orientation** de l'écran, avec les valeurs `portrait` ou `landscape` (paysage).
- Le **ratio hauteur/largeur** de l’écran, avec `aspect-ratio`. 
- La **résolution**, mesurée en DPI, avec les préfixes `min-` et `max-` et une valeur comme `144dpi`. On peut aussi mesurer la densité par pixel (dppx), avec des valeurs comme `1.5dppx`ou `2dppx`.
- La préférence d'un mode sombre avec `prefers-color-scheme: dark`.

```css
@media (aspect-ratio: 16/9) {
  /* … */
}

@media (min-resolution: 144dpi) {
  /* … */
}

@media (prefers-color-scheme: dark) {
  /* … */
}
```
Concernant la résolution, selon Raphaël Goetter:

> Il existe des tas de résolutions différentes à l’heure actuelle ; ça dépend entièrement de l’appareil. Certains, comme les ordinateurs non-retina sont à 1. Des téléphones sont à 1.3, d’autres à 1.5, des appareils de tout type sont à 2, certains sont à 3. C’est pour cette raison qu’il est préférable de tester une résolution supérieure à 1.3 ou 1.5, et de traiter tous ces écrans de la même façon.

### Le design Mobile First

La méthode du design "Mobile First" consiste à prévoir un design pour les petits écrans en priorité, puis d'élargir le cadre pour les grands écrans. Cette méthode utilise une succession de Media Queries:

```css
/**
  * Styles hors d’une Media Query
  * pour les petits écrans (smartphones)
  */

@media (min-width: 600px) {
   /**
    * Styles pour écrans à partir de 600 px de large,
    * vraisemblablement les premières tablettes
    */
}

@media (min-width: 900px) {
   /**
    * Styles pour écrans à partir de 900 px de large,
    * les ordinateurs portables et grandes tablettes
    */
}

@media (min-width: 1200px) {
   /**
    * Styles pour écrans à partir de 1200px de large,
    * les écrans de bureau et grands portables
    */
}
```

Les valeurs-limite que l'on définit pour basculer d'un design (p.ex: petite tablette) vers un autre (p.ex: ordinateur) se nomment **Breakpoints**.

### Tester la hauteur de l'écran

Bien que l’on teste souvent la largeur de l’écran, il peut parfois être utile de conditionner la mise en page en fonction de la hauteur de l’écran. Un cas d’usage intéressant serait de n’implémenter un en-tête fixe que lorsque l’écran fait une certaine hauteur.

```css
.header {
   height: 200px;
}
 /**
  * Uniquement les écrans ayant une hauteur
  * d’au moins 800 pixels
  */
@media (min-height: 800px) {
  .header {
    position: fixed;
    top: 0; 
  }
}
```


### Références:

- *[Responsive Web Design](http://alistapart.com/article/responsive-web-design)*, par Ethan Marcotte, alistapart, 2010
(aussi [en français](http://gobanclub.net/2010/11/17/responsive_webdesign_ethan_marcotte_trad_fr/))
- *[Responsive Webdesign – présent et futur de l’adaptation mobile](http://openweb.eu.org/articles/responsive-webdesign-present-et-futur-de-l-adaptation)*, par Stéphanie Walter, openweb, 2013. Sujets abordés: images responsives, `<picture>`, srcset, image-set(), WebP, flexbox, CSS columns, Grid Layout, iframes, navigation...

### Questions de détail

Faut-il les écrire les Media Queries en pixels ou en EM?

Un article qui préconise l'usage des EM:    
[http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/](http://blog.cloudfour.com/the-ems-have-it-proportional-media-queries-ftw/)

