# Guide — Avant d'écrire du code dans un repo applicatif

Checklist obligatoire :

1. Confirmer le repo cible.
2. Lire tous les `AGENTS.md` applicables.
3. Lire le `CLAUDE.md` du repo si présent.
4. Vérifier branche, remote, HEAD :

```bash
git status --short --branch
git remote -v
git show -s --format='%h %cI %s' HEAD
```

5. Pull `--ff-only` si possible.
6. Comparer avec `nysa-atlas` si la tâche dépend d'une spec ou d'un fil.
7. Écrire un plan court.
8. Attendre validation explicite si la tâche n'est pas clairement une implémentation demandée.
9. Après modification : tests, commit, PR.
