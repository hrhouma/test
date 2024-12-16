

## **1. Prérequis**

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

## **2. Étape par étape**

### **Étape 1 : Préparer la configuration dans `docusaurus.config.ts`**

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

### **Étape 2 : Désactiver Jekyll**

1. Ajoutez un fichier nommé **`.nojekyll`** dans le dossier `static` pour empêcher GitHub Pages de traiter les fichiers avec Jekyll.
2. Commande pour créer ce fichier si nécessaire :
   ```bash
   touch static/.nojekyll
   ```

---

### **Étape 3 : Configurer le dépôt local**

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

### **Étape 4 : Installer les dépendances et tester le site**

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

### **Étape 5 : Construire le site**

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

### **Étape 6 : Créer un workflow GitHub Actions**

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

### **Étape 7 : Pousser les modifications**

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

### **Étape 8 : Configurer GitHub Pages**

1. Accédez à votre dépôt sur GitHub :  
   [https://github.com/hrhouma/skiller2](https://github.com/hrhouma/skiller2).

2. Allez dans l'onglet **Settings > Pages**.

3. Sous **Source**, sélectionnez **GitHub Actions** pour activer GitHub Pages.

---

### **Étape 9 : Vérifier le déploiement**

1. Allez dans l'onglet **Actions** pour vérifier l'exécution du workflow. Assurez-vous qu'il se termine sans erreur.

2. Une fois terminé, votre site sera disponible à l'adresse suivante :  
   ```
   https://hrhouma.github.io/skiller2/
   ```

---

## **Dépannage des problèmes courants**

### **Le site affiche une erreur 404**
- Vérifiez que le `baseUrl` dans `docusaurus.config.ts` est correctement défini (`/skiller2/`).

### **Erreur Jekyll**
- Assurez-vous qu’un fichier `.nojekyll` est présent dans le dossier `static`.

### **Le workflow échoue**
- Consultez les logs dans l'onglet **Actions** pour identifier les erreurs.
- Assurez-vous que GitHub Actions a les **permissions en lecture et écriture** dans **Settings > Actions**.

---

Avec ces étapes, votre site sera déployé correctement sur GitHub Pages avec npm et Docusaurus. 🚀






































































--------------------------
------------------------------
------------------------


## **1. Introduction : Qu’est-ce que Docusaurus et CI/CD ?**

### Docusaurus
Docusaurus est un framework de documentation statique qui permet de créer des sites Web rapides et modernes. C'est idéal pour les sites de documentation, blogs, et pages statiques.
Ce document a pour objectif de créer un projet complet Docusaurus classique et le  déployer. Nous allons déployer notre framework statique Docusaurus via Github Actions qui sera notre plateforme CI/CD. 


- **Avantages :**
  - Facile à utiliser.
  - Basé sur React (mais aucune connaissance en React n’est nécessaire pour débuter).
  - Génère des sites Web rapides et performants.

### CI/CD avec GitHub Actions
CI/CD signifie **Integration Continue / Déploiement Continu**. Cela automatise la création, le test, et le déploiement d'un projet dès que vous effectuez des changements dans votre code.

- **GitHub Actions** est une plateforme d'automatisation directement intégrée à GitHub.

---

## **2. Pré-requis**

Avant de commencer, assurez-vous que chaque étudiant a :

- **Un ordinateur avec un système d’exploitation** (Windows, macOS ou Linux).
- **Un éditeur de texte** (comme Visual Studio Code, téléchargeable ici : [https://code.visualstudio.com/](https://code.visualstudio.com/)).
- **Node.js** installé (téléchargeable ici : [https://nodejs.org/](https://nodejs.org/)).
- **Git** installé (téléchargeable ici : [https://git-scm.com/](https://git-scm.com/)).
- Un compte **GitHub**.

---

## **3. Étape par étape : Créer un site Docusaurus**

### 3.1 Installer Node.js et vérifier l’installation
1. Téléchargez et installez **Node.js** depuis le site officiel.
2. Ouvrez un terminal ou une console (cmd/PowerShell sur Windows, Terminal sur macOS/Linux).
3. Vérifiez que **Node.js** est installé :
   ```bash
   node -v
   ```
   Vous devriez voir une version, par exemple `v18.17.1`.

4. Vérifiez que **npm** (le gestionnaire de paquets Node.js) est installé :
   ```bash
   npm -v
   ```
   Une version comme `9.8.1` devrait apparaître.

---

### 3.2 Créer le projet Docusaurus
1. Ouvrez un terminal dans un dossier où vous voulez créer le projet.
2. Exécutez cette commande pour installer le générateur Docusaurus :
   ```bash
   npx create-docusaurus@latest my-docusaurus-site classic
   ```
   **Explications :**
   - `npx` : Exécute un outil sans l’installer globalement.
   - `create-docusaurus@latest` : Installe la dernière version de Docusaurus.
   - `my-docusaurus-site` : Nom du dossier où sera créé le site.
   - `classic` : Utilise le thème classique de Docusaurus.

3. Naviguez dans le dossier de votre projet :
   ```bash
   cd my-docusaurus-site
   ```

4. Lancez le site en local pour le tester :
   ```bash
   npm start
   ```
   Cela démarre un serveur local. Allez à l’adresse affichée (souvent `http://localhost:3000`) pour voir le site.

---

### 3.3 Comprendre la structure du projet
- **`/docs`** : Contient les fichiers de documentation.
- **`/blog`** : Contient les fichiers de blog.
- **`/src`** : Contient le code source (personnalisation).
- **`docusaurus.config.js`** : Fichier de configuration du site.

---

## **4. Étape par étape : Héberger le projet sur GitHub**

### 4.1 Créer un dépôt GitHub
1. Connectez-vous à [https://github.com/](https://github.com/).
2. Cliquez sur **New Repository**.
3. Donnez un nom au dépôt (par exemple : `my-docusaurus-site`).
4. Laissez le dépôt **Public** et cochez **Add a README**.
5. Cliquez sur **Create Repository**.

---

### 4.2 Lier le projet local à GitHub
1. Dans le terminal, dans le dossier de votre projet, initialisez Git :
   ```bash
   git init
   ```
2. Ajoutez les fichiers à Git :
   ```bash
   git add .
   ```
3. Faites un premier commit :
   ```bash
   git commit -m "Initial commit"
   ```
4. Liez votre projet local au dépôt GitHub :
   ```bash
   git remote add origin https://github.com/votre_nom_utilisateur/my-docusaurus-site.git
   ```
   (Remplacez `votre_nom_utilisateur` et `my-docusaurus-site` par les informations de votre dépôt.)

5. Poussez les fichiers vers GitHub :
   ```bash
   git branch -M main
   git push -u origin main
   ```

---

## **5. Étape par étape : Configurer GitHub Actions pour CI/CD**

### 5.1 Ajouter le fichier de workflow GitHub Actions
1. Dans votre projet, créez ce dossier et fichier :
   ```bash
   mkdir -p .github/workflows
   nano .github/workflows/deploy.yml
   ```

2. Ajoutez ce contenu au fichier `deploy.yml` :


   ```yaml
   
    name: Deploy Docusaurus to GitHub Pages
    
    on:
      push:
        branches:
          - main
    
    jobs:
      build-and-deploy:
        runs-on: ubuntu-latest
    
        steps:
          - name: Checkout code
            uses: actions/checkout@v3
    
          - name: Set up Node.js
            uses: actions/setup-node@v3
            with:
              node-version: 18
    
          - name: Install dependencies
            run: npm ci
    
          - name: Build site
            run: npm run build
    
          - name: Deploy to GitHub Pages
            uses: peaceiris/actions-gh-pages@v3
            with:
              github_token: ${{ secrets.GITHUB_TOKEN }}
              publish_dir: ./build  # Assure-toi que le dossier build est déployé

   ```

**Explications :**
- Ce workflow se déclenche dès qu’un push est effectué sur la branche `main`.
- Il installe Node.js, construit le site, et le déploie sur GitHub Pages.

---

### 5.2 Configurer GitHub Pages
1. Allez dans les paramètres de votre dépôt GitHub.
2. Cliquez sur **Pages**.
3. Sous **Source**, sélectionnez **GitHub Actions**.



### 5.3 **Vérifier les permissions de GitHub Actions**
   - Assurez-vous que le workflow GitHub Actions dispose des permissions nécessaires pour pousser vers le dépôt. Dans les paramètres du dépôt :
     - Accédez à **Paramètres > Actions > Général**.
     - Faites défiler jusqu’à la section **Permissions des workflows**.
     - Vérifiez que l’option **Permissions en lecture et écriture** est sélectionnée.
     - Activez **Autoriser GitHub Actions à créer et approuver des pull requests** si nécessaire.

![image](https://github.com/user-attachments/assets/a89f20ba-9ea0-43b2-ae5e-f617ce9645d6)


---

## **6. Étape finale : Tester le déploiement**
1. Faites une modification simple dans le projet (par exemple, changez le titre dans `docusaurus.config.js`).
2. Poussez vos modifications :
   ```bash
   git add .
   git commit -m "Update site title"
   git push
   ```
3. Attendez que le workflow GitHub Actions termine (allez dans l’onglet **Actions** pour vérifier).
4. Votre site sera disponible à l’adresse : `https://votre_nom_utilisateur.github.io/my-docusaurus-site`.

 A CORRIGER





---

## **7. Points de révision pour vos étudiants**

1. **Qu’est-ce qu’un workflow GitHub Actions ?**
   - Un ensemble d’étapes automatiques déclenchées par des événements comme un push.
2. **Pourquoi utiliser CI/CD ?**
   - Pour automatiser les tests et le déploiement, et éviter les erreurs manuelles.
3. **Qu’est-ce que Docusaurus ?**
   - Un outil pour créer des sites de documentation modernes.

