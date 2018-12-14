# Description du dossier

Ce dossier est une analyse de l'oeuvre de fiction *Voyage au centre de la Terre* de Jules Verne. J'ai récupéré les données puis encodé l'œuvre de façon à ce que l'on puisse retrouver la structure des chapitres en introduisant une variable par chapitre. Par la suite, j'ai réalisé une analyse sur Iramuteq avec plusieurs types de visualisations et réalisé un compte-rendu ici-même.

## Version texte

Afin de pouvoir obtenir la version .txt de l'oeuvre, je suis allée sur [Wikisource](https://fr.wikisource.org/wiki/Voyage_au_centre_de_la_Terre/Texte_entier).

Par la suite, afin de pouvoir l'utiliser dans Iramuteq, j'ai créé des variables pour chaque chapitre puis aussi __formaté__ le texte de façon à ce que celui-ci soit compatible, selon la syntaxe suivante :

~~~~
**** *chapitreX
texte texte texte texte

**** *chapitreY
texte texte texte

A noter que :
**** : introduit chaque texte
*nomvariable : crée une variable
~~~~

[Lien vers la version .txt](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/voyageaucentredelaterreencode.txt)

## Version epub

Pour la version epub, je voulais la récupérer sur Wikisource également mais celui-ci n'étant pas disponible, je me suis rabattue sur le epub de [Feedbooks](http://fr.feedbooks.com/book/1474/voyage-au-centre-de-la-terre).

[Lien vers la version .epub](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/Jules_Verne_Voyage_au_centre_de_la_Terre.epub)

## Visualisation de données

### Statistiques

J'ai réalisé ce type d'analyse pour avoir plus de __lisibilité__. La *lemmatisation* permet de réduire les verbes à leurs formes infinitives. J'ai alors obtenu un schéma ainsi que plusieurs tableaux CSV permettant de voir la fréquence des mots dans l'oeuvre ainsi que leurs types (verbe, adjectif...).

Le dossier [csv_occurences](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/tree/master/csv_occurences) contient 3 types de fichiers CSV :
* [formes_actives.csv](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/csv_occurences/formes_actives.csv) : le plus __pertinent__ pour une analyse
* [formes_supplémentaires.csv](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/csv_occurences/formes_suppl%C3%A9mentaires.csv) : peu pertinent car uniquement des stopwords
* [total.csv](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/csv_occurences/total.csv) : regroupe les résultats des deux .csv précédents

#### Résumé

* Nombre de textes : 45
* Nombre d'occurrences : 71600
* Nombre de formes : 5663
* Nombre d'appax : 2423 (3,38% des occurrences - 42,79% des formes)
* Moyenne d'occurence par texte : 1591.11

![resume](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/resume.PNG)

### Nuages de mots

Cette analyse n'apporte pas vraiment d'information pertinente par elle-même, mais je pense qu'il peut être intéressant de la __coupler avec un autre type d'analyse__ afin d'apporter un aspect visuel.

![nuage](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/nuage_1.png)

### Analyses de similitudes

J'ai choisi la présentation __fruchterman reingold__ car c'est un algorithme de force qui calcule la distance entre les noeuds ainsi que leurs poids et la force de leurs liens.

#### Indice de cooccurence

Ici, j'ai réglé les paramètres de façon à ce que l'analyse se fasse sur la *cooccurence* (combien de fois des éléments apparaissent en même temps, présence simultanée de deux ou plusieurs mots dans un même énoncé - [Source](https://fr.wikipedia.org/wiki/Cooccurrence)). 

* Sur la totalité des occurences :

![similitudes](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_1.png)

* Sur des occurences strictement supérieures à 10 :
![similitudes10](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_10.png)

*Cette analyse devait me servir de base pour mon graphe sur Gephi, où je voulais améliorer la visualisation.*

* Sur des occurences supérieures ou égales à 50 :
![similitudes50](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_50.png)

* Avec comme paramètre __multilevel.community__ ainsi que __Communautés__ et __halo__ d'actifs, afin de pouvoir répartir l'ensemble les cooccurences selon plusieurs groupes :
![similitudesmot](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_3.png)


#### Indice de Mountford

Cet indice de Mountford note la force des affinités de 0 à 1, grâce à l'épaisseur du lien entre les mots. La comparaison est beaucoup plus simple car de type : présent/absent. Comme nous pourrons le voir, plus les occurences sont limitées à un grand nombre, plus la visibilité augmente.

* Sur la totalité :
![similitudesmountford](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_mountford.png)

* Sur des occurences strictement supérieures à 10 :
![similitudesmountford10](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_mountford10.png)

* Sur des occurences supérieures ou égales à 50 :
![similitudesmountford50](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_mountford50.png)

### Analyse factorielle des correspondances

Ce type d'analyse va transformer les données sous forme de graphique a 2 dimensions, montrant la différence entre chaque groupe ou chaque classe de mots dans le but de hiérarchiser les informations des textes. On utilise pour cela plusieurs paramètres comme la fréquence des mots ou encore le type de variables.

Le graphique ci-dessous possède une __fréquence minimale de 10__ et les deux types de variables : __actives__ et __supplémentaires__. Il est peu lisible tellement les informations sont concentrées.
![total](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/afcf_row.png)

Ce second graphique est réalisé avec une __fréquence minimale de 60__ et un seul type de variable, les __variables actives__. L'information y est plus claire.
![total](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/afcf_row10.png)

On peut constater que selon les degrés de fréquence et de sélection des variables, on peut réaliser une analyse factorielle efficace. Il est même possible de réaliser une analyse par chapitre, car ceux-ci sont balisés en tant que modalités dans mon fichier .txt.

### Méthode Reinhert

La classification de Reinert permet de classer les formes dans des classes de formes regroupées selon leur indépendance mesurée par un test au Chi². Ces mêmes classes peuvent alors être représentées à l'aide de différents arbres, comme ici avec un dendrogramme :

![dendrogramme](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/dendrogramme_1.svg)

Ce diagramme fournit la liste des formes les plus associées pour chaque classe. A noter qu’une forme peut se retrouver dans plusieurs classes différentes. Une classe est un regroupement de segments de texte qui contiennent des formes. Le graphique ci-dessus facilite le repérage des formes et leur degré de dépendance aux classes. 

Avec ce classement par dendrogramme, on peut effectuer par la suite un AFC, car le tableau donné par la classification de Reinert utilise des classes dans le tableau lexical. 

![similitudescolor](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/AFC2DL.png)

Les formes colorées correspondent aux classes de la méthode Reinert et permettent de repérer leur organisation sur deux dimensions.

#### Analyse d'un mot en particulier

Lorsque l'on applique la classification de Reinert, comme je l'ai dit précédemment, nous avons un tableau qui nous est donné. Il est possible d'analyse un ou plusieurs mots de ce tableau avec une analyse des cooccurences.

Analyse des cooccurences du mot __"savant"__ sur 2 chapitres

![similitudesmot](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/graph_simi_mot.png)

## Fichier Gephi

Analyse des similitudes avec l'indice de Mountford sur des occurrences supérieures ou égales à 10 :

![gephi](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/visualisation/gephi.png)

## Fichier Question Devoir

[Lien GitHub](https://github.com/belzepaf/Melanie_AUBRY_voyageaucentredelaterre/blob/master/question.md)
