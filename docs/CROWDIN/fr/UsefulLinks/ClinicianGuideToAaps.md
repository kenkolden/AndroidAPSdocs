# Pour les professionels de santé – Une introduction générale et un guide pour AAPS

Cette page est destinée aux professionels de santé qui ont exprimé leur intérêt pour la technologie du pancréas artificiel en open source comme AAPS, ou pour les patients qui veulent partager ces informations avec leur équipe médicale.

Ce guide contient des informations de haut niveau sur la boucle fermée DIY et plus précisément sur la façon dont AAPS fonctionne. Pour plus de détails sur tous ces sujets, veuillez consulter la [documentation complète AAPS en ligne](../index.md). Si vous avez des questions, demandez à votre patient pour plus de détails, ou n'hésitez pas à rejoindre la communauté. (Si vous n'êtes pas sur les réseaux sociaux (par ex. [Twitter](https://twitter.com/kozakmilos) ou Facebook), n'hésitez pas à envoyer un email à developers@AndroidAPS.org). [Vous pouvez également trouver quelques-unes des dernières études & et les données relatives aux résultats ici](https://openaps.org/outcomes/).

## Les étapes pour construire une boucle fermée DIY :

Pour commencer à utiliser AAPS, les étapes suivantes doivent être faites :

* Find a [compatible pump](../Getting-Started/CompatiblePumps.md), a [compatible Android device](../Getting-Started/Phones.md), and a [compatible CGM source](../Getting-Started/CompatiblesCgms.md).
* [Download the AAPS source code and build the software](../SettingUpAaps/BuildingAaps.md).
* [Configure the software to talk to their diabetes devices and specify settings and safety preferences](../SettingUpAaps/SetupWizard.md).

## Comment fonctionne une boucle fermée DIY

En l'absence d'un système à boucle fermée, une personne diabétique recueille les données de sa pompe et de sa MGC, décide de ce qu'il faut faire et agit.

Avec l'administration automatisée de l'insuline, le système fait la même chose: il recueille des données de la pompe, de la CGM, et partout ailleurs où des informations sont renseignées (comme Nightscout), utilise ces informations pour calculer et décider de la quantité d'insuline plus ou moins nécessaire (au-dessus ou en dessous du débit de basal sous-jacent), et utilise des débits de basal temporaires pour effectuer les ajustements nécessaires pour garder ou éventuellement amener les Glycémies dans la plage cible.

If the device running AAPS breaks or goes out of range of the pump, once the latest temporary basal rate ends, the pump falls back to being a standard pump with the preprogrammed basals rates running.

## Comment les données sont collectées :

Avec AAPS, un appareil Android exécute une application spéciale pour faire le calcul, l'appareil communique en Bluetooth avec une pompe prise en charge. AAPS peut communiquer avec d'autres appareils ainsi que vers le cloud en utilisant le wifi ou les données mobiles pour recueillir des informations supplémentaires, et de faire des rapports au patient, aux soignants et à ses proches sur ce qu'il fait et pourquoi.

Le périphérique Android doit :

* communiquer avec la pompe et lire l'historique - combien d'insuline a été délivrée
* communiquer avec le capteur MGC (soit directement, soit via le cloud) - pour voir ce que les Glycémies font / ont fait

Lorsque l'appareil a collecté ces données, l'algorithme s'exécute et prend la décision en fonction des paramètres (SI, ratio glucides/insuline , DAI, cible, etc.). Si nécessaire, il émet alors des commandes à la pompe pour modifier le débit d'insuline.

Il recueillera également toutes les informations sur les bolus, la consommation de glucides et les ajustements cibles temporaires de la pompe ou de Nightscout pour les utiliser pour le calcul des taux d'administration d'insuline.

## Comment sait-elle quoi faire?

Le logiciel open source est conçu pour permettre à l'appareil de faire facilement le travail que les gens faisaient (en mode manuel) pour calculer comment la livraison d'insuline doit être ajustée. Il recueille d'abord les données de tous les appareils pris en charge ainsi que sur le cloud, prépare les données et exécute les calculs, fait des prévisions sur les niveaux de glycémie attendus au cours des prochaines heures dans différents scénarios et calcule les ajustements nécessaires pour conserver ou ramener la Glycémie dans la plage cible. Ensuite, il envoie des ajustements nécessaires à la pompe. Puis il lit les données en retour, et refait les calculs encore et encore.

Comme le paramètre d'entrée le plus important est la glycémie provenant du capteur MGC, il est important d'avoir des données MGC de très bonne qualité.

AAPS est conçu pour suivre de façon transparente toutes les données d'entrée qu'il recueille, la recommandation qui en résulte et toute mesure prise. Il est donc facile de répondre à la question à tout moment, "pourquoi est-ce que cela fait X ?" en examinant les journaux.

## Exemples de prise de décision de l'algorithme AAPS :

AAPS utilise les mêmes algorithmes et les mêmes jeux de fonctions que OpenAPS. L'algorithme fait des prédictions multiples (basées sur les paramètres et la situation) représentant différents scénarios de ce qui pourrait arriver à l'avenir. Dans Nightscout, ces lignes sont affichées sous la forme de "lignes violettes". AAPS uses different colors to separate these [prediction lines](#aaps-screens-prediction-lines). Dans les logs, il décrira laquelle de ces prédictions et quelle période est à l'origine des actions nécessaires.

### Voici des exemples de lignes de prédiction pourpres et de la façon dont elles peuvent varier :

![Exemples de ligne de prédiction violette](../images/Prediction_lines.jpg)

### Voici des exemples de différents délais qui influencent les ajustements nécessaires à l'administration d'insuline :

### Scénario 1 - Zéro Temp pour la sécurité

Dans cet exemple, la Glycémie est en hausse à court terme ; cependant, il est prévu qu'elle sera faible sur une période plus longue. En effet, il est prévu de passer en dessous de la cible *et* sous le seuil de sécurité. Pour la sécurité et prévenir l'hypoglycémie, AAPS émettra une "Zéro-temp" (débit de base temporaire à 0%), jusqu'à ce que la glycémie estimée (dans toute la période projetée) soit au dessus du seuil de sécurité.

![Dosage scénario 1](../images/Dosing_scenario_1.jpg)

### Scénario 2 - Zéro temp pour la sécurité

Dans cet exemple, on prévoit que la glycémie sera faible à court terme, mais on prévoit qu'elle sera plus tard au-dessus de la cible. Cependant, comme le point bas à court terme est en dessous du seuil de sécurité, AAPS émettra une zéro-temp, jusqu'à ce qu'il n'y ait plus aucun point de la ligne de prédiction qui soit inférieur au seuil.

![Dosage scénario 2](../images/Dosing_scenario_2.jpg)

### Scénario 3 - Plus d'insuline nécessaire

Dans cet exemple, une prévision à court terme montre une baisse en dessous de la cible. Toutefois, il n'est pas prévu qu'elle soit inférieure au seuil de sécurité. La glycémie finale est au-dessus de la cible. Par conséquent, AAPS va s'abstenir de tout ajout à l'insuline qui contribuerait à court terme à une hypoglycémie (l'ajout d'insuline ferait passer la prédiction en-dessous du seuil de sécurité). Il évaluera plus tard s'il a besoin d'ajouter de l'insuline pour ramener le niveau de la glycémie prévisionnelle plus proche de la cible, une fois qu'il est sûr de pouvoir le faire sans risque. *(En fonction des paramètres, de la quantité et du moment où l'insuline est requise, cette insuline peut être administrée via des basales temporaires ou des SMB (super micro bolus)).*

![Dosage scénario 3](../images/Dosing_scenario_3.jpg)

### Scénario 4 - Temporaire basse pour la sécurité

Dans cet exemple, AAPS voit que la glycémie est bien au-dessus de la cible. Cependant, en raison de la durée d'action de l'insuline, il y a déjà assez d'insuline dans le corps pour amener la glycémie vers la cible. En fait, on prévoit même que la glycémie sera en dessous de la cible. Par conséquent, AAPS ne fournira pas d'insuline supplémentaire, de sorte qu'elle ne contribuera pas à rallonger une période de glycémie basse. Bien que la glycémie soit élevée/en hausse, un faible débit de basal temporaire sera probable dans ce cas.

![Dosage scénario 4](../images/Dosing_scenario_4.jpg)

## Optimiser les paramètres et faire des modifications

En tant que professionnel de santé qui n'a pas d'expérience avec AAPS ou les boucles fermées DIY, vous pouvez trouver qu'il est difficile d'aider votre patient à optimiser ses paramètres ou de faire des changements pour améliorer ses résultats. Nous avons plusieurs outils et [des guides](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/optimize-your-settings.html) dans la communauté pour aider les patients à faire de petits ajustements pour améliorer leurs paramètres.

La chose la plus importante pour les patients est de faire un seul changement à la fois, et d'observer l'impact pendant 2-3 jours avant de choisir de changer ou de modifier un autre paramètre (sauf s'il s'agit évidemment d'un mauvais changement qui aggrave les choses, auquel cas ils doivent revenir immédiatement au réglage précédent). La tendance humaine est de tourner tous les boutons et de tout changer en même temps; mais si on le fait, on peut se retrouver avec d'autres paramètres moins optimaux pour l'avenir et il peut être difficile de revenir à un bon état stable connu.

L'un des outils les plus puissants pour faire des changements de paramètres est un outil de calcul automatisé pour les débits de basale, SI et ratio G/I. Cela s'appelle « [Autotune](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html) ». Il est conçu pour être exécuté indépendamment / manuellement et permet de vous guider, vous ou votre patient, dans la modification progressive des paramètres. Il est recommandé dans la communauté d'exécuter (ou de revoir) les rapports Autotune avant de tenter de faire des ajustements manuels des paramètres. Avec AAPS, Autotune sera exécuté comme un "outil indépendant", bien qu'il y ait des efforts continus pour l'incorporer directement dans AAPS également. As these parameters are a prerequisite both for standard pump insulin delivery and for closed loop insulin delivery, discussion of the autotune results and adjustment of these parameters would be the natural link to the clinician.

En outre, le comportement humain (tiré des enseignements d'une gestion manuelle du diabète) influence souvent les résultats, même avec une boucle fermée DIY. Par exemple, si une hypoglycémie est prévue et que AAPS réduit l'insuline pendant la baisse, seule une petite quantité de glucides (par exemple 3 à 4 g) peut être suffisante pour ramener la glycémie au dessus de 70 mg/dl (3,9 mmol). Toutefois, dans de nombreux cas, quelqu'un peut choisir de traiter avec beaucoup plus de glucides (par ex. en appliquant la règle des 15g), qui provoqueront un pic de la glycémie lié à la fois aux glucides pris en excédent et parce que l'insuline a été réduite dans la période ou la glycémie était en train de descendre.

## OpenAPS

**Ce guide a été adapté de [The clinician's guide to OpenAPS](https://openaps.readthedocs.io/en/latest/docs/Resources/clinician-guide-to-OpenAPS.html).** OpenAPS est un système développé pour fonctionner sur un tout petit ordinateur portable (généralement appelé le « Rig »). AAPS utilise beaucoup des techniques mises en œuvre dans OpenAPS, et partage une grande partie de la logique et des algorithmes, c'est pourquoi ce guide est très similaire au guide original. Une grande partie des informations concernant OpenAPS peuvent être transposées à AAPS, la principale différence étant la plate-forme matérielle sur laquelle est exécuté le logiciel.

## Résumé

Il s'agit d'un aperçu macroscopique de la façon dont AAPS fonctionne. Pour plus de détails, demandez à votre patient, à la communauté, ou lisez la documentation complète de AAPS disponible en ligne.

Autres lectures recommandées :

* The [full AAPS documentation](../index.md)
* Le document [OpenAPS Reference Design](https://OpenAPS.org/reference-design/), qui explique comment OpenAPS est conçu pour la sécurité : https://openaps.org/reference-design/
* La [documentation complète OpenAPS](https://openaps.readthedocs.io/en/latest/index.html) 
  * Plus de [détails sur les calculs d'OpenAPS](https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/Understand-determine-basal.html#understanding-the-determine-basal-logic)