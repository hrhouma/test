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
             publish_dir: ./build
   ```

**Explications :**
- Ce workflow se déclenche dès qu’un push est effectué sur la branche `main`.
- Il installe Node.js, construit le site, et le déploie sur GitHub Pages.

---

### 5.2 Configurer GitHub Pages
1. Allez dans les paramètres de votre dépôt GitHub.
2. Cliquez sur **Pages**.
3. Sous **Source**, sélectionnez **GitHub Actions**.

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

---

## **7. Points de révision pour vos étudiants**

1. **Qu’est-ce qu’un workflow GitHub Actions ?**
   - Un ensemble d’étapes automatiques déclenchées par des événements comme un push.
2. **Pourquoi utiliser CI/CD ?**
   - Pour automatiser les tests et le déploiement, et éviter les erreurs manuelles.
3. **Qu’est-ce que Docusaurus ?**
   - Un outil pour créer des sites de documentation modernes.

