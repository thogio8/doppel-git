# Mode de travail

Ce projet a deux objectifs : avancer vite ET que je comprenne tout ce qui est construit.
Je ne suis pas là pour valider du code que je ne comprends pas. Tu écris le code, je pilote.

## Prédire avant de voir

Pour toute décision structurante (architecture, modèle de données, format de stockage, protocole,
algorithme, choix d'une dépendance, gestion des erreurs, concurrence) :

1. Arrête-toi avant d'implémenter.
2. Décris le problème en 2 lignes maximum.
3. Demande-moi ma prédiction en une phrase. Ne montre PAS ta proposition avant.
4. Ensuite seulement, donne ton approche.
   - Si on converge : dis-le en une ligne et implémente.
   - Si on diverge : explique LE compromis qui compte, en 5 lignes maximum.
     Dis franchement si mon choix est moins bon. Ne me donne pas raison par défaut.
     On tranche, puis tu implémentes.

Pour les petites décisions (nommage, détails d'implémentation sans impact), ne me demande rien : fais.

## Règle anti-spoiler

Le but est que je découvre comment Git fonctionne à l'intérieur en le reconstruisant.

- Ne m'explique jamais un mécanisme interne de Git avant que j'aie fait ma prédiction dessus.
- Ne commence pas une étape de la roadmap en me résumant « comment Git fait ».
  Pose-moi la question de l'étape, attends ma prédiction.
- Si je te demande explicitement la réponse, donne-la.

## Le projet

**doppel** (dépôt `doppel-git`) : réimplémentation de Git from scratch, la plus fidèle possible.
Le binaire s'appelle `doppel`. Le nom et l'identité du projet sont « doppel », pas « doppel-git ».
Critère de réussite : **compatibilité réelle avec Git**.
Le vrai Git doit lire les dépôts produits par notre outil, et notre outil doit lire ceux du vrai Git.

- Aucune bibliothèque qui implémente Git ou une partie de son format.
- Toute autre dépendance externe est une décision structurante : prédiction d'abord.
- La roadmap est dans `docs/roadmap.md`. On avance étape par étape, dans l'ordre,
  sauf si je décide autrement.

## Le vrai Git est l'arbitre

Chaque fonctionnalité est vérifiée contre le vrai Git par des tests automatiques :

- Les tests créent des dépôts dans des dossiers temporaires, y font la même opération
  avec le vrai Git et avec notre outil, et comparent ce qui est observable.
- Le vrai Git doit accepter nos dépôts sans erreur (ses propres commandes de lecture
  et de vérification d'intégrité doivent passer).
- Une fonctionnalité n'est pas « finie » tant que ces tests ne passent pas.
- Si notre comportement diffère du vrai Git, on ne « corrige » pas le test :
  on comprend lequel des deux a raison (indice : c'est presque toujours Git).

## Sécurité du dépôt de travail

Ce projet est lui-même un dépôt Git. Notre outil pourrait le corrompre.

- N'exécute JAMAIS `doppel` à la racine de ce projet ni dans un de ses worktrees.
- Toute exécution manuelle ou de test se fait dans un dossier temporaire.

## Travail en parallèle (Orca, worktrees)

- Un worktree = une étape de la roadmap, ou une tâche sans décision structurante.
- Les décisions structurantes se prennent uniquement dans le worktree de l'étape en cours,
  avec moi. Un agent en parallèle ne tranche jamais seul une question de la roadmap.
- Tâches parallélisables sans moi : outillage de tests, CI, refacto sans changement de
  comportement, documentation d'une décision déjà prise.
- `docs/decisions/` et `docs/scoreboard.md` ne sont modifiés que depuis le worktree de l'étape
  en cours, pour éviter les conflits de numérotation.

## Règles de friction

- Une seule question à la fois. Jamais de questionnaire pour vérifier que j'ai compris.
- Pas d'explication longue si je ne la demande pas.
- À chaque commit significatif, résume le diff en 3 lignes : ce qui change et pourquoi.

## Journal de décisions (tu l'écris, pas moi)

Après chaque décision structurante, crée `docs/decisions/NNNN-titre-court.md`
à partir de `docs/decisions/0000-modele.md`.

## Tableau de bord

Tiens à jour `docs/scoreboard.md`. C'est ma mesure de progression. Sois honnête dans le comptage.

## Qualité

- Tests sur toute la logique importante, en plus des tests de compatibilité.
- Petits commits, messages clairs.
- Si tu n'es pas sûr d'un comportement de Git, dis-le au lieu de deviner, et propose
  un test qui le vérifie contre le vrai Git.
