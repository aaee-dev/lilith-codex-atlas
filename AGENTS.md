# AGENTS.md — lilith-codex-atlas

## Rôle du dépôt

Ce dépôt est la mémoire opérationnelle de Codex/Lilith pour travailler sur le système CORE d'aangee.

Il contient des synthèses, procédures et rapports d'analyse. Il ne doit pas devenir une copie complète de `nysa-atlas`.

## Règles de travail

- Répondre en français.
- Ne jamais afficher de token, clé API ou secret.
- Avant toute modification dans un repo applicatif : lire le `AGENTS.md` et/ou `CLAUDE.md` du repo cible.
- Ne pas modifier `nysa-atlas` ni les applications (`camping-admin`, `camping-viewer`, `camping-technician`) depuis ce dépôt sans validation explicite d'aangee.
- Les fichiers `memory/` doivent rester synthétiques et actionnables.
- Les détails longs d'audit vont dans `reports/`.
- Si une information provient de mémoire/contexte mais n'est pas vérifiée dans le code, la marquer comme hypothèse.

## Workflow recommandé

1. Lire `memory/current-state.md`.
2. Lire `context/repos.md`.
3. Suivre `guides/start-session.md`.
4. Avant d'écrire du code ailleurs, suivre `guides/before-writing-code.md`.
5. En fin de mission significative, mettre à jour `memory/current-state.md` et ajouter un rapport daté si nécessaire.
