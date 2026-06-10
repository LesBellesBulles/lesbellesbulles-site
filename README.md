# Les Belles Bulles — Site v5

Refonte complète du site, orienté "vitrine" : présentation des Maisons et des cuvées, sans système de panier ni prix affichés. Le but est de pousser les visiteurs à prendre contact pour commander.

## Ce qui change par rapport à la v4

### Structure
- **Splash d'âge conservé** (avec son champagne pop)
- **Splash Particulier/Entreprise supprimé** — site unifié pour tous les publics
- **Système de panier et de commande retiré** — plus de prix affichés, plus de validation K-bis sur le site
- **Aucune mention de Lanson International Distribution** — la sélection est présentée comme la nôtre propre

### Nouvelles sections
- **Notre Maison** — refondue avec lettrine, signature italique gold, et values block "Pourquoi nous choisir" (4 piliers)
- **Nos Maisons** — 5 cartes (Lanson, Chanoine, Heidsieck, Tsarine, Massé), avec modale détaillée pour chaque (histoire, style, particularité, signature stripe Cépage/Style/Particularité)
- **Nos Cuvées** — 9 cartes pédagogiques par type (Brut, Extra Brut, Sec & Demi-Sec, Rosé, Blanc de Blancs, Blanc de Noirs, Millésimés, Bio, Cuvées Prestige). Chaque carte contient un dosage/sous-titre, une description, et un encadré "À table" (accords mets).
- **La Sélection** — galerie filtrable par Maison (Toutes / Lanson / Chanoine / Heidsieck / Tsarine / Massé), 30 cuvées affichées avec image et type, sans prix
- **Conditions de commande** — bande beige avec 3 chiffres clés (6 bouteilles par pack, 4 packs minimum, 0€ de livraison franco)
- **Services** — étoffée à 8 cartes : Conseil personnalisé, Disponibilité, Organisation d'événements, Réceptions privées, Dégustations commentées, Cadeaux d'entreprise, Accompagnement professionnel, Livraison soignée

### Direction artistique
- **Palette refondue** : blanc, crème, beige champagne, encre (navy), or — fini le sky blue dominant
- **Hero typographique sur fond encre** — pas de banner-summer.jpg (qui jurerait avec le nouveau palette). Si tu veux conserver la bannière, je peux l'utiliser ailleurs comme bande de transition.
- **"Champagne everyday" présent à 5 endroits** : splash, tagline sous logo dans nav, eyebrow du hero, section contact, signature footer
- **Typographie nette** : Playfair Display + Lato, hiérarchie clarifiée avec eyebrows accompagnés de tirets or
- **Animations** : reveal au scroll, bulles subtiles sur splash et hero, hover sur cartes (élévation + bordure or), transitions de filtre sur galerie

## Fichiers

```
.
├── index.html              # Le site complet (un seul fichier ~1900 lignes)
├── bottles/                # 31 visuels de bouteilles (réutilisés depuis la v4)
└── logo-summer.jpg         # Le logo (à conserver depuis votre repo actuel)
```

Pas besoin de `banner-summer.jpg` ni `divider-summer.jpg` — le hero est typographique pur. Tu peux les laisser dans le repo, ils ne sont juste plus référencés.

## Déploiement

Comme pour la v4 :

1. **Backup la v4 actuelle** : sur GitHub, renomme `index.html` en `index-v4.html` avant d'uploader.
2. **Upload le nouveau `index.html`** (depuis ce ZIP).
3. **Le dossier `bottles/` est déjà en place** dans ton repo depuis la v4. Tu n'as rien à changer dessus.
4. Pousse → GitHub Pages déploie en ~1 min.

## Photos manquantes (à remplacer dès que LID t'envoie les vraies)

10 illustrations SVG restent en placeholders, identiques à la v4 :
- Heidsieck : Blue Top, White Top, Silver Top, Rose Top, Gold Top
- Lanson Noble Champagne : Brut, Brut Coffret, BdB, BdB Coffret
- Tsarine Précision N°15

Pour remplacer une illustration par une photo PNG :
1. Renomme ta photo `heidsieck-blue-top.png` (par exemple)
2. Place-la dans `bottles/`
3. Dans `index.html`, recherche `bottles/heidsieck-blue-top.svg` et remplace `.svg` par `.png`

## Contenu modifiable

Toutes les présentations des Maisons sont dans la constante `MAISONS_DETAIL` au début du `<script>` en bas du fichier. Les paragraphes, la signature stripe et la mention "Notre sélection" sont éditables directement dans le code.

La galerie est dans la constante `BOTTLES` — facile d'ajouter, retirer ou réordonner une bouteille.

---

© 2026 SAS Les Belles Bulles
