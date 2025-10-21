# dna_mediation
Ce projet applique une méthode d'analyse de médiation statistique avancée, incluant la prise en compte d'une cause commune non mesurée, à un jeu de données réelles explorant la relation entre les traumatismes infantiles, la méthylation de l'ADN et la réactivité au stress cortisonique.

## Contexte Scientifique
L'étude vise à comprendre les mécanismes biologiques sous-jacents à l'association entre les expériences traumatiques vécues pendant l'enfance (qui augmentent le risque de troubles psychiatriques) et la réponse au stress. Elle revisite l'étude de de Houtepen et al.[^1] en appliquant une nouvelle méthode qui réintègre un médiateur secondaire corrélé (cg26179948) au médiateur ciblé (cg27512205).

## Méthodologie
L'analyse de médiation a été réalisée pour estimer l'effet direct et indirect des traumatismes infantiles (CTQ) sur la réactivité au stress (Cort_AUCi), avec le locus cg27512205 (gène KITLG) comme médiateur principal d'intérêt.

Deux méthodes d'estimation ont été utilisées pour gérer la forte corrélation entre les deux loci de méthylation (cg27512205 et cg26179948), soupçonnée d'être due à une cause commune non mesurée:
* Méthode CC (Corrélation Constante) : suppose une corrélation constante entre les résidus des médiateurs.
* Méthode CNC (Corrélation Non Constante) : tient compte des corrélations non constantes entre les médiateurs, en fonction du niveau d'exposition.

[^1]: Houtepen, L. C., Vinkers, C. H., Carrillo-Roa, T., Hiemstra, M., Van Lier, P. A., Meeus, W., Branje, S., Heim, C. M., Nemeroff, C. B., Mill, J. et al. (2016). Genome-wide DNA methylation levels and altered cortisol stress reactivity following childhood trauma in humans. Nature communications, 7(1), 10967.
