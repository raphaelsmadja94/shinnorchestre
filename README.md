# ShinNO OS

Orchestrateur multi-agents dédié aux projets ShinNO.

## Architecture

```
ShinNO AI (router)
├── Mémoire utilisateur
│   └── memory Hermes
└── Experts
    ├── CTO
    ├── Tech Lead
    ├── Product
    ├── Business
    ├── Growth
    ├── Content Creator
    ├── Designer
    ├── Teacher
    ├── Career Advisor
    └── Coach Sport
```

## Composants

| Composant | Rôle | Répertoire |
|-----------|------|------------|
| ShinNO AI | Orchestrateur et router | `experts/router.md` |
| Experts | Experts métier délégués | `experts/*.md` |
| Skills | Compétences réutilisables | `skills/*/SKILL.md` |
| Workflows | Procédures d’exécution | `workflows/*.md` |
| Projets | Contextes projet | `projects/*/PROJECT.md` |
| Agents anciens | Archives | `agents/deprecated/` |
| Gouvernance | Règles et politiques | `GOVERNANCE.md` |

## Démarrage rapide

1. Choisir un projet dans `projects/`.
2. Laisser ShinNO AI router vers le bon expert.
3. L’expert charge les skills et workflows adaptés.
4. Produire un livrable court : diagnostic, plan, diff, tests, risques, décision attendue.

## Références

- `GOVERNANCE.md` : règles de gouvernance
- `experts/router.md` : règles de routing
- `audit_coherence_report.md` : audit automatique de cohérence
