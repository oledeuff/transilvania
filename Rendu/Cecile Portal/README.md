# Mathias Sandorf
## Description du dossier
Ce dossier analyse de *Mathias Sandorf* de Jules Verne récupéré en version E-pub et .txt sur Gallica. Afin de bien encoder le texte en .txt pour utiliser Iramuteq j'ai introduit des variables de chapitre selon la partie. Ainsi:
**** *chapitreX_partieX
texte texte texte texte

### Visualisation de données

Voici quelques graphique réalisés avec Iramuteq.
#### Statistiques
Avec Iramuteq j'ai commencé par créer un graphique Statistique permettant avec les tableaux CSV du dossier de determiner la fréquence d'apparition des termes et leurs type (adjectif, verbe etc.).

![resume](https://github.com/Portalc/portal_cecile_MathiasSandorf/blob/master/image/resume.png)

Résumé
Nombre de textes : 35
Nombre d'occurrences : 191006
Nombre de formes : 8355
Nombre d'appax : 3348 (1,75% des occurrences - 40,07% des formes)
Moyenne d'occurence par texte : 5457.31
resume

#### Nuages de mots
Il est possible de réaliser un nuage de mot comme celui-là mais sans les termes étranges (comme le "ã") en mettant les "termes non reconnus" comme supplémentaire dans les propriété du graphique.

![resume](https://github.com/Portalc/portal_cecile_MathiasSandorf/blob/master/image/nuagedemot_part1chap_part2chap1.png)

#### Analyses de similitudes
Ici la le graphique de fruchterman reingold représente la distance des liens entre les mots et leurs force dans le chapitre 1 de la première partie et le chapitre 1 de la seconde partie.
![resume](https://github.com/Portalc/portal_cecile_MathiasSandorf/blob/master/image/similitude_part1chap1_part2chap1.png)


#### Analyse des correspondances
Ce graphique montre la différence entre chaque groupe de mots afin de classer entre elles (hiérarchiser) les informations du textes grâce à la fréquence des mots ou avec le type de variables.

![resume](https://github.com/Portalc/portal_cecile_MathiasSandorf/blob/master/image/analyse%20des%20correlation.png)

#### Méthode Reinhert

![resume](https://github.com/Portalc/portal_cecile_MathiasSandorf/blob/master/image/dendrogramme_1.png)
![resume](https://github.com/Portalc/portal_cecile_MathiasSandorf/blob/master/image/AFC2DL.png)
