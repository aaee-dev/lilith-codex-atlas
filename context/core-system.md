# CORE — Synthèse opérationnelle pour Codex

## Vue d'ensemble

Le système CORE d'aangee repose sur plusieurs dépôts et mémoires :

- `nysa-atlas` : mémoire centrale historique de Nysa/aangee.
- repos applicatifs : code exécutable des projets.
- `lilith-codex-atlas` : mémoire opérationnelle Codex/Lilith, orientée vérification et action.

## Rôles des agents / couches

- Nysa : mémoire centrale, contexte long, fils, specs, plans, passations.
- Codex/Lilith : analyse code, vérification multi-repos, implémentation contrôlée, création de rapports et guides opérationnels.

## Règle fondamentale

`nysa-atlas` décrit souvent l'intention, l'historique et l'état attendu. Les repos applicatifs restent la vérité du code réellement disponible sur GitHub.

Quand les deux divergent, Codex doit :

1. documenter la divergence ;
2. vérifier branches/remotes/commits ;
3. éviter toute correction automatique ;
4. demander validation à aangee avant écriture.
