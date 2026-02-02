---
layout: page
title: Les sélecteurs CSS
permalink: selectors.html
---


Le sélecteur définit à quel élément de la page un style CSS sera appliqué. Par exemple: 

```css
H1 { color: Tomato }
```

La couleur <span style="color: Tomato">Tomato</span> sera appliquée à tous les éléments H1 de la page.

Il est possible de grouper plusieurs sélecteurs, en les séparant par des virgules. Exemple:

```css
H1 { color: Tomato }
H2 { color: Tomato }
H3 { color: Tomato }
```

Ces trois règles peuvent être groupées comme ceci:

```css
H1, H2, H3 { color: Tomato }
```

## L'importance des sélecteurs

Le choix des sélecteurs appropriés joue un grand rôle, c'est là que se joue la qualité architecturale du code CSS.

Quand on essaie de juger la qualité d'un code CSS, la partie à l'intérieur des crochets, les valeurs et propriétés, c'est la partie "cosmétique". Ça marche, ou pas.

Le choix des sélecteurs, au contraire, est très délicat, et repose sur des hypothèses: 

> The stuff outside the curly braces — the selectors — that’s harder to judge. It needs to be evaluated with lots of “what ifs”: What if this selects something you didn’t intend to? What if the markup changes? What if someone else writes some CSS that negates this? 
> *[Jeremy Keith](https://adactio.com/journal/11541)*


## Sélecteurs du CSS niveau 1

Introduits dès le début du CSS en 1996, ces sélecteurs sont décrits ici: [https://www.w3.org/TR/CSS1/](https://www.w3.org/TR/CSS1/)

-----|-----|-------:
`E` | tout élément de type E | [lien codepen](https://codepen.io/andreajdsdnjkndk/pen/yyJPQOp)
`#myid` | tout élément avec un ID égal à "myid"
`E#myid` | tout élément E avec un ID égal à "myid"
`.c` | tout élément ayant la classe "c"
`E.warning` | tout élément E ayant la classe "warning"
`E F` | un élément F qui est contenu dans un élément E

##### Les pseudo-classes pour les liens

Ces pseudo-classes permettent de distinguer les liens déjà visités.

-----|-----:
`E:link` | tout élément E qui est l'ancre d'un hyperlien. permet de définir l’aspect d’un lien sur lequel on n’a pas encore cliqué.
`E:visited` | un hyperlien qui a déjà été visité.
`E:focus` | un élément E faisant l'objet d'une sélection, notamment en utilisant le clavier.
`E:hover` | un élément E que l'utilisateur survole.
`E:active` | un élément E soumis à des actions utilisateur.

Exemple:

```css
input:focus {
  border-color: red;
}
```

##### Les pseudo-elements typographiques

-----|-----:
`E::first‑line` | la première ligne d'un élément E.
`E::first‑letter` | la première lettre d'un élément E.

Voici un exemple utilisant "first-letter" pour produire une lettrine ([essayer sur Codepen](https://codepen.io/eracom/pen/KKxLegW)):

```css
p::first-letter {
  font-size: 200%;
  float: left;
}
```

## Sélecteurs du CSS niveau 2

Les sélecteurs du CSS 2, introduits en 1998, sont décrits ici: [https://www.w3.org/TR/CSS2/](https://www.w3.org/TR/CSS2/)

-----|-----|-------:
`*` | tous les éléments du document. Aussi appelé "the universal selector". | [lien codepen](https://codepen.io/Schems-Mahfoudh/pen/azZVRdy)
`E:first‑child` | un élément E qui est le premier enfant de son parent. 
`E:lang(fr)` | un élément E en langue "fr".
`E::before` | du contenu généré avant le contenu de l'élément E.
`E::after` | du contenu généré après le contenu de l'élément E.


##### Child selectors

-----|-----:
`E > F` | un élément F enfant d'un élément E.

##### Les sélecteurs d'attribut

-----|-----:
`E[foo]` | un élément E avec un attribut "foo".
`E[foo="bar"]` | un élément E dont l'attribut "foo" est exactement égal à "bar".
`E[foo~="bar"]` | un élément E dont l'attribut "foo" est une liste de valeurs séparées par des espaces, dont l'une est exactement égale à "bar".
`E[foo|="en"]` | un élément E dont l'attribut "foo" est une liste de valeurs séparées par des traits d'union, et commence depuis la gauche par "en".

Un exemple réel:

```css
input[type="checkbox"],
input[type="radio"] {
	padding: 0;
}
```

Cette règle annule le "padding" pour les éléments interactifs de type "case à cocher" <input type="checkbox"> ou "bouton radio" <input type="radio">.

Voici un autre exemple réel, plutôt subtil:

```css
a[href]::after {
	content: " (" attr(href) ")";
}
```

Cette règle est contenue dans les feuilles de style "print" (dédiées à l'impression) du framework HTML5Boilerplate. Son effet est de détecter tous les liens (élément `a` ayant un attribut `href`), et va afficher à la suite du lien son URL. Ainsi, si on imprime une page du site, chaque lien sera suivi de l'URL.

## Sélecteurs du CSS niveau 3

Les sélecteurs CSS de niveau 3 sont ajoutés dans la spécification CSS3, qui était en travail depuis 1999, et est devenue une recommandation depuis 2011. Documentation: [https://www.w3.org/TR/selectors-3/](https://www.w3.org/TR/selectors-3/)

### Pseudo-classes

#### Pseudo-classes de structure

-----|-----:
`E:root` | un élément E qui constitue la racine du document. Il s'agit toujours de l'élément `html`.
`E:empty` | un élément E qui n'a pas d'enfants (donc sans contenu).
`E:only‑child` | le seul enfant de son parent.
`E:only‑of‑type` | le seul de son type.

#### Pseudo-classes de position

-----|-----:
`E:first‑child` | un élément E qui est le premier enfant de son parent.
`E:last‑child` | le dernier enfant de son parent.
`E:first‑of‑type` | le premier de son type.
`E:last‑of‑type` | le dernier de son type.
`E:nth‑child(n)` | le n-ième enfant de son parent (n étant un nombre).
`E:nth‑last‑child(n)` | le n-ième enfant de son parent, en comptant depuis la fin.
`E:nth‑of‑type(n)` | le n-ième jumeau de son type.
`E:nth‑last‑of‑type(n)` | le n-ième jumeau de son type, en comptant depuis la fin.

### Substring matching attribute selectors

-----|-----:
`E[foo^="bar"]` | an E element whose "foo" attribute value begins exactly with the string "bar".
`E[foo$="bar"]` | an E element whose "foo" attribute value ends exactly with the string "bar".
`E[foo*="bar"]` | an E element whose "foo" attribute value contains the substring "bar".
`E:target` | un élément qui est la cible d'une URL.

### UI element states pseudo-classes

-----|-----:
`E:enabled` | un élément d'interface E qui est activé.
`E:disabled` | un élément d'interface E qui est désactivé.
`E:checked` | un élément d'interface E qui est coché (par exemple un `radio-button` ou `checkbox`).

### Les pseudo-éléments

Depuis la version CSS3, la notation des pseudo-éléments comporte deux double-points (afin de les distinguer des pseudo-classes):

-----|-----:
`E::first‑line` | la première ligne d'un élément E
`E::first‑letter` | la première lettre d'un élément E
`E::before` | du contenu généré avant le contenu de l'élément E.
`E::after` | du contenu généré après le contenu de l'élément E.

----

[Un exercice Codepen](https://codepen.io/eracom/pen/KKxLegW?editors=1100): produisez une lettrine en trouvant le bon sélecteur.

----

Un exemple de contenu généré avec `:before` :

```css
a[href*="tumblr.com"]:before {
	content: "\2b8a";
}
```

Cette règle CSS a pour effet d'ajouter une icône (l'élément `\2b8a` qui correspond à un glyphe dans la fonte d'icônes [Icomoon](https://icomoon.io/)) devant chaque lien pointant vers [Tumblr](https://www.tumblr.com).

<style>

@font-face {
  font-family: "icomoon";
  src: url('/fonts/icomoon.woff') format('woff');
}

a[href*="tumblr.com"]:before {
	content: "\2b8a";
	font-family: "icomoon";
	padding-right: 0.3em;
    vertical-align: -0.1em;
}
</style>


### Sibling combinators

Les "sibling combinators" - en français, opérateurs d'adjacence - permettent de cibler en élément en fonction de sa position.

#### Next-sibling combinator

-----|-----:
`E + F` | un élément F *directement précédé* d'un élément E.

En français, on le nomme "opérateur d'adjacence directe". Il assure que l'élément ciblé (F) est directement adjacent à un élément E qui le précède.

#### Subsequent-sibling combinator

-----|-----:
`E ~ F` | un élément F *précédé* par un élément E.

En français, "opérateur d'adjacence générale".

Ce sélecteur est parfois utilisé pour faire réagir un élément au clic sans recourir au Javascript. En effet, en utilisant une checkbox, on peut intercepter le clic:

```css
#menuToggle input:checked ~ ul
{
  /* code qui fait apparaître le menu, avec une transition */
}
```

Un autre exemple similaire:

```css
.menu-btn:checked ~ .menu {
    max-height: 240px;
  }
```

Trois exemples de cette technique:

- [Responsive hamburger menu - pure CSS #1](https://codepen.io/mutedblues/pen/MmPNPG) by mutedblues
- [Pure CSS Hamburger Menu](https://janessagarrow.com/blog/pure-css-hamburger-menu/)
- [Pure CSS Hamburger fold-out menu](https://codepen.io/erikterwan/pen/EVzeRP?editors=1100) by Erik Terwan


##### The negation pseudo-class

`E:not(s)` | an E element that does not match simple selector s - voir [un codepen](https://codepen.io/mbuchmannn/pen/ogLoaoP)


## Sélecteurs du CSS niveau 4

Les sélecteurs de niveau 4 sont en élaboration depuis 2011. En mai 2022, ils se trouvent encore en version "working draft". 
La documentation se trouve sous [https://www.w3.org/TR/selectors-4/](https://www.w3.org/TR/selectors-4/). 
Quelques nouveautés:

- La pseudo-classe `:is()` - voir [le support actuel](https://caniuse.com/css-matches-pseudo) - voir [un codepen](https://codepen.io/mbuchmannn/pen/ogLoaoP)
- La pseudo-classe `:where()` - voir [le support actuel](https://caniuse.com/mdn-css_selectors_where)
- La pseudo-classe `:has()` - voir [le support actuel](https://caniuse.com/css-has)
