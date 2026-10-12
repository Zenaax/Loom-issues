# Loom — tracker de bugs

Dépôt **d'issues seulement**. Le code de Loom n'est pas ici : il est dans un dépôt privé, et il le reste pour l'instant. Ce qui est public, c'est la liste de ce qui casse.

**Loom** est un IDE agentique de bureau (Tauri + SvelteKit) avec un moteur d'agent et un moteur d'intelligence de code maison. L'agent intégré s'appelle **Navette**.

## À quoi sert ce dépôt

- consigner les dysfonctionnements rencontrés, avec assez d'éléments pour agir sans relancer l'auteur du rapport;
- rendre lisible l'état de santé du produit avant qu'un correctif existe;
- éviter deux rapports pour la même panne (`duplicate` est là pour ça).

Ce n'est ni un support ni une file d'améliorations : une demande de fonctionnalité se discute ailleurs.

## Ce qu'est un rapport utilisable

Un bon rapport tient en une page et ne demande rien de plus à lire. Les sections attendues :

| Section | Ce qu'elle porte |
| --- | --- |
| **Résumé** | ce qui était fait, ce qui est arrivé, et la zone concernée (`Zone: moteur`, `agent`, `acp`, `ledger`, `ui`, `persistance`, `identité`, `règles`, `build`, `unknown`) |
| **Impact** | qui est touché, à quelle fréquence, et qu'est-ce que ça bloque |
| **Environnement** | version de Loom, canal, système, modèle et harness utilisés |
| **Déclencheur** | ce qui a précédé — « inconnu, constaté après coup » est une réponse acceptable |
| **Attendu / Observé** | la différence entre les deux, en deux lignes |
| **Ce qui marche encore** | les comportements voisins vérifiés sains : c'est ce qui délimite la panne |
| **Cause racine** | une conclusion assumée, ou `Undetermined` avec ce qui a été écarté et la meilleure piste restante |
| **Preuves** | quelques lignes de log, pas le fichier entier |
| **Écarté** | les hypothèses tuées par une preuve précise |

« Undetermined » n'est pas un échec : une issue qui écarte trois pistes en vaut une qui en avance une fausse.

## Comment les rapports sont produits

Loom embarque une commande `/doctor`. Elle ne remplit pas un formulaire : elle **mène l'enquête** sur la machine — le journal de diagnostic (`logs\runtime.<date>.log`), le journal des appels d'outils, les métriques des runs, l'état de l'index de code — puis rédige le brouillon ci-dessus, l'expurge pendant qu'elle cite, et demande un accord explicite avant toute publication. Rien n'est posté sans que le texte exact ait été montré.

Tu peux aussi ouvrir une issue à la main : garde les mêmes sections, ça aidera autant.

## Ce qui ne doit jamais atterrir ici

Les rapports passent par une passe d'expurgation, mais le dernier filet appartient à qui poste :

- aucune clé API, aucun jeton — ils ne sont pas dans le journal de Loom (ils vivent dans le trousseau du système), mais ils peuvent se trouver dans un extrait de fichier ou une ligne de commande;
- aucun contenu de prompt, de réponse ou de conversation : on décrit, on ne cite pas;
- aucun nom de projet privé, de dépôt ou de branche, sauf si tu dis expressément qu'il est public;
- aucun chemin absolu : `~\Documents\mon-projet` suffit, le prénom de l'utilisateur n'apporte rien au diagnostic.

Si un rapport publié contient l'une de ces choses, ouvre une issue ou signale-le : la correction est faite, pas discussion.

## Licence de ce dépôt

Les issues sont publiques. Le contenu y est placé pour servir le débogage ; n'y mets rien que tu ne veux pas voir cité.
