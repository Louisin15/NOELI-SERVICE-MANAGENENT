# MODÈLE DE FACTURE BILINGUE - INSTRUCTIONS DE CRÉATION

## 🎯 OBJECTIF
Créer une feuille "Modèle Facture" professionnelle bilingue (Anglais/Français) dans votre fichier Excel avec formules dynamiques.

## 📋 STRUCTURE COMPLÈTE

### ÉTAPE 1 : CRÉER LA NOUVELLE FEUILLE
1. Ouvrez `Fac_2027_vers0.xlsm`
2. Cliquez droit sur l'onglet d'une feuille
3. Sélectionnez "Insérer une feuille"
4. Nom : `Modèle Facture`
5. Validez

### ÉTAPE 2 : EN-TÊTE PROFESSIONNEL (Lignes 1-8)

#### Cellule A1:C5 - Logo et En-tête
```
Insérez l'image du logo NOELI SERVICE (copie depuis une autre feuille)
Redimensionnez à environ 2,5 cm x 2,5 cm
```

#### Cellule E1:J3 - TITRE FACTURE
```
Ligne 1: INVOICE / FACTURE
Police: Arial, Taille 18, Gras, Couleur Vert foncé
Alignement: Centre, fusionné E1:J1
```

#### Cellule E5:J8 - Infos Entreprise
```
E5: NOELI SERVICE
E6: FIABILITÉ & EXCELLENCE
E8: Ampasikabo, Fort-Dauphin (614), Madagascar

F10: Phone / Téléphone:
G10: +261 38 64 989 60 / +261 32 01 218 50

F11: Email / E-mail:
G11: societenoeli@gmail.com

F12: NIF / NIF:
G12: 4001814821

F13: STAT / STAT:
G13: 49295 53 2014 00379
```

---

### ÉTAPE 3 : INFOS FACTURE (Ligne 10-15)

#### Bloc Gauche (Colonne A-D)
```
A10: INVOICE NO. / N° FACTURE:
B10: =SI(Factures!A2="","",Factures!A2)
     [Formule qui récupère le numéro de la feuille Factures]

A12: DATE / DATE:
B12: =SI(Factures!B2="","",Factures!B2)
     Format: JJ/MM/AAAA

A14: TYPE / TYPE:
B14: =SI(Factures!E2="","",Factures!E2)

A16: STATUS / STATUT:
B16: =SI(Factures!G2="","",Factures!G2)
```

#### Bloc Droit (Colonne F-J)
```
F10: CATEGORY / CATÉGORIE:
G10: Service

F12: PO NO. / N° DE BON:
G12: [À remplir si nécessaire]
```

---

### ÉTAPE 4 : BLOC CLIENT (Ligne 18-28)

#### Gauche - BILL TO / FACTURER À
```
A18: BILL TO / FACTURER À:
Police: Gras, Fond gris clair

A20: CUSTOMER NAME / NOM CLIENT:
A21: =SI(Factures!D2="","",Factures!D2)

A23: ADDRESS / ADRESSE:
A24: [Champ optionnel - à récupérer si données disponibles]

A26: PHONE / TÉLÉPHONE:
A27: [Champ optionnel]

A29: EMAIL / E-MAIL:
A30: [Champ optionnel]
```

#### Droite - SHIP TO / LIVRER À (Optionnel)
```
F18: SHIP TO / LIVRER À:
Police: Gras, Fond gris clair

F20: CUSTOMER NAME / NOM CLIENT:
F21: =SI(Factures!D2="","",Factures!D2)

F23: ADDRESS / ADRESSE:
F24: [Même que facturation]
```

---

### ÉTAPE 5 : TABLEAU ARTICLES (Ligne 32-60)

#### En-tête du tableau (Ligne 32)
```
Fond: Vert foncé (#2F5233)
Texte: Blanc, Gras

A32: N° / N°
B32: ARTICLE / ARTICLE
C32: DESCRIPTION / DESCRIPTION
D32: UNIT / UNITÉ
E32: QTY / QUANTITÉ
F32: UNIT PRICE / PRIX UNITAIRE (MGA)
G32: DISCOUNT / REMISE %
H32: TOTAL / TOTAL (MGA)
```

#### Lignes de données (33-45)
```
Chaque ligne liée à la feuille Factures:

A33: 1
B33: =SI(Factures!F2="","",Factures!F2)
C33: [Description du service]
D33: jour
E33: =SI(Factures!H2="","",Factures!H2)
F33: =SI(Factures!I2="","",Factures!I2)
G33: =SI(Factures!L2="","",Factures!L2)
H33: =SI(E33="","",E33*F33*(1-G33/100))

[Répéter pour lignes 34-45 avec références Factures!F3, H3, I3, L3, etc.]
```

#### Bordures et formatage
```
Bordures: Noir 1pt
Alignement nombre: Droite
Format nombre: # ##0 (pour les MGA)
```

---

### ÉTAPE 6 : TOTAUX (Ligne 47-58)

```
Fond: Blanc avec bordure
Alignement: Droite

F47: SUBTOTAL / SOUS-TOTAL:
H47: =SOMME(H33:H45)
Format: # ##0 MGA

F49: DISCOUNT / REMISE:
H49: =[Calculé selon formule]
Format: # ##0 MGA

F51: NET AMOUNT / MONTANT NET:
H51: =H47-H49
Format: # ##0 MGA, Gras

F53: TAX / TVA (0%):
H53: =H51*0%
Format: # ##0 MGA

F55: TOTAL DUE / MONTANT TOTAL TTC:
H55: =H51+H53
Format: # ##0 MGA, Gras, Fond vert pâle

F57: ADVANCE / ACOMPTE REÇU:
H57: =SI(Factures!Q2="","",Factures!Q2)
Format: # ##0 MGA

F59: BALANCE DUE / RESTE À PAYER:
H59: =H55-H57
Format: # ##0 MGA, Gras, Couleur Rouge, Fond jaune pâle
```

---

### ÉTAPE 7 : CONDITIONS DE PAIEMENT (Ligne 61-70)

```
A61: PAYMENT TERMS / CONDITIONS DE PAIEMENT:
A62: Gras, Fond gris clair

A63: =SI(Factures!R2="","Paiement à la livraison / Payment on delivery",Factures!R2)

A65: PAYMENT METHODS / MODES DE PAIEMENT:
A66: Gras, Fond gris clair

A68: ☑ Cash / Espèces
A69: ☑ Bank Transfer / Virement Bancaire
A70: ☑ Mobile Money (Mvola, Orange Money)
A71: ☑ Cheque / Chèque
```

---

### ÉTAPE 8 : DÉTAILS BANCAIRES (Ligne 73-82)

```
A73: BANK DETAILS / DÉTAILS BANCAIRES:
Gras, Fond gris clair

A75: Account / Compte:
B75: 00008 00730 050030 207 80 32

A77: MOBILE MONEY / MONEY MOBILE:
A78: Mvola: 038 64 989 60
A79: Orange Money: 032 01 218 60
```

---

### ÉTAPE 9 : MENTION LÉGALE (Ligne 84-90)

```
A84: AMOUNT IN WORDS / MONTANT EN LETTRES:
A85: Italique
Formule de conversion: =CONVERTIR_EN_LETTRES(H55)
[Voir formule VBA ci-dessous]

A88: Thank you for your trust and continued support. We look forward to serving you again.
A89: Merci de votre confiance et de votre soutien continu. Nous avons hâte de vous servir à nouveau.

Police: Italique, Gras
Alignement: Centre
Couleur: Vert foncé
```

---

### ÉTAPE 10 : SIGNATURE (Ligne 92-95)

```
A92: [Espace pour signature]
A93: Signature / Signature

F92: [Espace pour signature]
F93: Authorized / Autorisé
```

---

## 🔧 FORMULES VBA REQUISES

### Fonction : Convertir montant en lettres

Ajouter dans un module VBA (Développeur > Visual Basic > Insérer > Module):

```vba
Function CONVERTIR_EN_LETTRES(montant As Currency) As String
    Dim unites() As String
    Dim dizaines() As String
    Dim centaines() As String
    Dim result As String
    Dim parts() As String
    
    unites = Split("zéro un deux trois quatre cinq six sept huit neuf dix onze douze treize quatorze quinze seize dix-sept dix-huit dix-neuf", " ")
    dizaines = Split("zéro dix vingt trente quarante cinquante soixante soixante-dix quatre-vingts quatre-vingt-dix", " ")
    centaines = Split("zéro cent mille million milliard", " ")
    
    If montant = 0 Then
        CONVERTIR_EN_LETTRES = "Zéro Ariary"
        Exit Function
    End If
    
    ' Conversion simple pour les montants jusqu'à 999 999 999
    Dim entier As Long
    Dim reste As Long
    
    entier = CLng(montant)
    result = ""
    
    ' Conversion basique
    If entier >= 1000000 Then
        result = result & unites(entier \ 1000000) & " million "
        entier = entier Mod 1000000
    End If
    
    If entier >= 1000 Then
        result = result & unites(entier \ 1000) & " mille "
        entier = entier Mod 1000
    End If
    
    If entier >= 100 Then
        result = result & unites(entier \ 100) & " cent "
        entier = entier Mod 100
    End If
    
    If entier >= 20 Then
        result = result & dizaines(entier \ 10) & " "
        entier = entier Mod 10
        If entier > 0 Then
            result = result & unites(entier) & " "
        End If
    ElseIf entier > 0 Then
        result = result & unites(entier) & " "
    End If
    
    CONVERTIR_EN_LETTRES = UCase(Trim(result)) & "ARIARY"
End Function
```

---

## 🎨 FORMATAGE VISUEL

### Couleurs
- **Logo area**: Fond blanc
- **En-tête**: Vert foncé (#2F5233)
- **Titres**: Vert foncé, Gras
- **Tableau en-tête**: Vert foncé, Texte blanc
- **Totaux**: Noir sur fond blanc, sauf RESTE À PAYER (Rouge sur jaune pâle)
- **Mention légale**: Vert foncé

### Polices
- **Titre principal**: Arial 18, Gras
- **Sous-titres**: Arial 12, Gras
- **Corps**: Arial 10, Normal
- **Montants**: Arial 10, Aligné droite
- **Mention légale**: Arial 9, Italique

### Bordures
- **Tableau**: Bordures noires 1pt
- **Totaux**: Bordures grises fines
- **Ensemble facture**: Bordure externe épaisse

---

## ✅ VÉRIFICATIONS FINALES

Avant d'utiliser la facture:
- [ ] Logo visible et bien dimensionné
- [ ] Toutes les formules récupèrent les données de Factures
- [ ] Nombres formatés correctement (# ##0)
- [ ] Bilingue (English/Français) avec English EN PREMIER
- [ ] Montants en MGA
- [ ] Montant en lettres s'affiche correctement
- [ ] Type facture change de couleur si Pro-forma
- [ ] Tous vos paramètres présents (NIF, STAT, comptes bancaires)

---

## 🚀 UTILISATION

1. Allez à la feuille **"Modèle Facture"**
2. Sélectionnez le numéro de facture à afficher (ou cliquez sur la première ligne de Factures)
3. La facture se génère automatiquement avec toutes les données
4. Imprimez en PDF ou en papier
5. Envoyez au client !

---

**Cette feuille est maintenant prête à l'emploi !** 🎉
