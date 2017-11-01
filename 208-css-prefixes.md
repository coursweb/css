---
layout: page
title: Préfixes
permalink: /css/prefixes/
---


## Les préfixes CSS

Durant le développement des modules du CSS 3, au début des années 2000, les navigateurs (Chrome, Safari, Firefox...) ont commencé à introduire les nouveaux modules sous forme expérimentale, en leur appliquant un "préfixe" différent selon le navigateur. 

Cela afin de permettre aux développeurs web de tester les futures fonctionalités du CSS "en cours d'implémentation".

On les appelle en anglais "vendor prefixes" (les "vendors" étant les producteurs de navigateurs: Apple, Google, Microsoft, Mozilla, Opera).

Les préfixes les plus utilisés sont:  

* `-moz-` pour Firefox
* `-ms-` pour IE
* `-o-` pour Opera
* `-webkit-` pour Safari et Chrome

### Utilitaires

Quelques outils pour mieux gérer les préfixes, et écrire un CSS plus lisible et plus simple:

* http://leaverou.github.io/prefixfree/ - *Prefix-free*, un utilitaire JavaScript par Lea Verou
* *Autoprefixer* - un "post-processeur" qui ajoute les préfixes manquants. Lire [cet article](https://css-tricks.com/autoprefixer/).

Ces deux outils ont le même objectif: vous permettre d'écrire du code CSS simple et propre, **sans préfixes**. Leur mode de fonctionnement est toutefois très différent:

**Prefix-Free** est un petit utilitaire JavaScript. Il s'agit d'un fichier JavaScript à charger, qui va analyser votre code CSS, et ajouter les préfixes lorsque c'est nécessaire. À noter que cela aura un impact sur le temps de chargement du site, car le calcul se fait dans le navigateur, après le chargement de la page. Il n'est donc pas recommandé de l'utiliser dans des projets en production. Mais pour faciliter votre apprentissage du CSS et produire des sites-maquette, c'est un outil pratique.

**Autoprefixer** est un utilitaire qui s'exécute sur votre ordinateur. Il va analyser votre code CSS, et produire une version complétée avec les préfixes nécessaires. Il n'y a ainsi pas d'impact sur le temps de chargement du site. C'est un outil approprié pour des sites en production.

### Abandon des préfixes

Selon l'analyse de Lea Verou (dans son livre *CSS Secrets*), l'utilisation massive des "vendor prefixes" a été un échec ("an epic failure").

C'est pourquoi, pour les nouvelles propriétés en développement (comme le *CSS Grid Layout*), la stratégie adoptée est de les rendre fonctionnels par un réglage dans les préférences du navigateur. Ainsi, les développeurs peuvent les tester, mais ne seront pas tentés de les utiliser sur des sites en production.