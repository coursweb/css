---
layout: page
title: CSS bling
permalink: /css/css3-bling
---


Effets visuels apportés par le CSS3
---------

Selon l'article "[CSS3 Bling in the Real World](http://alistapart.com/article/css3-bling-in-the-real-world)", par Chris Mills, 2011:

- Les dégradés de couleurs ([Linear gradients](http://caniuse.com/#feat=css-gradients))
- Les ombres portées (Drop shadows) - [box-shadow](http://caniuse.com/#feat=css-boxshadow), [text-shadow](http://caniuse.com/#feat=css-textshadow)
- L'opacité ([Opacity](http://caniuse.com/#feat=css-opacity))
- Les bords arrondis (Rounded corners) - [border-radius](http://caniuse.com/#feat=border-radius)
- Les fontes web ([Web fonts](http://caniuse.com/#feat=fontface)) 

Couleurs CSS
=== 

Les couleurs peuvent être exprimés en différents formats:

```css
color: yellow;
color: #FFFF00;
color: #FF0;
color: rgb(255, 255, 0); /*Red, Green, Blue*/
color: hsl(60, 100%, 50%); /*Hue, Saturation, Luminosity*/
```

La couleur jaune peut être définie indifféremment par les cinq variantes ci-dessus. Le résultat sera strictement identique.


#### Par leur nom: 

Il existe quelques 140 couleurs qui sont définies par des mots-clés: on y trouve des couleurs fondamentales comme 
<span style="padding: 0 0.3em; background:black;color:#fff">black</span>, 
<span style="padding: 0 0.3em; background:blue;color:#fff">blue</span>, 
<span style="padding: 0 0.3em; background:red;color:white">red</span>, 
mais aussi des teintes plus originales comme 
<span style="padding: 0 0.3em; background:aquamarine;">aquamarine</span>, 
<span style="padding: 0 0.3em; background:hotpink;color:white">hotpink</span>, 
<span style="padding: 0 0.3em; background:tomato;color:white">tomato</span>, 
<span style="padding: 0 0.3em; background:olive;color:white">olive</span> ...

La liste complète peut être consultée: 

* sur [Wikipédia](https://fr.wikipedia.org/wiki/Couleur_du_Web#Noms_de_couleurs_SVG_1.0)
* sur [HTMLColorCodes.com](http://htmlcolorcodes.com/)
* dans la [spécification W3C](https://www.w3.org/TR/css3-color/#svg-color)

<h4>Code héxadécimal</h4>

Le code hexadécimal (ou *triplet hexadécimal*) est une manière d'exprimer les couleurs du modèle RVB (en anglais: RGB). En RVB, la valeur du rouge (R), vert (V) et bleu (B) sont définis sur un intervalle allant de zéro à 255, ou de 00 à FF en notation hexadécimale. 

Voici trois chats dont les couleurs sont traduites en notation hexadécimale (de manière approximative, 000000 devrait correspondre au noir absolu):

![Chats avec codes hex](/cours-css/img/funny-pictures-hexcode-colors.jpg)

Le nombre total de couleurs possibles est de 256 * 256 * 256, càd quelques 16'777'216 teintes. C'est beaucoup plus que le nuancier pantone, qui n'en comporte que 992!

Dans son œuvre *[#BADA55 in a Can](http://www.evan-roth.com/work/bada55-in-a-can/)* (2008), l'artiste Evan Roth propose de créer des peintures murales "badass" en utilisant le vert correspondant au code hexadécimal #BADA55:

![#BADA55 in a Can](/cours-css/img/bada55-paint-can.JPG)

Si les caractères sont dédoublés, la triplette peut être racourcie à trois chiffres: 

- `#0099cc` est équivalent à `#09c`
- `#00ff00` équivaut à `#0f0`
- `#666666` équivaut à `#666`, etc.

Un bon site de référence: [http://htmlcolorcodes.com/](http://htmlcolorcodes.com/)

#### Rouge, Vert, Bleu

Le CSS autorise également la définition d'une couleur en notation RVB (en anglais: RGB). 

Pour chacune des trois valeurs, on peut utiliser un nombre entier allant de 0 à 255, ou un pourcentage allant de 0% à 100%.

Exemple de deux couleurs identiques:

```css
p { color: rgb(255,0,0) } 
p { color: rgb(100%,0%,0%) }
```

La première valeur étant au maximum, cette couleur correspond au <span style="padding: 0 0.3em; background:rgb(255,0,0);color:#fff">rouge le plus intense</span>.

#### RGBA

RVB avec transparence (alpha), définie sur un intervalle allant de 0.0 à 1.0.

Exemple:

```css
p { color: rgba(255,0,0,0.5) } 
```

La dernière valeur (l'opacité) étant de 0.5, il en résulte <span style="padding: 0 0.3em; background:rgba(255,0,0,0.5);color:#fff">un rouge semi-transparent</span>.

#### Teinte, saturation, luminosité (HSL)

Une nouvelle manière de représenter les couleurs a été introduite avec le CSS3: c'est le modèle HSL (Hue-saturation-lightness), basé sur un cercle chromatique

* **H - Hue**: la teinte (en anglais: *Hue*) correspond à une position (un angle) sur le cercle chromatique. Cet angle est mesuré en degrés, mais il est indiqué sans unité en CSS. Le point de départ du cercle (0 ou 360°) correspond au <span style="color:hsl(0, 100%, 50%)">rouge</span>. Les couleurs sont réparties sur ce cercle, le <span style="color:hsl(120, 100%, 50%);background:#fff">vert</span> se trouvant au premier tiers (120°), le <span style="color:hsl(180, 100%, 50%);background:#fff">cyan</span> à mi-parcours (180°) et le <span style="color:hsl(240, 100%, 50%)">bleu</span> aux deux tiers (240°). 

![Modèle HSL](/cours-css/img/HSL-model.png)

La saturation et la luminosité sont exprimés en pourcentage. 

* **S – saturation**: 100% correspond à la saturation maximale, à 0% on se situe dans les niveaux de gris. 

* **L - luminosité**: 0% correspond au noir, 100% au blanc. À 50% on obtient la luminosité "normale".

Quelques exemples:

-----|-----:
`p { color: hsl(0, 100%, 50%) }` | <span style="padding: 0 0.3em; background:hsl(0, 100%, 50%);color:#fff">rouge</span>
`p { color: hsl(120, 100%, 25%) }` | <span style="padding: 0 0.3em; background:hsl(120, 100%, 25%);color:#fff">vert foncé</span>
`p { color: hsl(120, 100%, 50%) }` | <span style="padding: 0 0.3em; background:hsl(120, 100%, 50%);">vert standard</span>
`p { color: hsl(120, 100%, 75%) }` | <span style="padding: 0 0.3em; background:hsl(120, 100%, 75%);">vert clair</span>
`p { color: hsl(120, 100%, 90%) }` | <span style="padding: 0 0.3em; background:hsl(120, 100%, 90%);">vert très clair</span>
`p { color: hsl(120, 50%, 75%) }` | <span style="padding: 0 0.3em; background:hsl(120, 50%, 75%);">vert désaturé</span>

#### HSLA

Avec une quatrième valeur définissant l'opacité:

```css
p { color: hsla(240, 100%, 50%, 0.5) } /* semi-transparent solid blue */
p { color: hsla(30, 100%, 50%, 0.1) }  /* very transparent solid orange */
```

#### Définir la couleur du texte

Pour donner une couleur au texte en CSS, utiliser la propriété `color`:

```css
p { color: #333; }
```

#### Définir la couleur de fond

Pour donner une couleur de fond à un élément, utiliser la propriété `background-color`:

```css
p { background-color: #C0C0C0; }
```


Dégradés (gradients)
===

Exemple d'utilisation de dégradé CSS:

```css
.gradient {
    background: linear-gradient(180deg, red, blue); 
}
```

<p style="background: linear-gradient(180deg, red, blue);padding:3em 2em;color:#fff">Le résultat.</p>

Exemple avec un angle modifié:

```css
.gradient {
    background: linear-gradient(135deg, red, blue); 
}
```

<p style="background: linear-gradient(135deg, red, blue);padding:3em 2em;color:#fff">Le résultat.</p>

Exemple où on ajoute du noir à mi-chemin (le 50% indique la position sur la longueur du dégradé):

```css
.gradient {
    background: linear-gradient(135deg, red, black 50%, blue);
}
```

<p style="background: linear-gradient(135deg, red,black 50%,blue 100%);padding:3em 2em;color:#fff">Le résultat.</p>

NOTE: ces exemples n'utilisent que la propriété CSS sans préfixe, qui fonctionne dans les navigateurs suivants: IE 10+, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+.

Générateurs de gradients CSS:

- [ColorZilla](http://www.colorzilla.com/gradient-editor/)
- [CSSmatic](http://www.cssmatic.com/gradient-generator)

Drop shadows
===

Opacity
===

Rounded corners
===

Animation
===

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

