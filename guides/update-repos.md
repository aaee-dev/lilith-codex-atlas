# Guide — Mettre à jour les repos

## Vérification token

Ne jamais afficher le token. Utiliser uniquement :

```bash
python3 - <<'PY'
import os
for name in ['GITHUB_TOKEN','GitHub','GH_TOKEN']:
    print(f'{name}=' + ('[set]' if os.environ.get(name) else '[missing/empty]'))
PY
```

## Pull standard

```bash
git status --short --branch
git pull --ff-only
```

## Si repo privé bloqué

- Ne pas insister en clair avec le token dans la ligne de commande.
- Demander à aangee de réactiver un secret ou fournir une méthode temporaire.
- Documenter le blocage dans `memory/current-state.md`.
