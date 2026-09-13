# Workflows ACE-Step

Méthodes de travail, procédures et recettes testées et réutilisables.

## Protocole expérimental actuel

Pour les premières expérimentations, privilégier des extraits courts plutôt que des morceaux complets lorsque le temps de génération est élevé. Utiliser un batch réduit, idéalement `1` pour une génération de référence et `2` seulement lorsqu’une comparaison immédiate est utile.

Le protocole actuel privilégie :
- voix féminine uniquement ;
- texte original conservé lors du point de référence ;
- une seule variable modifiée à la fois lorsque l’objectif est de comparer ;
- seed aléatoire pour l’exploration, seed fixe pour les comparaisons ;
- mesure du temps de génération réel ;
- distinction entre paramètres visibles dans notre interface locale et paramètres trouvés dans d’autres interfaces ou versions.

Une génération réussie n’est pas considérée comme un preset validé tant qu’elle n’a pas été suffisamment comprise ou reproduite.