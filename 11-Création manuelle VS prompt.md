# **Objectif**
- Créer une documentation organisée pour **Linux**, divisée en modules et leçons, tout en garantissant qu'ils apparaissent correctement dans la barre latérale via le fichier `sidebars.ts`.

---

# **Étape 1 : Création des fichiers Markdown**

#### **1. Créez une structure pour les modules dans `docs`**
Organisez les fichiers Markdown par module dans des sous-dossiers pour une gestion simplifiée.

```bash
mkdir -p docs/linux/module1
mkdir -p docs/linux/module2
```

#### **2. Créez les fichiers Markdown pour les leçons**

**Exemple : `docs/linux/module1/lesson001.md`**

```markdown
---
id: lesson001
title: Comprendre Linux
sidebar_label: Comprendre Linux
---

# Comprendre Linux

Dans cette leçon, nous explorerons :

- L'histoire de Linux.
- Les distributions populaires.
- Les cas d'utilisation de Linux.

## L'histoire de Linux

Linux est un système d'exploitation open-source basé sur UNIX...

[Prochaine leçon : Architecture de Linux](../module1/lesson002.md)
```

**Exemple : `docs/linux/module1/lesson002.md`**

```markdown
---
id: lesson002
title: Architecture de Linux
sidebar_label: Architecture de Linux
---

# Architecture de Linux

La structure de Linux repose sur trois composants principaux :

1. Le **Kernel**.
2. Le **Shell**.
3. Le **Système de fichiers**.

[Prochaine leçon : Commandes de base](../module1/lesson003.md)

```

Répétez cette étape pour toutes les leçons de chaque module.

---

# **Étape 2 : Ajouter le Frontmatter aux fichiers Markdown**
Pour chaque fichier Markdown, incluez un **frontmatter** précis contenant les métadonnées nécessaires :

- **`id`** : Identifiant unique utilisé dans `sidebars.ts`.
- **`title`** : Titre affiché sur la page.
- **`sidebar_label`** : Nom affiché dans la barre latérale.

**Exemple : `lesson003.md`**
```markdown
---
id: lesson003
title: Commandes de base
sidebar_label: Commandes de base
---

# Commandes de base

Apprenez les commandes essentielles pour gérer les fichiers et naviguer dans le système Linux.
```

---

# **Étape 3 : Configurer le fichier `sidebars.ts`**

Le fichier `sidebars.ts` permet de définir la structure et l'ordre des modules et des leçons.

#### **1. Créez ou modifiez le fichier `sidebars.ts`**
**Exemple complet de `sidebars.ts` pour les deux premiers modules :**
```typescript
const sidebars = {
  tutorialSidebar: [
    {
      type: 'category',
      label: 'Linux',
      collapsible: true,
      collapsed: false,
      items: [
        {
          type: 'category',
          label: 'Module 1 : Introduction à Linux et ses Fondamentaux',
          items: [
            'linux/module1/lesson001', // Correspond à id dans lesson001.md
            'linux/module1/lesson002', // Correspond à id dans lesson002.md
            'linux/module1/lesson003',
            'linux/module1/lesson004',
          ],
        },
        {
          type: 'category',
          label: 'Module 2 : Gestion des Fichiers et du Système',
          items: [
            'linux/module2/lesson005',
            'linux/module2/lesson006',
            'linux/module2/lesson007',
            'linux/module2/lesson008',
          ],
        },
      ],
    },
  ],
};

export default sidebars;
```


# Correction:

```typescript
import type { SidebarsConfig } from '@docusaurus/plugin-content-docs';

const sidebars: SidebarsConfig = {
  tutorialSidebar: [
    {
      type: 'category',
      label: 'Linux',
      link: {
        type: 'generated-index',
        title: 'Documentation Linux',
        description: 'Découvrez Linux et ses fondamentaux pour le DevOps',
      },
      items: [
        'linux/introduction',
        {
          type: 'category',
          label: 'Module 1 : Introduction à Linux et ses Fondamentaux',
          items: [
            'linux/module1/lesson001',
            'linux/module1/lesson002',
            'linux/module1/lesson003',
          ],
        },
      ],
    },
  ],
};

export default sidebars;

```

---

### **Étape 4 : Lancer et tester le projet**

1. Nettoyez le cache du projet pour que les modifications soient prises en compte :
   ```bash
   npm run clear
   ```

2. Relancez le serveur de développement :
   ```bash
   npm start
   ```

3. Accédez à [http://localhost:3000/docs/category/linux](http://localhost:3000/docs/category/linux) pour vérifier :

   - Les modules apparaissent correctement dans la barre latérale.
   - Les leçons sont accessibles et bien ordonnées.

---

### **Étape 5 : Ajout d’un nouveau module (par exemple, Module 3) via le prompt**

Pour automatiser l'ajout du **Module 3**, utilisez un **prompt** avec un générateur de contenu Markdown.

#### **Exemple de prompt :**
```plaintext
Créez un nouveau module pour Docusaurus intitulé "Module 3 : Administration Système de Base". 

Dossier cible : docs/linux/module3.
Les leçons doivent inclure :
1. Gestion des utilisateurs : id=lesson009, sidebar_label=Gestion des utilisateurs.
2. Gestion des processus : id=lesson010, sidebar_label=Gestion des processus.
3. Gestion des paquets : id=lesson011, sidebar_label=Gestion des paquets.
4. Pratique 03 - Administration de base : id=lesson012, sidebar_label=Pratique 03.

Mettez à jour automatiquement `sidebars.ts` pour inclure ce nouveau module.
```

---

### **Étape 6 : Résultat attendu dans la barre latérale**

Après avoir ajouté les deux premiers modules manuellement et le troisième module via le prompt, votre barre latérale devrait ressembler à ceci :

```
Linux
├── Module 1 : Introduction à Linux et ses Fondamentaux
│   ├── Comprendre Linux
│   ├── Architecture de Linux
│   ├── Commandes de base
│   ├── Pratique 01
├── Module 2 : Gestion des Fichiers et du Système
│   ├── Arborescence Linux
│   ├── Permissions et ownership
│   ├── Gestion des archives
│   ├── Pratique 02
├── Module 3 : Administration Système de Base
│   ├── Gestion des utilisateurs
│   ├── Gestion des processus
│   ├── Gestion des paquets
│   ├── Pratique 03
```

---

### **Étape 7 : Comparaison entre méthode manuelle et automatisée**

| Aspect                   | Méthode Manuelle                                      | Via Prompt                                                 |
|--------------------------|------------------------------------------------------|-----------------------------------------------------------|
| **Temps**                | Long pour créer les fichiers et configurer la sidebar. | Rapide, avec les fichiers et la sidebar générés.          |
| **Précision**            | Contrôle total sur les contenus et leur ordre.       | Risque d’erreurs si le prompt est mal conçu.              |
| **Complexité**           | Plus d'étapes, mais meilleure compréhension.         | Automatisation, mais nécessite de valider les résultats.  |
| **Apprentissage**        | Favorise la maîtrise de Docusaurus.                  | Moins d’apprentissage, idéal pour des tâches répétitives. |

---

### **Conseils supplémentaires**

1. **Validation des fichiers Markdown :** Vérifiez que chaque fichier possède un frontmatter correct et que les liens entre les leçons fonctionnent.
2. **Customisation de la sidebar :** Pour des projets complexes, pensez à utiliser des catégories imbriquées pour organiser les contenus.
3. **Collaboration :** Versionnez les fichiers Markdown et `sidebars.ts` dans un dépôt Git pour faciliter les modifications en équipe.

---

Avec cette démarche exhaustive, vous pouvez structurer efficacement votre documentation tout en expérimentant avec des approches manuelles et automatisées. 😊
