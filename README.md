<img src="assets/icon.svg" width="72" height="72" alt="Voyages Voyages">

# Voyages • Voyages — Hub Personnel & Familial (Thomas, Marie & Émile)

Application web / PWA d'organisation de voyages, portefeuille de cartes de réduction et guichet de réservation express, synchronisée avec les données réelles extraites d'**Apple Mail**, **iMessage** et des **agendas Cochin / Famille**.

## Fonctionnalités principales

### 1. Portefeuille Cartes Avantage & Fidélité (avec vrais QR codes Aztec & PDF officiels)
- **Carte Avantage Adulte SNCF (Thomas Lefèvre)** — `N° 29090108799317681`
  - **Période active** : `23/12/2025 → 23/12/2026` (dossier et TCN dans le 🔒 coffre) avec code Aztec officiel scannable et justificatif PDF.
  - **Renouvellement déjà payé** : `26/12/2026 → 26/12/2027` (dossier et TCN dans le 🔒 coffre, acheté le 29/09/2026) avec bascule instantanée entre les deux périodes.
- **Carte Air France Week-End+ (Thomas Lefèvre)** — `N° 912766841`
  - Validité : `08/05/2027 → 07/05/2028` (achetée le 14/10/2026 pour la Corse).
- **Carte Air France Week-End+ (Marie Parizot)** — `N° 912766896`
  - Validité : `08/05/2027 → 07/05/2028` (achetée le 14/10/2026).
- **Flying Blue Air France-KLM (Thomas Lefèvre)** — `N° 1137477046`
  - Statut `Explorer` • Solde `3 575 Miles`.
- **Mode Contrôleur Plein Écran** : affichage haute luminosité des QR codes SNCF et reçus Air France, copie des numéros en 1 clic.

### 2. Prochaines Vacances, Séminaires & Voyages (2026–2027)
- **12–14 Nov 2026 — Relais Émile (Maman) & Séminaire Strasbourg** : *8° Ateliers Urgences scanner et IRM* (programme PDF inclus).
- **3–4 Déc 2026 — Masterclass Cryo MSK (Valence)** : déplacement pro (Off Cochin validé), lancement rapide de réservation TGV Paris ↔ Valence.
- **28 Déc 2026 – 3 Jan 2027 — Vacances de Noël en Famille à Valloire** :
  - Congés Cochin validés par Anne-Marie Fortin.
  - Billets TGV INOUI réservés par Nicolas Lefèvre (captures officielles incluses) :
    - **Aller (28/12)** : TGV `6407` `11h34` Paris Gare de Lyon → `15h48` St-Michel Valloire (`1re classe`, Voiture `13`, Places `346, 355, 358, 367, 370`).
    - **Retour (03/01)** : TGV `6406` `15h06` St-Michel Valloire → `19h55` Paris Gare de Lyon (`2e classe`, Voiture `7`, Places `740, 741, 742, 744, 745`).
- **26–27 Fév 2027 — Séminaire / Congrès Radiologie** (après garde de nuit du jeudi 25/02 à Cochin).
- **13–17 Mai 2027 — Inauguration de la Bergerie à Ajaccio (Corse)** *(Réservé ✓ — dossier Air France dans le 🔒 coffre, 773,08 € pour Thomas & Marie)* :
  - **Aller** : `Jeudi 13 mai 2027` — `AF0777` (opéré par Air Corsica) Paris Orly `21h50` → Ajaccio `23h25` (même vol qu'Arthur et Matt).
  - **Retour** : `Lundi 17 mai 2027` — `AF0772` (opéré par Air Corsica) Ajaccio `10h45` → Paris Orly `12h25`.
  - Tarif Carte Week-End+ (`912766841` & `912766896`) : modifiable, remboursable (20 € de frais), 1 valise 23 kg chacun, sans assurance.
  - ⚠️ **Émile (né le 10/07/2024)** : billet enfant à ajouter par téléphone (Air France `09 69 39 36 54`) sur les vols du dossier (référence dans le 🔒 coffre).
- **Historique 2026** : Normandie / Étretat / Cerza Safari Lodge / Dieppe (août), Marseille TGV (août), Trouville-Deauville (juillet), Corfou Transavia & Sixt (mai), Bandol (mai), Marbella Vueling (mars) — références dans le 🔒 coffre.
- **Ajout de voyage & Export `.ics`** : création de nouveaux voyages sauvegardés localement et export calendrier Apple/Google en 1 clic.

### 3. Guichet Express (Achat de billets & Réservations simplifiés)
- **Sélection des voyageurs en 1 clic** (Thomas, Marie, Émile, Famille) avec **injection et copie automatique** des bons numéros de carte (`29090108799317681`, `912766841`, `912766896`, `1137477046`) dans le presse-papiers avant d'ouvrir SNCF Connect, Trainline, Air France, Transavia, Booking, Airbnb ou Sixt.
- **Vérificateur automatique de conflits Garde Cochin & Garde d'Émile** : alerte immédiate si les dates choisies chevauchent une garde de nuit à Cochin ou un événement familial.
- **Routes favorites pré-configurées** : Corse Ajaccio (13–17 mai 2027, réservé), Valence TGV (3–4 déc 2026), Strasbourg TGV (13–14 nov 2026), Marseille St-Charles, Deauville, St-Michel Valloire.

## Lancement local

Ouvrir directement [`index.html`](index.html) dans un navigateur ou servir le dossier avec un serveur HTTP statique :

```bash
python3 -m http.server 8080
```

## 🔒 Coffre chiffré (références de dossier, billets, justificatifs)
- Le dépôt est public : les références de réservation, billets et justificatifs ne sont **jamais** publiés en clair.
- Source privée locale (non versionnée) : `private/vault_source.json` + `private/docs/`.
- Construction : `node scripts/build_vault.mjs` → `assets/vault/data.js` + `assets/vault/docs/*.enc` (AES-GCM 256, PBKDF2-SHA256 600 000 itérations).
- Mot de passe : Trousseau macOS (`t3-vault get voyages-coffre`). Dans l'app : 🔒 en haut → mot de passe une seule fois par appareil (ou lien `#cle=…`), puis l'appareil reste déverrouillé.
- Dans `index.html`, utiliser `{{cle}}` dans les textes/copies des voyages et `vault:<id>` pour les documents.
