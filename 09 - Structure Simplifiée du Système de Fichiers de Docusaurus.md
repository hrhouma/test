# Structure Simplifiée du Système de Fichiers de Docusaurus

Docusaurus organise les fichiers de manière claire pour séparer les **contenus**, la **configuration** et les **éléments statiques**. Voici une explication simple de chaque dossier et fichier important dans votre projet.

![image](https://github.com/user-attachments/assets/06e4f908-5544-4097-857d-bb2e0e880a2d)

### *Représentation de la structure du système de fichiers de Docusaurus* :

```
/skillr1
├── blog/                     # Articles de blog (optionnel)
│   ├── first-post.md         # Exemple d'article de blog
│   └── second-post.md        # Un autre article de blog
├── docs/                     # Contenus de la documentation
│   ├── intro.md              # Introduction par défaut (modifiable)
│   ├── linux/                # Dossier pour la catégorie "Linux"
│   │   ├── introduction.md   # Introduction à Linux
│   │   ├── tutorial-basics.md# Tutoriel basique sur Linux
│   │   └── tutorial-extras.md# Tutoriel avancé sur Linux
│   ├── kubernetes/           # Dossier pour la catégorie "Kubernetes"
│   │   ├── introduction.md   # Introduction à Kubernetes
│   │   └── advanced-topics.md# Sujets avancés sur Kubernetes
├── src/                      # Code source et personnalisation
│   ├── components/           # Composants React personnalisés
│   │   └── Navbar.js         # Exemple de composant pour la barre de navigation
│   ├── css/                  # Styles CSS personnalisés
│   │   └── custom.css        # Fichier CSS principal
│   ├── pages/                # Pages personnalisées (hors docs)
│       ├── about.js          # Page "À propos"
│       └── contact.js        # Page "Contact"
├── static/                   # Fichiers statiques (images, vidéos, PDF)
│   ├── img/                  # Dossier pour les images
│   │   └── logo.png          # Logo du site
│   └── pdf/                  # Dossier pour les fichiers PDF
│       └── guide.pdf         # Un guide téléchargeable
├── .gitignore                # Exclure certains fichiers du dépôt Git
├── docusaurus.config.js      # Fichier principal de configuration
├── sidebars.js               # Configuration de la barre latérale
├── package.json              # Dépendances et scripts du projet
├── README.md                 # Documentation pour votre projet
└── node_modules/             # Dépendances Node.js (générées automatiquement)
```

### Explication des éléments :
- **`blog/` :** Contient les articles de blog. Chaque fichier `.md` est un article.
- **`docs/` :** Contient la documentation principale (les leçons et modules). Les sous-dossiers représentent des catégories.
- **`src/` :** Gère les composants, styles et pages personnalisées de votre site.
- **`static/` :** Fichiers accessibles directement via le site (images, PDF, etc.).
- **`docusaurus.config.js` :** Configuration générale du site (titre, URL, etc.).
- **`sidebars.js` :** Structure et navigation dans la barre latérale.
- **`package.json` :** Dépendances nécessaires au projet (gérées par `npm` ou `yarn`).



---

#### **1. `docs/`**
Ce dossier contient tout le **contenu de la documentation** que vous voulez afficher sur votre site.

- **Exemple :**
  - `linux/` → Une catégorie (par exemple, pour les cours Linux).
    - `introduction.md` → Le fichier d'introduction pour Linux.
  - `intro.md` → Une documentation par défaut créée par Docusaurus (modifiable ou supprimable).

---

#### **2. `blog/`**
Ce dossier est utilisé pour les **articles de blog**. Chaque fichier `.md` représente un article.

- Si vous ne voulez pas de blog, vous pouvez ignorer ce dossier ou le supprimer.

---

#### **3. `src/`**
Ce dossier contient tout le **code source** de votre site (HTML, CSS, React).

- **Sous-dossiers importants :**
  - `components/` → Pour vos **composants React personnalisés**.
  - `pages/` → Pour créer des **pages personnalisées** (hors documentation, comme une page "À propos").
  - `css/` → Pour les **fichiers de style** de votre site (CSS).

---

#### **4. `static/`**
Ce dossier contient vos **fichiers statiques**, comme les images, vidéos ou PDF. Tout ce qui est placé ici est directement accessible depuis l'URL de votre site.

- **Exemple :**
  - Si vous ajoutez une image `logo.png` dans `static/`, elle sera accessible via `/logo.png` sur votre site.

---

#### **5. Fichiers de Configuration**

- **`docusaurus.config.js` :**  
  Le **fichier principal de configuration**. Il contient :
  - Le titre de votre site.
  - Les paramètres de navigation.
  - Les chemins vers vos dossiers (`docs/`, `blog/`, etc.).

- **`sidebars.js` :**  
  Gère la structure de la barre latérale. Vous listez ici les catégories et les fichiers que vous voulez afficher.

---

#### **6. Fichiers Utilitaires**

- **`package.json` :**  
  Liste les **dépendances** et scripts nécessaires pour faire fonctionner votre projet (par exemple, `npm start` pour lancer le site).

- **`.gitignore` :**  
  Spécifie les fichiers et dossiers à **exclure** du dépôt Git (par exemple, `node_modules/`).

---

### En Résumé
- **`docs/` :** Documentation principale.  
- **`blog/` :** Articles de blog.  
- **`src/` :** Code source et pages personnalisées.  
- **`static/` :** Fichiers statiques (images, etc.).  
- **Configuration :** `docusaurus.config.js` et `sidebars.js`.

Avec cette organisation, tout est bien séparé pour que vous puissiez gérer facilement chaque partie de votre site.
