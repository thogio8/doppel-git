# doppel

*Le doppelgänger de Git.* Une réimplémentation from scratch que le vrai Git
ne sait pas distinguer de lui-même : doppel lit les dépôts créés par Git,
et Git lit ceux de doppel.

## Pourquoi

J'utilise Git tous les jours. Je veux comprendre toute la machinerie, pas juste les commandes.
Le seul moyen honnête de le prouver : reconstruire, et laisser le vrai Git juger.

## La méthode

Le code est écrit avec Claude Code. Je pilote et je tranche.
Avant chaque décision structurante, je fais ma propre prédiction, puis je la compare
à la proposition de l'IA. Chaque décision est documentée dans [`docs/decisions/`](docs/decisions/),
avec les options écartées et qui avait raison.

Le [tableau de bord](docs/scoreboard.md) compte les convergences, les divergences,
et les fois où j'ai corrigé l'IA.

## Avancement

Voir la [roadmap](docs/roadmap.md).

## Compatibilité

Chaque fonctionnalité est testée contre le vrai Git : même opération des deux côtés,
résultats comparés, et Git doit accepter nos dépôts sans erreur.

## Installation

À venir. Le binaire s'appellera `doppel` (`doppel init`, `doppel commit`…).

## Licence

MIT
