# 0001 — Langage d'implémentation

**Étape de la roadmap :** 0 (préalable)
**Date :** 2026-10-30

## Contexte
Avant l'étape 1, il faut choisir le langage de doppel. Il doit manipuler des octets bruts,
de la compression et du hachage, produire un binaire `doppel`, et permettre des tests
qui exécutent le vrai Git et notre outil côte à côte.

## Options envisagées
- Option A : C, bas niveau total, chaque octet visible, mais tout est à faire à la main (buffers, tables de hachage, erreurs, mémoire).
- Option B : Rust, tout aussi bas niveau (pas de GC, binaire natif), mais avec la sûreté mémoire et `cargo test` intégré.

## Ma prédiction
C : un langage bas niveau, pour apprendre en profondeur (l'assembleur serait trop bas).

## Proposition de Claude
Rust : on garde le contrôle bas niveau sans dépenser l'effort dans la tuyauterie
mémoire, et le harnais de tests est fourni de base.
Claude justifiait aussi son choix en disant que je connaissais déjà bien le C via EPITECH.
C'était faux (je ne suis pas dans le programme PGE) et je l'ai corrigé.

## Décision finale et pourquoi
Rust (edition 2024, sans dépendance pour l'instant). Le compromis contrôle / productivité
colle mieux à l'objectif « avancer vite ET comprendre », et le langage m'intéresse.

## Ce qu'on a écarté et pourquoi
C : trop d'effort passerait dans la gestion mémoire et les structures de base, au détriment de Git lui-même.

## Verdict
Divergence, et la proposition de Claude a été retenue. Un de ses arguments (mon expérience en C) était faux.
