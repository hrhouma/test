# Créer et Lancer votre Premier Blog avec **Docusaurus** 🚀

Dans ce tutoriel, nous allons apprendre à créer un site web attractif et professionnel avec **Docusaurus**. Le projet portera le nom accrocheur **Skillr1**, conçu pour séduire un large public et devenir une référence pour les blogs éducatifs et de partage de documents importants. 🔥

---

### Étape 1 : Installer les prérequis

Avant de commencer, assurez-vous que les outils suivants sont installés sur votre machine :

1. **Node.js** (LTS recommandé) :  
   - Téléchargez et installez Node.js depuis [Node.js](https://nodejs.org).

2. **npm** (inclus avec Node.js) :  
   - Vérifiez si `npm` est bien installé avec :  
     ```bash
     npm -v
     ```

3. **npx** (inclus avec npm 5.2+ et Node.js 8.2+) :  
   - Vérifiez sa version avec :  
     ```bash
     npx --version
     ```

---

### Étape 2 : Créer votre application Docusaurus

1. **Créer le projet** :  
   Ouvrez un terminal et exécutez la commande suivante :  
   ```bash
   npx create-docusaurus@latest Skillr1 classic
   ```

   - **Explications** :
     - `create-docusaurus@latest` : Installe la dernière version de Docusaurus.
     - `Skillr1` : Le nom de votre projet (court, moderne, et mémorable).
     - `classic` : Utilise le template de base **classic**, parfait pour débuter rapidement.

2. **Accéder au projet** :  
   Une fois la création terminée, déplacez-vous dans le répertoire :  
   ```bash
   cd Skillr1
   ```

---

### Étape 3 : Lancer votre site localement

1. **Démarrer le serveur de développement** :  
   Dans le terminal, exécutez :  
   ```bash
   npx docusaurus start
   ```

2. **Accéder au site** :  
   - Ouvrez votre navigateur et allez à l’adresse suivante :  
     👉 [http://localhost:3000](http://localhost:3000)
   - Vous verrez votre site en ligne, prêt à être personnalisé.

---

### Étape 4 : Personnaliser le contenu

Docusaurus fournit des fichiers de documentation et un blog par défaut. Voici comment les modifier pour adapter votre site :

1. **Fichiers principaux** :
   - Les fichiers de documentation sont dans le répertoire **`/docs`**.
   - Les articles de blog sont dans **`/blog`**.

2. **Modifier un document** :
   - Ouvrez le fichier `docs/intro.md` dans un éditeur comme VS Code.  
     Remplacez le contenu par :  
     ```markdown
     ---
     id: introduction
     title: Bienvenue sur Skillr1
     ---
     ## Pourquoi Skillr1 ?
     Skillr1 est conçu pour vous permettre de partager vos cours, notes, et documents importants avec une interface conviviale et professionnelle.

     ### Ce que vous apprendrez ici :
     - Créer et organiser vos contenus facilement.
     - Rendre vos documents accessibles à tous.
     - Faire de votre blog une plateforme incontournable.
     ```

3. **Ajouter un article de blog** :
   - Créez un nouveau fichier dans **`/blog`**, par exemple `premier-article.md`, avec ce contenu :  
     ```markdown
     ---
     title: Mon aventure avec Skillr1
     description: Découvrez comment créer un blog attractif en quelques minutes avec Docusaurus.
     author: Votre Nom
     tags: [docusaurus, blog, éducation]
     ---
     ## Bienvenue sur Skillr1
     Avec Docusaurus, j’ai rapidement mis en ligne un blog pour partager mes cours et documents. C'est simple, rapide, et efficace !
     ```

4. **Recharger votre site** :  
   - Enregistrez vos modifications, et votre site sera automatiquement mis à jour dans le navigateur.


