### **Cours : Comprendre le routage de Docusaurus pour /blog**

Docusaurus est un framework puissant pour créer des sites web modernes, y compris des blogs. Ce cours vous expliquera en détail comment Docusaurus gère le routage pour le dossier **/blog**. Vous apprendrez à configurer et personnaliser vos articles de blog en utilisant les fonctionnalités natives de Docusaurus.

---

### **1. Structure de Base**
- **Répertoire Spécial :** Le dossier `/blog` est automatiquement reconnu par Docusaurus pour gérer la fonctionnalité de blog.
- **Routage Automatique :** Lorsque vous accédez à `http://localhost:3000/blog`, Docusaurus génère automatiquement une page d’index pour votre blog. Cette page liste tous vos articles.
  - Les articles sont triés par **date**, du plus récent au plus ancien.

---

### **2. Routage Basé sur les Fichiers**
- **Articles de Blog :** Chaque fichier Markdown (`.md` ou `.mdx`) placé dans le répertoire `/blog` devient un article de blog.
- **Structure des URLs :** 
  - **Définie par le slug (dans le frontmatter) :** Si un `slug` est spécifié dans le fichier, il détermine directement l’URL.
  - **Basée sur le nom de fichier :** Si aucun slug n’est défini, l’URL est dérivée du nom du fichier. Par exemple :
    - `2021-08-26-welcome.md` devient accessible à l’URL `/blog/welcome`.

#### **Exemple de frontmatter :**
```markdown
---
slug: welcome
title: Bienvenue sur le Blog
date: 2021-08-26
tags: [introduction, docusaurus]
---
```
- **Résultat :** Cet article sera accessible via `http://localhost:3000/blog/welcome`.
- **Le slug remplace l’URL par défaut :** Si vous spécifiez un slug, il remplace la structure d’URL basée sur le nom du fichier.

---

### **3. Page d’Index du Blog**
- L’URL principale `/blog` affiche une **page d’index** qui contient :
  - Une liste de tous les articles disponibles.
  - Les articles sont triés par date (les plus récents en haut).
  - Les métadonnées, comme le titre, la date et les tags, sont extraites du **frontmatter** de chaque fichier Markdown.

#### **Sources de la date d’un article :**
1. **Nom du fichier :** Si le nom du fichier commence par une date (exemple : `2021-08-26-welcome.md`), cette date est utilisée.
2. **Champ `date` dans le frontmatter :** Si vous spécifiez une date dans le frontmatter, elle prend la priorité.

---

### **4. Configuration du Plugin Blog**
Le routage pour les blogs est géré par le plugin **`@docusaurus/plugin-content-blog`**. Vous pouvez personnaliser son comportement dans le fichier de configuration **`docusaurus.config.js`**.

#### **Exemple de Configuration :**
```javascript
module.exports = {
  plugins: [
    [
      '@docusaurus/plugin-content-blog',
      {
        path: './blog', // Chemin vers le répertoire du blog
        routeBasePath: 'blog', // URL de base du blog
        blogSidebarTitle: 'Tous les articles', // Titre de la barre latérale
        blogSidebarCount: 'ALL', // Afficher tous les articles dans la barre latérale
        showReadingTime: true, // Affiche le temps de lecture estimé
      },
    ],
  ],
};
```

#### **Personnalisation du routage :**
- **`routeBasePath` :** Par défaut, l’URL de base est `/blog`. Vous pouvez la modifier, par exemple en remplaçant `blog` par `articles` pour avoir des URLs comme `/articles`.
- **`path` :** Spécifie le chemin du dossier contenant les articles de blog.
- **`blogSidebarCount` :** Détermine combien d’articles sont affichés dans la barre latérale.

---

### **5. Fonctionnalité Automatisée**
Docusaurus simplifie grandement le processus de gestion des routes pour votre blog :
- **Aucune configuration manuelle requise :** Tant que vos articles respectent la convention (placés dans le dossier `/blog`), Docusaurus génère automatiquement les routes.
- **Slug et métadonnées :** Les slugs définissent des URLs propres et lisibles. Les métadonnées enrichissent l’affichage des articles.

---

### **Conclusion**
Docusaurus fournit un système de routage intuitif et puissant pour gérer vos articles de blog. En utilisant les conventions de base, comme le répertoire `/blog` et les fichiers Markdown, vous pouvez rapidement mettre en place un blog bien structuré. Pour des besoins spécifiques, le plugin blog offre des options de personnalisation flexibles.

Avec ces connaissances, vous êtes prêt à configurer et personnaliser le routage de votre blog dans Docusaurus. 🎉
