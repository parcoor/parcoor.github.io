---
layout: post
title: Données et Information
subtitle: Pour alimenter un bon modèle, il ne faut pas forcément beaucoup de données, mais suffisamment d'information...
tags: [data]
---

Une idée reçue sur le machine learning est qu'il faut beaucoup de données pour entraîner un modèle. Or il ne faut pas *beaucoup de données* mais *suffisamment d'information*. L'[information](https://fr.wikipedia.org/wiki/Th%C3%A9orie_de_l%27information) est contenue dans les données, mais en est distincte.
Combien d'information faut-il pour entraîner un modèle? Cela dépend de la complexité du modèle. Pour une simple [régression linéaire](https://fr.wikipedia.org/wiki/R%C3%A9gression_lin%C3%A9aire), quelques dizaines d'entrées peuvent suffire. Pour un réseau de neurones avec des millions voire des [milliards de paramètres](https://www.datanami.com/2019/11/13/deep-learning-has-hit-a-wall-intels-rao-says/) à calibrer, il faut souvent de l'ordre de plusieurs dizaines de milliers voire millions d'entrées.

## Distinction *données* / *information* (a.k.a. *signal*)
Mais revenons à cette distinction données / information. Pourquoi est-elle importante? Un modèle va essayer d'extraire l'information contenue dans les données relatives à la tâche qu'il doit accomplir. Cette tâche peut être la prévision d'une valeur, la classification d'un objet etc.

Plusieurs facteurs peuvent faire que l'information (appelée souvent aussi *signal*) contenue dans les données n'est pas suffisante:

* **Trop de bruit par rapport au signal.** Par exemple si les données proviennent d'un capteur fonctionnant mal. Si le but du modèle est de détecter une anomalie sur la machine monitorée par le capteur et que le capteur envoie régulièrement des valeurs fausses ou aucune valeur, il faudra une phase de pré-traitement pour débruiter et compléter les données envoyées par le capteurs. 

Parfois, le ratio signal/bruit est intrinsèquement faible, comme dans le cas de séries financières. Dans ce cas, il faudra un grand volume de données pour extraire suffisamment de signal pour un modèle, de même qu'il faut extraire des tonnes de terre pour extraire quelques grammes d'or

![extraction terre](/img/extraction-terre.jpeg?raw=true "extraction terre")

*Il faut 100 tonnes de terre pour extraire une once (28g) d'or...*

Enfin il peut arriver que les données en entrées n'aient pas ou peu de rapport avec la tâche à accomplir par le modèle, sans que ce soit évident à première vue. Par exemple, inférer les ventes d'un produit à partir de celle d'un autre produit proche alors qu'ils sont perçus très différemment par les consommateurs. Dans ce cas là, les données en entrées seront surtout du bruit pour le modèle, dont il sera difficile d'extraire un signal pertinent.

* **données tronquées.** Imaginons que le but du modèle soit de prévoir le CA d'un restaurant afin de prévoir le personnel nécessaire. Si le modèle ne dispose que de données durant l'année scolaire, il n'aura pas assez d'information pour prévoir la fréquentation durant les grandes vacances. Il en aura, car il aura appris à inférer l'effet de la météo, du jour de la semaine etc., mais ses prévisions seront moins bonnes que pendant l'année scolaire. 

Autre exemple, le problème de la "cible mouvante" (*moving target*). Imaginons un SEO qui essaye de prévoir le [CTR](https://fr.wikipedia.org/wiki/Taux_de_clics) (click through rate) d'un article en fonction de son titre etc. Le modèle marche bien mais ses performances se détériorent au cours du temps car le public de son site change, devient par exemple plus jeune, s'étend à d'autres CSP etc. Le signal sur lequel a été entraîné le modèle est tronqué, il ne correspond qu'au public initial, qui n'est qu'une partie du public actuel

![données tronquées](/img/truncated-data.png?raw=true "données tronquées")
*Des données tronquées font dévier les résultats du modèle*
## Solutions
Chez [Parcoor](https://parcoor.com/), nous avons des modules permettant d'automatiser en grande partie les opérations les plus courantes de la phase de pré-traitement. De plus, au lieu d'utiliser un modèle complexe, nous combinons plusieurs modèles plus simples. Les avantages sont que:
1. Besoin de moins de données: chaque modèle est suffisamment simple pour se contenter de peu de données
2. Extraction augmentée du signal dans les données: certains modèles extraient le partie linéaire du signal (arbres etc.) d'autres la partie non-linéaire etc.
3. Prédictions plus robustes face à des patterns (situations) plus rares ou extrêmes que dans les donnée d'entraînement

Ainsi nous pouvons déployer plus rapidement des modèles plus efficaces, fidèles à notre mission de rentre le machine learning accessible à tous.
