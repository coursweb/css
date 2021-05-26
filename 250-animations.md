---
layout: page
title: Animations
permalink: animations.html
---

Produire des animations en CSS

Le langage CSS permet de définir des animations. Il existe pour cela deux approches possibles: 

* Les **transitions**, pour des animations consistant à aller d'un état A vers un état B (fondu d'une couleur vers une autre, d'opaque à transparent, d'une taille à l'autre, d'une position à l'autre...).
* Les **animations** permettent de définir des comportements passant pas plusieurs états successifs. Elles peuvent se répéter ou tourner en boucle.

## Transitions

En définissant une transition CSS, on rend le changement d'état progressif au lieu d'être immédiat.

Voici un exemple de transition: on veut qu'au survol d'un lien, le changement de couleur soit appliqué progressivement durant 1/2 seconde.

```css
a {
  transition-property: color;
  transition-duration: 0.5s;
  transition-timing-function: ease-in-out;
  transition-delay: 0s;
}
```

On peut aussi exprimer cela avec la syntaxe compacte ("shorthand syntax"): 

```css
a {
  transition: color 0.5s ease-in-out;
}
```

**Exemple:** <a href="#" class="transition-link">Un lien pour tester</a>

<style>
.transition-link {
  transition: color 0.5s ease-in-out;
}
</style>

## Animations

Voici comment définir une animation avec les keyframe: il s'agit d'une animation qui fait tourner un objet sur lui-même.

```css
@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

On peut ensuite appliquer cette animation à un objet. C'est là qu'on définit la durée et le nombre de répétitions:

```css
.spinner {
  animation: spin 3s linear infinite;
}
```

La propriété "animation" est un raccourci, qui comporte quatre éléments:

- Le nom de l'animation
- Sa durée, en secondes (s) ou millisecondes (ms)
- Son mode d'accélération (timing-function)
- Le nombre de répétitions (iteration-count). Donner un chiffre, ou "infinite" pour une boucle infinie.

On peut aussi écrire ces propriétés séparément:

```css
.spinner {
  animation-name: spin;
  animation-duration: 3s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}
```

On peut s'amuser à augmenter la vitesse de rotation au survol de l'objet. Pour l'accéler, on réduit la durée:

```css
.spinner:hover {
  animation-duration: 1s;
}
```

Vous pouvez voir cet exemple en action sur cette page (il s'agit de la petite icône qui tourne):

[https://eracom-gr461.github.io/jsclocks/](https://eracom-gr461.github.io/jsclocks/)

### Keyframes à plusieurs étapes

Il est possible de définir plusieurs étapes dans une keyframe:

```css
@keyframes pulse {
  0%, 100% {
    background-color: #ddd;
  }
  50% {
    transform: scale(1.5) rotate(90deg);
    background-color: orange;
  }
  100% {
    transform: scale(1) rotate(180deg);
  }
}
```

Voici comment appliquer cette animation à un objet dans notre page:

```css
.object:hover, .runpulse {
  animation: pulse 1s linear infinite;
}
```

Cette animation a le nom "pulse", sa durée est d'une seconde, et elle se répète à l'infini.

Vous pouvez voir l'exemple en action à cette page:
...

## Documentation 

* [Sur le site Mozilla](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Transitions/Utiliser_transitions_CSS) 