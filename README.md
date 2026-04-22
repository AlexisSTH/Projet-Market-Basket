<div align="center">

# 🛒 Market Basket Analysis — Instacart

**Quels produits vos clients achètent-ils ensemble ?**

![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.8-11557C?style=flat)
![mlxtend](https://img.shields.io/badge/mlxtend-Apriori-orange?style=flat)
![Status](https://img.shields.io/badge/Status-Terminé-00e676?style=flat)



*Analyse de 3.4 millions de commandes pour identifier les associations produits et générer des recommandations business actionnables.*

---

[Contexte](#-contexte) · [Dataset](#-dataset) · [Résultats](#-résultats-clés) · [Structure](#-structure-du-projet) · [Installation](#-installation) · [Méthodologie](#-méthodologie)

</div>

---

## 🎯 Contexte

Un retailer en ligne souhaite **augmenter son panier moyen** et **optimiser le placement de ses produits**. Pour répondre à ce besoin, j'ai réalisé une analyse Market Basket Analysis (MBA) sur les données transactionnelles d'Instacart afin d'identifier les produits fréquemment achetés ensemble et proposer des recommandations cross-sell concrètes.

**Questions business :**
- Quels produits sont le plus souvent achetés ensemble ?
- Comment optimiser le placement en rayon pour favoriser les achats croisés ?
- Quelles promotions croisées proposer pour augmenter le chiffre d'affaires ?

---

## 📊 Dataset

| Donnée | Détail |
|---|---|
| **Source** | [Instacart Market Basket Analysis — Kaggle](https://www.kaggle.com/c/instacart-market-basket-analysis) |
| **Commandes** | 3.4 millions |
| **Lignes** | 32 millions (order_products) |
| **Produits** | 49 688 uniques |
| **Clients** | 206 209 |
| **Tables** | 6 (orders, products, order_products_prior, order_products_train, aisles, departments) |

---

## 🔑 Résultats clés

### Chiffres de l'exploration

| Métrique | Valeur |
|---|---|
| Produits par commande (moyenne) | **10.1** |
| Taux de réachat global | **59%** |
| Rayon le plus fréquent | Fresh fruits (55.3% des commandes) |
| Top produit | Banana |

### Top associations découvertes

| Si le client achète... | Il achète aussi... | Lift | Confidence |
|---|---|---|---|
| Fromage emballé | Pain | **1.56** | 36% |
| Herbes fraîches | Légumes emballés | **1.51** | 55% |
| Pain | Lait | **1.49** | 36% |

### Recommandations business

🏪 **Placement en rayon** — Rapprocher le fromage emballé du rayon boulangerie (lift 1.56)

🎯 **Promotions croisées** — Bundle "plateau apéro" fromage + pain, pack "cuisine maison" herbes + légumes

🛒 **Cross-sell en ligne** — Suggérer du fromage quand le client ajoute du pain au panier (confidence 36%)

---

## 🔬 Méthodologie

### 1. Exploration & Nettoyage
- Chargement et fusion de 6 tables relationnelles via les clés de jointure
- Vérification de l'intégrité des données (0 perte, 0 duplication)
- Statistiques descriptives et visualisations des comportements d'achat
- Échantillonnage de 10 000 clients avec paniers complets conservés

### 2. Transformation
- Construction d'une matrice panier binaire (commandes × rayons)
- Agrégation au niveau rayon (134 catégories) pour réduire la dimensionnalité
- Encodage binaire : 1 si le rayon est présent dans la commande, 0 sinon

### 3. Algorithme Apriori
- Extraction des itemsets fréquents (support minimum : 5%)
- Génération de 326 règles d'association
- Filtrage par lift (> 1.2) et confidence (> 40%)
- Exclusion des rayons trop fréquents pour révéler les associations surprenantes

### 4. Recommandations
- Traduction des règles statistiques en actions business concrètes
- Propositions de cross-merchandising, bundles promotionnels et cross-sell en ligne

---

## 💡 Ce que j'ai appris

- **Jointures multi-tables** sur des données volumineuses (32M de lignes)
- **Feature engineering transactionnel** : transformer des logs de commandes en matrice binaire exploitable
- **Algorithme Apriori** et interprétation des métriques (support, confidence, lift)
- **Gestion de la volumétrie** : échantillonnage intelligent pour garder des résultats fiables
- **Storytelling data** : traduire des résultats statistiques en recommandations business

---

<div align="center">

**Réalisé par [Alexis Sayasith](https://www.linkedin.com/in/alexis-sayasith-729a9819a/)**

Si ce projet vous intéresse, n'hésitez pas à ⭐ le repo !

</div>
