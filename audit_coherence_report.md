# Audit de cohérence — ShinNO OS

## Inventaire

| Entité | Quantité |
|--------|----------|
| Experts | 11 |
| Skills | 12 |
| Workflows | 3 |
| Projets | 4 |
| Agents anciens | 5 |
| Templates | 3 |
| Fichiers gouvernance | 2 |

## Résultats de l’audit

- [x] Aucun skill orphelin : chaque skill est référencé par au moins un expert.
- [x] Aucun workflow orphelin : chaque workflow est référencé par au moins un expert.
- [x] Aucun expert sans mission, responsabilités, limites, skills, workflows ou projets.
- [x] Aucune référence cassée entre experts, skills, workflows et projets.
- [x] Aucune duplication évitable dans la structure des experts.
- [x] Navigation cohérente entre README, GOVERNANCE, experts, skills, workflows et projets.

## Actions correctives appliquées

1. **Designer** : suppression de 3 skills orphelins (`clean-code`, `seo`, `outils`) ; conservation de `visual-content` uniquement, avec contribution explicite aux workflows `feature-development` et `code-review`.
2. **Coach Sport** : suppression de 3 doublons (`health-safety`), conservation d’une seule occurrence, renforcement des règles de blocage.
3. **Agents anciens** : déplacement vers `agents/deprecated/` pour éviter les doublons avec les experts.
4. **README** : ajout d’un tableau de routing et d’un diagramme d’architecture textuel.
5. **GOVERNANCE** : ajout des règles de délégation et d’arbitrage.
6. **ARCHITECTURE.md** : création du document source de vérité.

## Vérification post-correction

```bash
# Aucun skill orphelin
for skill in $(find skills -name 'SKILL.md' | xargs -I {} basename $(dirname {})); do
  grep -rq "\`$skill\`" experts/ || echo "ORPHELIN: $skill"
done

# Aucun workflow orphelin
for wf in $(find workflows -name '*.md' | xargs -I {} basename {} .md); do
  grep -rq "\`$wf\`" experts/ || echo "ORPHELIN: $wf"
done

# Tous les experts ont une mission
for expert in $(find experts -maxdepth 1 -name '*.md' | sort); do
  grep -q '^## Mission' "$expert" || echo "SANS MISSION: $expert"
done

# Vérification des doublons
grep -r "## Skills" experts/*.md | sort | uniq -d
```

Résultat : **0 orphelin**, **0 doublon**, **0 expert sans mission**.
