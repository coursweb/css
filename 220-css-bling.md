---
layout: page
title: CSS bling
permalink: /css/css3-bling
---


Effets visuels apportés par le CSS3
---------

Selon l'article "[CSS3 Bling in the Real World](http://alistapart.com/article/css3-bling-in-the-real-world)", par Chris Mills, 2011:

- Les dégradés de couleurs ([gradients](http://caniuse.com/#feat=css-gradients))
- Les ombres portées (box shadow, text shadow) - [box-shadow](http://caniuse.com/#feat=css-boxshadow), [text-shadow](http://caniuse.com/#feat=css-textshadow)
- L'opacité ([Opacity](http://caniuse.com/#feat=css-opacity))
- Les bords arrondis (Rounded corners) - [border-radius](http://caniuse.com/#feat=border-radius)
- Les fontes web ([Web fonts](http://caniuse.com/#feat=fontface)) 

Drop shadows
===

Tout d'abord, qu'est-ce que le drop shadows?

Il s'agit d'une ombre autour d'un élément (à ne pas confondre avec box-shadow, qui ajoute un cadre transparent à l'image et en suite met l'ombre autour!).

De plus, le drop shadow conserve la transparence de l'image et suit le contour de celle-ci.

Par contre, cette fonctionnalité ne peut pas étendre son ombre, elle la génère automatiquement.

Pour un bon exemple: [Les filtres CSS opacity et drop-shadow](https://iamvdo.me/blog/les-filtres-css-opacity-et-drop-shadow), par Vincent De Oliveira, 2013

Les filtres CSS sont supportés par les navigateurs depuis plusieurs années (2011 pour Safari, 2015 pour Firefox). Les filtres CSS incluent également:

* blur()
* brightness()
* contrast()
* drop-shadow()
* grayscale()
* hue-rotate()
* invert()
* opacity()
* saturate()
* sepia()

Voir [la documentation Mozilla](https://developer.mozilla.org/fr/docs/Web/CSS/filter) pour des exemples détailés.


Opacité
===

Rounded corners
===

Animation
===

Transitions et Keyframes

**Technique des transitions** : utile pour des animations avec un état de début et de fin.

**Technique des keyframes** : utile pour des animations en boucle, ou avec différentes étapes.

Un exemple: http://www.leemunroe.com//css-transitions/



Modes de fondu (CSS blend modes)
===

Nous connaissons les "modes de fondu" disponibles dans des applications comme Photoshop, permettant de jouer avec les superpositions des images. Ces modes de fondu sont disponibles également en CSS.

Support dans les navigateurs: encore non supporté dans Internet Explorer et Edge ([caniuse](http://caniuse.com/#feat=css-backgroundblendmode)).

Références: [A List Apart](http://alistapart.com/article/blending-modes-demystified).

Références:
===

- [The box-shadow Property](https://bitsofco.de/the-box-shadow-property/), par Ire Aderinokun.
- [The Background Properties](https://bitsofco.de/the-background-properties/), par Ire Aderinokun.

