# Roadmap

Chaque étape est une question à trancher, pas une spécification.
Une étape est finie quand son critère de compatibilité passe contre le vrai Git.

## Fondations

- [ ] **1. Stocker un fichier.**
  Comment identifier un contenu de façon unique et ne jamais stocker deux fois le même ?
  *Fini quand* : le vrai Git relit un contenu stocké par notre outil, et inversement.

- [ ] **2. Photographier un dossier.**
  Comment représenter une arborescence entière à un instant donné ?
  *Fini quand* : le vrai Git lit nos arborescences, et inversement.

- [ ] **3. Commit et historique.**
  Comment relier les versions entre elles pour remonter le temps ?
  *Fini quand* : l'historique créé par notre outil s'affiche correctement avec le vrai Git.

- [ ] **4. Branches et position courante.**
  Qu'est-ce qu'une branche, concrètement ? Comment sait-on « où on est » ?
  *Fini quand* : les deux outils voient les mêmes branches et la même position.

## Le quotidien

- [ ] **5. La zone de staging.**
  Pourquoi `add` existe-t-il, et comment `status` est-il si rapide sur un gros projet ?
  *Fini quand* : le vrai Git et notre outil donnent le même `status` sur le même dossier.

- [ ] **6. Revenir en arrière.**
  Comment restaurer un dossier tel qu'il était à un commit donné, sans rien perdre ?
  *Fini quand* : checkout croisé (l'un écrit, l'autre restaure) sans différence.

- [ ] **7. Ignorer et configurer.**
  Comment décider ce qui ne doit pas être suivi, et d'où viennent les réglages ?

- [ ] **8. Diff.**
  Comment montrer ce qui a changé entre deux versions, et pourquoi y a-t-il plusieurs « bonnes » réponses ?
  *Fini quand* : nos diffs sont équivalents à ceux de Git sur un jeu de cas réels.

- [ ] **9. Merge.**
  Le boss de fin. Comment combiner deux historiques, et quand faut-il abandonner et demander à l'humain ?

## En profondeur

- [ ] **10. Stockage efficace.**
  Comment un dépôt avec des années d'historique reste-t-il compact ?
  *Fini quand* : on lit les dépôts compactés par le vrai Git, et il lit les nôtres.

- [ ] **11. Réécrire l'histoire.**
  Que se passe-t-il vraiment pendant un rebase ? Qu'est-ce qui est conservé, qu'est-ce qui disparaît ?

- [ ] **12. Le réseau.**
  Comment deux dépôts s'échangent-ils uniquement ce qui manque à l'autre ?
  *Fini quand* : clone, fetch et push fonctionnent avec un vrai serveur Git.
