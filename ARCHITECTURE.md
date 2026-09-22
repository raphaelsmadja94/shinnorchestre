# ARCHITECTURE — ShinNO OS

> Document de référence de l’architecture ShinNO OS.
> Version : 1.0
> Date : 2026-07-23

## 1. Vue d’ensemble

ShinNO OS est un orchestrateur de profils spécialisés pour les projets ShinNO.
Il est composé de :

1. **Mémoire utilisateur** : système de mémoire Hermes, sans profil opérationnel séparé.
2. **ShinNO AI** : point d’entrée unique. Il analyse la demande, route vers le ou les experts, charge les skills, sélectionne le workflow, fusionne les réponses et fournit une réponse unique.
3. **Experts** : 10 profils métier délégués. Chaque expert possède une mission, des responsabilités, des limites, des skills, des workflows et des projets.
4. **Skills** : 12 compétences réutilisables.
5. **Workflows** : 3 procédures d’exécution + 4 workflows métier.
6. **Projets** : 4 contextes projet.
7. **Gouvernance** : règles de délégation, d’arbitrage et de sécurité.

## 2. Architecture schématique

```
┌─────────────────────────────────────────────────────────┐
│                    UTILISATEUR                           │
└───────────────────────────┬─────────────────────────────┘
                            │ message
                            ▼
┌─────────────────────────────────────────────────────────┐
│                  ShinNO AI (router)                      │
│  - Analyse l’intention                                   │
│  - Identifie projet / risque / action / compétences      │
│  - Choisit 1 expert principal + 0-2 contributeurs       │
│  - Charge les skills et workflows                        │
│  - Fusionne les réponses                                 │
│  - Affiche : Profils / Skills / Workflow / Projet        │
└───────┬──────────────┬──────────────┬──────────────┬────┘
        │              │              │              │
        ▼              ▼              ▼              ▼
   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐
   │   CTO   │   │ Tech Lead│   │ Product │   │ Business│
   └─────────┘   └─────────┘   └─────────┘   └─────────┘
        │              │              │              │
        ▼              ▼              ▼              ▼
   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐
   │  Growth │   │Content   │   │Designer │   │ Teacher │
   │         │   │Creator   │   │         │   │         │
   └─────────┘   └─────────┘   └─────────┘   └─────────┘
        │              │              │              │
        ▼              ▼              ▼              ▼
   ┌─────────┐   ┌─────────┐
   │Career   │   │Coach    │
   │Advisor  │   │Sport    │
   └─────────┘   └─────────┘
        │              │
        ▼              ▼
   ┌─────────────────────────┐
   │   Skills / Workflows    │
   │   / Projets             │
   └─────────────────────────┘
```

## 3. Mémoire utilisateur

- **Implémentation** : système Hermes `memory` + `user` profile.
- **Contenu** : préférences, ton, projets en cours, décisions passées.
- **Pas de profil opérationnel séparé** : l’utilisateur n’est pas un expert, c’est la mémoire continue.

## 4. Orchestrateur

- **Fichier** : `experts/router.md`
- **Mission** : analyser, router, charger, sélectionner, fusionner, répondre.
- **Règles** :
  - Basé sur intention, projet, risque, action demandée, compétences nécessaires.
  - Jamais uniquement sur des mots-clés.
  - 1 expert principal + 2 contributeurs maximum.
  - Transparence systématique avant chaque réponse.

### 4.1 Ordre d’arbitrage

1. Sécurité, santé, droit, confidentialité, intégrité des données.
2. Contraintes explicites de l’utilisateur.
3. CTO tranche les décisions techniques structurantes.
4. Product tranche les priorités fonctionnelles.
5. Business tranche les recommandations commerciales.
6. En cas de désaccord significatif : présenter les options et demander une décision humaine.

## 5. Experts

### 5.1 CTO

- **Mission** : garantir la cohérence technique, la sécurité, la dette et la performance.
- **Responsabilités** : valider les choix structurants, arbitrer les agents techniques, définir les standards, refuser ce qui sort du cadre de risque acceptable.
- **Limites** : ne déploie pas sans validation humaine ; ne publie pas ; ne donne pas de recommandations commerciales ou créatives.
- **Skills** : `spring`, `angular`, `php`, `security`, `clean-code`, `architecture`, `devops`, `testing`, `git`, `github`
- **Workflows** : `feature-development`, `bug-fix`, `code-review`, `release`, `rollback`
- **Projets** : `shinno`, `celebraplume`, `formations`, `personal`

### 5.2 Tech Lead

- **Mission** : exécuter et superviser les tâches techniques courantes.
- **Responsabilités** : implémenter, refactoriser, débugger, vérifier les conventions, produire des diffs minimaux, ajouter des tests.
- **Limites** : pas d’architecture structurante sans validation CTO ; pas de déploiement sans validation ; pas de modification de secrets.
- **Skills** : `spring`, `angular`, `php`, `clean-code`, `testing`, `git`, `github`
- **Workflows** : `feature-development`, `bug-fix`, `code-review`
- **Projets** : `shinno`, `celebraplume`

### 5.3 Product

- **Mission** : définir, prioriser et mesurer le produit.
- **Responsabilités** : analyser les besoins métier, traduire les objectifs business en epics/stories, prioriser par valeur utilisateur, définir critères d’acceptation et KPIs.
- **Limites** : ne promet pas de livraison sans validation technique ; ne modifie pas les dépôts applicatifs ; ne publie pas de contenu.
- **Skills** : `seo`, `linkedin`, `content-strategy`, `research-watch`, `source-verification`
- **Workflows** : `feature-development` en amont
- **Projets** : `shinno`, `celebraplume`, `formations`, `personal`

### 5.4 Business

- **Mission** : développer le chiffre d’affaires par la prospection et le suivi commercial.
- **Responsabilités** : cartographier les cibles, qualifier les prospects, construire des séquences d’approche, mesurer la couverture et le pipeline.
- **Limites** : n’envoie rien sans validation humaine ; n’invente pas de coordonnées ; ne rédige pas le contenu éditorial ; ne contacte personne directement.
- **Skills** : `prospecting`, `lead-qualification`, `contact-research`, `gdpr-prospecting`, `crm`, `sales-copywriting`
- **Workflows** : `school-prospecting`, `prospect-follow-up`
- **Projets** : `celebraplume`, `formations`

### 5.5 Growth

- **Mission** : piloter la stratégie d’acquisition, le SEO, les canaux et les opportunités de croissance.
- **Responsabilités** : définir la stratégie d’acquisition, auditer le SEO, proposer des optimisations de canaux, identifier de nouvelles opportunités de croissance.
- **Limites** : ne produit pas les contenus finaux ; ne touche pas au code sans workflow validé ; ne garantit pas de positionnement.
- **Skills** : `seo`, `content-strategy`, `editorial-calendar`, `visual-content`, `research-watch`, `source-verification`
- **Workflows** : `weekly-content-plan`
- **Projets** : `shinno`, `celebraplume`, `formations`

### 5.6 Content Creator

- **Mission** : produire les contenus prêts à valider, alignés à la marque et aux personas.
- **Responsabilités** : rédiger posts, articles, briefs, séquences éditoriales ; proposer des formats ; respecter la charte et le ton.
- **Limites** : ne publie jamais sans validation ; ne touche pas au code ; ne contacte personne ; ne modifie pas les dépôts.
- **Skills** : `copywriting`, `content-strategy`, `editorial-calendar`, `visual-content`, `personal-branding`, `social-media`, `linkedin`
- **Workflows** : `weekly-content-plan`, `linkedin-post`
- **Projets** : tous avec visibilité externe

### 5.7 Designer

- **Mission** : concevoir layouts, chartes et expériences visuelles cohérentes.
- **Responsabilités** : définir tokens, charte, composants visuels, améliorer l’UX sans casser l’existant.
- **Limites** : ne déploie pas sans validation ; ne touche pas à la logique métier ; ne retire pas la sécurité.
- **Skills** : `visual-content`
- **Workflows** : contribue à `feature-development` et `code-review`
- **Projets** : `shinno`, `celebraplume`, `formations`

### 5.8 Teacher

- **Mission** : concevoir et améliorer des parcours pédagogiques clairs.
- **Responsabilités** : définir objectifs pédagogiques, critères de progression, structurer supports de formation, proposer évaluation et suivi apprenant.
- **Limites** : ne modifie pas les dépôts applicatifs sans workflow validé ; ne certifie pas sans validation humaine.
- **Skills** : `training-offer`, `content-strategy`, `seo`
- **Workflows** : contribue à `feature-development` si digitalisation d’une formation
- **Projets** : `formations`

### 5.9 Career Advisor

- **Mission** : conseiller sur la carrière, la négociation et le positionnement professionnel.
- **Responsabilités** : préparer des dossiers de négociation, conseiller sur les parcours, les salaires, les repositionnements, structurer le profil professionnel.
- **Limites** : ne donne pas de conseil juridique contraignant ; ne modifie pas les dépôts ; ne contacte pas les employeurs.
- **Skills** : `personal-branding`, `content-strategy`, `research-watch`
- **Workflows** : aucun dédié
- **Projets** : `personal`

### 5.10 Coach Sport

- **Mission** : accompagner vers une perte de masse grasse progressive et sécurisée.
- **Responsabilités** : construire des plans progressifs, suivre habitudes, analyser tendances, alerter sur les risques.
- **Limites** : ne pose pas de diagnostic médical ; ne modifie pas un traitement ; ne recommande pas de sèche extrême.
- **Skills** : `fitness-coaching`, `fat-loss`, `nutrition-basics`, `strength-training`, `habit-tracking`, `progress-analysis`, `health-safety`
- **Workflows** : `weekly-fitness-review`
- **Projets** : `personal`

## 6. Skills

| Skill | Description | Experts |
|-------|-------------|---------|
| `angular` | Frontend Angular | CTO, Tech Lead |
| `architecture` | Architecture logicielle | CTO |
| `clean-code` | Code propre et maintenable | CTO, Tech Lead |
| `content-strategy` | Stratégie de contenu | Product, Growth, Content Creator, Teacher, Career Advisor |
| `copywriting` | Rédaction persuasive | Content Creator |
| `crm` | Gestion de la relation client | Business |
| `devops` | CI/CD, infrastructure | CTO |
| `editorial-calendar` | Calendrier éditorial | Growth, Content Creator |
| `fat-loss` | Perte de masse grasse | Coach Sport |
| `fitness-coaching` | Coaching sportif | Coach Sport |
| `gdpr-prospecting` | Prospection RGPD-compatible | Business |
| `git` | Gestion de version | CTO, Tech Lead |
| `github` | GitHub et PRs | CTO, Tech Lead |
| `habit-tracking` | Suivi des habitudes | Coach Sport |
| `health-safety` | Sécurité santé/sport | Coach Sport |
| `lead-qualification` | Qualification de prospects | Business |
| `linkedin` | LinkedIn et personal branding | Product, Content Creator |
| `nutrition-basics` | Nutrition fondamentale | Coach Sport |
| `personal-branding` | Branding personnel | Content Creator, Career Advisor |
| `php` | Développement PHP | CTO, Tech Lead |
| `progress-analysis` | Analyse de progression | Coach Sport |
| `prospecting` | Prospection commerciale | Business |
| `research-watch` | Veille et recherche | Product, Growth, Career Advisor |
| `sales-copywriting` | Copywriting commercial | Business |
| `school-prospecting` | Prospection scolaire | Business |
| `security` | Sécurité applicative | CTO |
| `seo` | SEO et visibilité | CTO, Product, Growth, Content Creator, Designer, Teacher |
| `social-media` | Réseaux sociaux | Content Creator |
| `source-verification` | Vérification des sources | Product, Growth |
| `spring` | Spring Boot | CTO, Tech Lead |
| `strength-training` | Renforcement musculaire | Coach Sport |
| `testing` | Tests automatisés | CTO, Tech Lead |
| `training-offer` | Offre de formation | Teacher |
| `visual-content` | Contenu visuel | Growth, Content Creator, Designer |
| `weekly-fitness-review` | Revue hebdomadaire fitness | Coach Sport |
| `weekly-content-plan` | Planification éditoriale | Growth, Content Creator |
| `linkedin-post` | Publication LinkedIn | Content Creator |
| `contact-research` | Recherche de contacts | Business |
| `prospect-follow-up` | Suivi de prospects | Business |
| `feature-development` | Développement de fonctionnalité | CTO, Tech Lead, Product, Designer, Teacher |
| `bug-fix` | Correction de bug | CTO, Tech Lead |
| `code-review` | Revue de code | CTO, Tech Lead, Designer |
| `release` | Mise en production | CTO |
| `rollback` | Retour arrière | CTO |

## 7. Workflows

| Workflow | Déclencheur | Experts impliqués |
|----------|-------------|-------------------|
| `feature-development` | Nouvelle fonctionnalité | CTO, Tech Lead, Product, Designer, Teacher |
| `bug-fix` | Bug ou anomalie | CTO, Tech Lead |
| `code-review` | Revue de code | CTO, Tech Lead, Designer |
| `release` | Mise en production | CTO |
| `rollback` | Retour arrière | CTO |
| `weekly-content-plan` | Planification éditoriale | Growth, Content Creator |
| `linkedin-post` | Publication LinkedIn | Content Creator |
| `school-prospecting` | Prospection scolaire | Business |
| `prospect-follow-up` | Suivi de prospects | Business |
| `weekly-fitness-review` | Revue hebdomadaire fitness | Coach Sport |

## 8. Projets

| Projet | Description | Experts principaux |
|--------|-------------|-------------------|
| `shinno` | Plateforme ShinNO SaaS | CTO, Tech Lead, Product, Growth, Designer |
| `celebraplume` | Projet CelebraPlume | Business, Product, Growth, Content Creator, CTO, Tech Lead |
| `formations` | Formations et pédagogie | Teacher, Product, Content Creator, Designer, Business |
| `personal` | Projets personnels | Coach Sport, Career Advisor, Content Creator |

## 9. Gouvernance

- **Niveau 1** : autonome (lecture, modifications locales, tests, docs, branches, PRs).
- **Niveau 2** : validation obligatoire (architecture, migration DB, sécurité, dépendances, infrastructure).
- **Niveau 3** : interdit sans ordre CTO (merge, déploiement, suppression de données, sudo, email, réseaux sociaux, paiement).
- **Délégation** : 1 expert principal + 2 contributeurs max.
- **Arbitrage** : sécurité/santé/droit > contraintes utilisateur > CTO > Product > Business.

## 10. Routing

### 10.1 Critères

- Intention
- Projet
- Niveau de risque
- Action demandée
- Compétences nécessaires

### 10.2 Exemples

| Demande | Expert principal | Contributeurs | Skills | Workflow |
|---------|------------------|---------------|--------|----------|
| Corriger un bug Spring | Tech Lead | CTO | spring, testing, clean-code, security | bug-fix |
| 10 idées posts LinkedIn | Content Creator | Growth, SEO | copywriting, content-strategy, linkedin | weekly-content-plan |
| Préparer formation Spring AI | Teacher | CTO, Content Creator | training-offer, content-strategy, seo | feature-development |
| Développer CelebraPlume | Business | Product, SEO | prospecting, seo, content-strategy | school-prospecting |
| Perdre du poids | Coach Sport | Aucun | fitness-coaching, fat-loss, health-safety | weekly-fitness-review |
| Négociation salariale | Career Advisor | Business | personal-branding, research-watch | — |

## 11. Structure du répertoire

```
shinno-os/
├── ARCHITECTURE.md          ← document de référence
├── AGENTS.md                ← agents généraux
├── GOVERNANCE.md            ← règles de gouvernance
├── README.md                ← démarrage rapide
├── audit_coherence_report.md ← audit de cohérence
├── agents/
│   └── deprecated/          ← agents anciens archivés
├── experts/
│   ├── router.md            ← ShinNO AI orchestrateur
│   ├── cto.md
│   ├── tech-lead.md
│   ├── product.md
│   ├── business.md
│   ├── growth.md
│   ├── content-creator.md
│   ├── designer.md
│   ├── teacher.md
│   ├── career-advisor.md
│   └── coach-sport.md
├── skills/
│   ├── angular/SKILL.md
│   ├── architecture/SKILL.md
│   ├── clean-code/SKILL.md
│   ├── content-strategy/...
│   ├── copywriting/...
│   ├── crm/...
│   ├── devops/SKILL.md
│   ├── editorial-calendar/...
│   ├── fat-loss/...
│   ├── fitness-coaching/...
│   ├── gdpr-prospecting/...
│   ├── git/SKILL.md
│   ├── github/SKILL.md
│   ├── habit-tracking/...
│   ├── health-safety/...
│   ├── lead-qualification/...
│   ├── linkedin/SKILL.md
│   ├── nutrition-basics/...
│   ├── personal-branding/...
│   ├── php/SKILL.md
│   ├── progress-analysis/...
│   ├── prospecting/...
│   ├── research-watch/...
│   ├── sales-copywriting/...
│   ├── school-prospecting/...
│   ├── security/SKILL.md
│   ├── seo/SKILL.md
│   ├── social-media/...
│   ├── source-verification/...
│   ├── spring/SKILL.md
│   ├── strength-training/...
│   ├── testing/SKILL.md
│   ├── training-offer/...
│   ├── visual-content/...
│   ├── weekly-fitness-review/...
│   ├── weekly-content-plan/...
│   ├── linkedin-post/...
│   ├── contact-research/...
│   ├── prospect-follow-up/...
│   ├── feature-development/...
│   ├── bug-fix/...
│   ├── code-review/...
│   ├── release/...
│   └── rollback/...
├── workflows/
│   ├── bug-fix.md
│   ├── code-review.md
│   ├── feature-development.md
│   ├── school-prospecting.md
│   ├── prospect-follow-up.md
│   ├── weekly-content-plan.md
│   ├── linkedin-post.md
│   └── weekly-fitness-review.md
├── projects/
│   ├── shinno/PROJECT.md
│   ├── celebraplume/PROJECT.md
│   ├── formations/PROJECT.md
│   └── personal/PROJECT.md
└── templates/
    ├── cto-report.md
    ├── pull-request.md
    └── technical-task.md
```

## 12. Maintenance

- Toute modification d’un expert doit être tracée dans une PR.
- Tout nouveau skill doit être référencé par au moins un expert.
- Tout nouveau workflow doit être référencé par au moins un expert.
- L’audit de cohérence doit être relancé après chaque modification structurelle.
 
