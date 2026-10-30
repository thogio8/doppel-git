# 0004 — SHA-1 écrit à la main plutôt qu'une crate

**Étape de la roadmap :** 1
**Date :** 2026-10-30

## Contexte
SHA-1 ne fait pas partie du format de Git, donc une crate est autorisée.
Mais toute dépendance est une décision structurante.

## Options envisagées
- Option A : utiliser une crate (`sha1`), ce qui fait zéro code à écrire.
- Option B : l'implémenter nous-mêmes en suivant FIPS 180-4 (~100 lignes).

## Ma prédiction
On l'écrit nous-mêmes : une dépendance retire de la complexité mais ne permet pas d'apprendre,
et nous restreindrait dans l'usage qu'on en fait.

## Proposition de Claude
Option B, pour l'apprentissage. L'argument de la restriction ne tient pas vraiment :
les crates offrent une API incrémentale suffisante.

## Décision finale et pourquoi
Option B. L'algorithme est court, la spécification est publique et les vecteurs de test officiels
permettent de vérifier le résultat. C'est aussi un bon exercice de Rust (bit à bit, arithmétique modulaire).
API incrémentale (`update` / `finalize`) pour pouvoir hacher l'en-tête puis le contenu sans tout concaténer.

## Ce qu'on a écarté et pourquoi
La crate : elle n'apporte rien ici, puisque les performances ne sont pas un enjeu à ce stade.

## Verdict
Convergence sur la conclusion. Un de mes deux arguments (la restriction d'usage) était faible.
