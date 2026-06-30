# Repos connus

| Repo | Organisation / owner | Rôle | Accès observé | Notes |
|---|---|---|---|---|
| `lilith-codex-atlas` | `aaee-dev` | Mémoire opérationnelle Codex/Lilith | remote configuré localement, fetch bloqué sans auth | Ce dépôt |
| `nysa-atlas` | `aangee` | Mémoire centrale Nysa/aangee | privé, nécessite token | Source contexte/fils/specs |
| `camping-admin` | `aangee` | Studio admin local, source de vérité spatiale | privé, nécessite token | Produit exports `viewer`, `technique`, `scene3d` |
| `camping-viewer` | `aangee` | PWA publique lecture seule du plan | cloné publiquement | Consomme `public/data.json` |
| `camping-technician` | `aangee` | PWA technicien Supabase + vue 3D | cloné publiquement | Consomme Supabase + `public/scene3d.json` si présent |

## État d'accès au 2026-06-30

- Les repos publics `camping-viewer` et `camping-technician` ont été clonés avec succès sans token.
- Les repos privés `nysa-atlas` et `camping-admin` ne peuvent pas être reclonés/pull dans cette session sans token.
- Des analyses antérieures de `nysa-atlas` et `camping-admin` existent dans le transcript, mais doivent être revalidées après réactivation d'un token.
