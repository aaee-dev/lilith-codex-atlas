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

## V4 — tentative sur les fins de phrases
### Hypothèse
Réduire l'insistance sur les dernières syllabes observée avec V1/V2 sans toucher au reste du caractère musical de V2.

### Modification
À partir de V2, ajout de contraintes de formulation vocale visant notamment à raccourcir les fins de phrases et à limiter les vocalises prolongées.

### Résultat utilisateur
Résultat rejeté : la diction s'est détériorée, avec des mots coupés et des phrases devenues difficiles à comprendre. La tentative a modifié le comportement vocal de manière trop brutale.

### Conclusion
Les consignes explicites du type `clipped phrase endings` / `avoid long sustained notes` ne sont pas retenues comme solution directe au problème des fins de mots.

## V2.1 et variantes — tentative d'adoucir le phrasé
Plusieurs variantes légères dérivées de V2 ont été testées pour corriger les vocalises en début de morceau et les syllabes parfois avalées.

### Résultat utilisateur
Les variantes ont perdu une partie du caractère convaincant de V2. Les vocalises initiales et la perte de mots restent problématiques sur certaines versions. Une variante ajoutant `no vocal intro` et `clear fully articulated French lyrics` a également été jugée franchement mauvaise, avec perte du « cœur » du rendu V2.

### Conclusion
Ne pas continuer à corriger V2 en surchargeant la Caption. Le comportement global de V2 semble fragile dès qu'on ajoute trop de contraintes vocales. Les modifications futures doivent être minimales et isoler une seule variable.

## Paramètres verrouillés de référence V2
Lorsqu'une reproduction exacte de V2 est nécessaire :
- Seed : `80592360`
- Random Seed : désactivé
- Caption : version V2 ci-dessus
- Même extrait de lyrics que la V2 originale

Ce seed est celui confirmé après correction pendant l'expérimentation ; les valeurs de seed précédemment communiquées comme alternatives ne doivent pas être utilisées pour identifier la V2.

## Nouveau candidat prometteur — génération avec session sauvegardée
Une génération ultérieure a produit un résultat décrit par l'utilisateur comme « un truc qui sonne vraiment bien », mais la génération a ensuite échoué/crashé. Une session ACE-Step a néanmoins été sauvegardée avec les paramètres de la génération.

### Métadonnées effectivement enregistrées dans la session
- `task_type` : `text2music`
- `reference_audio` : null
- `src_audio` : null
- `instrumental` : false
- Modèle : `acestep-v15-turbo`
- Vocal language : `fr`
- BPM enregistré : **96**
- Key/scale : vide / automatique
- Time signature : `4`
- Duration : `-1` (Auto)
- Inference steps : `8`
- Seed enregistré : **3889886077**
- Guidance scale : `7`
- Shift : `3`
- Inference method : `ode`
- Sampler : `euler`
- Velocity norm threshold : `0`
- Velocity EMA factor : `0`
- DCW : activé
- DCW mode : `double`
- DCW scaler : `0.02`
- DCW high scaler : `0.06`
- DCW wavelet : `haar`
- Thinking : activé
- LM temperature : `0.85`
- LM CFG scale : `2`
- LM Top-K : `0`
- LM Top-P : `0.9`
- CoT metas : activé
- CoT caption : désactivé
- CoT lyrics : désactivé
- CoT language detection : activé
- Constrained decoding : activé
- LoRA : aucune
- Audio : MP3, 128 kbps, 48 kHz

### Caption
La Caption enregistrée est exactement la Caption V2 documentée plus haut.

### Lyrics enregistrés
```text
[Verse 1]
Vous prendrez pas ma maison ni ma terre,
Coupez-moi l’eau et l’électricité, je ferai sans.
Vous pouvez bien fermer toutes vos frontières,
Vos lignes sur vos cartes, j’en ai rien à foutre.
Vous tracez des traits, vous plantez des panneaux,
Vous dites « ici oui, là-bas c’est interdit ».

[Pre-Chorus]
Mais la terre, elle, n’a jamais signé vos mots,
Et vos frontières n’existent que dans vos esprits.
Vous avez dessiné le monde,
Mais vous ne l’avez pas créé.

[Chorus]
Cette maison est la mienne,
Cette terre est la mienne.
Vous pouvez remplir tous vos papiers,
Je ne partirai pas.
Cette maison est la mienne,
Cette terre est la mienne.
Vous pouvez écrire toutes les lois que vous voulez,
Je ne partirai pas.
```

### Ambiguïté à conserver
Au moment de la génération, l'interface affichait à l'utilisateur **110 BPM** et un seed **909101276**. Le fichier de session enregistré par ACE-Step indique quant à lui **96 BPM** et le seed **3889886077**. Il est donc impossible de conclure que les valeurs affichées à l'écran correspondent aux paramètres effectivement utilisés sans vérifier l'audio ou les autres artefacts de cette génération.

Pour la reproduction, ne pas appeler ce candidat « preset » et ne pas mélanger les deux jeux de paramètres. Utiliser les valeurs de session seulement si l'audio candidat est bien celui correspondant à cette session.

## État actuel des connaissances
1. La Caption influence fortement le caractère dancehall et la présence de la basse.
2. La Caption V2 constitue la meilleure base expérimentale stable à ce stade.
3. Une tentative trop explicite de voix grave dégrade fortement le résultat global.
4. Les voix féminines et la diction française sont déjà satisfaisantes sur la base V2.
5. Les lyrics n'ont pas encore été optimisés de manière isolée.
6. Les contraintes trop agressives sur les fins de phrase peuvent détériorer la diction.
7. Les essais récents montrent qu'un bon résultat peut apparaître avec très peu de modification, ce qui renforce l'intérêt de repartir d'une base simple plutôt que d'empiler les consignes.
8. Le candidat enregistré à BPM 96 / seed 3889886077 est intéressant mais doit être relié sans ambiguïté à son audio avant d'en tirer une conclusion reproductible.

## Prochaine étape proposée
Repartir de **V2** comme référence et modifier une seule variable à la fois. Priorité : reproduire V2, puis isoler séparément les effets du texte des lyrics (par exemple `j’ferai sans`) et du tempo. Ne pas forcer davantage le registre vocal dans la Caption.

## Évaluation
Cette série n'est pas encore un preset validé.

- **V2** : référence expérimentale prometteuse, à reproduire.
- **V3/V4/V2.1 et variantes** : variantes rejetées.
- **Candidat session sauvegardée** : prometteur selon l'évaluation utilisateur, mais non validé et encore ambigu sur le lien exact entre l'interface et les paramètres enregistrés.
