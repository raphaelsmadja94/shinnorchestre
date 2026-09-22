# Skill : Testing

## Objectif
 Concevoir et exécuter une stratégie de tests pertinente, reproductible et maintenable

## Quand le charger
- Nouvelle fonctionnalité ou correction.
- Ajout de tests unitaires/d’intégration.
- Revue de couverture/robustesse.

## Quand ne pas le charger
- Tâche sans périmètre fonctionnel testable.
- Projet sans infrastructure d’exécution.

## Checklist
- Tests couvrant les cas heureux et limites.
- Jeux de données bornés et réalistes.
- Exécution reproductible localement et en CI.
- Aucun test dépendant de l’ordre d’exécution.

## Bonnes pratiques
- Nommage explicite du comportement testé.
- Tests courts et isolés.
- Mocks sur les limites du système.
- Mesure de couverture utile, pas quantitative seulement.

## Erreurs fréquentes
- Tests trop couplés à l’implémentation.
- Données de test partagées without isolation.
- Tests ignorés/skippés sans justification.
- Absence de tests sur les cas limites.

## Critères de validation
- Suite verte sur environnement standard.
- Rapports exploitables.
- Aucune régression visible non couverte.

## Règles opérationnelles

### Unitaires
- Une responsabilité par test.
- Mock des dépendances externes.
- Focus sur la logique métier.

### Intégration
- Bases de test isolées.
- Contrats API vérifiés.

### E2E
- Parcours critiques priorisés.
- Réutiliser les identifiants de test dédiés.

### Reporting
- Échecs lisibles et actionnables.
- Historique conservé.

## Processus d’intervention
1. Lister les fonctionnalités à risque.
2. Choisir le niveau de test adapté.
3. Écrire les cas de test.
4. Exécuter et corriger.
5. Produire un rapport court.

## Références officielles
- Documentation des frameworks de test du projet.
