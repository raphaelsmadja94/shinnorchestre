# Skill : PHP

## Objectif
Conseiller et valider les pratiques PHP modernes, stables et sécurisées.

## Quand le charger
- Mission backend PHP.
- Revue de code PHP.
- Conception d’API ou de pages dynamiques.

## Quand ne pas le charger
- Projet sans PHP.
- Tâche purement frontend sans logique serveur.

## Checklist
- Version PHP respectée.
- Entrées utilisateur validées/nettoyées.
- Accès base de données préparé.
- Erreurs gérées sans fuite d’informations.
- Secrets externalisés.
- Tests présents et non bloqués.

## Bonnes pratiques
- Typage explicite des paramètres et retours.
- Séparation des responsabilités.
- Journalisation métier sans données sensitives.
- Gestion des erreurs avec exceptions métiers.

## Erreurs fréquentes
- Concaténation SQL.
- Secrets en dur.
- Absence de validation/sanitization.
- Mixage de logique PHP et HTML.

## Critères de validation
- Lint/syntaxe OK.
- Tests unitaires/intégration passent.
- Revue sécurité minimale.

## Règles opérationnelles

### Compatibilité
- Respecter la version PHP du projet.
- Ne pas introduire d’extension non justifiée.

### Architecture
- Séparer la logique métier de l’affichage.
- Préférer des services/classes pour les règles métier.
- Éviter le code PHP dans les vues autant que possible.

### Sécurité
- Requêtes préparées/ORM paramétré uniquement.
- Externaliser les secrets ; aucun cred en dur.
- Cookies de session sécurisés.

### Tests
- Tests unitaires sur la logique métier.
- Tests d’intégration pour les parcours critiques.
- Données de test bornées et réalistes.

## Processus d’intervention
1. Lire la version PHP et les conventions du projet.
2. Identifier le périmètre minimal.
3. Modifier sans casser l’architecture existante.
4. Compiler/syntax-checker.
5. Tester les chemins impactés.
6. Vérifier sécurité et configuration.
7. Produire un rapport court.

## Références officielles
- Documentation PHP.
- Documentation des librairies utilisées.
