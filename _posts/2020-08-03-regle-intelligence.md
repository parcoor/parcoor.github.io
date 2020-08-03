---
layout: post
title: Règle, flexibilité et intelligence (artificielle...)
subtitle: Gagner en intelligence par le volume ou la hauteur, une méta-perspective
tags: [ai, ethics]
---

En re-lisant [Gödel-Escher-Bach](https://en.wikipedia.org/wiki/G%C3%B6del,_Escher,_Bach) (que je ne saurais trop recommander), l'auteur [Douglas Hofstadter](https://en.wikipedia.org/wiki/Douglas_Hofstadter) dans sa longue introduction met trois idées en perspective:
* Les paradoxes dus à l'auto-référencement, du type [paradoxe d'Épiménide](https://fr.wikipedia.org/wiki/Paradoxe_du_menteur): "Je suis un menteur"
* L'incomplétude des systèmes formels (premier [théorème d'incomplétude](https://fr.wikipedia.org/wiki/Th%C3%A9or%C3%A8mes_d%27incompl%C3%A9tude_de_G%C3%B6del) de Gödel)
* Le paradoxe à première vu de l'intelligence artificielle: comment des ordinateurs, c'est à dire des machines certes très puissantes, mais complètement obtus et bornés dans leur application des règles, pourraient faire preuve d'intelligence?

Pour parler d'intelligence, il faut d'abord s'entendre sur ce que c'est. Tracer une limite formelle entre ce qui relève de l'intelligence ou pas est une gageure, mais on peut toutefois en décrire quelques caractéristiques:
* répondre de façon flexible à des situations
* faire sens de messages contradictoires ou ambigues (Et VlAn)
* trouver des similarités entre des situations malgré leurs différences
* etc.

Rappelons que ce livre a été publié en 1979, époque où l'intelligence artificielle était très très loin d'être ce qu'elle est maintenant.

D'accord, mais où veut-on en venir avec ça?

## Insuffisance des règles
Ce que nous apprend le premier théorème de Gödel, c'est que tout système formel contient des affirmations vraies mais non-prouvables au sein de ce système. Aucun système ne se contient en lui-même. Pour chaque socle de règles (système), il faut un méta-système, un système sur ce système. Ce méta-système nécessite lui-même un méta-méta-système etc.

Pire encore, un système qui se contiendrait lui-même serait inconsistent, contiendrait des paradoxes du type de celui d'Épiménide. Ce combat est donc perdu d'avance.

![Gödel Einstein](/img/goedel-einstein.png?raw=true "Gödel Einstein")

*Kurt Gödel en ballade avec Einstein...*

Pour la petite histoire, le théorème d'incomplétude de Gödel était une réponse au [programme de Hilbert](https://fr.wikipedia.org/wiki/Programme_de_Hilbert), visant à prouver la consistence des [Principia Mathematica](https://en.wikipedia.org/wiki/Principia_Mathematica) de Russell et Whitehead, dont le but était de donner des fondations solides aux mathématiques qui avaient été durement ébranlés après la découverte de géométries non-euclidiennes (comme prétendre que les mathématiques représentent la réalité si elles représentent plusieurs réalités??) et d'autres crises au 19e siècle. Mais le projet de mettre en place des principes complets, consistents et immuables s'est confronté à son impossibilité...

Mais qu'est-ce que ça a à voir avec l'intelligence, humaine et artificielle?

## Intelligence et méta-règles
Quand on y pense, le machine learning réussit la prouesse de rendre une machine aussi obtue et bornée qu'un ordinateur flexible, capable de découvrir des coups au jeu d'échecs ou de go qui échappent aux humains, d'être créatif etc. Pour cela, on entraîne des modèles. Pour schématiser, on fait passer des données dans le modèle, et en fonction du résultat le modèle se modifie lui-même (en deep-learning, cette opération s'appelle [rétropropagation](https://fr.wikipedia.org/wiki/R%C3%A9tropropagation_du_gradient)).. Au final, ça consite à donner à l'ordinateur des règles pour modifier ses propres règles. Tout comme un pays peut avoir une assemblée pour modifier les propres règles du pays. Tout comme un humain réagit différemment selon la situation qui se présente. Et c'est comme ça qu'émerge l'ntelligence, qu'elle soit individuelle, collective ou artificielle: en ayant des règles pour modifier ses règles.

## Augmenter l'intelligence: prendre du volume ou de la hauteur
Pour s'adapter et résoudre des situations et des problèmes de plus en plus complexes, il faut augmenter l'intelligence qui les traite. Pour cela, deux solutions possibles:
1. Augmenter les règles applicables par cette intelligence: augmenter son volume
2. Lui donner des règles permettant d'adapter au mieux ses propres règles: lui faire prendre de la hauteur.

### Intelligence artificielle
Prenons un exemple en intelligence artificielle. [OpenAI](https://openai.com/) a sorti récemment [GPT-3](https://github.com/openai/gpt-3), un modèle de deep learning de génération de textes aux performances proprement [époustouflantes](https://www.gwern.net/GPT-3), capable de tenir des conversations très réalistes avec des humains, d'improviser de la poésie, même d'écrire des programmes etc. Ce modèle restera sans doute dans l'histoire comme une des étapes majeures de l'intelligence artificielle, loin de moi l'idée de sous-estimer cette prouesse. Toutefois, cette prouesse a eu lieu grâce à un réseau de neurone mastodontesque contenant pas moins de 175 milliards de cellules qui a aspiré une grande partie d'internet pour s'entraîner.

![volume GPT-3](/img/gpt3-volume.png?raw=true "volume GPT-3")

*GPT-3 bat tous les records, aussi en terme de volume*

À l'heure actuelle, les réseaux de neurones sont plutôt statiques. Une fois qu'on a définit leur architecture, leurs règles d'adaptation, on les entraîne avec un volume suffisant de données et la "magie" apparaît. Mais au lieu d'augmenter en volume ces réseaux de neurones, pourquoi ne pas imaginer leur donner des méta-règles, c'est à dire des règles à leurs règles? Imaginer que durant son entraînement, le réseau de neurone modifie par lui-même non seulement ses paramètres, mais aussi ses hyper-paramètres, comme sa propre architecture, ses règles de mise à jour etc.? Serait-il possible alors d'obtenir des performances semblables mais avec un modèle bien moins volumineux?

### Société
Au niveau collectif également, on entend souvent des voix s'élever contre les réglementations de plus en plus nombreuses, chaque nouveau problème appelant une nouvelle règle qui s'accumulent. Pourquoi ne pas se donner des méta-règles, c'est à dire des règles sur la façon de se donner des règles pour être plus flexibles avec moins de réglementation? Certes cela existe déjà, mais de façon peut-être trop clairesemée.

Récemment aussi sur l'hydroxichloroquine, sans vouloir rentrer dans le débat et certaines de ses intrications plus ou moins reluisantes, mais sur le fond, les deux perspectives qui s'affrontaient étaient: d'un côté ceux qui voulaient appliquer la règle (test en double-aveugle randomisé...), de l'autre ceux qui voulaient une méta-règle sur cette règle, c'est à dire l'utilisation de cette règle ou d'une autre selon les circonstances, très exceptionnelles en l'occurrence.

![Assemblée nationale](/img/assemblee-nationale.jpg?raw=true "Assemblée nationale")

*Une société a aussi des règles pour se donner des règles, comme ici l'Assemblée nationale. C'est très certainement nécessaire, mais est-ce suffisant?*


### Individuellement
Individuellement aussi, sans vouloir épiloguer sur ce sujet, on se rend compte qu'outre des règles et des connaissances de base, on peut difficilement faire l'impasse sur des méta-règles, comme apprendre à apprendre, apprendre à s'adapter etc. Le volume de connaissance qu'il faudrait assimiler pour faire face à toute situation possible serait beaucoup trop vaste, donc l'accent est de plus en plus mis sur l'assimilation de méta-règles pour être capable d'acquérir ou de générer ses connaissances de manière ad-hoc.

## Conclusion
Que ce soit au niveau individuel, collectif ou artificiel, il semblerait que la course à l'intelligence se fasse plus au profit du volume, au détriment de la hauteur. Il n'est jamais mal d'augmenter le volume, bien au contraire. C'est nécessaire, mais insuffisant. Faire prendre de la hauteur à un système, c'est-à-dire avoir un méta-système gouvernant ce système (puis un méta-méta-système etc.) - *si c'est bien fait* - permet de gagner de la flexibilité, de l'agilité, de la réactivité, c'est-à-dire de l'intelligence, quand le volume de ce système atteint ses limites. Ceci est valable aussi bien pour les intelligences individuelles, collectives qu'artificielles.
