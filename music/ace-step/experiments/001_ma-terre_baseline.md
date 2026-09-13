# EXP-001 — Ma terre — baseline et premières variantes

## Objectif
Établir une première référence ACE-Step sur un extrait court de « Ma terre », avec une voix féminine uniquement, puis isoler progressivement les variables qui influencent le résultat.

## Contexte matériel / interface observée
- Interface : ACE-Step local via Gradio
- Modèle observé : `acestep-v15-turbo`
- GPU : RTX 4060 Laptop 8 Go
- GPU tier : 3
- LM : `acestep-5Hz-lm-0.6B` avec vLLM
- Offload LM → CPU : activé
- Offload DiT → CPU : activé
- Torch compile : activé
- INT8 : activé
- DiT steps : 8
- Inference method : ODE
- Sampler : Euler
- Shift : 3
- LM temperature : 0,85
- LM CFG : 2
- Top-P : 0,9
- Thinking : activé
- Parallel Thinking : activé

## Protocole initial corrigé
La première tentative sur un morceau plus long et en batch supérieur a montré un temps de génération trop élevé pour une exploration efficace. Le protocole a donc été réduit à :

- extrait court : Verse 1 + Pre-Chorus + Chorus
- batch size : 1
- seed aléatoire pour l'exploration
- paramètres techniques inchangés entre les variantes lorsque seule la Caption est étudiée

Temps observé lors du premier test court : environ 50 s dans l'interface.

## V1 — baseline
### Caption
```text
Modern French reggae dancehall, female lead vocal, French lyrics,
strong rhythmic groove, confident and expressive female performance,
natural conversational phrasing, clear French diction,
deep warm bass, tight syncopated drums,
reggae offbeat guitar skank, subtle Caribbean percussion,
modern polished production, organic dynamics,
powerful but controlled vocal delivery,
anthemic chorus, intimate verses,
clear contrast between verses, pre-chorus, chorus and bridge
```

### Lyrics testés
Extrait de « Ma terre » :
- Verse 1
- Pre-Chorus
- Chorus

Le texte source n'a pas été modifié pour cette expérience.

### Résultat utilisateur
- Voix féminine : conforme à l'objectif.
- Diction française : aucune erreur gênante relevée à l'écoute.
- Basse : trop discrète.
- Couleur musicale : pas assez dancehall ; résultat jugé trop peu percussif/tapant.
- Refrain : tendance à trop insister sur les dernières syllabes des mots.
- Une phrase du début, « j’ferai sans », passe un peu mal, sans toutefois constituer un problème majeur.

## V2 — amélioration de la Caption uniquement
### Modification
Les lyrics et les paramètres techniques ont été conservés. Seule la Caption a été renforcée vers un comportement dancehall plus rythmé et une basse plus présente.

### Caption
```text
Modern French dancehall reggae, female lead vocal,
strong contemporary dancehall groove,
syncopated rhythm, tight rhythmic vocal phrasing,
short punchy vocal lines, natural French prosody,
avoid excessive sustained vowels and exaggerated word endings,
confident expressive female delivery,
deep prominent sub bass, powerful bassline clearly present in the mix,
heavy kick and tight syncopated drums,
sharp reggae offbeat guitar skank,
Caribbean percussion,
modern bass-heavy dancehall production,
dynamic arrangement,
intimate verses, strong energetic chorus,
rhythmic and percussive vocal performance
```

### Résultat utilisateur
- Dancehall : nette amélioration ; groove beaucoup plus convaincant et percussif.
- Basse : nette amélioration ; présente et mieux intégrée à la production.
- Voix féminine : propre et intelligible.
- Registre vocal : jugé un peu trop haut, mais le résultat global est nettement meilleur que V1.
- Diction : toujours satisfaisante.
- Les lyrics n'ont pas été modifiés.

**Statut : meilleure référence actuelle.**

## V3 — tentative de voix plus grave
### Hypothèse
Tester si une indication explicite de registre vocal plus grave pouvait améliorer la couleur de la voix sans dégrader le reste.

### Modification
Même texte, mêmes paramètres et base de Caption V2, avec ajout de contraintes vocales :
- `low-register female voice`
- `deep warm feminine vocal tone`
- `slightly husky and mature vocal character`

### Résultat utilisateur
Résultat jugé nettement inférieur à V2, décrit comme « pas top du tout » / « très pourrie ».

### Conclusion
La tentative de forcer une voix féminine plus grave n'est pas retenue.

Ne pas empiler davantage de contraintes de registre tant qu'un autre moyen de contrôler la couleur vocale n'a pas été identifié. La priorité reste la qualité globale obtenue avec V2.

## État actuel des connaissances
1. La Caption influence fortement le caractère dancehall et la présence de la basse.
2. La Caption V2 constitue la meilleure base actuelle.
3. Une tentative trop explicite de voix grave peut dégrader fortement le résultat global.
4. La voix féminine et la diction française sont déjà satisfaisantes sur cette base.
5. Les lyrics n'ont pas encore été optimisés ; « j’ferai sans » est un candidat potentiel pour une expérience ultérieure, mais il ne faut pas modifier les lyrics et la Caption simultanément si l'objectif est d'isoler une variable.
6. Les fins de mots trop étirées restent un phénomène à surveiller, mais il n'est pas encore isolé expérimentalement.

## Prochaine étape proposée
Repartir de **V2** comme référence et modifier une seule variable à la fois. Ne pas chercher à forcer immédiatement un registre vocal plus grave.

## Évaluation
Cette série n'est pas encore un preset validé. V2 est une **référence expérimentale prometteuse**, à reproduire avant de la considérer comme configuration validée.
