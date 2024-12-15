## **1. Introduction : Pourquoi utiliser Vercel ?**

### Vercel
Vercel est une plateforme de déploiement qui permet de déployer rapidement des sites web statiques ou dynamiques. C'est idéal pour les frameworks modernes comme Docusaurus.

- **Avantages de Vercel :**
  - Gratuit pour des projets simples.
  - Déploiement rapide en quelques clics.
  - Compatible avec les frameworks JavaScript comme Next.js, React, et Docusaurus.

---

## **2. Pré-requis**

Assurez-vous que vos étudiants disposent de :
1. Un ordinateur avec **Node.js** installé ([Télécharger Node.js](https://nodejs.org/)).
2. **Git** installé ([Télécharger Git](https://git-scm.com/)).
3. Un compte **GitHub** ([Créer un compte GitHub](https://github.com/)).
4. Un compte **Vercel** ([Créer un compte Vercel](https://vercel.com/signup)).

---

## **3. Étape par étape : Créer un site Docusaurus**

### 3.1 Installer Node.js et vérifier
1. Installez Node.js en suivant [ce lien](https://nodejs.org/).
2. Ouvrez votre terminal et tapez :
   ```bash
   node -v
   ```
   Vous devriez voir une version, par exemple `v18.x`.

3. Vérifiez également que `npm` (Node Package Manager) est installé :
   ```bash
   npm -v
   ```
   Vous verrez une version comme `9.x`.

---

### 3.2 Créer un nouveau site Docusaurus
1. Dans votre terminal, créez un nouveau projet Docusaurus :
   ```bash
   npx create-docusaurus@latest my-docusaurus-site classic
   ```
   **Explications :**
   - `npx` : Exécute une commande sans avoir besoin d’installer le paquet globalement.
   - `my-docusaurus-site` : Nom du dossier où sera créé le projet.
   - `classic` : Utilise le modèle classique de Docusaurus.

2. Naviguez dans le dossier du projet :
   ```bash
   cd my-docusaurus-site
   ```

3. Lancez le site en local pour vérifier :
   ```bash
   npm start
   ```
   **Résultat attendu :** Une URL comme `http://localhost:3000` s'ouvre dans votre navigateur. Vous verrez le site Docusaurus par défaut.

---

### 3.3 Explorer la structure du projet
- **`/docs`** : Fichiers de documentation.
- **`/blog`** : Fichiers de blog.
- **`/src`** : Code source pour personnaliser le design.
- **`docusaurus.config.js`** : Fichier de configuration principal.

---

## **4. Héberger votre projet avec Vercel**

### 4.1 Préparer le dépôt GitHub
1. Initialisez un dépôt Git localement :
   ```bash
   git init
   ```
2. Ajoutez tous les fichiers à Git :
   ```bash
   git add .
   git commit -m "Initial commit"
   ```
3. Liez votre projet à un dépôt GitHub :
   ```bash
   git remote add origin https://github.com/votre_nom_utilisateur/my-docusaurus-site.git
   ```
   Remplacez `votre_nom_utilisateur` par votre nom d’utilisateur GitHub.

4. Poussez le code vers GitHub :
   ```bash
   git branch -M main
   git push -u origin main
   ```

---

### 4.2 Connecter Vercel à GitHub
1. **Créer un compte Vercel :**
   - Rendez-vous sur [https://vercel.com/](https://vercel.com/).
   - Connectez-vous avec votre compte GitHub.

2. **Importer votre projet GitHub :**
   - Cliquez sur **New Project** sur Vercel.
   - Sélectionnez votre dépôt **my-docusaurus-site**.

3. **Configurer le projet Vercel :**
   - Lors de l'importation :
     - **Framework Preset :** Choisissez **Other**.
     - **Build Command :** Remplacez par :
       ```bash
       npm run build
       ```
     - **Output Directory :** Remplacez par :
       ```bash
       build
       ```

4. **Déployer le projet :**
   - Cliquez sur **Deploy**.
   - Vercel commencera à construire et déployer votre site.

5. Une fois terminé, vous obtiendrez une URL comme :
   ```text
   https://my-docusaurus-site.vercel.app
   ```

---

## **5. Tester et Personnaliser**

### 5.1 Modifier le site
1. Ouvrez le fichier `docusaurus.config.js` dans votre éditeur de texte (par ex. Visual Studio Code).
2. Modifiez la propriété `title` pour changer le titre du site :
   ```javascript
   module.exports = {
     title: 'Mon Site Docusaurus',
     tagline: 'Documentation moderne et rapide',
     ...
   };
   ```
3. Sauvegardez, commitez vos changements, et poussez-les sur GitHub :
   ```bash
   git add .
   git commit -m "Update site title"
   git push
   ```

4. Vercel détectera automatiquement les changements et redéploiera le site.

---

### 5.2 Ajouter une nouvelle page
1. Créez un nouveau fichier dans `/docs`, par exemple `intro.md`.
2. Ajoutez du contenu Markdown :
   ```markdown
   # Introduction

   Bienvenue sur mon site Docusaurus déployé sur Vercel !
   ```
3. Ajoutez la page dans le menu (dans `sidebars.js`) :
   ```javascript
   module.exports = {
     docs: [
       {
         type: 'category',
         label: 'Documentation',
         items: ['intro'],
       },
     ],
   };
   ```

4. Poussez vos changements, et vérifiez la mise à jour sur Vercel.

---

## **6. Points à Réviser**

1. **Qu’est-ce que Vercel ?**
   - Une plateforme qui simplifie le déploiement des sites web.
2. **Pourquoi utiliser Vercel avec GitHub ?**
   - Pour automatiser le déploiement dès qu’une modification est poussée.
3. **Comment fonctionne le processus de déploiement ?**
   - Vous codez localement → Vous poussez sur GitHub → Vercel construit et déploie le site.

---

## **7. Résumé des commandes**

1. **Créer un projet Docusaurus :**
   ```bash
   npx create-docusaurus@latest my-docusaurus-site classic
   ```
2. **Lancer le site en local :**
   ```bash
   npm start
   ```
3. **Commiter et pousser les changements sur GitHub :**
   ```bash
   git add .
   git commit -m "Message"
   git push
   ```
4. **Déployer sur Vercel :**
   - Importer le projet depuis GitHub, configurer, et cliquer sur **Deploy**.



