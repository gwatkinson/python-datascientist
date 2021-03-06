---
title: "Git: un élément essentiel au quotidien"
date: 2020-09-30T13:00:00Z
draft: false
weight: 10
output: 
  html_document:
    keep_md: true
    self_contained: true
slug: introgit
---

Une grande partie du contenu de ce chapitre provient du cours
[Travail collaboratif avec `R`](https://linogaliana.gitlab.io/collaboratif/git.html).

## Pourquoi faire du `Git` <i class="fas fa-code-branch"></i> ?

Tous les statisticiens se sont déjà demandé (ou à leurs collègues) : 

* quelle était la bonne version d'un programme 
* qui était l'auteur d'un bout de code en particulier
* si un changement était important ou juste un essai
* comment fusionner des programmes
* etc.

Il existe un outil informatique puissant afin de répondre à tous ces besoins : la gestion de version (*version control system* (VCS) en anglais). Ses avantages sont incontestables et permettent de facilement :

* enregistrer l'historique des modifications d'un ensemble de fichiers 
* revenir à des versions précédentes d'un ou plusieurs fichiers
* rechercher les modifications qui ont pu créer des erreurs
* partager ses modifications et récupérer celles des autres
* proposer des modifications, les discuter, sans pour autant modifier la dernière version existante
* identifier les auteurs et la date des modifications

En outre, ces outils fonctionnent avec tous les langages informatiques (texte, R, Python, SAS, $\LaTeX$, Java, etc.) car reposent sur la comparaison des lignes et des caractères des programmes.


On peut ainsi résumé les principaux avantages du contrôle de version 
de la manière suivante :

1. Conserver et archiver l'ensemble des versions d'un code ou d'une documentation
2. Travailler efficacement en équipe
3. Améliorer la qualité des codes
4. Simplifier la communication autour d'un projet


### Conserver et archiver du code

Une des principales fonctionnalités de la gestion de version est conserver l'ensemble des fichiers de façon sécurisée et de proposer un archivage structuré des codes. Les fichiers sont stockés dans un **dépôt**, qui constitue le projet

Tout repose dans la gestion et la présentation de l'historique des modifications. Chaque modification (ajout, suppression ou changement) sur un ou plusieurs fichiers est identifiée par son auteur, sa date et un bref descriptif^[Plus précisément, chaque modification est identifiée de manière unique par un code `SHA` auquel est associé l'auteur, l'horodatage et des méta-données (par exemple le message descriptif associé)]. Chaque changement est donc unique et aisément identifiable quand ils sont classés par ordre chronologique. Les modifications transmises au dépôt sont appelées **commit**.

Avec des outils graphiques, on peut vérifier l'
[ensemble des évolutions d'un fichier (`history`)](https://github.com/linogaliana/python-datascientist/commits/master/README.md), 
ou [l'histoire d'un dépôt](https://github.com/linogaliana/python-datascientist/commits/master).
On peut aussi 
[se concentrer sur une modification particulière d'un fichier](https://github.com/linogaliana/python-datascientist/commit/7e5d30ae0e260f9485453b42f195b0181a53e32e#diff-04c6e90faac2675aa89e2176d2eec7d8) ou vérifier, pour un fichier, la
[modification qui a entraîné l'apparition de telle ou telle ligne (`blame`)](https://github.com/linogaliana/python-datascientist/blame/master/README.md)

Sur son poste de travail, les dizaines (centaines ?) de programmes organisés à la main n'existent plus. Tout est regroupé dans un seul dossier, rassemblant les éléments du dépôt. Au sein du dépôt, tout l'historique est stocké et accessible rapidement. Si on souhaite travailler sur la dernière version des programmes (ou sur une ancienne version spécifique), il n'y a plus besoin de conserver les autres fichiers car ils sont dans l'historique du projet. Il est alors possible de choisir sur quelle version on veut travailler (la dernière commune à tout le monde, la sienne en train d'être développée, celle de l'année dernière, etc.).


### Travailler efficacement en équipe

Le deuxième avantage de la gestion de version représente une amélioration notable du travail en équipe sur des codes en commun. 

 La gestion de version permet de collaborer simplement et avec méthode. De façon organisée, elle permet de:

* travailler en parallèle et fusionner facilement du code
* partager une documentation des programmes grâce :
    + aux commentaires des modifications
    + à la possibilité d'une documentation commune et collaborative
* trouver rapidement des erreurs et en diffuser rapidement la
correction

A ces avantages s'ajoutent les fonctionalités collaboratives des sites de dépôt
(les principaux étant `Github` et `Gitlab`), qui permettent d'intéragir via
des *issues*, faire des suggestions de modifications, etc. 


L'usage individuel, c'est-à-dire seul sur son projet, permet aussi de "travailler en équipe avec soi même" car il permet de retrouver des mois plus tard le contenu et le contexte des modifications. Cela est notamment précieux lors des changements de poste ou des travaux réguliers mais espacés dans le temps (par exemple, un mois par an chaque année). Même lorsqu'on travaille tout seul, on collabore avec un *moi* futur qui peut ne plus se souvenir de la modification des fichiers. 


### Améliorer la qualité des codes

Le fonctionnement de la gestion de version, reposant sur l'archivage structuré des modifications et les commentaires les accompagnant, renforce la qualité des programmes informatiques. Ils sont plus documentés, plus riches et mieux structurés. C'est pour cette raison que le contrôle de version ne doit pas être considéré comme un outil réservé à des développeurs : toute personne travaillant sur des programmes informatiques, gagne à utiliser du contrôle de version. 

Les services d'intégration continue permettent de faire des tests automatiques
de programmes informatiques, notamment de packages, qui renforcent la 
replicabilité des programmes. Mettre en place des méthodes de travail fondées
sur l'intégration continue rend les programmes plus robustes en forçant 
ceux-ci à tourner sur des machines autres que celles du développeur du code.


### Simplifier la communication autour d'un projet

Les sites de dépôts `Github` et `Gitlab` permettent de faire beaucoup plus
que seulement archiver des codes. Les fonctionalités de déploiement 
en continu permettent ainsi de:

* créer des sites web pour valoriser des projets (par exemple les sites
`pkgdown` en `R`)
* déployer de la documentation en continu
* rendre visible la qualité d'un projet avec des services de *code coverage*, 
de tests automatiques ou d'environnements intégrés de travail (binder, etc.)
qu'on rend généralement visible au moyen de badges
(exemple ici <a href="https://github.com/linogaliana/python-datascientist" class="github"><i class="fab fa-github"></i></a>)


### Comment faire du contrôle de version ?

Il existe plusieurs manières d'utiliser le contrôle de version : 

* en ligne de commande, via [git bash](https://gitforwindows.org/), par exemple ;
* avec une interface graphique spécialisée, par exemple [tortoise git](https://tortoisegit.org/) ou [GitHub Desktop](https://desktop.github.com/) ;
* avec un logiciel de développement : la plupart des logiciels de développement ([RStudio](https://rstudio.com/) pour `R`, [PyCharm](https://www.jetbrains.com/fr-fr/pycharm/) ou [jupyter](https://jupyter.org/) pour `python`, [atom](https://atom.io/), etc.) proposent tous des modules graphiques facilitant l'usage de `git` dont les fonctionnalités sont très proches.


{{% panel status="tip" title="Tip" icon="fa fa-lightbulb" %}}
`Git` a été conçu, initialement pour la ligne de commande. Il existe
néanmoins des interfaces graphiques performantes
et pratiques, notamment lorsqu'on désire comparer deux versions d'un même
fichier côte à côte. Ces interfaces graphiques couvrent la majorité des
besoins quotidiens. Néanmoins, pour certaines tâches, il faut nécessairement
passer par la ligne de commande.
{{% /panel %}}


## Git: le B.A-BA

