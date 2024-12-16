# **Cours Détaillé : Comprendre le Routage dans la Section "Docs" de Docusaurus**

---

## **Introduction : Pourquoi Docusaurus ?**

Imaginez que vous devez rédiger une documentation technique pour votre projet ou produit. Les utilisateurs, développeurs ou partenaires qui consulteront votre documentation doivent :
1. **Trouver facilement l’information qu’ils cherchent.**
2. **Naviguer intuitivement dans un contenu hiérarchisé.**
3. **Profiter d’une présentation claire et organisée, tout en ayant un accès rapide aux versions précédentes.**

C’est là qu’intervient **Docusaurus**, un générateur de sites statiques, conçu spécialement pour créer des documentations modernes, interactives et bien structurées. L’un de ses piliers est la **section "Docs"**, que nous allons explorer en profondeur.

---

## **1. Structure de Base**

### **Qu’est-ce que le dossier `/docs` ?**
Dans Docusaurus, le répertoire `/docs` est **le cœur de votre documentation**. Tous vos fichiers markdown (`.md`) y sont regroupés pour former des pages de documentation.

- **Chaque fichier markdown devient une page de documentation.**
- **Les sous-dossiers permettent de structurer votre contenu.**
- Docusaurus se charge de **traduire cette structure de fichiers en une navigation web fluide**, tout en générant les URLs correspondantes.

---

### **L’URL par défaut de la section "Docs"**
- Lorsque vous lancez votre site localement avec la commande `npm start`, la documentation est accessible via :  
  ```
  http://localhost:3000/docs
  ```

- **Personnalisation possible :** Si vous souhaitez modifier cette URL de base (par exemple pour `http://localhost:3000/guide`), vous pouvez configurer le champ `routeBasePath` dans le fichier `docusaurus.config.js` :

  ```javascript
  module.exports = {
    presets: [
      [
        '@docusaurus/preset-classic',
        {
          docs: {
            routeBasePath: 'guide', // Change /docs en /guide
          },
        },
      ],
    ],
  };
  ```

---

## **2. Organisation Hiérarchique**

L’un des points forts de Docusaurus est sa capacité à **organiser votre documentation selon la structure des fichiers dans le répertoire `/docs`**.

### **Exemple concret :**

```plaintext
docs/
├── intro.md
├── category/
│   ├── _category_.json
│   ├── doc1.md
│   └── doc2.md
└── autre-category/
    └── doc3.md
```

### **Comment Docusaurus interprète cette structure ?**
- **`intro.md`** : Accessible via l’URL `/docs/intro`.  
- **`category/doc1.md`** : Accessible via l’URL `/docs/category/doc1`.  
- **`autre-category/doc3.md`** : Accessible via l’URL `/docs/autre-category/doc3`.

### **Avantages de cette organisation :**
1. **Clarté visuelle** dans vos fichiers. Vous savez où se trouve chaque page.
2. **Simplicité de navigation** : Les utilisateurs comprennent directement où ils se trouvent grâce aux URLs.

> **Point important :** Si vous voulez personnaliser l’URL d’un fichier sans suivre la structure des dossiers, vous pouvez utiliser une métadonnée appelée `slug`, comme nous le verrons plus loin.

---

## **3. Configuration des Documents**

Chaque fichier `.md` peut contenir un en-tête spécial appelé **frontmatter**, qui est écrit en YAML. Ces métadonnées permettent de configurer :
1. **L’ordre des pages dans la barre latérale.**
2. **Le chemin de l’URL.**
3. **Un identifiant unique pour référencer le document.**

### **Exemple détaillé de métadonnées :**
```md
---
sidebar_position: 1
id: mon-doc
slug: chemin-personnalise
---
# Mon Document
Contenu de la page ici.
```

#### **Explications :**
- **`sidebar_position`** :  
  Détermine l’ordre d’affichage dans la barre latérale. Les valeurs plus petites apparaissent en premier.
  
- **`id`** :  
  C’est l’identifiant unique du document. Il est utile pour référencer ce document dans des configurations comme `sidebars.js`.

- **`slug`** :  
  Permet de personnaliser l’URL. Par exemple :  
  ```
  slug: guide/demarrage
  ```
  Cela génère une URL `/docs/guide/demarrage`, indépendamment de l’emplacement réel du fichier.

---

## **4. Catégories**

Les catégories permettent de **regrouper des documents** sous une même thématique. Elles sont définies par un fichier spécial : **`_category_.json`**.

### **Exemple de fichier `_category_.json` :**
```json
{
  "label": "Ma Catégorie",
  "position": 2,
  "link": {
    "type": "generated-index"
  }
}
```

#### **Détails des options :**
- **`label` :** Nom de la catégorie affiché dans la barre latérale.
- **`position` :** Ordre d’affichage dans la barre latérale.
- **`link` :** Permet de générer automatiquement une page d’index pour cette catégorie.

> **Remarque :** L’utilisation des catégories améliore grandement la navigation lorsque vous avez plusieurs documents à regrouper sous un même thème.

---

## **5. Configuration dans `docusaurus.config.js`**

Le fichier `docusaurus.config.js` contrôle le comportement global de votre site, y compris celui de la documentation.

### **Exemple de configuration pour la section "Docs" :**
```javascript
module.exports = {
  presets: [
    [
      '@docusaurus/preset-classic',
      {
        docs: {
          routeBasePath: 'docs', // URL de base
          sidebarPath: require.resolve('./sidebars.js'), // Chemin des barres latérales
        },
      },
    ],
  ],
};
```

### **Points à noter :**
- **`routeBasePath`** : Définit l’URL de base.
- **`sidebarPath`** : Définit le fichier où la configuration des barres latérales est stockée.

---

## **6. Configuration de la Barre Latérale**

Le fichier `sidebars.js` contrôle la structure et le contenu de la barre latérale. Il peut être configuré de manière statique ou généré automatiquement.

### **Exemple de configuration manuelle :**
```javascript
module.exports = {
  tutorialSidebar: [
    'intro', // Document direct
    {
      type: 'category',
      label: 'Ma Catégorie',
      items: ['category/doc1', 'category/doc2'], // Documents dans la catégorie
    },
  ],
};
```

---

## **7. Fonctionnalités Spéciales**

Docusaurus intègre des fonctionnalités pour rendre la documentation plus interactive et conviviale :

1. **Navigation automatique :**  
   Les liens "Précédent" et "Suivant" sont générés automatiquement entre les documents.

2. **Table des matières (ToC) :**  
   Une table des matières est générée automatiquement à partir des titres (`##`, `###`, etc.) présents dans le fichier markdown.

3. **Versioning de la Documentation :**  
   Permet de conserver plusieurs versions de la documentation, idéal pour les projets évolutifs.

4. **Recherche intégrée :**  
   Avec le plugin de recherche, les utilisateurs peuvent facilement trouver le contenu dont ils ont besoin.

---

## **8. Page d’Index**

Par défaut, le premier document (défini par `sidebar_position` ou `sidebars.js`) devient la page d’accueil de la documentation. Vous pouvez changer cela avec la configuration suivante dans `docusaurus.config.js` :

```javascript
docs: {
  routeBasePath: 'docs',
  homePageId: 'intro', // Page d’accueil personnalisée
},
```

---

## **9. Points Forts du Système de Routage**

1. **Hiérarchisation claire :**  
   Les dossiers et catégories permettent une organisation logique du contenu.

2. **Personnalisation avancée :**  
   Avec `slug`, `sidebar_position` et `_category_.json`, chaque aspect peut être ajusté.

3. **Automatisation intelligente :**  
   Même sans configuration, Docusaurus gère automatiquement la barre latérale et les liens.

4. **Adapté aux projets complexes :**  
   Le versioning et les catégories permettent de documenter des projets en évolution.

---

## **Conclusion**

Le routage dans Docusaurus est un système bien pensé, conçu pour répondre aux besoins des documentations modernes. Avec une structure claire, des outils de personnalisation, et des fonctionnalités avancées, il permet de créer une documentation professionnelle, évolutive, et facile à naviguer pour vos utilisateurs.

