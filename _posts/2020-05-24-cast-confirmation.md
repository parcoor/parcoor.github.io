---
layout: post
title: CAST se confirme: la suite
subtitle: CAST semble se confirmer, qu'envisager pour la suite
tags: [simulation]
---

Après avoir réussi à prévoir l'évolution de la période de confinement, le 11 mai, *CAST* (*Cell Agent State Transitions*), notre modélisation du COVID-19, nous avait permis de modéliser très exactement les décisions prises par le gouvernement Français : déconfinement, masque obligatoire dans les transports, non obligatoire en dehors mais porté à 30%, pas de tracking avant le 1er Juin, pas de tracking obligatoire, bar et restaurants fermés. 

Ce scénario  de déconfinement que nous avons appelé "soft" montrait une hausse immédiate des infections avec un Rt de 1,65 et 15 jours après une nouvelle hausse des hospitalisations puis à la mi-Juillet le retour d’une vague égale à celle que nous avons connu en Mars.

### CAST soft
Ce 24 Mai, 15 jours après, force est de constater que notre modèle était juste et permettait de reproduire fidèlement le comportement des Français mais surtout celui du virus. En effet, nous constatons aujourd’hui  le 5ème jour consécutif de hausse du nombre de nouvelles hospitalisations conformément à notre modèle.

![Évolution 5 derniers jours](/img/last-evolution.png?raw=true "Évolution des hospitalisations du 19 au 24 Mai")

![Scénario actuel](/img/scenario-actuel.png?raw=true "Scénario actuel selon CAST")


Compte tenu de la justesse de nos prévisions pour la deuxième fois (atterrissage confinement, et 15 premiers jours déconfinement), nous nous sentons fondé à de nouveau faire confiance à notre modèle et affirmer qu’en gardant les modalités actuelles du déconfinement nous retrouverons une situation sanitaire équivalente au 14 Mars à la mi-Juillet.

Grâce aux fonctionnalités de CAST permettant de trouver l’optimum des paramètres sous contraintes pour ajuster les politiques sanitaires, il nous est permis de dire que :

Pour obtenir un Rt < 1 sans toutefois avoir à reconfiner, il nous a été possible de modéliser un équilibre qui n’altère pas complètement la vie économique comme pourrait le faire le confinement avec les mesures suivantes :

Déconfinement optimisé :

* port du masque obligatoire en public =  90% de la population
* contact tracing obligatoire :  70% de la population = 100% des porteurs de smartphones = 49% des asymptomatiques détectables seulement
* les lieux publics où les mesures barrières ne peuvent pas être implémentés sont fermés = distances de 2 mètres et gestes barrières y compris les transports
* ouverture des restaurants sous contraintes sanitaires
* fermeture des bars intérieurs, ouverture des terrasses sous contraintes sanitaires
liberté totale de mouvement sur toute la France
* pas de cas importés = frontières fermées au transport aérien et ferroviaire hors activités indispensables ou à caractère économique

![Déconfinement optimisé](/img/deconfinement-optimise.png?raw=true "Évolution des hospitalisations du 19 au 24 Mai")

[Parcoor](https://parcoor.com) l’avait prévu avec *CAST*. Les hospitalisation repartent à la hausse sur 5 jours consécutifs. Voir ci-dessus notre scénario optimal pour la suite du déconfinement.

