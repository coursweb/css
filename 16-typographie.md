---
layout: page
title: Typographie
permalink: typographie.html
---


Les propriétés typographiques du CSS.


## Six propriétés basiques pour les fontes

1. `color` - la couleur du texte
2. `font-family` - la police typographique
3. `font-size` - la taille
4. `font-weight` - la graisse
5. `font-style` - normal ou italique
6. `text-decoration` - p.ex. texte souligné

Exemple

```css
h1 {
  font-family: Helvetica, Arial, sans-serif;
  font-weight: bold;
  font-style: italic;
  text-decoration: underline;
  font-size: 2em;
  color: red;
}
```

## Mettre en page du texte

Les propriétés suivantes vous aideront à mettre un texte en page:


- `text-align` : alignement (gauche, droite, centré, justifié)
- `line-height` : hauteur des lignes, interlignage
- `letter-spacing` : espacement des lettres
- `text-indent` : indentation de la première ligne

Exemple de ces propriétés en action

```css
p {
  line-height: 1.3;
  text-align: left;
  letter-spacing: .1em;
  text-indent: 1em
}
```

## Charger une webfont

Le code pour charger une webfont est documenté [dans le cours typographie web](https://cours-web.ch/typographie/webfonts.html).

Références:
===

- [Initiation à la mise en forme du texte](https://developer.mozilla.org/fr/docs/Learn/CSS/Styling_text/Fundamentals), MDN.
