# **Cours : Fonctionnement du Routage pour la Section "Docs" dans Docusaurus**

---

## **1. Structure de Base**

Dans Docusaurus, la section **"Docs"** est dédiée à la gestion et à l'organisation de votre documentation. 

- **Dossier spécial `/docs`**  
  Tous les fichiers de documentation sont centralisés dans le dossier `/docs`. Chaque fichier représente une page de documentation.

- **URL de base**  
  Par défaut, l'accès à cette section se fait via :  
  ```
  http://localhost:3000/docs
  ```
  Ce chemin peut être personnalisé dans le fichier de configuration (`docusaurus.config.js`) en modifiant la valeur `routeBasePath`.

---

## **2. Organisation Hiérarchique**

La structure des URLs dans la section "Docs" est directement liée à l'organisation des fichiers dans le répertoire `/docs`.

### Exemple de structure de fichiers :
```
docs/
├── intro.md
├── category/
│   ├── _category_.json
│   ├── doc1.md
│   └── doc2.md
└── autre-category/
    └── doc3.md
```

### Génération des URLs correspondantes :
- **`intro.md` → `/docs/intro`**  
- **`category/doc1.md` → `/docs/category/doc1`**  
- **`autre-category/doc3.md` → `/docs/autre-category/doc3`**

> **Note :** La structure des dossiers et des fichiers détermine automatiquement les catégories et les sous-catégories dans Docusaurus, sauf si une configuration spécifique est appliquée.

---

## **3. Configuration des Documents**

Chaque document peut être enrichi avec des **métadonnées (frontmatter)** en haut du fichier `.md`.

### Exemple de métadonnées :
```md
---
sidebar_position: 1
id: mon-doc
slug: chemin-personnalise
---
```

#### Explications :
- **`sidebar_position`**  
  Définit l'ordre d'affichage du document dans la barre latérale. Les numéros plus bas apparaissent en premier.
  
- **`id`**  
  Identifiant unique du document utilisé pour le référencer dans la configuration.

- **`slug`**  
  Permet de personnaliser l’URL de la page. Par exemple :  
  ```md
  slug: "guide/demarrage"
  ```
  Résulte en une URL `/docs/guide/demarrage`.

---

## **4. Catégories**

Les catégories permettent de regrouper les documents en sections logiques. Elles sont définies à l’aide d’un fichier spécial `_category_.json`.

### Exemple de `_category_.json` :
```json
{
  "label": "Nom de Catégorie",
  "position": 2,
  "link": {
    "type": "generated-index"
  }
}
```

#### Paramètres :
- **`label` :**  
  Nom affiché de la catégorie.
  
- **`position` :**  
  Ordre d'apparition dans la barre latérale.
  
- **`link` :**  
  Crée une page d’index générée automatiquement pour cette catégorie.

---

## **5. Configuration dans `docusaurus.config.js`**

Le fichier **`docusaurus.config.js`** contient les paramètres globaux de la documentation.

### Exemple de configuration pour la section "Docs" :
```javascript
module.exports = {
  presets: [
    [
      '@docusaurus/preset-classic',
      {
        docs: {
          routeBasePath: 'docs', // URL de base
          sidebarPath: require.resolve('./sidebars.js'), // Chemin de la configuration des barres latérales
          // Autres options comme le versioning, etc.
        },
      },
    ],
  ],
};
```

---

## **6. Configuration de la Barre Latérale**

La barre latérale est définie dans le fichier `sidebars.js`. Elle peut être configurée de manière statique ou générée automatiquement.

### Exemple de configuration manuelle :
```javascript
module.exports = {
  tutorialSidebar: [
    'intro', // Document direct
    {
      type: 'category',
      label: 'Ma Catégorie',
      items: ['category/doc1', 'category/doc2'], // Documents dans une catégorie
    },
  ],
};
```

### Génération automatique :
Si aucune configuration spécifique n’est ajoutée, Docusaurus génère automatiquement la barre latérale en suivant la structure des dossiers dans `/docs`.

---

## **7. Fonctionnalités Spéciales**

La section "Docs" intègre plusieurs fonctionnalités pour améliorer l’expérience utilisateur :

### 1. **Navigation Suivant/Précédent :**  
Docusaurus génère automatiquement des liens vers les pages suivantes et précédentes d’une catégorie.

### 2. **Table des Matières (ToC) :**  
Une table des matières est automatiquement générée à partir des titres (`#`, `##`, `###`) présents dans chaque document.

### 3. **Versioning de la Documentation :**  
Docusaurus permet de gérer plusieurs versions de documentation, idéal pour des projets avec des mises à jour régulières.

### 4. **Recherche Intégrée :**  
Avec le plugin de recherche, les utilisateurs peuvent trouver rapidement des informations dans la documentation.

---

## **8. Page d'Index**

### Par défaut :
Le premier document défini dans la barre latérale devient la **page d’accueil de la documentation**.

### Personnalisation :
Vous pouvez définir une autre page comme index via les paramètres :
```javascript
docs: {
  routeBasePath: 'docs',
  homePageId: 'intro', // Définit la page d’accueil
},
```

---

## **9. Avantages du Système de Routage**

- **Organisation claire :**  
  La structure hiérarchique permet une navigation logique et intuitive.

- **Configuration flexible :**  
  Avec les métadonnées et la gestion des barres latérales, vous pouvez personnaliser l’expérience utilisateur.

- **Fonctionnalités avancées :**  
  Navigation, recherche, et versioning augmentent la valeur de votre documentation.

- **Automatisation :**  
  Une grande partie de l’organisation est automatisée si vous respectez les conventions de fichiers.

---

## **Conclusion**

Le routage dans la section "Docs" de Docusaurus offre une expérience structurée, intuitive et hautement configurable. En combinant une bonne organisation des fichiers et une configuration adaptée, vous pouvez créer une documentation professionnelle, facile à maintenir et agréable pour les utilisateurs.
