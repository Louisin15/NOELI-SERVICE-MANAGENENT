# NOELI SERVICE — Gestion / Management

Classeur de gestion bilingue FR/EN pour NOELI SERVICE (Fort-Dauphin, Madagascar).

## Contenu / Contents

Les fichiers CSV sont des modèles importables dans Excel, LibreOffice Calc et Google Sheets :

- `data/DATA_CLIENTS.csv` — clients existants et lignes disponibles pour de nouveaux clients.
- `data/SERVICES_TARIFS.csv` — services et tarifs indicatifs flexibles.
- `data/PARAMETRES.csv` — paramètres de l’entreprise, TVA, paiements et numérotation.
- `templates/FACTURES.csv` — structure de suivi des factures.
- `templates/DEVIS.csv` — structure de suivi des devis.
- `templates/PAIEMENTS.csv` — structure de suivi des paiements.
- `templates/BONS_LIVRAISON.csv` — structure des bons de livraison.
- `templates/BONS_RECEPTION.csv` — structure des bons de réception.
- `templates/STOCKS.csv` — module de stock prêt à activer ultérieurement.
- `docs/CONFIGURATION_FR_EN.md` — guide de configuration et d’utilisation.

## Importation dans Excel / Import into Excel

1. Ouvrir Excel.
2. Utiliser **Données → À partir d’un fichier texte/CSV**.
3. Importer chaque fichier dans une feuille portant le nom indiqué.
4. Choisir l’encodage **UTF-8** et le séparateur **point-virgule**.
5. Enregistrer le classeur sous `NOELI_SERVICE_GESTION.xlsx`.

Les CSV servent de base fiable et compatible. Les formules de calcul et les contrôles peuvent ensuite être ajoutés dans le classeur selon Excel ou LibreOffice.

## Accès / Access

Le dépôt est privé. Ne partager l’accès qu’avec les utilisateurs autorisés. Les coordonnées de paiement sont des informations sensibles.

## Numérotation / Numbering

- Facture / Invoice : `FAC/NS-AAAA-000`
- Devis / Quote : `DEV/NS-AAAA-0000`
- Bon de livraison / Delivery note : `BL/NS-AAAA-000`
- Bon de réception / Receipt note : `BR/NS-AAAA-000`

L’année est volontairement paramétrable dans `data/PARAMETRES.csv`.
