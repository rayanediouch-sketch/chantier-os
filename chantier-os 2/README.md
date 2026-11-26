# CHANTIER OS — Version 2 (MVP amélioré)

Application web progressive (PWA) de suivi de chantier, en français. Cette première version fonctionne sans compte, sans backend et sans clé API. Les données sont conservées dans IndexedDB sur l'appareil.

## Fonctionnalités présentes
- Tableau de bord alimenté par les données locales.
- Entreprises préchargées et modifiables : AXIMA, ATEXIA, S2R, Briand charpente, Briand métallerie, CLIMEO et SBTPC.
- Fiches qualité, réserves et tâches avec création, modification, filtres et suppression.
- Saisie vocale prioritaire avec dictée continue via Web Speech API lorsque le navigateur la prend en charge.
- Transcription modifiable avant analyse ; possibilité de conserver aussi le fichier audio original.
- Secours iPhone : dictée native du clavier dans le champ de transcription.
- Classement local multi-éléments : effectifs, observations qualité, tâches et interventions, avec extraction de quelques entreprises, quantités, niveaux, bâtiments et échéances.
- Calendrier hebdomadaire et événements.
- Relevés d'effectifs par date et entreprise.
- Look Ahead.
- Comptes rendus de réunion (saisie et stockage des notes).
- Photos avant/après dans les fiches qualité et réserves.
- Ajout de photos et de vocaux depuis la saisie rapide.
- Export et restauration JSON, pièces jointes binaires comprises.
- PWA et cache hors connexion des fichiers de l'application.

## Limites connues
- Le classement est un moteur de règles métier local, pas une IA générative : il ne comprend pas toutes les formulations et chaque proposition doit être vérifiée.
- La dictée Web Speech dépend du navigateur, de la connexion et des autorisations micro. Sur iPhone, utiliser le micro du clavier si la dictée directe n'est pas prise en charge.
- L'enregistrement audio seul conserve le fichier vocal ; il ne le transcrit pas automatiquement.
- Aucun service cloud IA, abonnement ou clé API n'est utilisé. Une véritable compréhension générative gratuite et illimitée ne peut pas être garantie sans héberger/exécuter un modèle dédié.
- L'import et l'analyse de PDF, l'extraction automatique des actions de réunion, les notifications push et une galerie média dédiée restent à développer.
- Les données restent sur un seul navigateur/appareil. Il n'y a pas de synchronisation multi-appareils.
- Un hébergement HTTPS est nécessaire pour installer la PWA et utiliser le Service Worker. L'application n'inclut aucun service d'hébergement.

## Lancer en local
Nécessite un serveur HTTP local (pas `file://`). Avec Python :

```bash
python3 -m http.server 8080
```

Ouvrir ensuite `http://localhost:8080`.

## Installer sur iPhone
1. Héberger le dossier sur une adresse HTTPS (GitHub Pages peut convenir pour un dépôt public).
2. Ouvrir l'adresse dans Safari.
3. Toucher Partager puis « Sur l'écran d'accueil ».
4. Lancer CHANTIER OS depuis l'icône.

## Sauvegarde
Dans Paramètres & sauvegarde, utiliser « Exporter ma sauvegarde ». Conserver une copie du JSON dans un emplacement sûr. Pour restaurer, sélectionner le fichier JSON correspondant. Les photos et enregistrements audio sont inclus dans la sauvegarde.

## Sécurité
Les données sont stockées localement dans le navigateur. Elles ne sont pas chiffrées par l'application. Protéger le téléphone, faire des sauvegardes et ne pas importer de données confidentielles sans autorisation de l'entreprise.
