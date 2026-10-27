# Dar Al Qamar — La maison de la lune

Site vitrine et menu numérique d’un restaurant **entièrement fictif**, réalisé pour un portfolio avec React, Vite et CSS. Aucun backend, formulaire de réservation, suivi publicitaire ou service WhatsApp actif.

## Installation et lancement

Prérequis : Node.js 22.12+ (Node 24 recommandé), npm et Git.

```bash
npm ci
npm run dev
```

Exécuter les commandes depuis le dossier du projet. Ouvrir l’adresse indiquée par Vite dans votre terminal.

```bash
npm run build
npm run preview
```

Le dossier `dist/` est la version de production. `preview` permet de la vérifier localement, ce n’est pas un serveur de production.

## Organisation et personnalisation

- `src/data.js` : plats, catégories, prix en euros, adresse, numéro et horaires.
- `src/components/Menu.jsx` : cartes, recherche sans distinction de casse ou d’accent et filtres combinés.
- `src/App.jsx` : accueil, navigation mobile, histoire, contact et pied de page.
- `src/style.css` : couleurs, typographie, motifs et adaptations responsive.
- `public/images/` : illustrations SVG originales créées pour cette démonstration. Elles peuvent être réutilisées et modifiées avec ce projet ; aucune photo ni marque de restaurant tiers. Les images sont explicitement décrites comme illustrations dans leurs textes alternatifs.

Pour ajouter un plat, ajouter un objet dans `dishes` : `id` unique, `name`, `category` (une valeur de `categories`), `description`, `price` numérique, `image` (nom du fichier SVG sans extension) et `tag`. Déposer l’image dans `public/images/`. Pour utiliser un JPG ou WebP, adapter l’extension du chemin dans `Menu.jsx` et décrire son contenu dans le texte alternatif. Utiliser uniquement des images personnelles ou sous une licence autorisant votre usage ; conserver les crédits requis.

Les coordonnées sont modifiables dans `contact`. Le bouton WhatsApp affiche uniquement une explication : il n’ouvre aucune discussion et n’envoie aucun message. Les mentions de démonstration doivent rester tant que ce restaurant est fictif. Pour un vrai client, remplacer les informations, vérifier le numéro et implémenter explicitement le service voulu avant de le présenter comme actif.

## Publier et partager

### Netlify (déploiement manuel)

```bash
npm run build
npx netlify-cli deploy --dir=dist
# Après vérification du déploiement de test :
npx netlify-cli deploy --dir=dist --prod
```

La CLI demande une connexion et la création ou sélection d’un site. Partager l’URL HTTPS qu’elle fournit. On peut aussi déposer `dist/` via l’interface Netlify. Avec un dépôt Git connecté : commande de build `npm run build`, dossier publié `dist`, Node 24.

### GitHub Pages

Après avoir envoyé ce projet sur votre dépôt GitHub :

```bash
npm ci
npm run build
npx gh-pages -d dist
```

Cette dernière commande publie `dist/` sur la branche distante `gh-pages` et nécessite les droits d’écriture GitHub. Dans **Settings → Pages**, sélectionner **Deploy from a branch**, `gh-pages` et `/ (root)`. GitHub affichera le lien public à partager, normalement `https://la-hertz-yla.github.io/restaurant/` pour ce dépôt. Ce lien n’est actif qu’après publication réussie. Le `base: './'` dans `vite.config.js` prend en charge ce sous-dossier.

Aucun déploiement public n’a été réalisé automatiquement. Ne jamais ajouter de clés ou jetons au code.

## Validation

Compilation production vérifiée avec `npm run build`. Tests de navigateur réalisés avec Chromium/Playwright : dix plats initiaux ; cinq filtres ; recherche `THE A LA` trouvant « Thé à la menthe » ; état sans résultat et remise à zéro ; bouton WhatsApp de démonstration ; navigation mobile et ordinateur ; images chargées et absence de débordement horizontal aux largeurs 360, 390, 768, 1280 et 1440 px. Le test a été exécuté dans l’environnement de création et ne constitue pas une suite installée dans le projet.

Le site charge uniquement ses fichiers locaux, sans police ni image externe. Navigation clavier, lien d’évitement, focus visibles, attributs d’état des boutons et prise en compte de la réduction des animations sont inclus. Les contrôles ne remplacent pas un audit d’accessibilité exhaustif.
