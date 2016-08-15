---
layout: page
title: CSS
permalink: /css/
---

![CSS is awesome](/cours-web/cours-css/img/css-is-awesome.jpeg)

Introduction au CSS.
-------

Le langage **CSS** (*Cascading Style Sheets*) est apparu en 1997, afin de proposer une meilleure manière de créer des sites internet, en séparant le contenu (HTML) de la présentation.

Le standard CSS évolue et s'enrichit de nouvelles capactiés, afin de répondre aux besoins des designers web. La spécification **CSS 2** a été publiée en 1998. Une version révisée, CSS 2.1, a été en travail pendant des années, avant d'atteindre le statut de [Recommandation W3C](https://www.w3.org/TR/CSS2/) en 2011. 

La spécification **CSS 3**, qui l'a suivie, a été développée sous la forme de modules indépendants, dont certains sont déjà bien implémentés dans les navigateurs, et utilisés au quotidien (p.ex. Media Queries, Flexbox, Backgrounds and Borders...).

L'année 2010, qui marque une large adoption du standard HTML5, marque une percée importante du CSS3. C'est en 2010 que sort le livre "[CSS3 for Web Designers](https://abookapart.com/products/css3-for-web-designers)", par Dan Cederholm, et que le terme "Responsive Web Design" fait son apparition sous la plume d'Ethan Marcotte.

![CSS Working Group](/cours-web/cours-css/img/CSSWG2010.jpg)    
*Le CSS Working Group du W3C, lors d'une réunion en 2010*

Principes de base
----------

"Fundamental concepts of CSS like cascading, specificity rules, selectors, inheritance, box model and stacking context must be well understood."

Exemple de règle CSS...

- selectors
- inheritance

### Unités CSS

- Les pixels (px)
- Les pourcentages (%)
- em et ex
- Les points et les picas
- rem
- Unités relatives à la surface d’affichage (vh et vw)
- Les pouces (in) et les centimètres (cm)
- Les caractères (ch)
- Grille de texte (gd)
- Nombres bruts

Articles de référence:

- *[Dimensionner ses fontes avec rem](http://www.pompage.net/traduction/dimensionner-ses-fontes-avec-rem)*, par Jonathan Snook, 2011
- *[Quelles mesures CSS, pour quel usage ?](http://www.pompage.net/traduction/css-unites-et-usages)*, par Dudley Storey, 2013

### Cascade CSS et spécificité

Un article très détaillé:
*[Cascade CSS et priorité des sélecteurs](http://openweb.eu.org/articles/cascade_css)*, par Laurent Denis, 2005

Tous les sélecteurs CSS ne sont pas égaux. Certains sélecteurs sont plus "puissants" que d'autres, et parviennent à surcharger des règles CSS plus faibles. Un sélecteur par identifiant – `#titre` – est plus "spécifique", donc plus puissant, qu'un sélecteur par classe – `.titre` – qui est plus puissant qu'un sélecteur par élément – `h1`.

Voici comment la documentation du W3C explique le principe:

![Régles de spécificité dans la documentation CSS du W3C](/cours-web/cours-css/img/selector-specificity-W3C.png)

Quelques exemples:

```css
* {
    color: red;
}
```

Une règle utilisant comme sélecteur l'astérisque s'appliquera à tous les éléments d'une page, et aura la spécificité la plus basse, càd de zéro.

```css
li {
    color: red;
}
```

La même règle utilisant un sélecteur par élément. On aura une spécificité de (a=0 b=0 c=1), donc de 1.

```css
ul li {
    color: red;
}
```

Si on utilise deux sélecteurs de même type, leur puissance s'additionne. Ici, on aura une valeur de (a=0 b=0 c=2), donc 2.

```css
.red {
    color: red;
}
```

On utilise maintenant sélecteur de type "classe". Un monte d'un niveau de puissance (a=0 b=1 c=0), ce qui se traduit par une spécificité de 10.



Specificity:
[https://designshack.net/articles/css/what-the-heck-is-css-specificity/](https://designshack.net/articles/css/what-the-heck-is-css-specificity/)

Calculateur de spécificté: [http://specificity.keegan.st/](http://specificity.keegan.st/)


### Le modèle de boîte

Le *modèle de boîte* (box-model) utilisé par les navigateurs est de type "content-box". Si on donne une largeur à un élément, cela ne concerne pas les marges intérieures et extérieures. Un élément auquel on donnerait une largeur de 500px, et des marges intérieures (padding) de 25px, aurait une largeur effective de 550px.

Il est possible de modifier ce comportement avec la propriété `box-sizing`. Voir le chapitre **[CSS Layout](layout)** pour plus de détails.


### Le border-collapsing

Le comportement "border-collapsing" peut être surprenant: en cas de juxtaposition verticale, les marges verticales de deux éléments qui se suivent ne sont pas additionnées – elles "fusionnent". C'est uniquement la plus grande des deux marges qui est appliquée.

Exemple: une suite de paragraphes ayant chacun une marge verticale (haut / bas) de 10px. Les marges de deux paragraphes ne s'aditionnent pas, l'espace entre deux paragraphes reste 10px (pas 20px).

### Stacking context

Disposition verticale des éléments d'une page web. On contrôle l'ordre vertical des éléments avec la propriété z-index. Plus cette valeur est grande, plus un élément se trouve propulsé vers le "devant" de la scène.

### Les préfixes (vendor prefixes)

Afin de permettre aux développeurs web de tester les futures fonctionalités du CSS, les navigateurs utilisent des préfixes pour rendre utilisables des fonctionalités "en cours d'implémentation".

Les préfixes les plus utilisés sont:  -moz- pour Firefox, -ms- pour IE, -o- pour Opera, et -webkit- pour Safari et Chrome.

Selon l'analyse de Lea Verou (dans son livre *CSS Secrets*), l'utilisation massive des "vendor prefixes" a été un échec ("an epic failure").

C'est pourquoi, pour les nouvelles propriétés en développement (comme le *CSS Grid Layout*), la stratégie adoptée est de les rendre fonctionnels par un réglage dans les préférences du navigateur. Ainsi, les développeurs peuvent les tester, mais ne seront pas tentés de les utiliser sur des sites en production...

Ressources et références
---

Quelques bonnes ressources pour assimiler les bases du CSS, en trois chapitres:

- *[Getting to Know CSS](http://learn.shayhowe.com/html-css/getting-to-know-css/)*
- *[Opening the Box Model](http://learn.shayhowe.com/html-css/opening-the-box-model/)*
- *[Positioning Content](http://learn.shayhowe.com/html-css/positioning-content/)*


