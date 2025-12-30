---
title: Plan — Supervisor personal-blog-posts (spécification)
language: fr
---

# Plan pour le superviseur `personal-blog-posts`

Ce document suit la **phase 1 — Spécification** (ne pas compiler tant que les sections marquées *TO CLARIFY* ne sont pas levées).

## Workflow definition

### Étapes du workflow (cible)

1) **Cadrage** (intention, audience, langue, format, contraintes Chirpy)
- [x] Définir les formats d’articles supportés — SPECIFIED — REX (prioritaire)
- [x] Fixer la langue de sortie par défaut — SPECIFIED — français
- [x] Définir le “niveau” (débutant/intermédiaire/avancé) — SPECIFIED — variable (à demander à chaque nouveau post)

2) **Idéation & angle**
- [ ] Produire 3 angles + 3 titres + 1 promesse par option — TODO
- [ ] Sélectionner l’option retenue (avec critères) — TODO

3) **Plan détaillé**
- [ ] Générer un plan H2/H3 + liste des assets/snippets — TODO
- [ ] Valider la progression pédagogique (pré-requis → étapes → vérif) — TODO

4) **Rédaction V1**
- [ ] Générer un draft complet Markdown — TODO
- [ ] Intégrer code/commandes avec contexte et résultats attendus — TODO

5) **Conformité Chirpy**
- [x] Générer/valider le front matter Chirpy — SPECIFIED — layout/lang/title/description/date/last_modified_at/author/categories/tags/permalink/page_id/nav_section/toc/mermaid
- [x] Valider conventions de fichiers/chemins d’assets — SPECIFIED — images sous `assets/img/<slug>/...` + références relatives

6) **Révision & QA**
- [ ] Améliorer clarté, cohérence, style, et orthographe — TODO
- [ ] Vérifier liens, commandes, snippets (cohérence) — TODO
- [ ] SEO léger (titres, intro, mots-clés naturels) — TODO

7) **Export**
- [x] Sortir un fichier prêt à commit (nom + emplacement) — SPECIFIED — écriture directe dans le répertoire courant (workspace)
- [ ] Fournir une checklist publication — TODO

## Workers attributions

Tu veux **3 workers** :

### Worker `draft-and-ideas`
- [ ] Rôle: générer des idées + angles + titres, puis un **draft REX** (plan + V1) — IN PROGRESS
- [ ] Entrées: thématique, intention, audience, niveau (demandé à chaque post), contraintes — TODO
- [ ] Sorties: 3 propositions (angle/titre/promise) + recommandation + outline H2/H3 + draft Markdown — TODO
- [ ] Validation: REX complet (contexte → faits → décisions → apprentissages) + cohérence technique — TODO

### Worker `write-and-publish`
- [ ] Rôle: transformer le draft en post **prêt à publier** (Chirpy) — IN PROGRESS
- [ ] Entrées: draft, date, slug, règles nav semi-auto — TODO
- [ ] Sorties: fichier `_posts/YYYY-MM-DD-slug.md` + front matter complet + propositions `permalink/page_id/nav_section` (validation requise) + images sous `assets/img/<slug>/...` — TODO
- [ ] Validation: conformité front matter + validation explicite pour valeurs proposées (nav + tags/catégories) — TODO

### Worker `translate-to-en`
- [ ] Rôle: traduire un post FR en **anglais** en gardant le sens et le Markdown — IN PROGRESS
- [ ] Entrées: post FR (Markdown) + consignes (glossaire, termes à conserver) — TODO
- [x] Sorties: **2e fichier** `_posts/YYYY-MM-DD-<slug>-en.md` (version EN, `lang: en`, nom différent du FR) — SPECIFIED
- [ ] Validation: fidélité + terminologie cohérente + structure intacte — TODO

## Worker workspace

### Structure (cible)

```text
@workspace/
├── (répertoire courant)       # workspace racine (écriture directe)
│   ├── _posts/                # après compilation
│   ├── _drafts/               # optionnel
│   ├── assets/                # images / ressources (si utilisé)
│   └── _config.yml            # si présent
└── references/                # optionnel: guides internes
    ├── style-guide.md
    └── taxonomy.md
```

### Tools (à confirmer selon ton setup)

**Tools**:
- Lecture/écriture fichiers: produire `*.md`, relire des posts existants
- Recherche dépôt: retrouver conventions, tags/catégories, exemples
- Validation simple: vérifier front matter YAML et nommage de fichier

## Checklist de complétude de la spécification

- [x] Langue par défaut des posts décidée — SPECIFIED — français
- [x] Thématiques principales listées (3–7) — SPECIFIED — archi, observabilité, méthodes
- [x] Workspace confirmé (répertoire courant) — SPECIFIED
- [ ] Conventions Chirpy du repo confirmées (front matter, taxonomie, images, navigation) — IN PROGRESS
- [x] Workers finalisés (liste + responsabilités) — SPECIFIED — 3 workers
- [ ] Scénarios couverts (nouvel article / amélioration / traduction) — TODO
