# TP7 — Security Notes

## Partie 2 — Sécurité des actions tierces

### Q3. Pourquoi faut-il épingler une version (@v4) plutôt que @main ?

Utiliser @v4 permet de cibler une version majeure de l'action et d'éviter de suivre directement les modifications de la branche main. Cela améliore la stabilité et limite les risques de changements imprévus. Pour une sécurité renforcée en production, on peut épingler l'action à un SHA de commit précis.

### Q4. Le badge « créateur vérifié » garantit-il qu'une action est sûre ? Justifiez.

Non. Le badge indique que GitHub a vérifié l'identité du créateur, mais il ne garantit pas que le code est exempt de vulnérabilités ou de comportements malveillants. Il reste nécessaire d'examiner le code et la fiabilité de l'action.

### Q5. Citez deux vérifications à faire avant d'utiliser, en production, une action d'un fournisseur inconnu.

- Examiner le code source et les permissions demandées par l'action afin de repérer d'éventuels comportements dangereux.
- Vérifier la réputation du fournisseur, l'historique des mises à jour et les éventuelles vulnérabilités signalées.