# Camping Cottet — Carte opérationnelle

## Architecture logique

La suite Camping Cottet est composée de trois applications principales :

1. `camping-admin` / `app-admin`
   - Studio local React/Vite/Zustand.
   - Source de vérité spatiale.
   - Produit des exports JSON.

2. `camping-viewer` / `app-viewer`
   - PWA publique lecture seule.
   - Consomme `public/data.json`, généré depuis `app-admin`.

3. `camping-technician` / `app-technician`
   - PWA technicien.
   - Consomme Supabase pour zones/interventions/alertes/config.
   - Contient désormais une vue `PlanView3D` et un loader `scene3dLoader.js` dans le clone GitHub public actuel.

## Module scene3d — état observé

D'après les analyses précédentes et le reclonage du repo public `camping-technician` :

- `camping-admin` avait déjà un module `scene3d` partiellement/majoritairement implémenté dans l'analyse précédente : manifest, store `haies/arbres/routes`, `Scene3DEditor.jsx`, `sync_scene3d.mjs`.
- `camping-technician` actuel contient `src/components/PlanView3D.jsx` et `src/lib/scene3dLoader.js`.
- `camping-technician` dépend de `three`.

## Points à revalider dès retour du token

- Pull `nysa-atlas` et `camping-admin`.
- Vérifier si le panneau Propriétés scene3d annoncé dans `nysa-atlas` est maintenant bien présent dans `camping-admin`.
- Vérifier si `public/scene3d.json` est bien produit et/ou présent côté `camping-technician`.
- Vérifier cohérence des conversions d'unités entre `sync_scene3d.mjs`, `Scene3DEditor.jsx`, `scene3dLoader.js` et `PlanView3D.jsx`.
