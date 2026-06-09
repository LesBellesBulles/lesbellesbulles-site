# Les Belles Bulles — Site web

Site web statique pour SAS Les Belles Bulles, prêt à déployer sur GitHub Pages.

## Structure des fichiers

```
.
├── index.html              # Le site complet (un seul fichier)
├── bottles/                # 31 photos/illustrations de bouteilles
│   ├── lanson-*.png        # Lanson — photos réelles
│   ├── lanson-noble-*.svg  # Noble Champagne — illustrations (à remplacer)
│   ├── masse-brut.png      # Massé — photo réelle
│   ├── tsarine-*.png       # Tsarine — photos réelles
│   ├── tsarine-precision-n15.svg  # Précision N°15 — illustration (à remplacer)
│   ├── chanoine-*.png      # Chanoine Frères — photos réelles
│   └── heidsieck-*.svg     # Heidsieck & Co Monopole — illustrations (à remplacer)
├── logo-summer.jpg         # Le logo (à conserver tel que dans votre repo actuel)
└── banner-summer.jpg       # La bannière (à conserver tel que dans votre repo actuel)
```

> ⚠️ **`logo-summer.jpg` et `banner-summer.jpg`** sont des placeholders dans le ZIP livré. Conservez vos fichiers actuels du dépôt GitHub — ne pas écraser.

## Ce qui a été refondu

### Direction artistique
- Couleurs identiques (#34B2E5 + or)
- Typographie identique (Playfair Display + Lato)
- Rubriques identiques (Maison, Services, Champagnes, Événements, Contact)
- **Moins de bulles** : retirées de toutes les sections, conservées sur splash + hero uniquement
- **Coins moins arrondis** : 2-4px au lieu de 12-16px, finition plus pro
- **L'or utilisé avec parcimonie** : devient un vrai accent au lieu d'être omniprésent
- **Hiérarchie typographique nette** : eyebrows, titres serif, dividers or de 48px
- **Sections enchaînées en bandeaux** : crème → blanc → ciel → blanc → crème

### Nouvelles fonctionnalités

#### 1. Double splash screen
- **Splash 1** : vérification d'âge (avec son champagne pop)
- **Splash 2** : choix Particulier / Entreprise

#### 2. Site Particulier
Refonte propre du site existant : maison + valeurs + 3 services + 4 types de champagnes + 3 types d'événements + contact avec équipe complète.

#### 3. Site Entreprise (nouveau)
- Catalogue par type en accordéon (8 catégories : Brut, Extra Brut, Sec & Demi-Sec, Rosé, Blanc de Blancs & Blanc de Noirs, Millésimés, Bio, Cuvées Prestige)
- 31 cuvées des 5 maisons LID avec prix HT
- Heidsieck affiche le **tarif CHR/Cavistes BtoB** (avec remise 34%) avec le prix général barré
- Cuvées exclusives "Singulière" Tsarine signalées
- Panier sticky avec gestion des packs de 6 (1 marque par pack)
- Barre de progression vers le minimum 24 bouteilles
- Bouton "Valider" qui n'est actif qu'au-delà de 24 bouteilles
- Modal de validation avec : raison sociale, SIREN (9 chiffres), SIRET (14 chiffres, validation cohérence avec SIREN), upload K-bis (PDF/image, 10MB max, drag&drop), contact, adresse, commentaire
- Récapitulatif de commande inclus automatiquement dans l'email

## Configuration de l'envoi d'email

Le formulaire de commande peut fonctionner en deux modes :

### Mode A — Recommandé : Formspree (envoi automatique avec K-bis joint)

1. Créez un compte gratuit sur **https://formspree.io** (50 envois/mois gratuits, suffit largement pour démarrer)
2. Créez un nouveau formulaire avec `contact@lesbellesbulles.com` comme destination
3. Copiez votre endpoint Formspree (format : `https://formspree.io/f/xyzabcde`)
4. Dans `index.html`, repérez la ligne :
   ```js
   const FORMSPREE_ENDPOINT = "";
   ```
5. Remplacez par :
   ```js
   const FORMSPREE_ENDPOINT = "https://formspree.io/f/xyzabcde";
   ```
6. Commitez et pushez

Avec cette configuration, le K-bis est joint automatiquement et l'email arrive immédiatement à `contact@lesbellesbulles.com`. C'est la configuration de production attendue.

### Mode B — Fallback : `mailto:` (par défaut, sans configuration)

Si `FORMSPREE_ENDPOINT` est vide (état initial), le bouton "Envoyer la commande" ouvre le client mail du client avec un email pré-rempli contenant toutes les informations de commande. **Le client doit joindre son K-bis manuellement** avant d'envoyer — un message d'instruction le lui rappelle.

Mode utile pour démarrer rapidement, mais Mode A est fortement recommandé pour la production.

## Photos manquantes à remplacer

10 illustrations SVG ont été créées en placeholders pour les bouteilles dont aucune photo n'était disponible dans les PDF tarifs LID. À remplacer dès que vous obtenez les vraies photos auprès de Lanson International Distribution :

**Heidsieck & Co Monopole** (5)
- `bottles/heidsieck-blue-top.svg`
- `bottles/heidsieck-white-top.svg`
- `bottles/heidsieck-rose-top.svg`
- `bottles/heidsieck-gold-top.svg`
- `bottles/heidsieck-silver-top.svg`

**Lanson Noble Champagne** (4)
- `bottles/lanson-noble-brut.svg`
- `bottles/lanson-noble-brut-coffret.svg`
- `bottles/lanson-noble-bdb.svg`
- `bottles/lanson-noble-bdb-coffret.svg`

**Tsarine Prestige** (1)
- `bottles/tsarine-precision-n15.svg`

**Pour les remplacer :**
1. Préparez des PNG transparents (hauteur ≈ 480px, format portrait)
2. Sauvegardez-les avec le même nom mais en `.png` (ex. `heidsieck-blue-top.png`)
3. Dans `index.html`, repérez chaque référence à `.svg` dans le catalogue (`const CATALOGUE`) et remplacez par `.png`
4. Supprimez les `.svg` du dossier `bottles/`

Les illustrations actuelles s'affichent avec une petite mention "illustration" pour indiquer qu'il ne s'agit pas de la photo officielle.

## Mise à jour des prix

Tous les prix sont dans la constante `CATALOGUE` (script en bas du fichier). Champs disponibles par bouteille :

```js
{
  id: "lanson-black",
  brand: "Lanson",
  name: "Le Black Création",
  image: "bottles/lanson-black-creation.png",
  priceHT: 27.80,
  priceHT_general: 25.90,   // optionnel : prix général barré (pour Heidsieck)
  discount: "CHR",           // optionnel : badge de remise
  exclusive: "Gamme Singulière — exclusivité CHR & Cavistes"  // optionnel : mention exclusivité
}
```

## Déploiement

Le site est 100% statique. Pour le déployer :

1. Remplacez le `index.html` existant dans votre dépôt GitHub par celui-ci
2. Créez le dossier `bottles/` et copiez les 31 fichiers dedans
3. Conservez les `logo-summer.jpg` et `banner-summer.jpg` existants
4. Commit + push → GitHub Pages déploie automatiquement

## Test local

Pour tester avant de pousser :
```bash
cd dossier-site/
python3 -m http.server 8000
# puis ouvrez http://localhost:8000
```

---

© 2026 SAS Les Belles Bulles
