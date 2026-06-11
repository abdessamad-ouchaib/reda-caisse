# REDA — Caisse Enregistreuse Pro

Application de caisse enregistreuse professionnelle sous forme de **Progressive Web App (PWA)**.  
Fonctionne sur **téléphone, tablette et ordinateur** — installable comme une application native.

🔗 **Démo live :** déployable sur Vercel ou GitHub Pages en 1 clic.

---

## Fonctionnalités

| Fonctionnalité | Description |
|---|---|
| 🏷 Scanner code-barres | Caméra plein écran avec cadre de visée et retour sonore |
| ⚖ Produits au poids | Pavé numérique dédié pour les produits vendus au kg |
| 📦 Gestion du stock | Suivi par produit, alertes stock faible / épuisé |
| ✏ CRUD Produits | Ajouter, modifier, supprimer les produits |
| 💰 Remise & Rendu | Remise en % sur le total + calcul automatique du rendu |
| 🧾 Ticket PDF | Génération et impression du reçu |
| 📊 Dashboard Stats | CA/jour, CA total, panier moyen, graphiques par catégorie et par jour |
| 📋 Historique | 30 dernières ventes avec détail ticket |
| ⬇ Export CSV | Export des ventes pour Excel/comptabilité |
| 📲 PWA | Installable sur mobile iOS/Android, fonctionne offline |

---

## Stack technique

```
HTML5 / CSS3 / JavaScript (Vanilla)
IndexedDB        → Persistance locale robuste (remplace localStorage)
Chart.js 4.4     → Graphiques dynamiques (catégorie, CA 7 jours)
Quagga.js        → Scanner code-barres via caméra
Service Worker   → Mode hors-ligne (cache des assets)
```

---

## Structure du projet

```
reda-caisse/
├── index.html      → Application complète (HTML + CSS + JS)
├── manifest.json   → Configuration PWA
├── sw.js           → Service Worker (cache offline)
├── icon-192.png    → Icône PWA (192×192)
├── icon-512.png    → Icône PWA (512×512)
└── README.md       → Ce fichier
```

---

## Déploiement

### Option 1 — Vercel (recommandé)
```
1. Fork ce dépôt
2. Aller sur https://vercel.com → New Project → importer ce repo
3. Framework : Other
4. Root Directory : reda-caisse
5. Build Command : (laisser vide)
6. Output Directory : reda-caisse  (ou laisser vide)
7. Deploy
```

### Option 2 — GitHub Pages
```
1. Settings → Pages → Source : Deploy from a branch
2. Branch : main / (root) ou /reda-caisse
3. Save → URL générée automatiquement
```

### Option 3 — Local
```bash
# Avec Python
cd reda-caisse
python -m http.server 8080

# Avec Node.js
npx serve reda-caisse

# Ouvrir http://localhost:8080
```

---

## Utilisation

### Scanner un produit
1. Taper le code-barres dans le champ ou appuyer sur 📷 pour ouvrir le scanner caméra
2. Le produit est ajouté au ticket automatiquement avec retour sonore

### Ajouter un produit au poids
1. Appuyer sur **⚖ /kg**
2. Sélectionner le produit ou saisir le nom et le prix/kg
3. Entrer le poids via le pavé numérique
4. Appuyer sur **+ AJOUTER AU TICKET**

### Finaliser une vente
1. Vérifier le ticket de caisse
2. Appliquer une remise si nécessaire (champ %)
3. Appuyer sur **PAYER**
4. Saisir le montant reçu → le rendu s'affiche automatiquement
5. Télécharger le PDF ou valider directement

### Gestion des produits
- Onglet **📦 Produits** → ajouter, modifier, supprimer
- Scanner le code-barres depuis le formulaire

### Statistiques
- Onglet **📊 Stats** → KPIs du jour, graphiques, historique complet
- Exporter les ventes en CSV pour Excel

---

## Données

Toutes les données sont stockées localement dans **IndexedDB** du navigateur.  
Elles persistent même si le cache est vidé.  

> ⚠️ Les données restent sur l'appareil utilisé — pas de synchronisation cloud dans cette version.

---

## Produits de démonstration inclus

| Code | Produit | Prix | Type |
|---|---|---|---|
| 1234567890 | Coca-Cola 1L | 150 DA | Code-barres |
| 9876543210 | Pain baguette | 40 DA | Code-barres |
| KG-TOMATE | Tomates | 120 DA/kg | Au poids |
| KG-VIANDE | Viande hachée | 1200 DA/kg | Au poids |
| ... | ... | ... | ... |

---

## Compatibilité

| Appareil | Support |
|---|---|
| Android (Chrome) | ✅ Complet — installable |
| iPhone / iPad (Safari) | ✅ Complet — installable |
| Windows (Chrome, Edge) | ✅ Complet — installable |
| macOS (Chrome, Safari) | ✅ Complet |
| Linux (Chrome, Firefox) | ✅ Complet |

> Le scanner caméra nécessite HTTPS (automatique sur Vercel/GitHub Pages).

---

## Licence

MIT — libre d'utilisation et de modification.
