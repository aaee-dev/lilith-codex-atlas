# Rapport — Assimilation initiale Codex/Lilith

Date : 2026-06-30

## Objectif

Créer une première mémoire opérationnelle pour Codex/Lilith dans `aaee-dev/lilith-codex-atlas`, inspirée du fonctionnement de `nysa-atlas` mais plus courte et orientée action.

## Ce qui a été fait

- Remote local configuré vers `https://github.com/aaee-dev/lilith-codex-atlas.git`.
- Tentative de fetch du remote : échec faute d'authentification GitHub.
- Re-clonage public de `camping-viewer` : OK.
- Re-clonage public de `camping-technician` : OK.
- Re-clonage de `nysa-atlas` : bloqué sans token.
- Re-clonage de `camping-admin` : bloqué sans token.
- Création d'une structure mémoire Codex : `context/`, `memory/`, `guides/`, `reports/`.

## Découverte importante

Le clone public actuel de `camping-technician` contient bien la partie 3D qui manquait dans l'analyse précédente :

- `src/components/PlanView3D.jsx`
- `src/lib/scene3dLoader.js`
- dépendance `three`
- intégration dans `src/App.jsx`

Cela indique que l'analyse précédente était basée sur un état plus ancien du repo, ou que le repo a été mis à jour entre-temps.

## Limites

Les repos privés n'ont pas pu être actualisés sans token. L'état de `camping-admin` et `nysa-atlas` doit donc être revalidé plus tard.

## Amélioration apportée au système

La principale amélioration est la séparation claire entre :

- mémoire centrale longue (`nysa-atlas`) ;
- vérité du code (repos applicatifs) ;
- mémoire opérationnelle Codex (`lilith-codex-atlas`).

Cette séparation réduit le risque de traiter une note mémoire comme une preuve de code existant.
