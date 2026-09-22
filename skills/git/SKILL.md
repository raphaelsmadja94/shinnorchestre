# Skill : Git

## Objectif
Garantir un usage sûr, tracé et lisible de Git.

## Quand le charger
- Création de branche / PR.
- Revue d’historique avant merge.
- Nettoyage, cherry-pick, rollback.
- Gestion de dépôt multi-contributeurs.

## Quand ne pas le charger
- Dépôt sans Git.
- Tâche sans opération sur l’historique.

## Checklist
- Convention de branches respectée.
- Commits atomiques et clairs.
- Aucun secret dans l’historique.
- Merge propre sans conflict silencieux.

## Bonnes pratiques
- Commits impératifs et courts.
- Branches par périmètre fonctionnel.
- Rebase avant merge si la politique l’autorise.
- Tags pour les releases.

## Erreurs fréquentes
- Commit de secrets.
- Merge de fonctionnalités non relues.
- Historique pollué par des commits de merge géants.
- Force push sans coordination.

## Critères de validation
- `git status` / `git log` propres.
- `git diff --check` sans avertissement.
- Aucun fichier sensible ajouté.

## Règles opérationnelles

### Workflow
- Branches dédiées, jamais directement sur la branche stable.
- PR systématique pour toute modification.
- Validation humaine avant merge.

### Sécurité
- Ne pas committer `.env`, credentials, tokens.
- Vérifier `git diff --cached` avant commit.
- Ne jamais réécrire l’historique public sans validation.

### Nettoyage
- `git prune` / `git fetch --prune` périodiquement.
- Supprimer les branches mergées après validation.

## Processus d’intervention
1. Vérifier la branche courante.
2. Vérifier l’état du working tree.
3. Inspecter les fichiers modifiés.
4. Committer avec message explicite.
5. Pousser et ouvrir une PR si autorisé.
6. Produire un rapport court.

## Références officielles
- Documentation Git.
- Guides de conventions du projet.
