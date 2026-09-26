# Configuration / Configuration — NOELI SERVICE

## Important

Ce dépôt contient des modèles CSV compatibles avec Excel, LibreOffice Calc et Google Sheets. Les fichiers sont une base de travail : ils ne remplacent pas une validation comptable ou juridique locale.

## Création du classeur / Create the workbook

1. Télécharger le dépôt privé : **Code → Download ZIP**.
2. Décompresser l’archive.
3. Dans Excel, créer un nouveau classeur.
4. Importer chaque CSV comme une feuille séparée avec l’encodage UTF-8 et le séparateur `;`.
5. Nommer les feuilles : `Clients`, `Services_Tarifs`, `Parametres`, `Factures`, `Devis`, `Paiements`, `BL`, `BR`, `Stocks`.
6. Enregistrer en `.xlsx` ou `.ods`.

## Numérotation / Numbering

Les modèles utilisent les formats suivants :

- Factures : `FAC/NS-2026-001` — 3 chiffres.
- Devis : `DEV/NS-2026-0001` — 4 chiffres.
- Bons de livraison : `BL/NS-2026-001`.
- Bons de réception : `BR/NS-2026-001`.

Pour éviter les doublons, ne pas supprimer une ligne déjà utilisée. Pour une automatisation robuste avec plusieurs utilisateurs, attribuer le numéro au moment de la validation du document et protéger les colonnes de numérotation.

## Formules / Formulas

Dans Excel français, pour une ligne de facture :

- Montant HT : `=Quantité*Prix_unitaire`
- TVA : `=Montant_HT*TVA%`
- Total TTC : `=Montant_HT+TVA`
- Échéance : `=Date+Délai`
- Solde : `=Total_TTC-Montant_payé`

Dans Excel anglais, remplacer les fonctions localisées par leurs équivalents anglais si nécessaire.

## Nouveaux clients / New customers

La feuille `DATA_CLIENTS.csv` contient des lignes réservées `NS-CL-0011` à `NS-CL-0030`. Remplacer le nom et compléter les champs. Ajouter d’autres lignes en conservant le format `NS-CL-####`.

## Rôles recommandés / Recommended roles

- **Félix Fianara Louisin Faramanitra Razafindrabeno** — Admin : accès complet.
- **Rasolonirina Jocelyne** — Ventes : clients, devis, factures et bons.
- **FARAMANITRA Niritsambatra Ethan** — Finance : paiements, rapports et consultation.

Les autorisations réelles doivent être configurées dans OneDrive/SharePoint, Google Drive ou le serveur utilisé. Un fichier Excel envoyé par e-mail ne fournit pas une gestion fiable des permissions.

## Tableau de bord / Dashboard

Créer des tableaux croisés dynamiques sur `Factures` et `Paiements` pour :

- CA mensuel et annuel / Monthly and yearly revenue;
- CA par service / Revenue by service;
- clients les plus rentables / most profitable customers;
- impayés / unpaid invoices;
- état des stocks / inventory status;
- graphiques d’évolution / trend charts.

## Sauvegarde et sécurité / Backup and security

Effectuer une sauvegarde périodique. Ne pas publier le dépôt. Limiter les collaborateurs GitHub aux trois utilisateurs autorisés et éviter de placer des mots de passe ou des clés d’API dans les fichiers.
