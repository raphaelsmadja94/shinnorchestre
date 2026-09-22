# Skill : DevOps

## Objectif
Conseiller et valider les pratiques d’intégration, de déploiement et d’exploitation.

## Quand le charger
- Automatisation de build/tests/déploiement.
- Gestion d’infrastructure ou de configuration.
- Observabilité/alerting.
- Revue d’environnement ou de pipeline.

## Quand ne pas le charger
- Tâche purement métier sans déploiement.
- Projet sans infrastructure technique.

## Checklist
- Pipeline versionné et reproductible.
- Déploiement réversible.
- Monitoring et alertes utiles.
- Accès et secrets sécurisés.

## Bonnes pratiques
- Automatiser les étapes répétitives.
- Immuabilité autant que possible.
- Séparer les environnements clairement.
- Documenter les procédures de runbook.

## Erreurs fréquentes
- Déploiement sans rollback testé.
- Secrets dans les pipelines.
- Absence de monitoring après mise en production.
- Environnements divergents sans traçabilité.

## Critères de validation
- Pipeline exécuté avec succès.
- Procédure de rollback validée.
- Métriques et logs disponibles.

## Règles opérationnelles

### Pipelines
- YAML versionné, lisible, modulaire.
- Jobs bornés en temps et en permissions.
- Artefacts utiles uniquement.

### Infrastructure
- Automatisation reproductible.
- Changements tracés.
- Sécurité des accès.

### Observabilité
- Logs structurés.
- Alertes actionnables.
- Indicateurs utiles, pas exhaustifs.

## Processus d’intervention
1. Cartographier le flux de build/déploiement.
2. Identifier les points de risque.
3. Proposer les améliorations par priorité.
4. Valider avant exécution.
5. Produire un rapport court.

## Références officielles
- Documentation des outils d’intégration/déploiement utilisés.
