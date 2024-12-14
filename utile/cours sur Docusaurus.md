# **Cours sur Docusaurus : Création de sites web statiques modernes**

---

# **Introduction à Docusaurus**

Docusaurus est un générateur de sites web statiques basé sur **React**, conçu pour créer facilement :
- Des documentations techniques.
- Des blogs.
- Des pages personnalisées.

# **Avantages de Docusaurus**
1. **Flexibilité** :
   - Prend en charge Markdown pour une rédaction simplifiée.
   - Compatible avec React pour des fonctionnalités avancées.
2. **Prêt à l’emploi** :
   - Intègre un mode sombre, des thèmes et des plugins.
3. **Adapté aux développeurs** :
   - Déploiement facile sur GitHub Pages, Netlify, ou Vercel.

---

# **Pré-requis techniques**

1. **Node.js** : Version 18 ou supérieure (vérifiez avec `node -v`).
2. **npm** ou **Yarn** : Gestionnaires de paquets pour installer les dépendances.

---

# **Installation de Docusaurus**

#### **Étape 1 : Créer un nouveau site**
Exécutez la commande suivante :
```bash
npx create-docusaurus@latest my-website classic
```
- **`my-website`** : Nom du projet.
- **`classic`** : Utilise le modèle classique avec :
  - Un blog.
  - Une documentation.
  - Des pages personnalisables.

Pour activer TypeScript :
```bash
npx create-docusaurus@latest my-website classic --typescript
```

#### **Étape 2 : Structure du projet généré**
Après l’installation, la structure ressemble à ceci :
```
my-website/
├── blog/         # Articles de blog en Markdown.
├── docs/         # Fichiers de documentation.
├── src/          # Fichiers React ou pages personnalisées.
├── static/       # Fichiers statiques (images, styles CSS).
├── docusaurus.config.js   # Configuration principale.
├── sidebars.js   # Configuration de l’ordre des documents.
```

---

# **Utilisation et modifications**

#### **Lancer le site en mode développement**
```bash
cd my-website
npm run start
```
- Le site sera accessible à l’adresse : [http://localhost:3000](http://localhost:3000).
- Tout changement est automatiquement reflété.

#### **Construire le site pour la production**
```bash
npm run build
```
- Génère un site statique dans le dossier `/build`.
- Prêt à être déployé sur un service d’hébergement.

---

# **Configuration de Docusaurus**

#### **Fichier `docusaurus.config.js`**
Ce fichier centralise les paramètres globaux :
- **Métadonnées** :
  ```javascript
  export default {
    title: 'Mon site Docusaurus',
    url: 'https://example.com',
    baseUrl: '/',
    favicon: 'img/favicon.ico',
  };
  ```
- **Thèmes et plugins** :
  ```javascript
  export default {
    themes: ['@docusaurus/theme-classic'],
    plugins: ['@docusaurus/plugin-content-docs', '@docusaurus/plugin-content-blog'],
  };
  ```

#### **Exemple de configuration TypeScript**
```typescript
import type { Config } from '@docusaurus/types';

const config: Config = {
  title: 'Mon site Docusaurus',
  url: 'https://example.com',
  baseUrl: '/',
  themes: ['@docusaurus/theme-classic'],
};

export default config;
```

---

# **Modifier le contenu**

1. **Documentation** :
   - Ajoutez des fichiers Markdown dans le dossier `docs/`.
   - Exemple :
     ```markdown
     # Introduction
     Bienvenue dans notre documentation !
     ```
   - L’ordre des documents est défini dans `sidebars.js`.

2. **Blog** :
   - Créez des articles dans `blog/` :
     ```markdown
     ---
     title: "Mon premier article"
     date: 2024-12-14
     tags: [introduction]
     ---
     Voici le contenu de mon premier article.
     ```

3. **Pages personnalisées** :
   - Ajoutez des fichiers React ou Markdown dans `src/pages/`.

---

# **Déployer le site**

#### **GitHub Pages**
1. Configurez `docusaurus.config.js` :
   ```javascript
   export default {
     url: 'https://votre-utilisateur.github.io',
     baseUrl: '/mon-site/',
     projectName: 'mon-site',
     organizationName: 'votre-utilisateur',
   };
   ```
2. Déployez avec :
   ```bash
   npm run deploy
   ```

#### **Autres plateformes** :
- **Netlify** ou **Vercel** : Copiez le dossier `/build` et suivez leurs guides de déploiement.

---

# **Personnalisation avancée**

1. **Thèmes** :
   - Modifiez les styles dans `src/css/custom.css`.

2. **Ajouter des plugins** :
   Exemple : Blog avancé avec options.
   ```javascript
   export default {
     plugins: [
       [
         '@docusaurus/plugin-content-blog',
         {
           path: './blog',
           routeBasePath: '/articles',
           include: ['*.md', '*.mdx'],
         },
       ],
     ],
   };
   ```

---

# **Mise à jour de Docusaurus**

Modifiez la version dans `package.json` :
```json
"dependencies": {
  "@docusaurus/core": "3.6.3",
  "@docusaurus/preset-classic": "3.6.3"
}
```
Puis, exécutez :
```bash
npm install
```

---

# **Résumé des commandes essentielles**

| Commande                   | Description                                |
|----------------------------|--------------------------------------------|
| `npm run start`            | Lancer un serveur local.                  |
| `npm run build`            | Générer un site statique pour production. |
| `npm run deploy`           | Déployer le site (GitHub Pages).          |
| `npm install <package>`    | Ajouter un nouveau package.               |

---

# **Exercices pratiques**

1. **Créer une documentation complète** :
   - Ajoutez des fichiers Markdown dans `docs/`.
   - Configurez `sidebars.js` pour organiser le contenu.

2. **Créer un blog** :
   - Rédigez un article Markdown dans `blog/`.
   - Ajoutez des balises et une image.

3. **Déployer sur Netlify** :
   - Générez le site avec `npm run build`.
   - Importez le dossier `/build` sur Netlify.

---

# **Conclusion**

Docusaurus est un outil puissant pour créer des sites statiques, combinant simplicité et flexibilité. Grâce à ses fonctionnalités avancées, il permet de gérer efficacement des documentations et des blogs. Pour approfondir, explorez la [documentation officielle](https://docusaurus.io/docs).
