# Source of truth — règle Codex

## Règle courte

- Mémoire (`nysa-atlas`) = intention, historique, décisions, contexte.
- Code GitHub = vérité exécutable.
- `lilith-codex-atlas` = synthèse opérationnelle et garde-fous.

## En cas de divergence

Si `nysa-atlas` affirme qu'une feature existe mais que le repo applicatif ne la contient pas :

1. ne pas conclure immédiatement que la mémoire est fausse ;
2. vérifier le repo, la branche, le dernier commit et les remotes ;
3. vérifier si un push a été oublié ;
4. vérifier si le clone est shallow ou ancien ;
5. documenter l'écart dans `memory/known-gaps.md` ou un rapport ;
6. demander validation avant correction.

## Secret / token

Ne jamais afficher un token. Pour tester l'environnement, afficher uniquement `[set]` ou `[missing/empty]`.
