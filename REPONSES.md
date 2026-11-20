# TP7 — Actions tierces et actions personnalisées

## Partie 1 — Utiliser des actions tierces

### Q1. Pourquoi actions/checkout n'a-t-il pas besoin de with alors que setup-node en a besoin ?

actions/checkout@v4 fonctionne avec ses paramètres par défaut pour récupérer le dépôt courant. actions/setup-node@v4 utilise with pour préciser la version de Node.js souhaitée, ici la version 20. with est donc facultatif ou nécessaire selon la configuration attendue de l'action.

### Q2. Pourquoi le job verify ne retrouve-t-il pas report.txt sans l'artefact, alors que les deux jobs partagent le même dépôt ?

Les jobs build et verify s'exécutent dans des environnements distincts. Le fichier report.txt est généré pendant l'exécution de build et n'est pas automatiquement partagé avec verify. L'artefact permet de transférer ce fichier entre les deux jobs.

## Partie 3 — Action composite locale

### Q6. Pourquoi actions/checkout doit-il s'exécuter avant l'appel d'une action locale ?

actions/checkout récupère les fichiers du dépôt dans l'espace de travail du runner. Comme notre action locale se trouve dans .github/actions/build-info, elle doit être présente sur le runner avant de pouvoir être appelée avec uses.

### Q7. Pourquoi shell: bash est-il obligatoire sur les steps run d'une action composite ?

Dans une action composite, chaque step utilisant run doit préciser explicitement le shell à utiliser. shell: bash indique que les commandes seront exécutées avec Bash, contrairement aux steps classiques d'un workflow qui peuvent utiliser un shell par défaut.