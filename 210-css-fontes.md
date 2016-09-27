---
layout: page
title: Fontes & typographie
permalink: /css/typographie
---

Propriétés CSS spécifiques à la typographie:

* **font-family** : permet de spécifier la police.
* **font-size** : permet de spécifier la taille de la police.
* **font-style** : permet de spécifier un style (*italic* ou *oblique*).
* **font-weight** : permet de spécifier la graisse, avec un mot-clé (*normal*, *bold*) ou avec une valeur numérique allant de 100 à 900 (voir ci-dessous).
* **font-variant** : permet de spécifier des petites majuscules, avec la valeur "small-caps".

Liste des équivalences des valeurs numériques du `font-weight`:

* 100 - équivalent à *Ultra-light* ou *Thin*
* 200 - équivalent à *Light* ou *Extra-Light*
* 300 - équivalent à *Book* ou *Light*
* **400** - équivalent à *Normal* (ou *Roman*, *Regular*), c'est la valeur par défaut
* 500 - équivalent à *Medium*
* 600 - équivalent à *Semi-Bold* 
* **700** - équivalent à *Bold* (gras)
* 800 - équivalent à *Extra-Bold* ou *Black*
* 900 - équivalent à *Ultra-Bold* ou *Extra-Black*

Pour que ces variantes soient visibles, il faut que la fonte les supporte. De nombreuses fontes ne proposent que les versions *normal* et *bold*. D'autres offrent plus d'options: *Univers* propose 5 versions (*45 Light, 55 Roman, 65 Bold, 75 Black, 85 Extra Black*), *Helvetica Neue* en comporte 8 (*Ultra-Light, Thin, Light, Normal, Medium, Bold, Heavy, Black*). 

Voici quelques fontes qui proposent toutes les 9 variantes supportées par le CSS: [Exo](https://fonts.google.com/specimen/Exo), [Libre Franklin](https://github.com/impallari/Libre-Franklin), ou [Raleway](https://github.com/impallari/Raleway).

![Tailles CSS dans Exo, Libre Franklin, Raleway](/cours-web/cours-css/img/CSS-font-weight.png)

Autres propriétés:

* **line-height** : la hauteur de ligne 
* **text-transform** : permet de forcer les majuscules ou minuscules.
* **text-decoration** : permet d'appliquer un soulignement.
* **font-stretch** : permet de spécifier l'utilisation d'une fonte *condensed*, *semi-condensed*, *ultra-condensed* etc.

Réglages typographiques avancés
---------

- text-align (left, right, center, justify): alignement
- text-indent: retrait de la première ligne d'un paragraphe
- word-spacing: espacement entre les mots
- letter-spacing: espacement des caractères
- vertical-align

Retrait
====

Pour un retrait de la première ligne, utiliser le code suivant:

```css
p { text-indent: 1.8em }
```

Pour ajouter une lettrine ("drop cap" en anglais) au début d'un paragraphe:

```css
p::first-letter {
  font-size: 200%;
  float: left;
}
```

Hyphenation, césure
====

#### La propriété "hyphens"

Les navigateurs Firefox, Safari et IE10 supportent la césure (en anglais, *hyphenation*) depuis 2012. Actuellement (fin 2016) Chrome est en voie de l'implémenter.

Exemple de code fonctionnel en 2016:

```css
article p {
  word-break: break-word; /* solution de contournement pour Chrome */
  -webkit-hyphens: auto;
  -moz-hyphens: auto;
  -ms-hyphens: auto;
  hyphens: auto;
}
```

Les valeurs possibles sont: 

- `none` : pas de césure.
- `auto` : le navigateur applique la césure, en utilisant un dictionnaire de césure (fourni par le système d'exploitation). Pour que cela fonctionne, l'attribut `lang` doit être renseigné (normalement sur la balise html). 
- `manual` : la césure est uniquement appliqué si des caractères de césure sont présents, càd des tirets visibles, ou des tirets invisibles (*soft hyphen*, rendu par le code html `&shy;`).

Lire:  
[La gestion de la césure en CSS](http://openweb.eu.org/articles/la-gestion-de-la-cesure-en-css), par Nicolas Hoffmann, 2013.

widows & orphans
====

Le CSS propose des réglages typographiques concernant les [veuves et orphelines](https://fr.wikipedia.org/wiki/Veuves_et_orphelines).

Ces propriétés CSS permettent d'éviter des lignes isolées (avant ou après un saut de colonne) en indiquant un nombre de lignes minimum:

```css
.colonne p {
   orphans: 3; /* min 3 lignes en bas de colonne */
   widows: 2; /* min 3 lignes en haut de colonne */
}
```

Ces règles peuvent aussi être utilisées pour les sauts des pages dans les styles destinés à l'impression.

Acutellement, ces propriétés ne sont pas prises en compte dans Firefox: [http://caniuse.com/#feat=css-widows-orphans](http://caniuse.com/#feat=css-widows-orphans)

Macrotypographie du web
------

![](/cours-web/cours-css/img/macrotypographie-titres.png)

Exemples de styles appliqués aux titres, tirés de la conférence *[La macrotypographie de la page Web ](http://www.dailymotion.com/video/xfpf08_la-macrotypographie-de-la-page-web-anne-sophie-fradier_tech)*, par Anne-Sophie Fradier (Paris Web, 2010).

CSS3 et Webfonts
----

Depuis les débuts du web, la palette typographique à disposition des designers était limitée à une poignée de fontes (Arial, Verdana, Georgia, Times, Courier...), disponibles sur la grande majorité des systèmes d'exploitation.


Méthode classique: le "fontstack". 

Exemple, pour déclarer une fonte: 

```css
body {
   font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", 
   Helvetica, Arial, "Lucida Grande", sans-serif; 
   font-weight: 300;
}
```

Entre 2008 et 2010, tous les navigateurs ont implémenté le **CSS3 Fonts Module**, permettant de charger des fontes spécifiées par les styles CSS avec la propriété *@font-face*.


@Fontface
===

La syntaxe @font-face, optimisée (c'est la version proposée par FontSquirrel):

```css
@font-face {
    font-family: 'univers';
    src: url('univers.eot');
    src: url('univers.eot?#iefix') format('embedded-opentype'),
         url('univers.woff2') format('woff2'),
         url('univers.woff') format('woff'),
         url('univers.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
}
```

On notera que les fontes sont proposées dans quatre formats: eot, woff2, woff, ttf.

- **eot** : format utilisé par Microsoft (Internet Explorer)
- **ttf**
- **woff** : format compressé
- **woff2** : format compressé

Sources de fontes
===

Trouver de bonnes fontes sous licence libre:

Quelques fontes typographiques intéressantes, en majeure partie sous licence libre et/ou gratuites...

Bagnard, et Bagnard Sans:     
[http://www.love-letters.be/](http://www.love-letters.be/ )
http://maykim.co/Bagnard-Sans   
[https://github.com/sebsan/Bagnard-Sans](https://github.com/sebsan/Bagnard-Sans) 

les fontes du collectif OSP:   
[http://osp.kitchen/foundry/](http://osp.kitchen/foundry/)   
Limousine, Le Patin Helvète, Crickx...

les fontes du studio Uplaod:  
[http://uplaod.fr/allfonts](http://uplaod.fr/allfonts)  
[https://github.com/uplaod](https://github.com/uplaod)

les fontes d'Alfredo Marco Pradil (certaines sous licence libre):  
[https://fontlibrary.org/en/member/hanken](https://fontlibrary.org/en/member/hanken)  
[https://sellfy.com/hankendesignco](https://sellfy.com/hankendesignco)

Use & Modify, sélection de fontes curatée par Raphael Bastide:  
[http://usemodify.com/](http://usemodify.com/)

Gidole, open-source modern DIN:  
[https://github.com/larsenwork/Gidole](https://github.com/larsenwork/Gidole)

Work Sans:  
[https://github.com/weiweihuanghuang/Work-Sans](https://github.com/weiweihuanghuang/Work-Sans)

Fontes non-libres, mais intéressantes:

ECAL Typefaces  
[https://ecal-typefaces.ch/ ](https://ecal-typefaces.ch/ )

Grilli Type:  
[https://www.grillitype.com/](https://www.grillitype.com/)

Deux belles fontes mono-espacées:

**Fira mono**   
[https://github.com/mozilla/Fira](https://github.com/mozilla/Fira)

**Source code pro**   
[https://github.com/adobe-fonts/source-code-pro](https://github.com/adobe-fonts/source-code-pro)

Références
----------

Références majeures sur la typographie web :

- *[Using @font-face](https://css-tricks.com/snippets/css/using-font-face/)*, Chris Coyier, 2009
- *[Professional Web Typography](https://prowebtype.com/)*, par Donny Truong, 2015
- *[Typography Handbook](http://typographyhandbook.com/)*, par Kenneth Wang, 2016 

Articles :

- *[On Web Typography](http://alistapart.com/article/on-web-typography)*, par Jason Santa Maria, 2009
- *[De la vraie typographie pour le Web](http://www.pompage.net/traduction/de-la-vraie-typographie-pour-le-web)*, par Tim Brown, 2009
- *[Web Fonts at the Crossing](http://alistapart.com/article/fonts-at-the-crossing)*, par Richard Fink, 2010
- *[Pour une typographie qui a du sens](http://www.pompage.net/traduction/pour-une-typographie-qui-a-du-sens)*, par Tim Brown, 2011 (en anglais: *More Meaningful Typography*). - Sur le rythme typographique dans le design.
- *[The Value of Multi-Typeface Design](https://blog.prototypr.io/the-value-of-multi-typeface-design-ccd67227b0ee#.a6neeidbw)*, par Bethany Heck, 2016. - Sur l'art de combiner plusieurs fontes. 




