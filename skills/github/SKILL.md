# Skill : GitHub

## Objectif
Utiliser efficacement GitHub comme support de collaboration, d’audit et de livraison.

## Quand le charger
- Création/gestion de PR, issues, releases.
- Automatisation via Actions.
- Gestion de permissions, branches, tags.

## Quand ne pas le charger
- Projet hébergé hors GitHub.
- Tâche sans interaction avec la plateforme.

## Checklist
- PR avec titre et description clairs.
- Checks CI passés.
- Reviewers assignés.
- Aucun conflit non résolu.

## Bonnes pratiques
- PR small et focalisée.
- Conventional Commits.
- Protection des branches principales.
- Issues pour tracer demande, bug, tâche.

## Erreurs fréquentes
- PR trop larges.
- Merge sans review.
- Secrets dans les logs Actions.
- Workflows sans limitation de permissions.

## Critères de validation
- CI verte.
- Review approuvée.
- Aucun avertissement sécurité.

## Règles opérationnelles

### Permissions
- Accès minimal nécessaire.
- Secrets stockés dans GitHub Secrets uniquement.

### Actions
- Jobs versionnés, reproductibles.
- Timeouts et cache maîtrisés.
- Permissions explicites dans chaque workflow.

### Issues/PR
- Labels, milestones, assignees utiles.
- Template de PR obligatoire.
- Pas d’auto-merge sans validation humaine.

## Processus d’intervention
1. Identifier le besoin (issue, PR, release).
2. Vérifier l’état de la branche cible.
3. Ouvrir une PR ou une issue structurée.
4. Suivre les checks et les reviews.
5. Fusionner uniquement après validation.
6. Produire un rapport court.

## Références officielles
- Documentation GitHub.
- Documentation GitHub Actions.
