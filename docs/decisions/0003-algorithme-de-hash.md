# 0003 — Algorithme de hash

**Étape de la roadmap :** 1
**Date :** 2026-10-30

## Contexte
L'identifiant d'un objet doit être exactement celui que calcule le vrai Git.
Il fallait choisir l'algorithme.

## Options envisagées
- Option A : SHA-1, le format par défaut des dépôts Git.
- Option B : SHA-256, plus sûr, supporté par Git via un format de dépôt distinct (`objectFormat = sha256`).

## Ma prédiction
Git utilise SHA-1 bien qu'il soit déprécié. Si j'avais le choix, je prendrais SHA-256.

## Proposition de Claude
SHA-1 maintenant, parce que c'est ce qu'utilisent les dépôts par défaut, donc ce qu'exige notre critère de compatibilité.
L'algorithme reste isolé derrière un type dédié, pour pouvoir ajouter SHA-256 plus tard.

## Décision finale et pourquoi
SHA-1. Un dépôt SHA-256 n'est pas lisible par les outils qui attendent du SHA-1, et inversement.
Le défaut de Git 2.43 est SHA-1, donc c'est le seul choix compatible avec la plupart des dépôts existants.

## Ce qu'on a écarté et pourquoi
SHA-256 seul : on ne pourrait lire aucun dépôt Git créé avec les réglages par défaut.

## Verdict
Convergence.
