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
   npx docusaurus start 
   ```

   ou

   ```bash
   npm start
   ```

3. **Accéder au site** :  
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

#### Testez :
- http://localhost:3000/docs/intro
- http://localhost:3000/blog

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
     👉 [http://localhost:3000/intro](http://localhost:3000/docs/intro)


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
     👉 [http://localhost:3000/blog](http://localhost:3000/blog)


> **☠️ Vous avez un problème ? Pas de panique, nous allons le résoudre ensemble.**
> **☠️ Oui, c’est voulu !** Les problèmes sont une occasion d’apprendre et de progresser. Nous allons maintenant appliquer le **prompt engineering** pour aller plus loin.
> Consultez **l’annexe 02 ☠️** : elle contient toutes les informations nécessaires pour maîtriser le troubleshooting avec **Cursor AI**.









----------


# Annexe 01 - Résolution du Problème "Page Not Found" sur Docusaurus  

## **Méthodologie : Approche Itérative avec Cursor AI**  
1. **Tester le chemin suivant dans votre navigateur :**  
   **http://localhost:3000/docs/intro**  

   **Résultat attendu :** La page s’affiche correctement.  
   **Résultat actuel :** "Page Not Found"  

2. Utiliser Cursor AI pour identifier et résoudre le problème étape par étape.  

---

# **Étape 1 : Prompt Initial (Il se peut que cela ne fonctionne pas immédiatement)**  

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

```javascript
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

**Tester à nouveau le chemin :**  
- **Résultat :** Toujours **Page Not Found**  

---

# **Étape 2 : Prompt Simplifié (Basique)**  

- **Prompt 02 :**
  
```
J'ai toujours le même problème : la page http://localhost:3000/docs/intro retourne une erreur **Page Not Found** malgré les modifications précédentes. Pouvez-vous m'aider à diagnostiquer davantage ?
```

**Tester à nouveau le chemin :**  
- **Résultat :** Toujours **Page Not Found**  

---


# **Étape 3 (optionnelle) : Prompt avanc.**  

- Ce prompt met l'accent sur le problème spécifique du lien brisé et invite à examiner les fichiers de configuration ainsi que le contenu du fichier `intro.md`.
- Le prompt clair et détaillé pour insister sur la nécessité de vérifier le lien brisé entre `/docs/intro` et le fichier `intro.md` :

---

**Prompt :**  
> J'ai un problème avec Docusaurus : le chemin **http://localhost:3000/docs/intro** retourne une erreur **Page Not Found**.  
> Après analyse, il semble y avoir un lien brisé entre l’URL `/docs/intro` et le fichier `intro.md`. Voici les détails :  
>   
> - **Le fichier `intro.md`** est situé dans le dossier `docs/` et contient le frontmatter suivant :  
>   ```markdown
>   ---
>   id: intro
>   title: Introduction
>   ---
>   ## Bienvenue sur votre documentation !
>   ```
>   
> - **Le fichier `docusaurus.config.js`** inclut cette configuration pour les documents :  
>   ```javascript
>   docs: {
>     path: 'docs',
>     routeBasePath: 'docs',
>     sidebarPath: require.resolve('./sidebars.js'),
>   },
>   ```
>   
> **Points à vérifier :**  
> 1. Le fichier `intro.md` est-il correctement référencé dans la barre latérale (`sidebars.js`) ?  
> 2. La configuration `id: intro` dans `intro.md` correspond-elle bien à l'URL `/docs/intro` ?  
> 3. La configuration dans `docusaurus.config.js` ou dans `sidebars.js` contient-elle des erreurs ?  
>   
> **Ce que je souhaite :**  
> - Diagnostiquer précisément pourquoi `/docs/intro` ne trouve pas `intro.md`.  
> - Vérifier si le problème vient du chemin d’accès, du frontmatter, ou de la configuration dans `docusaurus.config.js` ou `sidebars.js`.  
> - Proposer des étapes détaillées pour corriger le lien entre l’URL `/docs/intro` et le fichier `intro.md`.  



---

## **Conseil Pro :**  
Toujours tester après chaque modification avec **http://localhost:3000/docs/intro** et redémarrer votre serveur avec :  
```bash
npx docusaurus start ou npm start
```  







-------------------
# Annexe 02 - Résolution du Problème "Blog Page Not Found" sur Docusaurus  
-------------------

## **Méthodologie : Approche Itérative avec Cursor AI**  
1. **Tester le chemin suivant dans votre navigateur :**  
   **http://localhost:3000/blog**  

   **Résultat attendu :** La page s’affiche correctement avec le nouvel article de blog.  
   **Résultat actuel :** "Page Not Found"  

2. Utiliser Cursor AI pour identifier et résoudre le problème étape par étape.  

---

# **Étape 1 : Prompt Initial (Première tentative)**  

```

# Prompt 01

> J'ai un problème avec Docusaurus : la page http://localhost:3000/blog retourne une erreur **Page Not Found**.
> Voici les détails :
> 1. J’ai ajouté un nouveau fichier `premier-article.md` dans le répertoire `/blog`.  
>    Voici son contenu :  
>    ```markdown
>    ---
>    title: Mon aventure avec Skillr1
>    description: Découvrez comment créer un blog attractif en quelques minutes avec Docusaurus.
>    author: Votre Nom
>    tags: [docusaurus, blog, éducation]
>    ---
>    ## Bienvenue sur Skillr1
>    Avec Docusaurus, j’ai rapidement mis en ligne un blog pour partager mes cours et documents. C'est simple, rapide, et efficace !
>    ```
> 2. J’ai sauvegardé mes modifications, et le serveur est automatiquement mis à jour.  
> 3. La page `http://localhost:3000/blog` ne fonctionne toujours pas.  

### Ce que je souhaite :
1. Diagnostiquer pourquoi la page `/blog` ne trouve pas le fichier `premier-article.md`.
2. Vérifier si le problème vient du fichier de configuration `docusaurus.config.js`, de la structure du dossier, ou du frontmatter.
3. Obtenir des étapes claires pour corriger ce problème et afficher la page de blog correctement.

```

**Tester à nouveau le chemin :**  
- **Résultat :** Toujours **Page Not Found**  

---

# **Étape 2 : Vérifications simplifiées et prompt adapté pour le problème lié au blog** :

---

**Prompt 02 :**

```
J'ai toujours le même problème : la page http://localhost:3000/blog retourne une erreur **Page Not Found** malgré les modifications précédentes. Pouvez-vous m'aider à diagnostiquer davantage ?  

Voici ce que j’ai vérifié jusqu’à présent :  
1. J’ai ajouté un fichier `premier-article.md` dans le dossier `/blog` avec un frontmatter valide :  
   ---
   title: Mon aventure avec Skillr1
   description: Découvrez comment créer un blog attractif en quelques minutes avec Docusaurus.
   author: Votre Nom
   tags: [docusaurus, blog, éducation]
   ---
2. La configuration dans `docusaurus.config.js` inclut une section `blog` :  
   ```javascript
   blog: {
     path: './blog',
     routeBasePath: 'blog',
     include: ['*.md', '*.mdx'],
     showReadingTime: true,
   },
   ```

3. J’ai redémarré le serveur avec `npx docusaurus start` ou `npm start`.  



- Vérifiez :  

1. **Structure des dossiers :**  
   - Le fichier `premier-article.md` est-il bien placé dans le répertoire `/blog` ?  

2. **Frontmatter :**  
   - Le fichier contient-il un frontmatter valide avec les champs obligatoires comme `title`, `description`, et `tags` ?  

3. **Configuration dans `docusaurus.config.js` :**  
   - La section `blog` est-elle correctement configurée dans le fichier ? Par exemple :

     ```javascript
     presets: [
       [
         '@docusaurus/preset-classic',
         {
           blog: {
             path: './blog',
             routeBasePath: 'blog',
             include: ['*.md', '*.mdx'],
           },
         },
       ],
     ],
     ```

4. **Redémarrage du serveur :**  
   - Avez-vous redémarré le serveur après avoir ajouté l'article de blog ?  

---


# **Étape 3 (OPTIONNELLE) : Prompt avancé pour un diagnostic approfondi**  

```

# Prompt 03

> J'ai un problème avec Docusaurus : la page http://localhost:3000/blog retourne toujours une erreur **Page Not Found** malgré les vérifications suivantes :  
> 1. Le fichier `premier-article.md` est bien placé dans le dossier `/blog` et contient un frontmatter valide.  
> 2. La configuration dans `docusaurus.config.js` inclut bien la section suivante :  
>    ```javascript
>    blog: {
>      path: './blog',
>      routeBasePath: 'blog',
>      include: ['*.md', '*.mdx'],
>    },
>    ```
> 3. Le serveur a été redémarré avec la commande `npx docusaurus start`.  
> 4. La structure des fichiers est correcte, mais la page ne se charge toujours pas.  

### Ce que je souhaite :  
1. Diagnostiquer pourquoi la page `/blog` ne trouve pas les articles du dossier `/blog`.  
2. Vérifier si le problème vient du fichier `docusaurus.config.js` ou d’un cache mal rafraîchi.  
3. Obtenir des étapes détaillées pour corriger ce problème et afficher le blog correctement.  

```

**Tester à nouveau le chemin :**  
- **Résultat :** Toujours **Page Not Found**  

---

# **Étape 4 (OPTIONNELLE): Correction et solution potentielle**  

Voici les modifications qui peuvent corriger le problème :  

1. **Vérifiez `premier-article.md` :**
   - Assurez-vous que le fichier commence bien par un frontmatter valide :  
     ```markdown
     ---
     title: Mon aventure avec Skillr1
     description: Découvrez comment créer un blog attractif en quelques minutes avec Docusaurus.
     author: Votre Nom
     tags: [docusaurus, blog, éducation]
     ---
     ```

2. **Modifiez `docusaurus.config.js` :**  
   - Confirmez que la configuration de la section `blog` est correcte :  
     ```javascript
     presets: [
       [
         '@docusaurus/preset-classic',
         {
           blog: {
             path: './blog',
             routeBasePath: 'blog',
             include: ['*.md', '*.mdx'],
             showReadingTime: true,
           },
         },
       ],
     ],
     ```

3. **Nettoyez le cache et redémarrez le serveur :**  
   - Supprimez le cache existant avec la commande :  
     ```bash
     rm -rf .docusaurus
     ```
   - Relancez le serveur :  
     ```bash
     npx docusaurus start
     ```

4. **Testez à nouveau l’URL :**  
   - Rendez-vous sur **http://localhost:3000/blog** et vérifiez si la page fonctionne.

---

# **Points Clés de la Solution :**  

1. Assurez-vous que la structure du dossier `/blog` et le frontmatter de chaque article sont corrects.  
2. Vérifiez que `docusaurus.config.js` inclut bien une section pour le blog.  
3. Supprimez le cache en cas de problème persistant avant de redémarrer le serveur.  

---

## **Conseil Pro :**  
Toujours tester après chaque modification en nettoyant le cache et en redémarrant le serveur avec :  
```bash
npx docusaurus start
```











