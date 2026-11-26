# CHANTIER OS — Version 1 (MVP)

Application web progressive (PWA) de suivi de chantier, en français. Cette première version fonctionne sans compte, sans backend et sans clé API. Les données sont conservées dans IndexedDB sur l'appareil.

## Fonctionnalités présentes
- Tableau de bord alimenté par les données locales.
- Entreprises préchargées et modifiables : AXIMA, ATEXIA, S2R, Briand charpente, Briand métallerie, CLIMEO et SBTPC.
- Fiches qualité, réserves et tâches avec création, modification, filtres et suppression.
- Saisie rapide par texte, dictée navigateur lorsqu'elle est disponible et enregistrement audio local.
- Extraction locale par règles : entreprises connues, effectifs (nombres et nombres écrits en lettres), localisation, certains mots-clés et dates relatives simples.
- Calendrier hebdomadaire et événements.
- Relevés d'effectifs par date et entreprise.
- Look Ahead.
- Comptes rendus de réunion (saisie et stockage des notes).
- Photos avant/après dans les fiches qualité et réserves.
- Ajout de photos et de vocaux depuis la saisie rapide.
- Export et restauration JSON, pièces jointes binaires comprises.
- PWA et cache hors connexion des fichiers de l'application.

## Limites connues
- L'analyse du langage est une extraction locale heuristique, pas un LLM. Toute proposition doit être vérifiée avant validation.
- La reconnaissance vocale dépend des fonctions disponibles dans le navigateur et peut nécessiter Internet. La dictée du clavier iPhone est une alternative.
- L'enregistrement audio conserve le fichier vocal, mais ne le transcrit pas automatiquement sur tous les appareils.
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
