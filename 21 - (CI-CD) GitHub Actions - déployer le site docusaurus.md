

# **1. Prérequis**

Assurez-vous d’avoir :
- **Node.js** installé (v16 ou supérieur). Vérifiez avec :
  ```bash
  node -v
  ```
- **npm** installé (automatiquement fourni avec Node.js). Vérifiez avec :
  ```bash
  npm -v
  ```
- Un dépôt GitHub déjà créé :  
  URL du dépôt : `https://github.com/hrhouma/skiller2.git`.

---

# **2. Étape par étape**

---
# **Étape 1 : Préparer la configuration dans `docusaurus.config.ts`**
---

Ouvrez le fichier `docusaurus.config.ts` et configurez les paramètres pour GitHub Pages :

```typescript
import { Config } from '@docusaurus/types';

const config: Config = {
  title: 'Skiller2',
  tagline: 'Documentation Docusaurus déployée avec GitHub Pages',
  url: 'https://hrhouma.github.io', // L'URL de base de votre site
  baseUrl: '/skiller2/', // Nom du projet GitHub (changer à '/' si projet principal)
  onBrokenLinks: 'throw',
  onBrokenMarkdownLinks: 'warn',
  favicon: 'img/favicon.ico',

  // Configuration GitHub Pages
  organizationName: 'hrhouma', // Nom de l'utilisateur GitHub
  projectName: 'skiller2', // Nom du dépôt
  deploymentBranch: 'gh-pages', // Branche où les fichiers statiques seront poussés
  trailingSlash: false, // Recommandé pour GitHub Pages

  // Autres configurations (modifiez selon vos besoins)
  presets: [
    [
      'classic',
      {
        docs: {
          sidebarPath: require.resolve('./sidebars.js'),
          editUrl: 'https://github.com/hrhouma/skiller2/edit/main/',
        },
        blog: {
          showReadingTime: true,
        },
        theme: {
          customCss: require.resolve('./src/css/custom.css'),
        },
      },
    ],
  ],
};

export default config;
```


---
# **Étape 2 : Désactiver Jekyll**
---

1. Ajoutez un fichier nommé **`.nojekyll`** dans le dossier `static` pour empêcher GitHub Pages de traiter les fichiers avec Jekyll.
2. Commande pour créer ce fichier si nécessaire :
   ```bash
   touch static/.nojekyll
   ```

---
# **Étape 3 : Configurer le dépôt local**
---

1. **Initialiser un dépôt Git local (si non fait) :**
   ```bash
   git init
   git add .
   git commit -m "Initialisation du projet local"
   ```

2. **Ajouter le dépôt GitHub comme distant :**
   ```bash
   git remote add origin https://github.com/hrhouma/skiller2.git
   git branch -M main
   git push -u origin main
   ```

---
# **Étape 4 : Installer les dépendances et tester le site**
---

1. **Installer les dépendances :**
   ```bash
   npm install
   ```

2. **Vérifier que le site fonctionne en local :**
   ```bash
   npm start
   ```
   - Ouvrez le navigateur à `http://localhost:3000` pour vérifier que tout fonctionne correctement.

---
# **Étape 5 : Construire le site**
---

1. **Générer les fichiers statiques :**
   ```bash
   npm run build
   ```
   Cela créera un dossier `build` contenant les fichiers statiques nécessaires pour le déploiement.

2. **Vérifier le dossier généré :**
   ```bash
   ls build
   ```
   Vous devriez voir un fichier `index.html` et d'autres fichiers.

---
# **Étape 6 : Créer un workflow GitHub Actions**
---

1. **Créer le dossier de workflow :**
   ```bash
   mkdir -p .github/workflows
   touch .github/workflows/deploy.yml
   ```

2. **Ajouter la configuration du workflow :**

Ouvrez **`.github/workflows/deploy.yml`** et ajoutez :

```yaml
name: Déployer Docusaurus sur GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  build:
    name: Construire et déployer
    runs-on: ubuntu-latest

    steps:
      - name: Récupérer le code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Configurer Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Installer les dépendances
        run: npm ci

      - name: Construire le site
        run: npm run build

      - name: Déployer sur GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: gh-pages
          publish_dir: ./build
```



---
# **Étape 7 : Pousser les modifications**
---

1. **Ajouter et commiter les fichiers :**
   ```bash
   git add .
   git commit -m "Ajouter workflow GitHub Actions pour déploiement"
   ```

2. **Pousser les modifications vers GitHub :**
   ```bash
   git push
   ```




---
# **Étape 8 : Configurer GitHub Pages**
---

1. Accédez à votre dépôt sur GitHub :  
   [https://github.com/hrhouma/skiller2](https://github.com/hrhouma/skiller2).

2. Allez dans l'onglet **Settings > Pages**.
3. Sous **Source**, sélectionnez **Deploy from a branch** pour activer GitHub Pages.
4. Sélectionnez **gh-pages** et ensuite **/root**.

![image](https://github.com/user-attachments/assets/0db97454-9b3b-458e-b323-bdccb723fd0d)



---
# **Étape 9 : Vérifier les permissions de GitHub Actions**
---

1. Assurez-vous que le workflow GitHub Actions dispose des permissions nécessaires pour pousser vers le dépôt. Dans les paramètres du dépôt :
2. Accédez à **Paramètres > Actions > Général**.
3. Faites défiler jusqu’à la section **Permissions des workflows**.
4. Vérifiez que l’option **Permissions en lecture et écriture** est sélectionnée.
5. Activez **Autoriser GitHub Actions à créer et approuver des pull requests** si nécessaire.

![image](https://github.com/user-attachments/assets/a89f20ba-9ea0-43b2-ae5e-f617ce9645d6)




---
# **Étape 10 : Vérifier le déploiement**
---

1. Allez dans l'onglet **Actions** pour vérifier l'exécution du workflow. Assurez-vous qu'il se termine sans erreur.
2. Une fois terminé, votre site sera disponible à l'adresse suivante :  
   ```
   https://hrhouma.github.io/skiller2/
   ```
![image](https://github.com/user-attachments/assets/ac8de273-ae56-4a6f-a217-5c83ea25e4ae)
