---
layout: page
title: Spécificité
permalink: /css/specificite/
---

# Cascade CSS et spécificité

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

Un autre calculateur sous forme de graphique: https://jonassebastianohlsson.com/specificity-graph/

## Ressources

Un article très détaillé:
*[Cascade CSS et priorité des sélecteurs](http://openweb.eu.org/articles/cascade_css)*, par Laurent Denis, 2005