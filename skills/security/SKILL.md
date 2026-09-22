# Skill : Security

## Objectif
Identifier, documenter et réduire les risques de sécurité applicative.

## Quand le charger
- Audit de configuration.
- Ajout d’authentification/autorisation.
- Exposition publique ou traitement de données sensibles.
- Revue de code sensible.

## Quand ne pas le charger
- Prototype local sans réseau.
- Tâche sans manipulation de données ou d’accès.

## Checklist
- Entrées validées.
- Sécurité par défaut.
- Aucun secret en clair.
- Journalisation sans fuite sensible.
- Dépendances à jour.

## Bonnes pratiques
- Principe de moindre privilège.
- Defense in depth.
- Gestion centralisée des erreurs sans fuite.
- Durcissement des en-têtes et configurations serveur.

## Erreurs fréquentes
- Exposition de secrets.
- Absence de validation côté serveur.
- Logs sensibles.
- Dépendances non surveillées.

## Critères de validation
- Revue sécurité effectuée.
- Aucune vulnérabilité critique ouverte.
- Scan de dépendances si applicable.

## Règles opérationnelles

### Authentification
- Gestion centralisée.
- Mots de passe hashés avec algorithme adapté.
- Sessions sécurisées.

### Autorisation
- Vérifier les droits à chaque opération sensible.
- Refus par défaut.

### Données
- Traitement sécurisé et minimisé.
- Chiffrement en transit/repos selon cas.
- Masquage/journalisation appropriée.

### Dépendances
- Maintenir les versions stables.
- Scanner les vulnérabilités connues.

## Processus d’intervention
1. Cartographier les entrées/sorties sensibles.
2. Identifier les risques applicatifs.
3. Proposer des mesures adaptées.
4. Vérifier l’implémentation.
5. Produire un rapport court.

## Références officielles
- OWASP ASVS / Top 10.
- Documentation des composants sécurité du projet.
