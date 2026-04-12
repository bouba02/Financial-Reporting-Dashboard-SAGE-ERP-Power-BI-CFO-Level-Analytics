# 📊 Tableau de Bord de Reporting des Etats Financiers — Power BI

## 🚀 Vue d’ensemble

Ce projet présente la conception et la mise en œuvre d’un **système de reporting financier et d’aide à la décision** développé avec Power BI.

[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)](https://www.microsoft.com/excel)
[![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)](https://dax.guide)
[![Licence](https://img.shields.io/badge/Licence-MIT-green?style=for-the-badge)](LICENSE)



L’objectif n’était pas de créer un simple dashboard, mais un **véritable outil de pilotage financier** permettant :

- Un suivi en temps réel de la performance  
- Une analyse fine des coûts et de la rentabilité  
- Un pilotage de la trésorerie et du BFR  
- Une prise de décision rapide et éclairée  

⚠️ **Note :** Pour des raisons de confidentialité, aucune donnée réelle ni capture du dashboard final ne sont partagées.  
Ce dépôt met l’accent sur **l’architecture, la modélisation et la logique métier**.

---

## 💡 Problématique métier

Dans de nombreuses entreprises :

- Le reporting financier est manuel et chronophage  
- Les indicateurs clés sont difficiles à exploiter  
- Les décisions sont prises avec du retard  
- Les données comptables sont peu valorisées  

👉 Ce projet répond à ces enjeux en transformant des données comptables brutes en **outil de pilotage dynamique et décisionnel**.

---

## 🧠 Fonctionnalités principales

### 📊 Analyse financière

- Analyse du chiffre d’affaires (Total, Export vs Local)  
- Suivi de la rentabilité (Marge brute, Résultat net)  
- Analyse de la structure des charges  
- Suivi de la performance financière  

### 💰 Trésorerie & BFR

- Calcul du Besoin en Fonds de Roulement (BFR)  
- Analyse du Cash Runway  
- Suivi des flux de trésorerie (entrées / sorties)  
- Système d’alertes sur la liquidité  

### 🧾 Intégration comptable avancée

- Intégration complète du **Grand Livre (SAGE)**  
- Exploitation de +4000 écritures comptables  
- Drill-through jusqu’au niveau des transactions  

### ⚡ Analyse avancée

- Alertes automatiques (marge, DSO, liquidité)  
- Analyse de concentration clients  
- Segmentation dynamique (clients, fournisseurs, géographie)  

---

## 🏗️ Architecture du modèle de données

Le projet repose sur une architecture en **schéma étoile (Star Schema)**, optimisée pour la performance et la scalabilité.

### 🔹 Composants principaux :

#### Table de faits
- `Faits_GrandLivre` → table centrale contenant les écritures comptables

#### Tables de dimensions
- `DimCalendrier` → analyse temporelle  
- `DimTiers` → clients & fournisseurs  
- `DimMapping` → classification comptable (PCGE)

#### Tables de liaison (Bridge)
- `Bridge_Piece_Tiers` → attribution du CA aux clients  
- `Bridge_Piece_Fourn` → attribution des achats aux fournisseurs  

#### Tables déconnectées
- Utilisées pour les waterfall, KPI, segmentation et logique métier avancée  

---

## 📐 Modèle de données

![Dashboard Preview](Schema_Etoile.png)
---

## ⚙️ Traitement des données

### 🔄 Power Query

- Extraction des données depuis plusieurs fichiers Excel (exports SAGE)  
- Nettoyage et normalisation des données  
- Création de colonnes calculées :
  - Classe de compte  
  - Racine comptable  
  - Détection des extournes  

### 📊 Volume de données

- +4 000 écritures comptables  
- 15+ tables  
- 100+ mesures DAX  

---

## 🧮 Mesures DAX

Plus de **100 mesures DAX** ont été développées pour couvrir les besoins métiers.

### 📈 Rentabilité

- `CA_Total`  
- `Marge_Brute`  
- `EBITDA`  : Earnings Before Interest, Taxes, Depreciation & Amortization = Marge Brute - Charges Personnel - Charges Fixes.
- `Résultat_Net`  

### 💰 Trésorerie & BFR

- `BFR`  : Besoin en Fonds de Roulement = Créances + Stock - Dettes fournisseurs - Dettes fiscales - Dettes associés. BFR négatif = favorable, les fournisseurs financent l'activité.
- `DSO`: Days Sales Outstanding = Créances clients / (CA / 365). Délai moyen de recouvrement client en jours.
- `DPO`: Days Payable Outstanding = Dettes fournisseurs / (Total Charges / 365). Délai moyen de paiement fournisseurs. 
- `DIO`  : Days Inventory Outstanding = Stock / (Coût Variable / 365). Délai moyen de rotation des stocks en jours. 
- `Cash_Runway_Mois`  : Nombre de mois pendant lesquels l'entreprise peut fonctionner avec sa trésorerie actuelle au rythme de dépenses actuel.

### 📊 Analyses avancées

- Calculs contextuels dynamiques  
- KPIs et labels intelligents  

---

## 🔍 Fonctionnalités avancées

- Drill-through jusqu’aux écritures du grand livre  
- Filtres dynamiques globaux  
- Indicateurs contextuels (global vs client)  
- Analyse en waterfall (CPC & BFR)  

---

## 📊 Structure du dashboard

Le dashboard est structuré en 6 pages principales :

1. Vue Exécutive  
2. Compte de Résultat (CPC)  
3. Analyse du CA & Tiers  
4. Analyse des Charges  
5. BFR & Trésorerie  
6. Détail du Grand Livre
7. Une page pour permettre au comptable d'ajouter des commentaires pour sa présentation 

---

## 📈 Impact métier

✔️ Réduction significative du temps de production des reportings  
✔️ Présentation plus rapide et plus claire des états financiers  
✔️ Meilleure communication entre comptabilité et direction  
✔️ Suivi en temps réel de la performance financière  

👉 Passage d’un reporting statique  
👉 à un pilotage financier continu et décisionnel  

---

## 🔐 Confidentialité des données

Afin de respecter la confidentialité du client :

- Aucune donnée réelle n’est exposée  
- Aucun visuel du dashboard final n’est partagé  
- Le modèle est présenté de manière générique  

---

## 🛠️ Outils & technologies

- Power BI  
- Power Query (M)  
- DAX  
- Excel (source de données)  



---

## 👤 Auteur

**Boubacar Nikiema**  
Data Analyst | Consultant BI  

📧 nikiemaboubacar@gmail.com  
📱 +212 676 86 1686  

---

## 🤝 Me contacter

Vous souhaitez :

- Automatiser votre reporting financier  
- Mettre en place un pilotage par la donnée  
- Transformer vos données en levier stratégique  

👉 N’hésitez pas à me contacter.
