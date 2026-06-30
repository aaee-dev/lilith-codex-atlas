# lilith-codex-atlas

Mémoire opérationnelle Codex/Lilith pour le système CORE d'aangee.

Ce dépôt ne remplace pas `nysa-atlas`. Il sert de couche courte, actionnable et orientée exécution pour Codex : reprendre le contexte, vérifier les repos, repérer les divergences entre mémoire et code, puis travailler sans casser les workflows multi-repos.

## Rôle

- `AGENTS.md` — règles racine pour Codex/Lilith dans ce dépôt.
- `context/` — cartes stables du système CORE et des repos.
- `memory/` — état courant, décisions et écarts connus.
- `guides/` — procédures réutilisables avant analyse ou écriture.
- `reports/` — rapports datés d'assimilation et d'audit.

## Principe source-of-truth

- `nysa-atlas` = mémoire centrale historique, intentions, fils, specs et contexte humain.
- Repos applicatifs = vérité du code exécutable.
- `lilith-codex-atlas` = mémoire opérationnelle Codex, avec synthèse et checklists.

En cas de divergence entre `nysa-atlas` et un repo applicatif, ne pas supposer : signaler l'écart, vérifier les branches/remotes, puis demander validation avant modification.
