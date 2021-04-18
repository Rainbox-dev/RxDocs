# II.A - Mise en pratique : choisir ses espaces colorimétriques et formats

Travaillant au sein d'une application dédiée à l'image numérique, il est important de savoir et maîtriser comment sont gérées les couleurs dans les différentes fonctionnalités de l'application en question, ainsi que tout au long de la chaîne de fabrication dans laquelle elle s'insère.

Cette seconde partie est destinée à expliquer concrètement comment organiser cette chaîne de fabrication pour ce qui concerne la couleur, et aider à la paramétrer.

[TOC]

## A.1 - Théorie

Avant de s'engager dans le paramétrage des différents logiciels, il faut bien comprendre que **les couleurs sont régulièrement converties lors de la production** d'images. En effet, à chaque étape depuis la génération de la couleur jusque son affichage sur un dispositif quelconque, chaque bout de logiciel et de matériel intervenant travaille dans son propre espace.

Maîtriser la chaîne de production des couleurs n'implique donc pas de bien choisir un espace colorimétrique unique, mais plutôt d'a**voir conscience des différentes conversions et des différents espaces colorimétriques entrant en jeu** à chaque étape, au sein d'une application autant qu'entre les applications.

Cette maîtrise ne garantira pas que les couleurs seront correctement reproduites sur le dispositif des spectateurs (TV, écran d'ordinateur, téléphone, écran de cinéma...) mais permet à minima d'avoir le contrôle tout au long de la production tout en s'assurant de livrer des images respectant les standards en vigueur. C'est ensuite au diffuseur de prendre le relai en toute fin de chaîne avec une chaîne correctement paramétrée aussi.

### A.1.a - Parcours d'une couleur

Suivons le chemin qu'une couleur doit parcourir avant d'être correctement affichée.

Une couleur générée par une première application et devant être exportée dans une autre application, via un fichier intermédiaire, est susceptible de subir deux conversions : depuis la première application vers le fichier, et depuis le fichier vers la deuxième application. Cette opération se répète à chaque étape de la chaîne de production, jusqu'à la diffusion, où l'application (et le matériel) de diffusion convertissent ce qu'ils reçoivent dans l'espace colorimétrique de la diffusion.

*![Schema entre deux applications]()*

Chacune des applications doit donc impérativement être correctement renseignée sur l'espace colorimétrique des fichiers qu'elle importe, afin de pouvoir effectuer la bonne conversion vers son propre espace colorimétrique. De même, au moment de l'exportation, la bonne conversion depuis l'espace colorimétrique de l'application vers celui du fichier exportée doit être effectuée.

Mais au sein même d'une application, de nombreuses conversions peuvent avoir lieu :

- Depuis l'espace de couleurs du fichier importé vers l'espace colorimétrique de l'application.
- Depuis l'espace colorimétrique de l'application vers celui de l'écran de l'ordinateur, pour la prévisualisation.
- Depuis l'espace colorimétrique de l'application vers celui du fichier de sortie.

En effet, tous ces espaces colorimétriques ne sont pas nécessairement les mêmes...

À chaque "brique" de l'application utilisant des couleurs, un espace colorimétrique est associé. Voyons ces différentes briques et quelques recommandations.

*![Schema d'une application et ses espaces colorimétriques]()*

!!! hint
    Toutes les applications ne permettent pas forcément d'accéder à tous les réglages de tous les espaces pour ces différents éléments. Les réglages "imposés" peuvent être plus ou moins pratiques et intelligents suivant les applications...

!!! note
    Toutes les explications qui suivent s'appliquent aussi bien aux applications de travail (3D, dessin, compositing, retouches...) qu'aux lecteurs (affichage d'image, lecteurs vidéo...)

## A.2 - Espace de travail (scene referred)

L'espace le plus important à connaître est celui dans lequel travaille l'application, dans lequel elle effectue la synthèse des couleurs et les calculs associés.

Cet espace est celui noté *scene referred*.

Voici les caractéristiques les plus couramment utiles pour un espace de travail :

- ***Linéaire*** dans la grande majorité des cas, pour améliorer la fusion des couleurs, il peut être utile pour les corrections colorimétriques d'utiliser un espace non-linéaire.
- ***Gammut large*** afin de travailler dans un espace capable de reproduire fidèlement un grand nombre de couleurs et gagner en précision.

## A.3 - Entrée

À chaque importation d'un fichier ou autre élément externe, l'application doit bien interpréter (connaître) l'espace colorimétrique de l'élément, afin de le convertir vers son espace de travail.

Il y a alors plusieurs possibilités :

- Soit les fichiers respectent les standards les plus courant (quand ils existent...), et l'application interprète correctement les fichiers par défaut.
- Soit les fichiers, ou l'application elle-même, ne respectent pas ces standards, ou bien aucun standard n'existe, et l'application doit alors permettre de modifier l'interprétation des données pour spécifier manuellement quel est l'espace colorimétrique importé[^1].

Dans tous les cas, afin de maîtriser la production, **il est impératif de contrôler l'interprétation des couleurs par les applications** lors de l'importation ; certaines se "tromperont" systématiquement sur certains fichiers, et il faudra alors penser à corriger l'interprétation à chaque import (ou l'automatiser)[^2].

*Cf.* *A.6 - Sortie intermédiaire* et *A.7 - Sortie finale* pour plus d'informations sur les espaces colorimétriques propres aux fichiers, et *[II.B - Quelques standards](2B-standards.md)* pour une liste des standards les plus courants.

## A.4 - Affichage

Il est primordial de garder à l'esprit que **l'espace colorimétrique de travail, *scene referred*, est le plus souvent différent de l'espace colorimétrique de l'affichage** !

L'application effectue donc une conversion des couleurs telles qu'elle les calcule vers l'espace d'affichage de l'écran.

Il y a plusieurs élément à prendre en compte pour cet affichage :

- L'espace colorimétrique de l'écran lui même
- Les réglages de l'écran qui peuvent altérer les couleurs
- Le profil colorimétrique appliqué à l'écran par le système d'exploitation
- La conversion effectuée par l'application depuis son espace de travail vers celui de l'affichage.

Voir la section *[2C - Calibrage des écrans](2C-calibration.md)* pour plus de détails sur le sujet.

### A.4.a - Espace de l'écran

Chaque écran affiche les couleurs dans un espace colorimétrique prédéfini et choisi par le constructeur pour le modèle particulier d'écran.

Il y a trois grandes catégories d'écrans :

- Les écrans (et projecteurs) d'ordinateurs
- Les Téléviseurs
- Téléphones, tablettes, etc.

Suivant ces catégories, la plupart des écrans utilisent ces espaces colorimétriques :

- Ordinateur : ***sRGB***, bien que certains écrans (souvent appelés *HDR*) soient aussi capables d'afficher les couleurs du ***P3*** ; les écrans *P3* affichent *aussi* le *sRGB*, qui est entièrement contenu "dans" le *P3*. Les écrans d'ordinateur affichent la *gamme complète (full/pc)* des couleurs (*cf.* *[K.4 - Full range / Limited / TV / PC ?](K-pix-format.md)*).
- Téléviseurs : ***Rec.709***, ou parfois ***sRGB*** (réglable), ou parfois d'autres espaces quand ils sont *HDR*. Les TV affichent la *game réduite (limited/tv)* des couelurs (*cf.* *[K.4 - Full range / Limited / TV / PC ?](K-pix-format.md)*).
- Téléphones, tablettes, etc. : ***sRGB***, bien que certains (rares) téléphones et tablettes soient aussi capables d'afficher les couleurs du ***P3***. Ces périphériques affichent la *gamme complète (full/pc)* des couleurs (*cf.* *[K.4 - Full range / Limited / TV / PC ?](K-pix-format.md)*).

Il est à noter que les écrans affichant *exactement* l'espace colorimétrique annoncé sont rares, et la plupart génèrent de (plus ou moins) petites variations ; ces variations sont en général en grande partie corrigées par une calibration maîtrisée. *Cf.* *[II.C - calibration des écrans](2C-calibration.md)*.

### A.4.b - Réglages et profils colorimétriques

La grande majorité des écrans proposent plusieurs réglages des couleurs sur l'écran lui même, notamment via les paramètres de luminosité et de contraste, complétés, suivant les écrans, par les *gammas[\*](ZZ-vocabulaire.md)* rouge, vert et bleu, et parfois encore d'autres réglagles.

Ces réglages permettent parfois de corriger les plus gros défauts des écrans tels qu'ils sont livrés en sortie d'usine (à condition d'avoir une méthode de calibration efficace), et peuvent être complétés par des réglages plus fin, à la fois via le *profil colorimétrique* appliqué par le système d'exploitation, et éventuellement des réglages au niveau du pilote de la carte graphique.

La connaissance de ces réglages est importante pour contrôler l'affichage correct des couleurs sur le poste de travail.

Il est à noter aussi que ces réglages doivent être contrôlés (et ajustés) régulièrement ; l'affichage des couleurs peut varier avec le vieillissement de l'écran, la température ambiante, etc.

*Cf.* *[II.C - calibration des écrans](2C-calibration.md)* pour des explications détaillées sur les réglages des écrans et comment les ajuster.

### A.4.c - Dans l'application

Une fois l'écran installé et correctement réglé (ou du mieux que possible), il n'y a plus qu'à sélectionner le bon profil d'affichage dans l'application.

La plupart du temps, une simple option d'affichage permet de spécifier si l'écran est *sRGB*, *Rec.709* ou *P3* ou autre ; parfois aucun réglage n'est disponible et l'application s'en remet au système d'exploitation.

Il faut garder en tête que l'application continue de travailler dans son propre espace, qui ne dépend pas de celui dans lequel sont affichées les couleurs, et que les sorties de fichiers ne dépendent pas non plus de cet espace d'affichage ; par contre, un mauvais choix d'affichage conduit à de mauvais choix de couleurs et donc des variations inattendues et pas standard lors de la sortie !

La pire erreur est par exemple de mal choisir l'espace d'affichage et croire par la suite que c'est l'espace de sortie qui est différent de ce à quoi on s'attendait. Cette erreur conduit alors à changer l'interprétation des couleurs lors de l'import dans l'application suivante pour tenter de compenser, et introduire de mauvaises corrections tout en perdant complètement la maîtrise de la chaîne de fabrication.

## A.5 - Sélecteurs de couleur

Dans une application les sélecteurs de couleurs (*color pickers*) peuvent avoir leur propre espace colorimétrique.

Le plus souvent, ils sont soit dans l'espace de travail de l'application, ce qui les rend difficile à utiliser quand l'espace est linéaire, soit dans l'espace de l'affichage, plus pratique.

On préfère des espaces non linéaires pour faciliter le choix des couleurs ; avoir des sélecteurs de couleur en *sRGB* permet aussi de récupérer facilement des couleurs depuis d'autres applications, depuis des images, etc. Une conversion est alors effectuée après la sélection de la couleurs vers l'espace de travail de l'application.

## A.6 - Sortie intermédiaire

Lors de l'export de fichiers *intermédiaires*, qui reserviront dans la suite de la production, le but est de perdre le moins d'informations possible, de garder un maximum de données pour la suite du travail.

Dans ce cas, le plus simple est, dans la mesure du possible, d'exporter des fichiers dans l'espace de travail de l'application. Pour ce faire, le format de fichier le mieux à même de stocker n'importe quelle information de couleurs et l'*openEXR* (qui est censé utiliser des espaces linéaires). Il est tout à fait possible d'utiliser d'autres formats, mais dans ce cas, soit le choix de l'espace ne sera pas standard et risque d'être mal interprété par la suite, soit on introduit des conversions inutiles, ou une perte de données en devant utiliser un espace plus petit ou non-linéaire.

Si il est impossible d'exporter dans l'espace de travail et en *openEXR* (ou autre format permettant de garder le bon espace), il faut privilégier les formats *RGB* (et éviter *YUV*, ou en tout cas bien utiliser le sous-échantillonage *4:4:4*).

Quand l'espace de travail est linéaire mais pas l'espace de sortie (et inversement), il faut savoir qu'une perte de précision et de qualité a lieu, et qu'il faut dans ce cas absolument que la profondeur de l'espace de travail soit plus grande que celle de sortie (travailler en *32 bpc linéaire* pour sortir en *16 bpc non linéaire* par exemple).

## A.7 - Sortie finale

Lors de la sortie finale, il faut bien évidemment essayer de respecter au mieux le standard correspondant à la livraison, ou se reférer à la demande du diffuseur.

*Cf.* *[II.B - Quelques standards](2B-standards.md)* pour une liste des standards les plus courants.

La plupart des sorties finales se feront dans des espaces colorimétriques dédiés à l'affichage, et donc avec un transfert non linéaire ; une perte de précision et de qualité ayant lieu lors du passage d'un espace de travail linéaire vers un espace d'affichage non linéaire, il est important dans ce cas que l'espace de travail ait une profondeur plus élevée que celle de la sortie finale (travail en *16 bpc* pour une sortie *8 bpc* par exemple).

----
Sources et références

[^1]:
    Si une application de vous permet pas de changer l'espace colorimétrique lors de l'importation, attendez-vous à avoir des variations de couleurs inattendues lors de l'importation. Il faudra alors deviner en quoi l'application "se trompe" afin d'effectuer manuellement une correction des couleurs pour rétablir les couleurs d'origine (le plus souvent simplement via une correction *gamma[\*](ZZ-vocabulaire.md)* ou bien l'application d'une *LUT[\*](ZZ-vocabulaire.md)*). Notez qu'une telle application n'a pas vraiment sa place dans une chaîne de production où l'on cherche à maîtriser la couleur...
[^2]:
    Toutes les applications ne permettent pas l'automatisation de la gestion des couleurs (par exemple *Adobe After Effects* ne possède pas d'*API* pour ce point précis). Dans la suite de ce document, nous noterons pour les applications expliquées les erreurs d'interprétation qu'elles font, que nous avons pu repérer, et les autres spécificités à savoir.

![META](authors:Nicolas "Duduf" Dufresne;medias:Nicolas "Duduf" Dufresne;license:CC-BY-NC-SA;copyright:2021;updated:2021/04/11)