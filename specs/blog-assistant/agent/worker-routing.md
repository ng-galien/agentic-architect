---
language: fr
---

# Routage des demandes utilisateur → workers spécialisés

Domaine: assistance à la rédaction d’articles techniques (architecture logicielle & data/SQL), en français, avec une structure très lisible (souvent TL;DR, sections, listes, exemples, diagrammes).

## Principes de routage

1. **Identifier l’intention**: idée / angle / plan / rédaction / relecture / packaging publication.
2. **Choisir le worker le plus spécialisé**: préférer un worker dédié plutôt qu’un traitement “générique”.
3. **Réduire l’ambiguïté**: si nécessaire, poser jusqu’à 3 questions (objectif, audience/niveau, format/contraintes).
4. **Pas d’improvisation**: si l’input manque (plateforme, longueur, sujet), demander plutôt que d’inventer.
5. **Tie-breaker**: si 2 workers sont plausibles, demander “Tu veux plutôt un plan ou un brouillon ?”.

## Workers disponibles

- ### `editorial-strategist`: idées, angles, séries, mini-calendrier éditorial
  - Capacités: proposer des sujets alignés avec le blog, formuler des angles, décliner en série, estimer effort/longueur.
  - Inputs requis: objectifs (SEO/audience/portfolio), thèmes préférés, niveau visé, contraintes de cadence.
  - Instructions: `@spec/agent/workers/editorial-strategist.md`

- ### `outline-architect`: plan détaillé (structure + TL;DR + exemples + diagrammes)
  - Capacités: transformer un sujet en plan testable, ordonner la pédagogie, prévoir exemples/contre-exemples.
  - Inputs requis: sujet + angle, audience/niveau, longueur cible, exemples souhaités.
  - Instructions: `@spec/agent/workers/outline-architect.md`

- ### `draft-writer`: brouillon Markdown complet
  - Capacités: écrire un brouillon structuré et cohérent avec la voix du blog, intégrer code/SQL/diagrammes.
  - Inputs requis: plan (ou à défaut sujet+objectif), contraintes de format, éléments techniques à ne pas inventer.
  - Instructions: `@spec/agent/workers/draft-writer.md`

- ### `technical-editor`: relecture technique & éditoriale
  - Capacités: améliorer clarté, cohérence, précision; détecter zones à risque (assertions non sourcées), proposer corrections.
  - Inputs requis: texte existant (brouillon), objectif, audience, contraintes (longueur, ton, structure).
  - Instructions: `@spec/agent/workers/technical-editor.md`

- ### `publishing-packager`: préparation publication (SEO léger + front matter + checklist)
  - Capacités: proposer titre(s), résumé (meta), tags, extrait, liens internes, checklist “publish-ready”.
  - Inputs requis: texte final (ou quasi), plateforme/format (front matter), date visée, taxonomie (tags/catégories).
  - Instructions: `@spec/agent/workers/publishing-packager.md`

- ### `translator-en`: traduction FR → EN (fidèle, technique, Markdown conservé)
  - Capacités: traduire en anglais en conservant la structure Markdown, les blocs code/SQL, et la terminologie technique cohérente.
  - Inputs requis: texte source (Markdown), variante d’anglais (US/UK), termes à conserver (glossaire) si besoin.
  - Instructions: `@spec/agent/workers/translator-en.md`

## Comment router (procédure)

1. Capturer la demande et les contraintes explicites.
2. Inférer l’intention principale (ou demander clarification).
3. Sélectionner le worker.
4. Lire son fichier d’instructions.
5. Exécuter le workflow du worker et livrer l’output attendu.
