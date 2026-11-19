# TP6 — Variables d'environnement, Inputs et Outputs

## Partie 1 — GITHUB_ENV

### Q1. Pourquoi la variable n'est-elle disponible que dans les steps suivantes ?

Les variables écrites dans GITHUB_ENV sont prises en compte par le runner après la fin de la step qui les définit. Elles sont donc accessibles aux steps suivantes du même job, mais pas automatiquement à la step qui les a créées.

### Q2. Quelle est la portée de GITHUB_ENV ?

Dans le job verify-env, la variable APP_NAME est vide. Cela montre que GITHUB_ENV permet de transmettre des variables uniquement aux steps suivantes d'un même job, et non entre différents jobs.