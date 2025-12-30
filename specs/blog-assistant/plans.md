# Plan pour le superviseur `blog-assistant`

Ce document sert de suivi (checklists) pour spécifier puis compiler un agent “superviseur + workers” qui aide à produire des articles pour le blog.

## Définition du domaine [ IN PROGRESS ]
- [x] done — Identifier le périmètre: aide à l’écriture d’articles techniques (architecture, data/SQL, DDD, event-driven, agents IA) en français.
- [x] done — Identifier les artefacts attendus: idée → angle → plan → brouillon → relecture → package de publication.
- [x] done — Clarifier la plateforme exacte: Jekyll + thème Chirpy (GitHub Pages).
- [ ] to do — Clarifier le format exact des posts (Markdown + front matter) et les conventions (champs requis, slug, conventions de catégories/tags).
- [ ] to do — Clarifier le niveau de “recherche externe” autorisé (sources obligatoires ? uniquement expérience perso ?).

## Ton, style et structure [ IN PROGRESS ]
- [x] done — Constat: style pédagogique, pragmatique, structuré (souvent avec une section “TL;DR”), listes, schémas/diagrammes, exemples.
- [ ] to do — Confirmer les invariants de structure (sections fixes ? longueur cible ? présence systématique de “Références”/“À retenir” ?).
- [ ] to do — Définir une “charte de voix” testable (phrases courtes/longues, registre, tutoiement/vouvoiement, niveau de nuance).

## Workers (spécification) [ TODO ]
## Workers (spécification) [ SPECIFIED ]
- [x] done — Définir `editorial-strategist` (idées, angles, série, calendrier, cohérence avec le blog).
- [x] done — Définir `outline-architect` (plan détaillé + TL;DR + déroulé pédagogique + points d’attention).
- [x] done — Définir `draft-writer` (brouillon Markdown complet: intro, sections, exemples, diagrammes, transitions).
- [x] done — Définir `technical-editor` (relecture: clarté, cohérence, précision, contre-exemples, risques, limites).
- [x] done — Définir `publishing-packager` (titre, meta description, tags, excerpt, CTA, liens internes, checklist publication).
- [x] done — Définir `translator-en` (traduction FR → EN, conservation du Markdown/tech, cohérence terminologique).

## Routing (superviseur → workers) [ SPECIFIED ]
- [x] done — Définir les signaux d’intention (ex: “donne-moi des idées”, “fais un plan”, “rédige”, “améliore”, “optimise SEO”).
- [x] done — Définir les questions de cadrage minimales (max 3) avant routage quand c’est ambigu.
- [x] done — Définir un fallback quand l’input est insuffisant (demander format/objectif/public plutôt que d’improviser).

## Politique de validation (Definition of Done) [ TODO ]
- [ ] to do — Checklist qualité de contenu (structure, progression, exemples, exactitude, cohérence).
- [ ] to do — Checklist “non-hallucination” (pas de sources inventées; marquer l’incertitude; demander des références).
- [ ] to do — Checklist “publish-ready” (front matter, tags, titre, résumé, liens internes, relecture orthographe).

## Compilation (templates → agent) [ SPECIFIED ]
- [x] done — Générer `specs/blog-assistant/agent/supervisor.md` depuis `templates/supervisor-template.md`.
- [x] done — Générer `specs/blog-assistant/agent/worker-routing.md` depuis `templates/worker-routing.template.md`.
- [x] done — Générer `specs/blog-assistant/agent/workers/*.md` depuis `templates/worker-spec.template.md`.

## Questions ouvertes [ TO CLARIFY ]
- [ ] to do — Quel est l’objectif principal du blog en 2026 (audience, SEO, portfolio, leads, notes personnelles) ?
- [ ] to do — Quelle cadence visée (ex: 2/mois) et quelle longueur moyenne (ex: 5–10 min de lecture) ?
- [ ] to do — Quel niveau de détails “code” (snippets, repo complet, benchs) et quelle exigence de reproductibilité ?
