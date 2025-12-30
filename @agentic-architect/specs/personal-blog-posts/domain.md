---
title: Domaine — Rédaction de posts (Chirpy)
language: fr
---

# Contexte

Tu souhaites un agent qui t’aide à rédiger des articles pour ton blog personnel basé sur le thème **Chirpy** (Jekyll / GitHub Pages).
Le résultat attendu est du contenu **prêt à publier** (Markdown + front matter compatible Chirpy), avec une qualité éditoriale constante et un style cohérent.

# Objectifs métier

- Accélérer l’idéation, la structuration et la rédaction des articles.
- Standardiser les formats (front matter, sections, conventions de tags/catégories).
- Améliorer la lisibilité (plans clairs, exemples, code, callouts).
- Réduire les erreurs (orthographe, liens, snippets, cohérence technique).

# Périmètre (ce que l’agent produit)

## Livrables principaux
- Un fichier Markdown d’article au format Chirpy, destiné à être placé dans `_posts/`.
- Optionnel: brouillon/outline, checklist de publication, variantes de titres, extraits/summary.
- Optionnel: version **traduite en anglais** (Markdown).

Décision prise :
- La traduction EN produit un **2e fichier** dans `_posts/` avec `lang: en` et un front matter adapté.
- Le nom du fichier EN **ne doit pas être identique** au fichier FR.
- Convention de nommage EN: même date + suffixe langue — `_posts/YYYY-MM-DD-<slug>-en.md`.

## Formats ciblés (à confirmer)
- Tutoriels techniques (pas-à-pas).
- Retours d’expérience (post-mortem, apprentissages).
- Notes courtes / “tips”.
- Synthèses (livres, talks, veille).

Décision prise :
- Format prioritaire: **Retour d’expérience (REX)**.

# Contraintes et conventions Chirpy (à respecter)

> À confirmer dans ton repo: conventions exactes de front matter et de structure.

- Front matter YAML en tête de fichier (structure confirmée ci-dessous).
- Nom de fichier généralement `YYYY-MM-DD-slug.md` dans `_posts/`.
- Markdown GitHub + extensions (tableaux, code fences, etc.).
- Images: conventions de chemin (souvent `assets/img/...`) et attributs (à confirmer).

## Front matter (confirmé via un exemple)

Champs à gérer (par défaut) :

```yaml
layout: post
lang: fr
title: "..."
description: "..."
date: 2025-11-09 00:00:00 +0100
last_modified_at: 2025-11-09 00:00:00 +0100
author: ab
categories: [Architecture]
tags: [sdd, state-driven design, data modeling, domain-driven design, ddd, sql, architecture]
permalink: /2025/11/09/sdd-manifesto/
page_id: article-sdd-manifesto
nav_section: articles
toc: true
mermaid: true
```

Règles implicites (à confirmer) :
- `date` et `last_modified_at` incluent un fuseau (`+0100`).
- `categories` et `tags` sont des listes YAML.
- `permalink`, `page_id` et `nav_section` suivent une convention interne au site.

Décision prise :
- `permalink`, `page_id`, `nav_section` : **semi-automatique** (l’agent propose des valeurs et demande validation avant de finaliser).

## Taxonomie (catégories / tags)

Décision prise :
- **Sans liste** : pas de taxonomie recommandée. L’agent propose `categories`/`tags` et **demande validation** systématique avant finalisation.

# Qualité attendue

- Ton: clair, direct, pédagogique, orienté “comment faire”.
- Structure: introduction → contexte → étapes → validation → conclusion.
- Code: snippets reproductibles, avec prérequis, commandes, versions si nécessaires.
- Références: liens vers docs officielles quand pertinent (sans surcharger).

Décision prise :
- Niveau technique: **variable selon le sujet** (l’agent demande à chaque nouveau post).

# Processus cible (vision humaine)

1. Définir l’intention de l’article (objectif, audience, niveau).
2. Proposer 3 angles + 3 titres, puis sélectionner.
3. Produire un plan détaillé (H2/H3) + liste des snippets/illustrations nécessaires.
4. Rédiger une V1 complète (Markdown + front matter Chirpy).
5. Réviser (clarté, cohérence, SEO léger, correction orthographique).
6. Vérifier la conformité Chirpy (front matter, chemins, conventions).
7. Exporter le fichier prêt à commit.
8. (Optionnel) Traduire en anglais.

# À CLARIFIER (bloquants pour finaliser la spec)

## Décisions prises

- Langue par défaut des articles: **français**

## Thématiques (confirmées)

- **Architecture** (logicielle / système): patterns, décisions, trade-offs, retours d’expérience
- **Observabilité**: logs, métriques, traces, SLO/SLI, incidents, dashboards, runbooks
- **Méthodes**: organisation personnelle, méthodes de travail, pratiques d’écriture/prise de notes

## Points à clarifier

1. **Repo / workspace**: écriture directe dans le **répertoire courant** (workspace). La structure Chirpy (`_posts/`, assets, config, etc.) sera mise en place après compilation du superviseur.
2. **Taxonomie**: sans liste recommandée (validation systématique confirmée).
3. **Conventions de navigation**: règles de génération de `permalink`, `page_id`, et valeurs possibles de `nav_section` (mode semi-auto confirmé, il reste la convention exacte).
4. **Conventions images/assets**: **confirmé** — `assets/img/<slug>/...` (références relatives dans le post).
5. **Niveau d’exigence**: longueur moyenne et présence systématique d’exemples (le niveau technique est variable et sera demandé).
