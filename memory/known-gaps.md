# Écarts et risques connus

## 1. Auth GitHub non résolue

Le secret GitHub n'était pas disponible dans l'environnement sous `GITHUB_TOKEN`, `GitHub`, `GH_TOKEN` ou variantes testées précédemment. Les opérations sur repos privés échouent sans token.

Impact : impossible de pull `nysa-atlas`, `camping-admin` et ce dépôt si privé.

## 2. Risque de divergence mémoire/code

`nysa-atlas` peut être plus récent que certains clones, ou inversement. Toujours vérifier HEAD/branche avant analyse.

## 3. `camping-admin` à revalider

L'analyse précédente a détecté un possible écart : le panneau Propriétés scene3d était annoncé comme livré dans `nysa-atlas`, mais absent du clone `camping-admin` disponible alors. Ce point doit être revalidé avec un pull authentifié.

## 4. Unités scene3d à auditer

Conversions à vérifier de bout en bout :

- SVG px dans `camping-admin` ;
- bake métrique dans `sync_scene3d.mjs` ;
- conversion vers unités `PlanView3D` dans `scene3dLoader.js` ;
- largeur route / hauteur haie / largeur haie.

## 5. Export disque app-admin

À revalider : `VITE_DEV_WRITE_TOKEN` est nécessaire au endpoint `/api/write-json` côté Vite. Si non documenté/configuré, les exports peuvent échouer silencieusement.
