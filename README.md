# ☢️ RadioPrev Pro

**La radioprotection, de l'évaluation à la décision.**

Suite de 5 outils web de radioprotection pour les médecins du travail, les infirmiers en santé au travail et les PCR (personnes compétentes en radioprotection) : dosimétrie interne, exposition externe, décontamination, suivi dosimétrique et surveillance d'ambiance.

Chaque module est une page HTML autonome. Il n'y a rien à installer, aucun serveur à faire tourner, et aucune donnée n'est envoyée sur Internet.

> ⚠️ **Outil d'aide à la décision.** RadioPrev Pro ne remplace ni l'expertise d'un professionnel qualifié, ni les logiciels de référence (MIODOSE, IRSN). Toute dose réglementaire doit être confirmée par un organisme agréé.

---

## Les modules

| # | Module | Rôle | Version |
|---|---|---|---|
| 1 | **DosiPrev** | Dosimétrie interne : dose efficace engagée E(50) après incorporation | v4.4 |
| 2 | **IrradPrev** | Exposition externe : γ, rayons X, β peau, neutrons, écrans, zonage | v1.1 |
| 3 | **DecoPrev** | Décontamination : triage des radio-victimes, décorporation, plaie contaminée | v1.0 |
| 4 | **SuiviDosi** | Suivi dosimétrique : registre individuel, catégorie A/B, aptitude, ESS | v1.0 |
| 5 | **AmbiPrev** | Surveillance d'ambiance : DAC/LDCA, contamination surfacique, radon | v1.0 |

### 1. DosiPrev — dosimétrie interne
- 34 radionucléides et 5 voies d'entrée : inhalation, ingestion, plaie, peau, muqueuse.
- Coefficients de dose **OIR (CIPR 130 à 151, DAMA 5 µm)** par défaut, CIPR 68 en option.
- Formes chimiques F / M / S, plus l'iode élémentaire en vapeur (type V).
- Rétention bi-exponentielle, excrétion urinaire et fécale, effet du DTPA.
- Ajustement multi-mesures : moindres carrés pondérés, χ² et vraie p-value, test automatique F/M/S.
- Dose minimale détectable (DMD) et comparaison de programmes de surveillance.
- Filiation radioactive (4 chaînes) et mélanges d'uranium (naturel, appauvri, enrichi).
- Auto-test intégré contre des cas de référence IRSN : **28/28**.

### 2. IrradPrev — exposition externe
- 15 sources γ (constantes Γ), 16 configurations de rayons X (médical, dentaire, vétérinaire, industriel).
- Dose β à la peau Hp(0,07), 5 sources de neutrons.
- Écrans : plomb, fer, béton, eau, verre ; couches de demi-atténuation (CDA) fixes pour le γ, interpolées selon le kV pour les X.
- Temps de séjour maximal, zonage réglementaire, niveaux de référence diagnostiques (NRD), rayonnement diffusé.

### 3. DecoPrev — décontamination
- Arbre de triage des radio-victimes (UA / UR / DI).
- Décontamination externe sur 8 zones du corps.
- Traitements décorporants pour 11 radionucléides (DTPA, KI, bleu de Prusse…).
- Prise en charge d'une plaie contaminée, 6 protocoles selon la situation.

### 4. SuiviDosi — suivi dosimétrique
- Registre individuel : Hp(10), Hp(0,07), Hp(3), E(50), neutrons.
- Cumul annuel avec jauges et histogramme, classement en catégorie A ou B.
- Check-list d'aptitude médicale, évaluation des événements significatifs (ESS) sur 4 niveaux.

### 5. AmbiPrev — surveillance d'ambiance
- DAC et LDCA pour 16 radionucléides, besoin d'un appareil de protection respiratoire (APR).
- Contamination surfacique (mesure directe et frottis).
- Radon : dose, niveaux de référence, zone à potentiel radon 3 (Limousin).
- Zonage réglementaire sur 5 niveaux.

---

## Démarrage rapide

**En ligne :** ouvrir la page d'accueil du dépôt sur GitHub Pages.

**Hors ligne :**
1. Télécharger le dépôt (bouton **Code → Download ZIP**).
2. Décompresser le dossier.
3. Double-cliquer sur `index.html`.

Tout fonctionne dans un navigateur récent (Chrome, Edge, Firefox, Safari), sur ordinateur comme sur téléphone.

---

## Structure du dépôt

```
RadioPrev-Pro/
├── index.html          ← page d'accueil (tableau de bord RadioPrev Pro)
├── DosiPrev.html
├── IrradPrev.html
├── DecoPrev.html
├── SuiviDosi.html
├── AmbiPrev.html
├── assets/
│   └── logo.png        ← logo (480 px, fond transparent)
└── README.md
```

> Le logo de la page d'accueil est **intégré directement dans le fichier HTML**. La page s'affiche donc avec son logo même sans le dossier `assets/`. Le fichier `assets/logo.png` sert à réutiliser le logo dans les autres modules.

Pour que les cartes de l'accueil ouvrent les modules sur GitHub Pages, chaque lien doit pointer vers le fichier du dépôt, par exemple `href="DosiPrev.html"`.

---

## Personnaliser la page d'accueil

### Changer le logo
Dans `index.html`, repérer la balise suivante dans `<div class="hero-img">` :
```html
<img src="data:image/webp;base64,..." alt="Logo ...">
```
Remplacer tout le `src` par le chemin de la nouvelle image :
```html
<img src="assets/mon-logo.png" alt="Description du logo">
```
Une image **PNG à fond transparent**, carrée, d'au moins 480 px donne le meilleur résultat.

### Ajouter une image au centre du trèfle
Le trèfle animé est un dessin SVG placé dans `<div class="hero-img">`. Pour superposer une petite image en son centre, ajouter juste après `<img ...>` :
```html
<img class="hero-center" src="assets/centre.png" alt="">
```
puis, dans le `<style>` :
```css
.hero-img .hero-center{
  position:absolute; width:30%; height:auto;
  left:50%; top:50%; transform:translate(-50%,-50%);
}
```
Le `width:30%` règle la taille par rapport au logo.

### Régler le trèfle animé
Dans le CSS, règle `.hero-img .trefoil` :

| Propriété | Effet | Exemple |
|---|---|---|
| `opacity:.12` | visibilité | `.20` le rend plus présent |
| `animation: spin 120s` | vitesse de rotation | `40s` tourne nettement plus vite |
| `width:150%` | taille par rapport au logo | `180%` le rend plus grand |
| `color:var(--sky)` | couleur | `var(--tl)` pour du turquoise |

L'animation s'arrête automatiquement quand l'utilisateur a demandé moins d'animations dans les réglages de son système.

---

## Validation de DosiPrev

DosiPrev a été comparé aux cas de référence présentés par l'IRSN avec MIODOSE (formation AMTSN, juin 2022) :

| Cas | MIODOSE | DosiPrev v4.4 | Écart |
|---|---|---|---|
| Cs-137, inhalation type F, 3 500 Bq en corps entier à J+3 | 0,0523 mSv | 0,0511 mSv | −2 % |
| I-131, 3 incorporations de vapeur I₂ (coefficient CIPR 68, comme MIODOSE v1) | 3,55 mSv | 3,79 mSv | +7 % |
| I-131, même cas avec le coefficient OIR | — | 3,22 mSv | — |

Les coefficients OIR ont été vérifiés contre la publication du BfS (*Dosiskoeffizienten bei innerer beruflicher Exposition*, BAnz AT 10.05.2023 B7), les tables CIPR 137/141 et la présentation IRSN sur l'arrêté du 16 novembre 2023.

### Limites connues
- **Rétention simplifiée.** Les courbes sont bi-exponentielles et non issues du modèle compartimental complet (HRTM + systémique). Un écart de l'ordre de ±15 % avec MIODOSE est attendu.
- **Une seule incorporation par ajustement.** En cas d'incorporations multiples, traiter chaque intervalle de surveillance séparément.
- **Coefficients OIR manquants.** Am-241, Pu-238, Th-232, Np-237, Cm-244, Cf-252, Ir-192 et K-40 restent en CIPR 68 ; l'outil l'indique (« P68 »).

---

## Références

- CIPR 103 (2007) — Recommandations, facteurs de pondération wT et wR
- CIPR 130, 134, 137, 141, 151 — *Occupational Intakes of Radionuclides* (OIR)
- CIPR 68 (1994) — coefficients de dose pour les travailleurs
- NCRP 161 — prise en charge des personnes contaminées
- Code du travail, articles R. 4451-1 et suivants
- Arrêté du 16 novembre 2023 — modalités de calcul des doses efficaces et équivalentes
- Directive 2013/59/Euratom

---

## Auteure

**Laure** — infirmière en santé au travail et préventrice, SPSTI 23/87 (Creuse – Haute-Vienne).
Projet de la collection [PréventIA-LaB](https://github.com/laurebonnefond/PreventIA-LaB).

Retours, corrections et cas de validation bienvenus via les *Issues* du dépôt.

## Licence

À définir.
