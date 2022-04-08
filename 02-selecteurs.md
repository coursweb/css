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

#### L'importance des sélecteurs

Le choix des sélecteurs appropriés joue un grand rôle, c'est là que se joue la qualité architecturale du code CSS.

Quand on essaie de juger la qualité d'un code CSS, la partie à l'intérieur des crochets, les valeurs et propriétés, c'est la partie "cosmétique". Ça marche, ou pas.

Le choix des sélecteurs, au contraire, est très délicat, et repose sur des hypothèses: 

> The stuff outside the curly braces — the selectors — that’s harder to judge. It needs to be evaluated with lots of “what ifs”: What if this selects something you didn’t intend to? What if the markup changes? What if someone else writes some CSS that negates this? 
> *[Jeremy Keith](https://adactio.com/journal/11541)*


#### Sélecteurs du CSS niveau 1

-----|-----:
`E` | tout élément de type E
`E:link` | tout élément E qui est l'ancre d'un hyperlien
`E:visited` | un hyperlien qui a déjà été visité
`E:hover` | un élément E que l'utilisateur survole
`E:focus` | un élément E faisant l'objet d'une sélection, notamment en utilisant le clavier
`E:active` | un élément E soumis à des actions utilisateur
`E::first‑line` | la première ligne d'un élément E
`E::first‑letter` | la première lettre d'un élément E
`.c` | tout élément ayant la classe "c"
`#myid` | tout élément avec un ID égal à "myid"
`E.warning` | tout élément E ayant la classe "warning"
`E#myid` | tout élément E avec un ID égal à "myid"
`E F` | un élément F qui est contenu dans un élément E

Voici un exemple utilisant "first-letter" pour produire une lettrine:

```css
p::first-letter {
  font-size: 200%;
  float: left;
}
```

#### Sélecteurs du CSS niveau 2

-----|-----:
`*` | tous les éléments du document
`E[foo]` | an E element with a "foo" attribute
`E[foo="bar"]` | an E element whose "foo" attribute value is exactly equal to "bar"
`E[foo~="bar"]` | an E element whose "foo" attribute value is a list of whitespace-separated values, one of which is exactly equal to "bar"
`E[foo|="en"]` | an E element whose "foo" attribute has a hyphen-separated list of values beginning (from the left) with "en"
`E:first‑child` | an E element, first child of its parent
`E:lang(fr)` | an element of type E in language "fr"
`E::before` | generated content before an E element's content
`E::after` | generated content after an E element's content
`E > F` | an F element child of an E element
`E + F` | an F element immediately preceded by an E element

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

#### Sélecteurs du CSS niveau 3

`E[foo^="bar"]` | an E element whose "foo" attribute value begins exactly with the string "bar"
`E[foo$="bar"]` | an E element whose "foo" attribute value ends exactly with the string "bar"
`E[foo*="bar"]` | an E element whose "foo" attribute value contains the substring "bar"
`E:root` | an E element, root of the document
`E:nth‑child(n)` | an E element, the n-th child of its parent
`E:nth‑last‑child(n)` | an E element, the n-th child of its parent, counting from the last one
`E:nth‑of‑type(n)` | an E element, the n-th sibling of its type
`E:nth‑last‑of‑type(n)` | an E element, the n-th sibling of its type, counting from the last one
`E:last‑child` | an E element, last child of its parent
`E:first‑of‑type` | an E element, first sibling of its type
`E:last‑of‑type` | an E element, last sibling of its type
`E:only‑child` | an E element, only child of its parent
`E:only‑of‑type` | an E element, only sibling of its type
`E:empty` | an E element that has no children (including text nodes)
`E:target` | an E element being the target of the referring URI
`E:enabled` | a user interface element E that is enabled
`E:disabled` | a user interface element E that is disabled
`E:checked` | a user interface element E that is checked (for instance a radio-button or checkbox)
`E:not(s)` | an E element that does not match simple selector s
`E ~ F` | an F element preceded by an E element

Un exemple réel:

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

