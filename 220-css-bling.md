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

Tout d'abord, qu'est-ce que les *drop shadows*?

Il s'agit d'une ombre autour d'un élément (à ne pas confondre avec *box-shadow*, qui ajoute un cadre transparent à l'image et ensuite met l'ombre autour!).

De plus, le *drop shadow* conserve la transparence de l'image et suit le contour de celle-ci.

Par contre, cette fonctionnalité ne peut pas étendre son ombre, elle la génère automatiquement.

Pour un bon exemple: [Les filtres CSS opacity et drop-shadow](https://iamvdo.me/blog/les-filtres-css-opacity-et-drop-shadow), par Vincent De Oliveira, 2013.

Et voici un exemple de code CSS, qui ajoute une ombre portée blanche à une image:

```css
img {
	-webkit-filter: drop-shadow(5px 5px 5px white);
	filter: drop-shadow(5px 5px 5px white);
}
```

![Illustration de l'exemple](/cours-css/img/filter-drop-shadow.png)

Les **filtres CSS** sont supportés par les navigateurs depuis plusieurs années (2011 pour Safari, 2015 pour Firefox). Les filtres CSS - similiares aux effets visuels de Photoshop - incluent également:

* blur() - permet d'ajouter du flou
* brightness() - modifie la luminosité
* contrast() - modifie le contraste des couleurs
* drop-shadow() - ombre-portée (on vient de le voir)
* grayscale() - niveaux de gris
* hue-rotate() - modifie la teinte
* invert()
* opacity() - modifie l'opacité
* saturate() - modifie la saturation des couleurs
* sepia() - donne une teinte monochrome

Voir [la documentation Mozilla](https://developer.mozilla.org/fr/docs/Web/CSS/filter) pour des exemples détailés.


Opacité
===
La fonction opacité permet de gérer la transparence d'un élément.

Opacité d'une image:
La fonction a une valeur allant de "0.0" à "1.0". "0.0" est le plus transparent et "1.0" le plus opaque.
(/cours-css/img/opacite02.jpg)(/cours-css/img/opacite05.jpg) (/cours-css/img/opacite1.jpg)

Veuillez noter qu'Internet Explorer 8 et ultérieur n'utilise pas le même code! Il faut utiliser filter:alpha(opacity=x) le x a une valeur allant de 0 jusqu'à 100, 100 étant le plus opaque. 

Exemple : 
img {
    opacity: 0.5;
    filter: alpha(opacity=50); /* Pour IE8 et ultérieur */
}

"Transparent Hover Effect":
l'effet d'opacité peut être utilisé avec le sélecteur :hover, pour qu'une image transparente devienne opaque quand la souris passe dessus. 

Exemple :
img {
    opacity: 0.5;
    filter: alpha(opacity=50); /* Pour IE8 et ultérieur */
}

img:hover {
    opacity: 1.0;
    filter: alpha(opacity=100); /* Pour IE8 et ultérieur */
}

Pour l'effet inverse, il suffit de mettre une valeur inférieur à 1
Exemple:
img:hover {
    opacity: 0.5;
    filter: alpha(opacity=50); /* Pour IE8 et ultérieur */
}

Box transparentes 
Il est possible d'utiliser l'effet d'opacité pour l'arrière-plan, des "box" qui composent la page.L'effet se répetera également sur les éléments se situant dans la box. 
Exemple: 
div {
    opacity: 0.3;
    filter: alpha(opacity=30); /* Pour IE8 et ultérieur */
}

Il est également possible d'utiliser les valeurs colorimétriques RGBA pour l'effet d'opacité. A utiliser comme dans cet exemple: div {
    background: rgba(76, 175, 80, 0.3) /* arrière-plan vert avec 30% d'opacité */
}

Pour que l'arrière-plan d'un texte soit en transparence, suivez l'exemple du code complet d'une page: 
<html>
<head>
<style>
div.background {
    background: url(img.jpg) repeat;
    border: 2px solid black;
}

div.transbox {
    margin: 30px;
    background-color: #ffffff;
    border: 1px solid black;
    opacity: 0.6;
    filter: alpha(opacity=60); /* Pour IE8 et ultérieur */
}

div.transbox p {
    margin: 5%;
    font-weight: bold;
    color: #000000;
}
</style>
</head>
<body>

<div class="background">
  <div class="transbox">
    <p>This is some text that is placed in the transparent box.</p>
  </div>
</div>

</body>
</html>

Référence : https://www.w3schools.com/css/css_image_transparency.asp

===

Rounded corners
===

Arrondir les coins est sûrement l'un des effets graphiques les plus recherchés par les webdesigners. Pour cela, on a longtemps utilisé des images avec plus ou moins de bonheur et de facilité pour obtenir l'effet recherché.

Tous les navigateurs récents permettent à présent d'arrondir les coins de cadres, d'images, de tableaux etc. avec une facilité déconcertante.

Arrondir les bords d'un cadre:

Code (X)HTML

```html
<div id="coin">
  <p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
  Mauris vulputate laoreet urna. Integer magna. 
  Donec facilisis lectus sed quam. 
  Curabitur sit amet lacus id lacus facilisis venenatis.
  </p>
</div>
```

Code CSS

Il n'y a normalement plus besoin d'utiliser des préfixes propriétaires tels -moz ou -webkit pour avoir la bonne restitution de l'arrondissement des coins. Néanmoins, pour assurer la compatibilité avec des versions de Firefox antérieures à la 4, ou pour le webkit de vieux smartphones, il vaut mieux encore les laisser.

La propriété `border-radius` peut accepter 4 valeurs pour l'arrondissement de chaque coin. La 1ère valeur correspond au coin haut gauche, puis on tourne dans le sens des aiguilles d'une montre.
On peut n'en indiquer que 2, qui correspondront aux coins opposés (voir l'exemple ci-dessous), ou une seule pour un même arrondis sur les 4 coins.

```css
.coin {
  /*arrondir les coins en haut à gauche et en bas à droite*/
  border-radius: 10% 0;
}
```

<p style="background: #b701b7; color: #fff; border-radius: 30px 0;padding:3em 2em;">exemple</p>

Lien avec des explications plus détailées: [https://www.alsacreations.com/tuto/lire/891-coins-arrondis-css-sans-images.html](https://www.alsacreations.com/tuto/lire/891-coins-arrondis-css-sans-images.html)


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




Pour faire un fondu
On applique un effet de dégradé sur chacun de nos élémentsde liste <li>

exemple:
ul li {
      background: linear-gradient (#900, #860083);
      
      Ensuite on applique sur chaque lien un fond de couleurs gris 
      Quand on arrive à notre :hover, on doit faire disparaitre ce fond avec les transitions
      
      D'abord 0 seconde et cela nous fait apparaitre un dégradé violet et il disparait en 0,5 
      Cela donne l'impression que le dégradé disparait.
      
===

- [The box-shadow Property](https://bitsofco.de/the-box-shadow-property/), par Ire Aderinokun.
- [The Background Properties](https://bitsofco.de/the-background-properties/), par Ire Aderinokun.

