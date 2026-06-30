# État courant — 2026-06-30

## Décision

Le dépôt `aaee-dev/lilith-codex-atlas` devient la mémoire opérationnelle Codex/Lilith pour le système CORE.

## Remote local

Le remote local `origin` a été configuré vers :

```text
https://github.com/aaee-dev/lilith-codex-atlas.git
```

Le fetch a échoué faute d'authentification GitHub disponible dans la session.

## Accès repos

- `camping-viewer` : clonage public OK, HEAD observé `7284644`.
- `camping-technician` : clonage public OK, HEAD observé `e137ffb`.
- `nysa-atlas` : reclonage impossible sans token.
- `camping-admin` : reclonage impossible sans token.

## Observation importante

Le reclonage actuel de `camping-technician` montre que la vue 3D est maintenant présente :

- `src/components/PlanView3D.jsx`
- `src/lib/scene3dLoader.js`
- dépendance `three`

Cela corrige l'analyse précédente qui était basée sur un clone plus ancien de `camping-technician`.

## Prochaine action recommandée

Quand un token GitHub fonctionnel est à nouveau disponible :

1. pull `nysa-atlas` ;
2. pull `camping-admin` ;
3. vérifier le panneau Propriétés scene3d dans `camping-admin` ;
4. vérifier les branches et commits récents ;
5. mettre à jour ce fichier.
