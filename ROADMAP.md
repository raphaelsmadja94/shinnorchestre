# Roadmap — ShinNO AI Platform

> Vision : transformer ShinNO AI en un véritable Chief of Staff personnel.
> Critère de réussite : valeur gagnée par semaine pour l’utilisateur.
> Approche : incrémentale, sans tout créer d’un coup.

## Principes directeurs
- Prioriser l’action immédiate sur la documentation.
- Chaque playbook doit produire un livrable court, actionnable.
- Routines > réactivité.
- Automatiser ce qui est répétable, préparer ce qui est stratégique.
- Transparence systématique : profils/skills/workflows/projets affichés avant chaque réponse.

## Livrables attendus par phase

## P0 — Immédiat
- [ ] Playbooks quotidiens minimalement actionnables
- [ ] Routine matinale automatique
- [ ] Génération automatique du daily brief Telegram
- [ ] Analyse quotidienne des nouvelles PR GitHub

## P1 — Court terme (1-2 semaines)
- [ ] Playbooks hebdomadaires complets
- [ ] Intégrations Telegram + GitHub actives
- [ ] Premier scheduler automatisé
- [ ] Métriques de valeur hebdomadaire

## P2 — Moyen terme (1 mois)
- [ ] Toutes les routines quotidiennes/hebdomadaires/mensuelles
- [ ] Intégration calendrier + email
- [ ] Playbooks Business/SEO/Content automatisés
- [ ] Premier système d’alertes intelligentes

## P3 — Long terme (2-3 mois)
- [ ] Intégrations avancées
- [ ] Apprentissage des préférences
- [ ] anticipation proactive des besoins
- [ ] Dashboard de valeur et de productivité

---

## PHASE P0 — IMMÉDIAT

### Objectif
Passer de ShinNO AI réactif à ShinNO AI proactif sur les sujets les plus à fort ROI.

### Playbooks quotidiens à créer en priorité
1. `daily-brief` — Résumé quotidien projet/en cours
2. `pr-review` — Analyse automatique des nouvelles PR
3. `todo-scan` — Scan des TODO et création de tickets
4. `debt-scan` — Détection de la dette technique
5. `dependency-scan` — Détection des dépendances obsolètes
6. `github-daily` — Activité GitHub quotidienne

### Routines quotidiennes
- **Matin (08:00)** : Daily Brief Telegram
  - Résumé des actions en cours
  - Rappels du jour
  - Nouvelles PR à reviewer
  - TODOs critiques
  - Activité GitHub overnight
  - Alertes sécurité/dette/dépendances
- **Soir (19:00)** : Check-out rapide
  - État d’avancement vs objectifs
  - Plan pour le lendemain
  - Alertes non traitées

### Nouveaux skills/workflows nécessaires
- `daily-brief` (skill) — Génération de briefs quotidiens
- `pr-analyzer` (skill) — Analyse de PR
- `debt-detector` (skill) — Détection de dette
- `dependency-tracker` (skill) — Suivi des dépendances
- `todo-manager` (skill) — Gestion des TODOs

### Intégrations immédiates
- **Telegram** : livraison des briefs
- **GitHub** : monitoring des PRs, issues, TODOs
- **Hermes cron** : scheduler natif pour routines

### Fonctionnalités réalisables immédiatement avec Hermes
- ✅ Cronjob Telegram quotidien pour le brief
- ✅ Webhooks GitHub pour analyser les PRs
- ✅ Scripts shell/Python pour scanner les dépôts
- ✅ Intégration memory Hermes pour persistance des TODO/alertes
- ✅ Rappels automatiques via cronjob
- ✅ Délégation vers experts via delegate_task

### Limites actuelles d’Hermes et contournements
- ❌ Pas d’accès natif aux dépôts distants en temps réel
  - → Workaround : scripts locaux + GitHub API polling via cron
- ❌ Pas de dashboard visuel
  - → Workaround : rapports Markdown + PDF hebdomadaires
- ❌ Pas d’apprentissage automatique
  - → Workaround : règles basées sur memory Hermes + ajustement manuel
- ❌ Pas d’intégration calendar/email native
  - → Workaround : exports .ics + webhooks via scripts externes

---

## PHASE P1 — COURT TERME (1-2 SEMAINES)

### Objectif
Étendre la proactivité aux sujets business, content et SEO.

### Playbooks hebdomadaires à créer
1. `weekly-review` — Revue hebdomadaire complète
2. `content-pipeline` — Pipeline de contenu hebdomadaire
3. `seo-audit` — Audit SEO hebdomadaire
4. `business-intel` — Veille concurrentielle et opportunités
5. `fitness-weekly` — Revue sportive hebdomadaire
6. `nutrition-weekly` — Plan nutrition hebdomadaire

### Routines hebdomadaires
- **Lundi 09:00** : Weekly Review
  - Bref de la semaine passée
  - Priorités de la semaine
  - TODOs en cours
  - Alertes
- **Lundi 10:00** : Content Pipeline
  - Idées d’articles/posts LinkedIn
  - Calendrier éditorial de la semaine
  - Visuels à préparer
- **Lundi 11:00** : SEO Audit
  - Nouveaux mots-clés
  - Contenus à améliorer
  - Opportunités de linking interne
- **Mardi 10:00** : Business Intel
  - Veille concurrentielle
  - Nouvelles opportunités
  - Stratégies à préparer
- **Mercredi 10:00** : Fitness Weekly
  - Programme d’entraînement
  - Objectifs course/corde/musculation
  - Progression et récupération
- **Jeudi 10:00** : Nutrition Weekly
  - Recettes adaptées à la sèche
  - Menus de la semaine
  - Liste de courses et batch cooking
  - Estimation calories/protéines

### Nouveaux skills/workflows nécessaires
- `weekly-review` (workflow) — Revue hebdomadaire
- `content-ideas` (skill) — Génération d’idées de contenu
- `seo-analyzer` (skill) — Analyse SEO
- `competitive-intel` (skill) — Veille concurrentielle
- `fitness-planner` (skill) — Planning sportif
- `nutrition-planner` (skill) — Planning nutritionnel
- `shopping-list` (skill) — Liste de courses intelligente

### Intégrations à activer
- **Telegram** : calendrier éditorial + weekly briefs
- **Google Calendar** : planification automatique des routines
- **GitHub** : analyse hebdomadaire des PRs/issues

---

## PHASE P2 — MOYEN TERME (1 MOIS)

### Objectif
Automatiser la préparation et l’accompagnement sur tous les projets.

### Playbooks supplémentaires
1. `training-prep` — Préparation des talks et formations
2. `quiz-generator` — Génération d’exercices et quiz
3. `slider-generator` — Création de slides
4. `career-tracker` — Suivi des opportunités et entretiens
5. `finance-review` — Revue financière mensuelle
6. `habit-tracker` — Suivi des habitudes
7. `alert-manager` — Gestion centralisée des alertes

### Routines mensuelles
- **1er du mois** : Monthly Business Review
  - Performance SEO/content
  - Pipeline business
  - Objectifs du mois
  - Ajustements de stratégie
- **15 du mois** : Architecture Review
  - Cohérence ShinNO OS
  - Dette technique
  - Gouvernance
  - Améliorations à venir

### Nouveaux skills/workflows nécessaires
- `slide-design` (skill) — Création de slides
- `quiz-builder` (skill) — Construction de quiz
- `interview-prep` (skill) — Préparation d’entretiens
- `cv-enhancer` (skill) — Amélioration de CV/LinkedIn
- `finance-tracker` (skill) — Suivi financier
- `habit-monitor` (skill) — Monitoring des habitudes

### Intégrations à activer
- **Email** : weekly/monthly reports automatisés
- **Calendar** : planification intelligente
- **n8n** : orchestrateur de workflows externes

---

## PHASE P3 — LONG TERME (2-3 MOIS)

### Objectif
ShinNO AI devient un véritable assistant proactif qui anticipe les besoins.

### Fonctionnalités avancées
- **Anticipation** : détecter les tendances et proposer des actions avant qu’elles ne soient urgentes
- **Apprentissage** : mémoriser les préférences et affiner les playbooks
- **Collaboration** : invoquer les experts automatiquement selon le contexte
- **Dashboard** : vue consolidée de la valeur produite
- **Notifications intelligentes** : seulement ce qui compte, au bon moment

### Nouveaux skills/workflows nécessaires
- `trend-detector` (skill) — Détection de tendances
- `predictive-planner` (skill) — Planification prédictive
- `value-dashboard` (workflow) — Dashboard de valeur
- `smart-notifier` (skill) — Notifications intelligentes

### Intégrations à activer
- **Slack/Discord** : canaux dédiés par projet/expert
- **Notion/Obsidian** : synchronisation des notes
- **Zapier/Make** : automatisations entre outils
- **API custom** : exposition de ShinNO AI en service

---

## INTÉGRATIONS FUTURES

| Intégration | Usage | Priorité | Workaround actuel |
|-------------|-------|----------|-------------------|
| Telegram | Briefs, alertes, rappels | P0 | Cronjob + messages |
| GitHub | PRs, issues, TODOs | P0 | Scripts + API polling |
| Google Calendar | Planification | P1 | Exports .ics |
| Email | Rapports hebdomadaires | P1 | Scripts SMTP |
| n8n/Make | Workflows externes | P2 | Cron + scripts |
| Slack/Discord | Canaux projet | P3 | Webhooks |
| Notion/Obsidian | Notes synchronisées | P3 | Exports Markdown |

## FONCTIONNALITÉS IMMÉDIATES vs EXTERNE

### Réalisables immédiatement avec Hermes
- Console/CLI
- Délégation vers experts
- Memory utilisateur
- Création/lecture de fichiers
- Exécution de code
- Cron jobs
- Webhooks via scripts
- Rapports Markdown/PDF
- Intégration Telegram

### Nécéssitant un scheduler externe
- Intégrations calendar/email complexes
- Workflows n8n entre plusieurs services
- Jobs longue durée avec notifications
- Pipelines CI/CD externes

## LIMITES ACTUELLES ET SOLUTIONS

| Limite | Impact | Solution |
|--------|--------|----------|
| Pas d’accès temps réel aux dépôts distants | Monitoring retardé | Scripts + cron + API GitHub |
| Pas de dashboard natif | Vue consolidée manquante | Rapports Markdown + PDF |
| Pas d’apprentissage automatique | Personnalisation basique | Memory Hermes + règles manuelles |
| Pas d’intégration calendar/email native | Automatisation limitée | Scripts + webhooks + cron |
| Pas de workflow visuel | Orchestration complexe | Workflows texte + n8n |
| Pas de stockage structuré | État éparpillé | Memory Hermes + fichiers projet |

## MÉTRIQUES DE SUCCÈS

### Court terme (P0)
- Temps gagné par jour : > 30 min
- Nombre de briefs quotidiens livrés : 1
- Nombre de PRs analysées/jour : toutes les nouvelles
- TODOs détectés et traités : 100%

### Moyen terme (P1)
- Routine hebdomadaire automatisée : 5 playbooks
- Content pipeline : 1 post LinkedIn/jour préparé
- SEO audit : 1 rapport hebdomadaire
- Business intel : 1 veille hebdomadaire

### Long terme (P2-P3)
- Temps gagné par semaine : > 5h
- Playsbooks actifs : 15+
- Intégrations actives : 5+
- Score d’anticipation : 70%+ des alertes avant échéance

---

## PLAYBOOKS À CRÉER — LISTE COMPLÈTE

### Développement
1. `pr-analyzer` — Analyser les nouvelles PR
2. `refactor-proposer` — Proposer des refactorings
3. `debt-detector` — Détecter la dette technique
4. `coverage-improver` — Améliorer la couverture de tests
5. `next-task-preparer` — Préparer les prochaines tâches
6. `todo-tracker` — Suivre les TODO
7. `dependency-updater` — Détecter les dépendances obsolètes
8. `tech-ticket-generator` — Générer des tickets techniques

### Architecture
9. `architecture-review` — Revue régulière de l’architecture
10. `governance-checker` — Contrôle des règles de gouvernance
11. `consistency-checker` — Détection des incohérences
12. `quality-monitor` — Suivi de la qualité

### Business
13. `saas-ideas-tracker` — Suivi des idées SaaS
14. `competitive-watch` — Veille concurrentielle
15. `opportunity-finder` — Nouvelles opportunités
16. `strategy-prep` — Préparation de stratégies
17. `objective-tracker` — Suivi des objectifs

### Content
18. `linkedin-daily` — Post LinkedIn quotidien
19. `editorial-calendar-weekly` — Calendrier éditorial hebdomadaire
20. `article-ideas` — Idées d’articles
21. `talk-prep` — Préparation des conférences
22. `visual-content-generator` — Proposer des visuels
23. `content-repurposer` — Réutiliser le contenu existant

### SEO
24. `content-audit` — Détecter les contenus à améliorer
25. `optimization-proposer` — Proposer des optimisations
26. `keyword-finder` — Identifier des mots-clés intéressants

### Sport
27. `training-program` — Programme d’entraînement
28. `race-objectives` — Objectifs de course
29. `jump-rope-objectives` — Objectifs corde à sauter
30. `strength-objectives` — Objectifs musculation
31. `progression-tracker` — Suivi de la progression
32. `recovery-planner` — Planification de la récupération

### Nutrition
33. `recipe-generator` — Recettes adaptées à la sèche
34. `weekly-menus` — Menus complets
35. `shopping-list-generator` — Liste de courses
36. `batch-cooking-planner` — Batch cooking
37. `calorie-estimator` — Estimation calories/protéines

### Formation
38. `talk-prep` — Préparer les talks
39. `slide-creator` — Créer des slides
40. `exercise-generator` — Générer des exercices
41. `demo-prep` — Préparer des démonstrations
42. `quiz-creator` — Créer des quiz

### Carrière
43. `opportunity-analyzer` — Analyser les nouvelles opportunités
44. `interview-prep` — Préparer les entretiens
45. `cv-enhancer` — Améliorer le CV
46. `linkedin-optimizer` — Améliorer LinkedIn
47. `career-objectives` — Suivre les objectifs professionnels

### Vie personnelle
48. `weekly-review` — Revue hebdomadaire
49. `habit-tracker` — Suivi des habitudes
50. `personal-objectives` — Suivi des objectifs
51. `finance-tracker` — Suivi des finances
52. `smart-reminders` — Rappels intelligents

## ROUTINES COMPLÈTES

### Quotidiennes
- 08:00 — Daily Brief
- 12:00 — Check-point mi-journée
- 19:00 — Check-out + plan lendemain

### Hebdomadaires
- Lundi 09:00 — Weekly Review
- Lundi 10:00 — Content Pipeline
- Lundi 11:00 — SEO Audit
- Mardi 10:00 — Business Intel
- Mercredi 10:00 — Fitness Weekly
- Jeudi 10:00 — Nutrition Weekly
- Vendredi 16:00 — Friday Retrospective

### Mensuelles
- 1er du mois — Monthly Business Review
- 15 du mois — Architecture Review
- Fin du mois — Personal Finance Review

## ORDRE D’EXÉCUTION RECOMMANDÉ

1. **Semaine 1** : P0 — Daily Brief + PR Review + TODO Scan
2. **Semaine 2** : P0 — Debt Scan + Dependency Scan
3. **Semaine 3-4** : P1 — Weekly Review + Content Pipeline
4. **Mois 2** : P1 — SEO Audit + Business Intel
5. **Mois 2-3** : P2 — Nutrition + Fitness + Formation
6. **Mois 3** : P3 — Anticipation + Dashboard + Intégrations avancées
