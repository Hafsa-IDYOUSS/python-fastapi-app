# TP6 — Variables d'environnement, Inputs et Outputs

## Partie 1 — GITHUB_ENV

### Q1. Pourquoi la variable n'est-elle disponible que dans les steps suivantes ?

Les variables écrites dans GITHUB_ENV sont prises en compte par le runner après la fin de la step qui les définit. Elles sont donc accessibles aux steps suivantes du même job, mais pas automatiquement à la step qui les a créées.

### Q2. Quelle est la portée de GITHUB_ENV ?

Dans le job verify-env, la variable APP_NAME est vide. Cela montre que GITHUB_ENV permet de transmettre des variables uniquement aux steps suivantes d'un même job, et non entre différents jobs.

### Q3. Que se passe-t-il si on utilise > au lieu de >> dans GITHUB_OUTPUT ?

L'opérateur > écrase le contenu précédent du fichier, tandis que >> ajoute une nouvelle ligne sans supprimer les précédentes. Si deux outputs sont définis avec >, seul le dernier est conservé.

### Q4. Pourquoi GITHUB_ENV ne suffit-il pas pour communiquer entre jobs ?

GITHUB_ENV permet de partager des variables uniquement entre les steps d'un même job. En revanche, GITHUB_OUTPUT permet de définir des outputs qui peuvent être exposés au niveau du job et récupérés par un autre job grâce à needs.

### Q5. Que se passe-t-il si on retire needs: build du job deploy ?

Sans needs: build, le job deploy devient indépendant de build et peut s'exécuter en parallèle. Il ne peut plus accéder à needs.build.outputs.full_version, donc la version complète n'est plus transmise correctement.