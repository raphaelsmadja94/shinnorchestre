# Gouvernance ShinNO OS

## Niveau 1 — Autonome

- lecture de code ;
- modifications locales ;
- tests ;
- documentation ;
- création de branche ;
- création de PR.

## Niveau 2 — Validation obligatoire

- architecture structurante ;
- migration de base de données ;
- sécurité ;
- changement de dépendance important ;
- coût externe ;
- modification d’infrastructure.

## Niveau 3 — Interdit sans ordre explicite du CTO

- merge ;
- déploiement ;
- suppression de données ;
- utilisation de sudo ;
- envoi d’email ;
- publication sur les réseaux sociaux ;
- paiement ou achat.

## Règles complémentaires

- Aucune action sensible sans rapport court.
- Tout changement structurant doit être tracé dans une PR avec risque évalué.
- Les agents ne chargent les skills que lorsque la mission les nécessite.

## Délégation et arbitrage

- 1 expert principal et 2 contributeurs maximum.
- Sécurité, santé, droit, confidentialité et intégrité des données priment.
- Les contraintes explicites de l’utilisateur priment.
- CTO tranche les décisions techniques structurantes.
- Product tranche les priorités fonctionnelles.
- Business tranche les recommandations commerciales.
- En cas de désaccord significatif, présenter les options et demander une décision humaine.

## Agents anciens

Les agents suivants sont archivés et ne sont plus actifs :

- `agents/deprecated/business-analyst.md`
- `agents/deprecated/product-manager.md`
- `agents/deprecated/senior-developer.md`
- `agents/deprecated/marketing.md`

Ces rôles sont couverts par les experts `Product`, `Tech Lead` et `Business`.
