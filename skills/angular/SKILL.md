# Skill : Angular

## Objectif
Conseiller et valider les pratiques Angular modernes.

## Quand le charger
- Mission frontend Angular.
- Création ou refonte de composants.
- Revue d’architecture front.

## Quand ne pas le charger
- Backend pur.
- Site statique sans Angular.

## Checklist
- Composants focalisés.
- Typage strict.
- Pas de store global par défaut.
- SSR gardé avec `isPlatformBrowser`.
- RxJS avec `takeUntilDestroyed`.

## Bonnes pratiques
- `signal()` + `computed()` pour l’état local.
- Services injectés racine pour API.
- Tests unitaires ciblés.
- Respect du design system projet.

## Erreurs fréquentes
- `localStorage` sans garde SSR.
- `BehaviorSubject` pour état local.
- Composants trop volumineux.

## Critères de validation
- Build.
- Tests unitaires passants.
- Revue de performance et accessibilité.
