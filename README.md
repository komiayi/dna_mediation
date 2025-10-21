# Application d'une Méthode d'Analyse de Médiation avec Cause Commune Non Mesurée


## Traumatisme Infantile, Méthylation de l'ADN et Réactivité au Stress

Ce projet applique une méthode d'analyse de médiation statistique avancée, incluant la prise en compte d'une cause commune non mesurée, à un jeu de données réelles explorant la relation entre les **traumatismes infantiles**, la **méthylation de l'ADN** et la **réactivité au stress cortisonique**.

### 📄 Document Complet

Pour une lecture détaillée de la méthodologie, des analyses et des discussions, veuillez consulter le mémoire original :

[**Lien vers le PDF du Mémoire**](docs/Memoire_final_2025 (1).pdf)

***

## Contexte Scientifique

L'étude vise à comprendre les mécanismes biologiques sous-jacents à l'association entre les expériences traumatiques vécues pendant l'enfance et la réponse au stress. Elle revisite l'étude de Houtepen et al.[^1] en appliquant une nouvelle approche pour estimer les effets en présence de plusieurs médiateurs corrélés.

### Enjeu méthodologique : médiation multiple et confusion

Bien que l'analyse de médiation simple soit bien établie, son extension à la médiation multiple est complexe, notamment lorsque les médiateurs sont corrélés par des causes communes non mesurées.

Notre approche se concentre sur l'estimation de l'effet à travers un médiateur cible unique en présence d'un second médiateur corrélé. Cette situation crée un problème de confusion non mesurée entre le médiateur cible et la réponse, rendant les méthodes d'ajustement standard inapplicables.

Pour résoudre ce dilemme, nous avons développé une approche novatrice qui :

1.  Redéfinit les effets : l'approche adapte l'hypothèse de composition pour intégrer le deuxième médiateur et redéfinir les effets direct et indirect du médiateur cible.
2.  Propose deux méthodes : Nous proposons la méthode CC (Corrélation Constante), qui simplifie l'identification des effets en supposant une corrélation constante entre les résidus des médiateurs.
3.  Surpasse la limitation : Nous proposons ensuite la méthode CNC (Corrélation Non Constante). Cette méthode paramétrique évalue l'impact de la violation de l'hypothèse de corrélation constante en estimant la corrélation entre les médiateurs potentiels à différents niveaux d'exposition.

### Méthodologie et Diagrammes Causaux
## Méthodologie
L'analyse de médiation a été réalisée pour estimer l'effet direct et indirect des traumatismes infantiles (CTQ) sur la réactivité au stress (Cort_AUCi), avec le locus cg27512205 (gène KITLG) comme médiateur principal d'intérêt.

Initialement, le modèle se concentrait uniquement sur le locus cg27512205 comme médiateur simple :
<p align="center">
  <img src="/figures/initial_diagram.png" alt="Diagramme initial d'analyse de médiation simple">
  <br>  
  Diagramme initial d'analyse de médiation simple.
</p>
L'approche développée dans cette analyse incorpore le second locus (cg26179948) en raison de sa forte corrélation avec cg27512205 et suspecte l'existence d'une cause commune non mesurée entre les deux médiateurs.

Deux méthodes d'estimation ont été utilisées pour gérer cette structure complexe :
* Méthode CC (Corrélation Constante) : suppose une corrélation constante entre les résidus des médiateurs.
* Méthode CNC (Corrélation Non Constante) : tient compte des corrélations non constantes entre les médiateurs, en fonction du niveau d'exposition.
  Plus de détails sur l'élaboration et la justification théorique des méthodes CC et CNC sont disponibles dans le Chapitre 2 du document PDF.

<p align="center">
  <img src="/figures/causal_diagram.png" alt="Diagramme initial d'analyse de médiation multiple">
  <br>  
  Diagramme causal de l’influence des traumatismes infantiles (CTQ) sur la réponse du cortisol
(Cort_AUCi), via cg27512205 en contrôlant l’âge et le sexe. La flèche pointillée bidirectionnelle indique une
cause commune non mesurée.
</p>
Le modèle final utilisé inclut les deux médiateurs et la flèche pointillée bidirectionnelle indiquant la cause commune non mesurée (facteur de confusion) entre eux.

## Variables Clés

| Variable | Type | Description |
| :--- | :--- | :--- |
| **Exposition (X)** | `CTQ` (Binaire) | Traumatismes infantiles (score CTQtotal > 41). |
| **Réponse (Y)** | `Cort_AUCi` (Continue) | Réactivité du cortisol au stress (Aire sous la courbe d'augmentation). |
| **Médiateur ciblé ($M_1$)** | `cg27512205` (Continue) | Méthylation du gène KITLG (transformée en valeurs M). |
| **Médiateur secondaire ($M_2$)** | `cg26179948` (Continue) | Méthylation du gène JAZF1 (transformée en valeurs M). |
| **Covariables (C)** | `âge`, `sexe` (Continu/Binaire) | Variables de contrôle incluses dans tous les modèles. |

## Résultats
Les analyses ont confirmé l'existence d'un lien statistique entre les traumatismes infantiles, la méthylation de l'ADN et la réactivité au stress.

### Effet Direct (non-médié)

L'étude révèle un effet direct significatif de l'exposition traumatique (CTQ) sur la réactivité au stress cortisonique (Cort\_AUCi), quel que soit le modèle ou la méthode utilisée. Cet effet représente la majeure partie de l'association totale entre l'exposition et la réponse.
* Résultat clé (méthode CC) : l'estimation de l'effet direct ($\varsigma$) est de $-399.2$ (IC 95% : $[-716.1, -127.1]$). Un intervalle de confiance qui exclut zéro indique une forte significativité statistique de l'effet non médié.

### Effet indirect (médiation par cg27512205)

L'effet médiateur du locus cg27512205 (effet indirect $\delta$) n'est pas statistiquement significatif dans cette population, ni avec la méthode CC ni avec la méthode CNC.
* Résultat clé (méthode CC) :L'estimation de l'effet indirect ($\delta$) est de $-25.47$ (IC 95% : $[-91.68, 86.58]$). L'intervalle de confiance inclut zéro, indiquant l'absence de preuve de médiation par ce gène spécifique.

## Apport Méthodologique

Les estimations de l'effet indirect restent relativement stables entre les méthodes CC et CNC, suggérant que, dans ce cas précis, le biais potentiel induit par l'absence de modélisation explicite de la cause commune non mesurée est faible. L'application de la méthode a ainsi permis de confirmer la robustesse de l'effet direct.

**Pour consulter les tableaux de résultats complets et intermédiaires (Tableaux 4.2, 4.7 et 4.9), veuillez vous référer au dossier [results/](results/).**

***

[^1]: Houtepen, L. C., Vinkers, C. H., Carrillo-Roa, T., Hiemstra, M., Van Lier, P. A., Meeus, W., Branje, S., Heim, C. M., Nemeroff, C. B., Mill, J. et al. (2016). Genome-wide DNA methylation levels and altered cortisol stress reactivity following childhood trauma in humans. Nature communications, 7(1), 10967.

