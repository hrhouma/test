# Partie approfondi : Comment Docusaurus gère le routage pour le blog

Bonjour et bienvenue dans ce cours où nous allons explorer en profondeur comment **Docusaurus**, un outil moderne pour la création de sites web, gère le **routage** de son module de blog. 

Mon objectif est de vous expliquer cela étape par étape, avec des analogies, des exemples concrets, et une progression logique pour vous permettre de comprendre chaque concept.

---

### **Introduction : Qu’est-ce que le routage ?**

Avant de commencer, il est important de comprendre le concept de **routage**. Imaginez un site web comme une grande bibliothèque. Le **routage**, c'est comme le système de classification des livres : il vous dit où aller pour trouver l’information que vous cherchez. Chaque URL sur votre site web agit comme une "adresse" qui vous amène à une page spécifique, tout comme une cote Dewey vous mène à un livre dans une bibliothèque.

Dans **Docusaurus**, le routage de base pour un blog est automatique et très flexible. Mais il est important de comprendre comment il fonctionne pour personnaliser votre site.

---

### **1. La structure de base : le répertoire `/blog`**

Quand vous créez un projet avec **Docusaurus**, le répertoire `/blog` joue un rôle **spécial**. Voici pourquoi :

- **Reconnaissance automatique :** Docusaurus sait que tout fichier Markdown (`.md` ou `.mdx`) placé dans ce répertoire est un article de blog.
- **Page d’index automatique :** Si vous accédez à `http://localhost:3000/blog`, Docusaurus génère une **page d’accueil pour le blog** qui liste tous les articles dans l’ordre chronologique inverse (les plus récents en premier).
- **Routage automatique :** Docusaurus crée une URL pour chaque article, sans que vous ayez à écrire une seule ligne de code pour configurer des routes.

#### Exemple de structure :
```plaintext
/my-docusaurus-site
├── blog
│   ├── 2023-01-01-intro-to-docusaurus.md
│   ├── 2023-02-15-advanced-routing.md
│   ├── 2023-03-10-blog-plugins.md
```

- Chaque fichier dans ce répertoire devient un article de blog avec son propre lien.
- La page `http://localhost:3000/blog` affichera automatiquement une **liste** de ces articles, avec les titres, dates, et extraits.

**💡 Astuce pédagogique :** 
Pensez au dossier `/blog` comme une boîte magique. Vous y déposez des fichiers Markdown, et Docusaurus fait tout le travail pour les transformer en pages web bien organisées.

---

### **2. Routage basé sur les fichiers**

#### **Comment les URLs sont-elles générées ?**
Chaque fichier Markdown dans `/blog` devient une page web, avec une URL basée sur **deux choses possibles** :
1. **Le slug** défini dans le fichier (prioritaire).  
2. **Le nom du fichier**, s’il n’y a pas de slug.

#### **Exemple 1 : URL basée sur le slug**
Prenons un fichier Markdown avec ce contenu au début (appelé **frontmatter**) :
```markdown
---
slug: docusaurus-introduction
title: Introduction à Docusaurus
date: 2023-01-01
---
```
- **Slug :** Le slug spécifié dans le frontmatter est `docusaurus-introduction`.  
- **URL générée :** Cet article sera accessible à l’adresse `http://localhost:3000/blog/docusaurus-introduction`.

#### **Exemple 2 : URL basée sur le nom de fichier**
Si vous ne spécifiez **pas de slug**, Docusaurus utilise le **nom du fichier**. Par exemple :
- Fichier : `2023-02-15-advanced-routing.md`  
- **URL générée :** `http://localhost:3000/blog/advanced-routing`.

#### **Résumons les règles :**
1. Si un slug est défini dans le frontmatter, il remplace le comportement par défaut.
2. Si aucun slug n’est défini, l’URL est dérivée du nom de fichier.
3. Si une date est présente dans le nom de fichier (`YYYY-MM-DD`), elle sera utilisée comme date de publication par défaut.

---

### **3. La page d’index du blog**

La page `http://localhost:3000/blog` est comme une **table des matières** de votre blog. Elle affiche :
- Une **liste chronologique** des articles.
- Les **titres**, **dates**, **tags**, et un extrait de chaque article.

#### **Tri des articles**
- Les articles sont triés du plus récent au plus ancien.
- **Source de la date :**
  1. Si une date est incluse dans le nom de fichier (par exemple : `2023-01-01-title.md`), elle sera utilisée.
  2. Si une date est spécifiée dans le frontmatter (`date: 2023-01-01`), elle prendra la priorité.
  3. Si aucune date n’est disponible, l’article apparaîtra sans tri chronologique.

#### **Personnalisation de l’index**
Vous pouvez personnaliser cette page dans votre fichier de configuration. Nous aborderons cette configuration un peu plus tard.

---

### **4. Le rôle du frontmatter dans les fichiers Markdown**

Le **frontmatter**, c’est la partie entre les délimiteurs `---` au début d’un fichier Markdown. C’est ici que vous définissez des métadonnées pour votre article.

#### **Exemple complet d’un frontmatter :**
```markdown
---
slug: advanced-routing
title: Routage avancé avec Docusaurus
date: 2023-02-15
tags: [docusaurus, blog, routing]
description: Une introduction approfondie au routage des blogs dans Docusaurus.
---
```

- **slug :** Personnalise l’URL.
- **title :** Titre de l’article (affiché sur la page d’index).
- **date :** Détermine l’ordre chronologique.
- **tags :** Catégorise l’article pour faciliter la recherche.
- **description :** Texte affiché sur la page d’index comme résumé.

---

### **5. Configuration du plugin @docusaurus/plugin-content-blog**

#### **Qu’est-ce que ce plugin ?**
C’est un plugin natif de Docusaurus qui gère tout le système de blog : la création des pages, la génération des routes, et même les options de personnalisation.

#### **Configurer le plugin dans `docusaurus.config.js`**
Voici un exemple de configuration du plugin blog :
```javascript
module.exports = {
  plugins: [
    [
      '@docusaurus/plugin-content-blog',
      {
        path: './blog', // Dossier contenant les articles
        routeBasePath: 'blog', // URL de base (par défaut : "blog")
        blogSidebarTitle: 'Tous les articles', // Titre de la barre latérale
        blogSidebarCount: 'ALL', // Nombre d’articles dans la barre latérale
        showReadingTime: true, // Affiche le temps de lecture estimé
      },
    ],
  ],
};
```

#### **Quelques options importantes :**
- **`routeBasePath` :** Change l’URL de base. Par exemple, changer `"blog"` en `"articles"` donne des URLs comme `/articles`.
- **`blogSidebarCount` :** Affiche un nombre limité d’articles ou `"ALL"` pour tous les articles.
- **`showReadingTime` :** Ajoute un temps de lecture estimé pour chaque article.

---

### **6. Fonctionnement automatisé de Docusaurus**

L’un des plus grands avantages de Docusaurus est qu’il automatise énormément de tâches :
- **Routage :** Vous n’avez pas besoin de configurer manuellement des routes pour vos articles.
- **Tri :** Les articles sont automatiquement triés par date.
- **URLs :** Générées automatiquement à partir des noms de fichiers ou des slugs.

En suivant les conventions de base (mettre vos fichiers Markdown dans `/blog`), vous obtenez un blog fonctionnel sans effort supplémentaire.

---

### **Conclusion**

**Docusaurus** simplifie grandement la gestion des blogs grâce à son système de routage intuitif et puissant. Que vous soyez un développeur débutant ou expérimenté, ses fonctionnalités automatiques vous permettent de vous concentrer sur le contenu plutôt que sur la configuration.

**À retenir :**
1. Le dossier `/blog` est le cœur du système.
2. Chaque fichier Markdown devient une page, avec une URL propre.
3. Vous pouvez personnaliser le comportement du blog via le plugin `@docusaurus/plugin-content-blog`.

Maintenant, à vous de jouer ! Testez ces concepts dans votre propre projet et personnalisez votre blog Docusaurus pour qu’il corresponde parfaitement à vos besoins. 😊
