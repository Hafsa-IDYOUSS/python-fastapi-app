# TP7 — Actions tierces et actions personnalisées

## Partie 1 — Utiliser des actions tierces

### Q1. Pourquoi actions/checkout n'a-t-il pas besoin de with alors que setup-node en a besoin ?

actions/checkout@v4 fonctionne avec ses paramètres par défaut pour récupérer le dépôt courant. actions/setup-node@v4 utilise with pour préciser la version de Node.js souhaitée, ici la version 20. with est donc facultatif ou nécessaire selon la configuration attendue de l'action.

### Q2. Pourquoi le job verify ne retrouve-t-il pas report.txt sans l'artefact, alors que les deux jobs partagent le même dépôt ?

Les jobs build et verify s'exécutent dans des environnements distincts. Le fichier report.txt est généré pendant l'exécution de build et n'est pas automatiquement partagé avec verify. L'artefact permet de transférer ce fichier entre les deux jobs.