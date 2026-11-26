# TP8 — Stratégies GitHub Actions

## Partie 1 — La matrice de base

### Q1 – Combien de jobs sont générés ? Donnez la liste des combinaisons

La matrice génère 6 jobs (2 systèmes d'exploitation × 3 versions de Python) :

1. ubuntu-latest + Python 3.11
2. ubuntu-latest + Python 3.12
3. ubuntu-latest + Python 3.13
4. windows-latest + Python 3.11
5. windows-latest + Python 3.12
6. windows-latest + Python 3.13

### Q2 – Combien de jobs au total ? Rappel : exclude s'applique avant include.

La matrice génère 6 jobs :
6 combinaisons initiales - 1 combinaison exclue (windows-latest + Python 3.11) + 1 combinaison ajoutée (ubuntu-latest + Python 3.14 expérimentale).

### Q3 – Que se passerait-il si vous tentiez d'exclure la combinaison 3.14 ? Pourquoi ?

La combinaison Python 3.14 est ajoutée par include, après l'application de exclude. Elle ne peut donc pas être supprimée par exclude dans cette configuration car exclude agit sur les combinaisons de base avant l'ajout de la nouvelle combinaison par include.