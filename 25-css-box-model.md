---
layout: page
title: Box Model
permalink: box-model.html
---

Le modèle de boîte
------------------

Le modèle de mise en page du HTML / CSS repose sur un principe de "boîtes" (en anglais: box-model). Ces boîtes sont définies géométriquement par les paramètres suivants:

- **Largeur** (width)
- **Hauteur** (heigth)
- **Bordure** (border)
- **Marge intérieure** (padding)
- **Marge extérieure** (margin)

On peut définir les quatre côtés séparément: 

```css
h1 {
  margin: 0 16px 30px 16px;
       /* haut, droite, bas, gauche */
}
```

Les valeurs vont dans le sens des aiguilles d'une montre, en commençant par le haut (puis: droite, bas, gauche).

Si on indique seulement deux valeurs, la première désigne "haut et bas", la deuxième "droite et gauche".

```css
h1 {
  margin: 0px 16px;
       /* haut/bas, droite/gauche */
}
```
Si on indique une seule valeur, elle s'applique sur les quatre côtés de l'objet.

```css
h1 {
  margin: 16px;
}
```

### Le border-collapsing

Le comportement "border-collapsing" peut être surprenant: en cas de juxtaposition verticale, les **marges verticales** de deux éléments qui se suivent ne sont pas additionnées – elles "fusionnent". C'est uniquement *la plus grande* des deux marges qui est appliquée.

Exemple: une suite de paragraphes ayant chacun une marge verticale (haut / bas) de 16px. Les marges séparant deux paragraphes ne s'aditionnent pas, l'espace entre deux paragraphes reste 16px (pas 32px).

Cela est uniquement le cas dans l'axe vertical. Sur l'axe horizontal (par exemple des éléments juxtaposés dans une Flexbox), les marges des éléments s'additionnent.

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="vYMwEKP" data-user="eracom" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/eracom/pen/vYMwEKP">
  Collapsing margins</a> by Manuel Schmalstieg (<a href="https://codepen.io/eracom">@eracom</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


La propriété box-sizing: border-box
-----------------------------------

Le *modèle de boîte* (box-model) utilisé par les navigateurs est de type "content-box". Si on donne une largeur à un élément, cela ne concerne pas les marges intérieures et extérieures. Un élément auquel on donnerait une largeur de 500px, et des marges intérieures (padding) de 25px, aurait une largeur effective de 550px.

![Comparaison de deux logiques Box-Model](img/box-model-comparison.png)

La propriété **box-sizing**, ajoutée en CSS3, permet de définir la manière dont la largeur d'un élément est calculée. Les valeurs possibles sont `content-box` et `border-box`.

La valeur par défaut est `content-box`, elle signifie que la **largeur** est celle du **contenu** uniquement. La *marge intérieure* (*padding*), la *bordure* (*border*) et la *marge extérieure* (*margin*) vont s'ajouter.

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

<p class="codepen" data-height="520" data-default-tab="result" data-slug-hash="wvzeWZB" data-editable="true" data-user="eracom" style="height: 520px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/eracom/pen/wvzeWZB">
  Box Model</a> by Manuel Schmalstieg (<a href="https://codepen.io/eracom">@eracom</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

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
[Contrôler le modèle de boîte](https://la-cascade.io/controler-le-modele-de-boite/), par [Ire Aderinokun](https://bitsofco.de/controlling-the-box-model/), trad. Pierre Choffé.
