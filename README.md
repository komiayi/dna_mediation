# dna_mediation
Ce projet applique une méthode d'analyse de médiation statistique avancée, incluant la prise en compte d'une cause commune non mesurée, à un jeu de données réelles explorant la relation entre les traumatismes infantiles, la méthylation de l'ADN et la réactivité au stress cortisonique.

## Contexte Scientifique
L'étude vise à comprendre les mécanismes biologiques sous-jacents à l'association entre les expériences traumatiques vécues pendant l'enfance (qui augmentent le risque de troubles psychiatriques) et la réponse au stress. Elle revisite l'étude de de Houtepen et al.[^1] en appliquant une nouvelle méthode qui réintègre un médiateur secondaire corrélé (cg26179948) au médiateur ciblé (cg27512205).

## Méthodologie
L'analyse de médiation a été réalisée pour estimer l'effet direct et indirect des traumatismes infantiles (CTQ) sur la réactivité au stress (Cort_AUCi), avec le locus cg27512205 (gène KITLG) comme médiateur principal d'intérêt.

Deux méthodes d'estimation ont été utilisées pour gérer la forte corrélation entre les deux loci de méthylation (cg27512205 et cg26179948), soupçonnée d'être due à une cause commune non mesurée:
* Méthode CC (Corrélation Constante) : suppose une corrélation constante entre les résidus des médiateurs.
* Méthode CNC (Corrélation Non Constante) : tient compte des corrélations non constantes entre les médiateurs, en fonction du niveau d'exposition.
  Plus de détails sur l'élaboration et la justification théorique des méthodes CC et CNC sont disponibles dans le Chapitre 2 du document PDF.

## Variables Clés
 Variable,Type,Description
Exposition (X),CTQ (Binaire),Traumatismes infantiles (score CTQtotal > 41).
Réponse (Y),Cort_AUCi (Continue),Réactivité du cortisol au stress (Aire sous la courbe d'augmentation).
Médiateur ciblé (M1​),cg27512205 (Continue),Méthylation du gène KITLG (transformée en valeurs M).
Médiateur secondaire (M2​),cg26179948 (Continue),Méthylation du gène JAZF1 (transformée en valeurs M).
Covariables (C),"âge, sexe (Continu/Binaire)",Variables de contrôle incluses dans tous les modèles.

[^1]: Houtepen, L. C., Vinkers, C. H., Carrillo-Roa, T., Hiemstra, M., Van Lier, P. A., Meeus, W., Branje, S., Heim, C. M., Nemeroff, C. B., Mill, J. et al. (2016). Genome-wide DNA methylation levels and altered cortisol stress reactivity following childhood trauma in humans. Nature communications, 7(1), 10967.
