# Créer et Lancer votre Premier Blog avec **Docusaurus** 🚀

Dans ce tutoriel, nous allons apprendre à créer un site web attractif et professionnel avec **Docusaurus**. Le projet portera le nom accrocheur **Skillr1**, conçu pour séduire un large public et devenir une référence pour les blogs éducatifs et de partage de documents importants. 🔥

---

# Étape 1 : Installer les prérequis

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

# Étape 2 : Créer votre application Docusaurus

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

# Étape 3 : Lancer votre site localement

1. **Démarrer le serveur de développement** :  
   Dans le terminal, exécutez :  
   ```bash
   npx docusaurus start ou npm start
   ```

2. **Accéder au site** :  
   - Ouvrez votre navigateur et allez à l’adresse suivante :  
     👉 [http://localhost:3000](http://localhost:3000)
   - Vous verrez votre site en ligne, prêt à être personnalisé.
   - Vérifiez la page d'introduction :
     👉 [http://localhost:3000](http://localhost:3000/docs/intro)

---

# Étape 4 : Personnaliser le contenu

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


   - Vérifiez la nouvelle page d'introduction :
     👉 [http://localhost:3000](http://localhost:3000/docs/intro)


> **☠️ Vous avez un problème ? Pas de panique, nous allons le résoudre ensemble.**
> **☠️ Oui, c’est voulu !** Les problèmes sont une occasion d’apprendre et de progresser. Nous allons maintenant appliquer le **prompt engineering** pour aller plus loin.
> Consultez **l’annexe 01 ☠️** : elle contient toutes les informations nécessaires pour maîtriser le troubleshooting avec **Cursor AI**.



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


   - Vérifiez la nouvelle page de blog :
     👉 [http://localhost:3000](http://localhost:3000/blog)


> **☠️ Vous avez un problème ? Pas de panique, nous allons le résoudre ensemble.**
> **☠️ Oui, c’est voulu !** Les problèmes sont une occasion d’apprendre et de progresser. Nous allons maintenant appliquer le **prompt engineering** pour aller plus loin.
> Consultez **l’annexe 02 ☠️** : elle contient toutes les informations nécessaires pour maîtriser le troubleshooting avec **Cursor AI**.









----------
------------


# Annexe 01 - 🚀 Résolution du Problème "Page Not Found" sur Docusaurus  

## **🌟 Méthodologie : Approche Itérative avec Cursor AI**  
1. **📍 Tester le chemin suivant dans votre navigateur :**  
   **http://localhost:3000/docs/intro**  

   **Résultat attendu :** La page s’affiche correctement.  
   **Résultat actuel :** ❌ **"Page Not Found"**  

2. Utiliser Cursor AI pour identifier et résoudre le problème étape par étape.  

---

## **🔍 Étape 1 : Prompt Initial (Il se peut que cela ne fonctionne pas immédiatement)**  

 ```

# Prompt 01

> Je rencontre un problème avec Docusaurus : la page http://localhost:3000/docs/intro retourne une erreur **Page Not Found**.
> Cela semble lié à un problème de chemin ou de configuration. Voici les détails :
> 1. Le fichier `intro.md` est situé dans le répertoire `/docs` et contient cet en-tête frontmatter :
   ---
   id: intro
   title: Introduction
   ---
   ## Bienvenue sur votre documentation !

   ```

2. La configuration dans `docusaurus.config.js` ressemble à ceci :

   ```ssh

   presets: [
     [
       '@docusaurus/preset-classic',
       {
         docs: {
           path: 'docs',
           routeBasePath: 'docs',
           sidebarPath: require.resolve('./sidebars.js'),
         },
       },
     ],
   ],

   
   ```


3. La commande `npx docusaurus start` démarre le site, mais le chemin `/docs/intro` ne fonctionne pas et retourne une erreur **Page Not Found**.

### Ce que je souhaite :
1. Diagnostiquer si le problème vient du chemin d’accès, du fichier, ou d'une mauvaise configuration.
2. S'assurer que la page `/docs/intro` s'affiche correctement sur http://localhost:3000/docs/intro.
3. Obtenir des étapes claires pour corriger ce problème.

Merci !


**🌐 Tester à nouveau le chemin :**  
- **Résultat :** Toujours **Page Not Found** ❌  

---

## **🔄 Étape 2 : Prompt Simplifié (Basique)**  

- **Prompt 02:**
  
```
J'ai toujours le même problème : la page http://localhost:3000/docs/intro retourne une erreur **Page Not Found** malgré les modifications précédentes. Pouvez-vous m'aider à diagnostiquer davantage ?
```


## **✨ Conseil Pro :**  
Toujours tester après chaque modification avec **http://localhost:3000/docs/intro** et redémarrer votre serveur avec :  
```bash
npx docusaurus start ou npm start
```


**🌐 Tester à nouveau le chemin :**  
- **Résultat :** **Problème résolu** ✅  



---

## **🛠 Étape 3 (OPTIONNELLE) : Prompt Avancé pour Approfondir la Résolution**  

Voici les modifications qui ont corrigé le problème :  

### **Modification du fichier `docs/intro.md` :**
```markdown
---
id: intro
title: Introduction
sidebar_position: 1
---
```

### **Simplification de `docusaurus.config.js` :**
```javascript
docs: {
  sidebarPath: require.resolve('./sidebars.js'), // Lien vers les barres latérales
  // Suppression des paramètres inutiles comme `routeBasePath` et `path`
},
```

### **Modification de `sidebars.js` :**
```javascript
const sidebars = {
  tutorialSidebar: [ // Changement de 'docs' à 'tutorialSidebar'
    'intro',
    {
      type: 'category',
      label: 'Linux',
      items: [], // Ajouter vos éléments si nécessaire
    },
  ],
};

module.exports = sidebars;
```

---

## **✅ Points Clés de la Solution :**  
1. **🛠 Utilisation de `tutorialSidebar`** au lieu de `docs` dans la configuration des barres latérales.  
2. **❌ Suppression des configurations superflues** dans `docusaurus.config.js` pour éviter les conflits.  
3. **📄 Simplification du frontmatter dans `intro.md`** pour garantir une structure conforme aux standards de Docusaurus.  

**🌐 Résultat Final :**  
La page **http://localhost:3000/docs/intro** s’affiche correctement. 🎉  




---

## **✨ Conseil Pro :**  
Toujours tester après chaque modification avec **http://localhost:3000/docs/intro** et redémarrer votre serveur avec :  
```bash
npx docusaurus start ou npm start
```

















