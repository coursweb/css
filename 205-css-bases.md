---
layout: page
title: Bases CSS
permalink: /css/bases/
---


### Unités CSS

Il existe diverses unités de mesure disponibles en CSS. Elles peuvent être classées en trois catégories:

- **Unités absolues:** mm (millimètres), cm (centimètres), in (pouces), pt (point), pc (pica)
- **Unités relatives:** %, em, ex, rem, ch, vh, vw
- **Unités dépendantes de l'interface:** px

Les unités *absolues* correspondent à ce que l'on connaît de la mise en page "papier". Elles sont à éviter sur le web, sauf pour les styles d’impression (p.ex. pour spécifier les marges des pages). Comme l'indiquent les inventeurs du CSS, Håkon Wium Lie et Bert Bos (dans *Cascading Style Sheets: Designing for the Web*): 

- Utilisez les unités *ems* pour créer des feuilles de styles s'adaptant à différentes échelles.
- Utilisez les *ems* pour définir les tailles de fonte.
- Utilisez des unités relatives pour définir la longueur des éléments de mise en page.
- N'utilisez les longueurs absolues uniquement si les caractéristiques physiques du medium de sortie sont connues.

#### Unités relatives:

- **Les pourcentages** (%): Définit une mesure en % par rapport à la taille de l'élément parent. Utile pour créer des mises en page flexibles, et pour définir des tailles de fonte.
- **em**: Unité typographique ancienne, correspondant historiquement à la largeur de la lettre "m". Par défaut, 1em est équivalent à 16px. Voici les équivalences par défaut du em: `1em == 16px == 0.17in == 12pt == 1pc == 4.2mm == 0.42cm`.
- **rem**: Unité relative, qui fonctionne comme le **em**, mais la taille est relative à la taille de fonte à la racine du document (attribuée à l'élément `html`).
- **ex**: Unité verticale, correspondant à la *x-height*, càd. la hauteur de la lettre x. Contrairement au **em**, cette unité varie en fonction de la fonte. 
- **ch**: Unité correspondant à la largeur du charactère "0". 
- **vh** et **vw**: Unités relatives à la surface d’affichage. Ces unités sont relatives à la taille de la fenêtre de navigateur. Cela permet p.ex. de spécifier une taille de fonte qui s'adapte à la taille du navigateur. Un **vh** ou **vw** est équivalent à 1% de la taille de fenêtre. Donc un élément avec `height: 100vh` occupera toute la hauteur de la fenêtre.
- **vmin**: correspond à la plus petite valeur de vh ou vw.

#### Les pixels

- **Les pixels** (px): ils ont été pendant longtemps l'unité la plus utilisée en webdesign, autant pour définir des mises en page que pour les tailles de fontes. On préfère actuellement utiliser des em ou des pourcentages.

Articles de référence:

- *[Dimensionner ses fontes avec rem](http://www.pompage.net/traduction/dimensionner-ses-fontes-avec-rem)*, par Jonathan Snook, 2011
- *[Quelles mesures CSS, pour quel usage ?](http://www.pompage.net/traduction/css-unites-et-usages)*, par Dudley Storey, 2013

### Cascade CSS et spécificité

Un article très détaillé:
*[Cascade CSS et priorité des sélecteurs](http://openweb.eu.org/articles/cascade_css)*, par Laurent Denis, 2005

Tous les sélecteurs CSS ne sont pas égaux. Certains sélecteurs sont plus "puissants" que d'autres, et parviennent à surcharger des règles CSS plus faibles. Un sélecteur par identifiant – `#titre` – est plus "spécifique", donc plus puissant, qu'un sélecteur par classe – `.titre` – qui est plus puissant qu'un sélecteur par élément – `h1`.

Voici comment la documentation du W3C explique le principe:

![Régles de spécificité dans la documentation CSS du W3C](/cours-css/img/specificity/selector-specificity-W3C.png)

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

Si on utilise deux sélecteurs de même type, leur puissance s'additionne. Avec le code qui précède, on aura une valeur de (a=0 b=0 c=2), donc 2.

```css
.red {
    color: red;
}
```

On utilise maintenant sélecteur de type "classe". Un monte d'un niveau de puissance (a=0 b=1 c=0), ce qui se traduit par une spécificité de 10.

```css
header .red {
    color: red;
}
```

Ici le résultat sera (a=0 b=1 c=1), autrement dit: 11.

```css
#sidebar {
    color: red;
}
```

Avec l'utilisation d'un sélecteur ID (#), on monte au troisième niveau de puissance. La valeur de ce sélecteur sera (a=1 b=0 c=0), autrement dit: 100.

Les différences de puissance entre les sélecteurs font que l'ordre de la "cascade CSS" ne s'applique pas forcéement.

Par exemple dans ce code:

```css
#sidebar a { color: blue; }
.header nav > a { color: red }
```

De manière non intuitive, c'est la ligne du haut (couleur bleue) qui s'applique, car sa spécificité est plus puissante que celle du bas (100 vs. 12)

Pour mieux comprendre ce principe, des designers ont créés des explicatifs visuels:

Visualisation basée sur The Shining: http://cdn.w3cplus.com/sites/default/files/blogs/2013/1312/CSS_Specificity.jpg

Visualisation basée sur Star Wars, [Specificity Wars](http://blog4coders.com/wp-content/uploads/2014/07/rsz_specificitywars-05v2-800x637.jpg), par Andy Clarke (créé en 2005, mis à jour en 2018).

![Specificity Wars](/cours-css/img/specificity/css-specificity-wars.png)

Visualisation aquatique, [CSS SpeciFISHity](http://www.standardista.com/css3/css-specificity/), par Estelle Weyl.

Specificity:
[https://designshack.net/articles/css/what-the-heck-is-css-specificity/](https://designshack.net/articles/css/what-the-heck-is-css-specificity/)

Calculateur de spécificité: [http://specificity.keegan.st/](http://specificity.keegan.st/)



![](/cours-css/img/Strip-CSS-respect-650-final.jpg)


Ressources et références
---

Quelques bonnes ressources pour assimiler les bases du CSS, en trois chapitres:

- *[Getting to Know CSS](http://learn.shayhowe.com/html-css/getting-to-know-css/)*
- *[Opening the Box Model](http://learn.shayhowe.com/html-css/opening-the-box-model/)*
- *[Positioning Content](http://learn.shayhowe.com/html-css/positioning-content/)*


