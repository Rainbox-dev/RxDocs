# I.E - Retour sur les blancs : température

Le blanc étant perçu différemment en fonction de l'environnement et de l'observateur, on doit, avant d'en parler, définir exactement ce qui est blanc. Encore une fois, il faut un référenciel invariant, physique, sur lequel tout le monde puisse être d'accord, un peu comme l'usage des *raies de Fraunhofer* peuvent servir de référence pour définir des lumières *monochromatiques[\*](ZZ-vocabulaire.md)* précises.

On utilise généralement pour définir le blanc ce qu'on appelle le rayonnement des *corps noirs[\*](ZZ-vocabulaire.md)*.

[TOC]

## E.1 - Corps noir

Un *corps noir* est un élément qui n'apparait pas nécessairement *noir*, mais qui est noir dans le sens où il absorbe l'intégralité des rayons électromagnétiques (et donc de lumière visible) qu'il reçoit ; autrement dit, **si** le corps noir était parfaitement froid[^1], il serait d'un noir pur. Mais tout corps possède une certaine chaleur, et cette chaleur fait qu'il émet des rayonnements, dont une partie dans le spectre visible, ce qui explique que ce qu'on appelle un *corps noir* n'est pas *vu* comme noir.

La conséquence est que la lumière, et donc la couleur, d'un corps noir n'est pas du tout influencée par la lumière qu'il reçoit, mais est uniquement le résultat de sa chaleur. Plusieurs éléments peuvent être considérés comme des corps noirs : les braises d'un barbecue, le feu, un métal incandescent, le soleil... Tous ces éléments de sont pas de réels corps noirs au sens physique (le rayonnement qu'ils émettent n'est pas parfaitement indépendant de celui qu'ils reçoivent) mais en sont une approximation, très proche dans le cas du soleil[^2].

L'intérêt des *corps noirs* est que la lumière qu'ils émettent, et donc leur couleur perçue, ne dépend pas de l'environnement dans lequel ils sont ; ils forment donc de bons référentiels objectifs. De plus, on sait que leur spectre de rayonnement dépend directement de leur énergie, de leur chaleur. On peut donc associer à une chaleur donnée un spectre donné, c'est à dire une lumière d'une composition précise de rayons *monochromatiques[\*](ZZ-vocabulaire.md)*, résultant en un *blanc[\*](ZZ-vocabulaire.md)* précis et mesurable.

*![Tableau de quelques couleurs en fonction de leur température](img/temperature.svg)*

!!! note
    Contrairement aux autres éléments incandescents des exemples ci-dessus, la couleur apparente du soleil n'est pas directement le résultat de sa chaleur bien qu'il soit un corps noir ; en effet, l'absorption des rayons par l'atmosphère change sa couleur à notre niveau.

## E.2 - Lieu planckien

Plutôt que de définir le spectre de la lumière des corps noirs par la description des rayons qui le composent, on simplifie en liant simplement cette couleur, ce blanc, à la température du corps noir qui l'a émis ; et cette mesure est donnée en *Kelvin* (et pourrait tout aussi bien être convertie en degrés *Celsius* ou *Fahreneit*). On peut ainsi définir une lumière *blanche* directement en fonction de cette température théorique.

| Description | Kelvin | Degré Celsius | Degré Farenheit |
|---|---|---|---|
| Lave en fusion | `1000 K` | `726,85°C` | `1340,33°F` |
| Soleil à midi | `5800 K` | `5526,85°C` | `9980,33°F` |
| Jour nuageux | `7000K` | `6726,85°C` | `12140,33°F` |
| Foudre | `9000 K` | `8726,85°C` | `15 740,33°F` |

On constate que la *température* du blanc rend bien compte de sa teinte et non pas de la température réelle du corps qui émet cette lumière ; **cette température est celle du corps noir qui aurait émis un rayonnement de la même couleur**, mais **pas** la température ni l'énergie de l'élément vu. On utilise ces valeurs de température en Kelvin **par convention** pour standardiser la description des blancs.

L'ensemble de ces températures peut être représentée en un *dégradé* allant du jaune-orangé au bleu, dans une gamme blanchâtre (ce sont bien des couleurs résultant d'un mélange complexe de rayons *monochromatiques[\*](ZZ-vocabulaire.md)* du spectre visible ; seules les proportions changent[^3]).

On appelle cet ensemble de couleurs réparties en une ligne le *Lieu planckien*.

*![Lieu planckien avec températures](img/planckian-locus.svg)*

## E.3 - Balance des blancs

*![Photos de paysage enneigé à différents moments de la journée](img/snow.svg)*  
*Sous le soleil, à l'ombre ou dans les nuages, quel que soit le moment de la journée, dans la réalité nous percevons la neige comme* blanche *même si en réalité la lumière qu'elle réfléchit est à chaque fois différente.*

Le cerveau effectue en permanence des ajustements pour compenser la couleur de la lumière éclairant une scène, et toujours voir les blancs... blancs. Le problème se pose lors de la capture des couleurs via un appareil photo ou une caméra de faire la même compensation.

En effet, un capteur qui recevrait du blanc à midi au soleil "verrait" en réalité la "vraie" couleur, tirant plutôt vers le jaune, alors que le même objet un jour nuageux serait "vu" par le capteur comme bien plus bleu.

On effectue donc une opération de correction de ces couleurs pour ramener la couleur de l'objet à un "blanc" neutre : celui du dispositif de reproduction. C'est ce qu'on appelle la *balance des blancs* : on "efface" l'influence de la lumière ayant éclairé la scène au moment de la capture.

Ainsi, cette image "neutralisée" peut être reproduite par le dispositif dans des conditions standard.

- Pour afficher l'image sur un écran, le travail est de ramener la couleur du blanc dans la scène (`5800 K` sous le soleil ou `7000 K` sous les nuages par exemple) à celle du blanc de l'écran (en général celui qu'on nomme *D65*, `6500 K`).
- Lors d'un tirage papier, le blanc de la scène devra être ramené au blanc du papier. Une fois l'image imprimée, elle pourra être vue correctement sous tous les éclairages possible.

Sans ce travail de "neutralisation", l'image est décalée par rapport au blanc de référence (le blanc de l'écran ou le blanc du papier) et apparait bleutée ou orangée.

----
Sources et références

- [Le corps noir sur *Wikipedia*](https://fr.wikipedia.org/wiki/Corps_noir)
- [Le lieu planckien sur *Wikipedia*](https://fr.wikipedia.org/wiki/Lieu_planckien)
- [Température de couleur sur *Wikipedia*](https://fr.wikipedia.org/wiki/Temp%C3%A9rature_de_couleur)

[^1]:
    Seuls les trous noirs, qui absorbent toute lumière par gravitation, peuvent être considérés comme des *corps noirs* presque parfaits **et** n'émettant eux mêmes aucun rayonnement ; mais on sait aujourd'hui que même les trous noirs émettent un très faible rayonnement, de manière un peu détournée, le *[rayonnement de Hawking](https://fr.wikipedia.org/wiki/%C3%89vaporation_des_trous_noirs)*. Par contre, on ne sait pas encore vraiment si ce rayonnement dépend de la composition du trou noir (ce qu'on appelle *[le paradoxe de l'information](https://fr.wikipedia.org/wiki/Paradoxe_de_l%27information)*, mais c'est un tout autre sujet que la couleur...).
[^2]:
    Théoriquement, même le soleil renvoie les rayons qu'il reçoit ; mais la proportion entre les rayons réfléchis et les rayons émis est tellement insignifiante qu'on peut considérer le soleil comme un corps noir. Et à notre échelle il en est de même pour le feu, les braises, les étincelles...
[^3]:
    Plus le corps a de l'énergie (plus il est chaud), plus la proportion de rayons de haute *fréquence[\*](ZZ-vocabulaire.md)* (et de faible *longueur d'onde[\*](ZZ-vocabulaire.md)*) est élevée : en effet, la quantité d'énergie portée par les rayons lumineux dépend directement de leur fréquence. Hors les rayons de longueur d'onde plus courte sont ceux du côté bleu du spectre. Ainsi, plus le corps est chaud, plus la proportion de rayons bleus augmente dans le mélange émis, plus la couleur s'éloigne des rouges orangés vers les bleus. Mais il faut bien garder à l'esprit que la lumière émise reste un mélange, et qu'on parle bien de nuances de blancs.  
    La découverte de ce lien entre longueur d'onde et énergie, et le travail sur la couleur des corps noirs par le physicien Max Planck à la fin du XIX<sup>è</sup> siècle sont à l'origine de la *physique quantique* moderne, avec la découverte par Planck que l'énergie est composée de valeurs discrètes et non pas continue (c'est la fondation préalable à la théorisation du *photon* par Albert Einstein en 1905).

![META](authors:Nicolas "Duduf" Dufresne;medias:Nicolas "Duduf" Dufresne;license:CC-BY-NC-SA;copyright:2021;updated:2021/03/23)