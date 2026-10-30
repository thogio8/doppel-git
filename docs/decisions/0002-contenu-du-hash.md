# 0002 — Ce qui entre dans le hash d'un fichier

**Étape de la roadmap :** 1
**Date :** 2026-10-30

## Contexte
On identifie un contenu par son hash. Il fallait décider ce qu'on donne à la fonction de hash :
juste le contenu, ou aussi le nom, les droits et les métadonnées.

## Options envisagées
- Option A : hacher tout ce qui identifie le fichier (nom, droits, métadonnées, taille, contenu).
- Option B : hacher seulement un en-tête (type d'objet + taille) suivi du contenu brut.

## Ma prédiction
Option A : nom, droits, métadonnées, taille et contenu, c'est-à-dire tout ce qui identifie le fichier.

## Proposition de Claude
Option B. Le nom, les droits et les dates ne font pas partie de l'identité d'un *contenu*.
Ils seront portés par le niveau au-dessus (étape 2).

## Décision finale et pourquoi
Option B, parce qu'avec A :
- un renommage ou un simple `touch` changerait le hash, et le même contenu serait stocké plusieurs fois ;
- nos identifiants seraient différents de ceux du vrai Git, ce qui casse la compatibilité.

## Ce qu'on a écarté et pourquoi
Option A : elle confond l'identité d'un contenu et celle d'un fichier placé dans un dossier.

## Verdict
Divergence partielle : j'avais vu juste pour la taille, Claude avait raison pour le reste.
Ce que j'en retiens : séparer « ce que contient le fichier » de « où il est et comment il s'appelle ».
