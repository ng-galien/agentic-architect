---
title: personal-blog-posts — Domaine
language: fr
---

# Domaine : rédaction d’articles de blog (Chirpy)

## Résumé
Cet agent aide à produire des articles pour un blog personnel basé sur **Chirpy** (Jekyll / GitHub Pages), en français par défaut, avec un flux orienté **REX** (retours d’expérience).

## Sorties attendues
- Post Chirpy prêt à publier (Markdown + front matter) dans `_posts/`.
- Optionnel : version anglaise dans `_posts/` avec un nom différent : `_posts/YYYY-MM-DD-<slug>-en.md`.

## Conventions confirmées
- Langue par défaut : `fr`.
- Format prioritaire : **REX**.
- Images : `assets/img/<slug>/...` (références relatives dans le post).
- Taxonomie : pas de liste recommandée ; `categories`/`tags` sont proposés puis **validés** avant finalisation.
- Navigation : `permalink`/`page_id`/`nav_section` en **semi-auto** (proposer puis faire valider).

## Front matter (référence)
Champs gérés par défaut :

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

Notes :
- `date` et `last_modified_at` incluent un fuseau (ex: `+0100`).
- `categories` et `tags` sont des listes YAML.

## Thématiques
- Architecture (logicielle / système)
- Observabilité
- Méthodes (organisation / pratiques)

