# Téléversement Open Humans

## Donner vos données pour la science

Vous pouvez aider la communauté en faisant don de vos données à des projets de recherche ! Cela aide les scientifiques à avancer, à développer de nouvelles idées scientifiques et à élargir les esprits concernant les systèmes de boucle fermée open source. AAPS is ready to synchronize your data with [Open Humans](https://www.openhumans.org), a platform allowing you to upload, connect, and store your personal data – such as genetics, activity and health data.

Vous gardez le contrôle total sur l'utilisation de vos données et sur les projets que vous voulez soutenir en leur donnant accès à vos données. Selon les projets que vous avez rejoint, les données sont évaluées et utilisées par eux de différentes manières.

Les données suivantes seront envoyées sur votre compte Open Humans :

- Glycémies
- Événements Careportal (sauf les notes)
- Bolus étendus
- Changements de profil
- Doses Quotidiennes Totales
- Basales temporaires
- Cibles temporaires
- Préférences
- Version de l'application
- Modèle d’appareil
- Dimensions de l'écran

Les informations secrètes ou privées telles que votre URL Nightscout ou votre API secret ne seront pas téléchargées.

## Paramètres

1. Créez votre compte sur [Open Humans](https://www.openhumans.org) si ce n'est pas déjà fait. Vous pouvez réutiliser vos comptes Google ou Facebook existants si vous le souhaitez.
2. Enable the “Open Humans” plugin in [Config Builder > Synchronization](../SettingUpAaps/ConfigBuilder.md).
3. Ouvrez son réglage en utilisant le bouton roue crantée. Vous pouvez restreindre le téléversement au périodes où le téléphone utilise le Wi-Fi et/ou est en charge.
4. Open the Open Humans Plugin (either through OH tab or hamburger menu) and click 'LOGIN'.

![Open Humans Config Builder](../images/OHUploader1.png)

5. Lisez attentivement les informations fournies à propos du téléversement Open Humans et les conditions d'utilisation.
6. Confirmez en cochant la case et cliquez sur 'CONNEXION'.
7. Le site web Open Humans sera ouvert. Veuillez vous connecter avec vos identifiants.
8. Decide whether you want to hide your AAPS Uploader membership in your public Open Humans profile.
9. Cliquez sur le bouton 'Authorize project'.

![Open Humans Terms of Use + Login](../images/OHUploader2.png)

10. En retournant à AAPS, vous verrez un message de connexion réussie.
11. Garder le plugin Open Humans Uploader et le téléphone activés pour que l'installation se termine.
12. Après avoir cliqué sur fermer, vous verrez votre identifiant de membre (ID). La taille de la file d'attente > 0 montre qu'il y a encore des données à télécharger.
13. Cliquez sur 'DECONNEXION' si vous voulez arrêter de télécharger des données vers Open Humans.
14. La notification Android vous informera sur le téléversement en cours.

![Open Humans finish setup](../images/OHUploader3.png)

15. Vous pouvez gérer vos données en vous connectant sur le [site web Open Humans](https://www.openhumans.org).

![Open Humans manage data](../images/OHWeb.png)

## Opportunités de partage

### [Le projet 'OPEN'](https://www.open-diabetes.eu/)

Le projet "OPEN" rassemble un consortium international et intersectoriel de patients innovateurs, de médecins, de spécialistes des sciences sociales, d'informaticiens et d'organisations de défense des patients afin d'étudier les divers aspects des systèmes de pancréas artificiels à faire soi-même (DIY APS) qui sont utilisés par un nombre croissant de personnes atteintes de diabète. Pour plus de détails, voir leur [site web](https://www.open-diabetes.eu/).

En septembre 2020, le projet 'OPEN' a lancé une [enquête](https://survey.open-diabetes.eu/) incluant l'option de donner des données que vous avez téléchargées sur Open Humans. Un [tutoriel](https://open-diabetes.eu/en/open-survey/survey-tutorials/) sur comment faire don de vos données au projet 'OPEN' est disponible sur leur site et dans le cadre de l'enquête.

### [Données communes OpenAPS](https://www.openhumans.org/activity/openaps-data-commons/)

OpenAPS Data Commons a été créé pour permettre facilement de partager les jeux de données de la communauté DIYAPS pour la recherche. Les données sont partagées à la fois avec des chercheurs traditionnels qui créeront des études de recherche traditionnelles et avec des groupes ou des individus de la communauté qui souhaitent examiner les données dans le cadre de leurs propres projets de recherche. The OpenAPS Data Commons uses the 'Open Humans' platform to enable people to easily upload and share their data from DIYAPS including AAPS, Loop, and OpenAPS.

Vous pouvez envoyer vos données dans Open Humans par l'un des trois moyens suivants :

1. use the AAPS uploader option to get your data into Open Humans
2. utilisez le transfert de données Nightscout pour déverser vos données dans Open Humans
3. téléchargez manuellement des fichiers de données dans Open Humans.

Une fois que vous avez créé un compte et remonté vos données dans Open Humans, assurez-vous également de rejoindre OpenAPS Data Commons afin de donner vos données pour la recherche si vous le souhaitez.

## Conditions d’Utilisation

Ceci est un outil open source qui copiera vos données dans [Open Humans](https://www.openhumans.org). Nous ne nous réservons aucun droit de partager vos données avec des tiers sans votre autorisation explicite. Les données que le projet et l'application reçoivent sont identifiées via un identifiant utilisateur aléatoire et ne seront transmises de manière sécurisée à un compte Open Humans qu'avec votre autorisation. Vous pouvez arrêter le téléchargement et supprimer vos données à tout moment via [www.openhumans.org](https://www.openhumans.org). Ayez conscience que certains projets qui reçoivent les données ne le supportent pas.

Voir aussi les [Conditions d'utilisation Open Humans](https://www.openhumans.org/terms/).

## Protection des données

Open Humans s'occupe de la protection de votre vie privée en vous assignant un identifiant numérique pour chaque projet. Cela permet aux projets de vous reconnaître mais pas vous identifier. The Application ID uploaded by AAPS is similar and only helps administrate the data. Plus d'informations peuvent être trouvées ici :

- [Règles d'utilisation des données Open Humans](https://www.openhumans.org/data-use/)
- [Open Humans et GDPR](https://www.openhumans.org/gdpr/)
