# Structure Simplifiée du Système de Fichiers de Docusaurus

Docusaurus organise les fichiers de manière claire pour séparer les **contenus**, la **configuration** et les **éléments statiques**. Voici une explication simple de chaque dossier et fichier important dans votre projet.

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
