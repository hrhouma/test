
# Prompt 1

> Refacorisez le projet Docusaurus existant pour effectuer les tâches suivantes:  
> - Créez une page d’accueil avec des blocs représentant les catégories principales suivantes :  
>   - **Linux**
>   - **Docker**
>   - **Ansible**  
>   - **Kubernetes**  
>   - **Jenkins**  
>   - **Terraform**  
>   - **GitOps**  
>   - **Helm**  
>   - **Introduction à DevOps**  
> - Chaque bloc doit inclure un titre et une icône (utilisez des icônes placeholders pour l’instant).  
> - Configurez les blocs pour qu’ils redirigent vers une page placeholder dédiée à chaque catégorie.
> - Rendez le blog attrayant digne de visites de 1 millions d'utilisateurs

**Livrable attendu :**  
Une page d’accueil fonctionnelle avec des blocs interactifs pour chaque catégorie.  

# Réponse:

### Cursor a répondu par 5 modifications :

- index.js ==> dans src/components/CategoryBlock/index.js (*Modification 1*)
- styles.modules.css ==> dans src/components/CategoryBlock/styles.modules.css (*Modification 2*)
- index.js ==> page d'accueil dans src/pages/index.js (*Modification 3*)
- index.module.css ==> dans src/pages/index.js (*Modification 4*)
- installer npm install react-icons (*Modification 5*)
- docusaurus.config.js dans la racine (*Modification 5*)
- introduction.md dans docs/linux/introduction.md (*Modification 5*)


# Modification 1 

- Je vais vous aider à restructurer votre projet Docusaurus. Je vais créer plusieurs fichiers pour organiser la page d'accueil avec les catégories demandées.

![image](https://github.com/user-attachments/assets/c4cf4734-282c-4ef2-ac69-8a5cf7331a28)


```python
import React from 'react';
import Link from '@docusaurus/Link';
import styles from './styles.module.css';

export default function CategoryBlock({title, icon, link}) {
  return (
    <Link to={link} className={styles.categoryBlock}>
      <div className={styles.blockContent}>
        <div className={styles.icon}>{icon}</div>
        <h3 className={styles.title}>{title}</h3>
      </div>
    </Link>
  );
} 
```


# Modification 2 : 

- Ajoutons les styles pour les blocs :

![image](https://github.com/user-attachments/assets/ece6f180-ea7a-40de-aaf4-67c60d22b60f)

```python
.categoryBlock {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  border-radius: 8px;
  background: var(--ifm-card-background-color);
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  text-decoration: none;
  color: var(--ifm-font-color-base);
}

.categoryBlock:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
  text-decoration: none;
}

.blockContent {
  text-align: center;
}

.icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.title {
  margin: 0;
  font-size: 1.2rem;
} 

```


# Modification 3 : 

- Modifions la page d'accueil :

![image](https://github.com/user-attachments/assets/4352a338-b982-4751-864c-9b1a300fdb90)


```python

import React from 'react';
import Layout from '@theme/Layout';
import CategoryBlock from '@site/src/components/CategoryBlock';
import { FaLinux, FaDocker, FaServer, FaCloud, FaJenkins, FaCogs, FaGitAlt, FaChartBar, FaRocket } from 'react-icons/fa';
import styles from './index.module.css';

const categories = [
  {
    title: 'Linux',
    icon: <FaLinux />,
    link: '/docs/category/linux',
  },
  {
    title: 'Docker',
    icon: <FaDocker />,
    link: '/docs/category/docker',
  },
  {
    title: 'Ansible',
    icon: <FaServer />,
    link: '/docs/category/ansible',
  },
  {
    title: 'Kubernetes',
    icon: <FaCloud />,
    link: '/docs/category/kubernetes',
  },
  {
    title: 'Jenkins',
    icon: <FaJenkins />,
    link: '/docs/category/jenkins',
  },
  {
    title: 'Terraform',
    icon: <FaCogs />,
    link: '/docs/category/terraform',
  },
  {
    title: 'GitOps',
    icon: <FaGitAlt />,
    link: '/docs/category/gitops',
  },
  {
    title: 'Helm',
    icon: <FaChartBar />,
    link: '/docs/category/helm',
  },
  {
    title: 'Introduction à DevOps',
    icon: <FaRocket />,
    link: '/docs/category/intro-devops',
  },
];

export default function Home() {
  return (
    <Layout
      title="Accueil"
      description="Ressources et tutoriels DevOps">
      <main className={styles.main}>
        <div className={styles.hero}>
          <h1 className={styles.title}>Bienvenue sur DevOps Learning Hub</h1>
          <p className={styles.subtitle}>
            Découvrez nos ressources complètes pour maîtriser les outils et pratiques DevOps
          </p>
        </div>
        <div className={styles.categories}>
          {categories.map((category, idx) => (
            <CategoryBlock
              key={idx}
              title={category.title}
              icon={category.icon}
              link={category.link}
            />
          ))}
        </div>
      </main>
    </Layout>
  );
} 

```

# Modification 4 :

- Ajoutons les styles pour la page d'accueil :
- 
![image](https://github.com/user-attachments/assets/a4c321d0-ed48-459d-9c72-ba85a8888831)

- Ajout de ceci :

```python
.main {
  padding: 2rem;
}

.hero {
  text-align: center;
  padding: 4rem 0;
  background: linear-gradient(to right, var(--ifm-color-primary-lightest), var(--ifm-color-primary));
  margin: -2rem -2rem 2rem -2rem;
  color: white;
}

.title {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.subtitle {
  font-size: 1.5rem;
  opacity: 0.9;
}

.categories {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 1rem;
  }
  
  .title {
    font-size: 2rem;
  }
  
  .subtitle {
    font-size: 1.2rem;
  }
}
```


dans ceci :

```python

/**
 * CSS files with the .module.css suffix will be treated as CSS modules
 * and scoped locally.
 */

.heroBanner {
  padding: 4rem 0;
  text-align: center;
  position: relative;
  overflow: hidden;
}

@media screen and (max-width: 996px) {
  .heroBanner {
    padding: 2rem;
  }
}

.buttons {
  display: flex;
  align-items: center;
  justify-content: center;
}

.main {
  padding: 2rem;
}

.hero {
  text-align: center;
  padding: 4rem 0;
  background: linear-gradient(to right, var(--ifm-color-primary-lightest), var(--ifm-color-primary));
  margin: -2rem -2rem 2rem -2rem;
  color: white;
}

.title {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.subtitle {
  font-size: 1.5rem;
  opacity: 0.9;
}

.categories {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 1rem;
  }
  
  .title {
    font-size: 2rem;
  }
  
  .subtitle {
    font-size: 1.2rem;
  }
}

```


# Modification 5

### 5.1

```ssh
npm install react-icons
```
### 5.2
- Pour rendre le blog plus attrayant, voici quelques recommandations supplémentaires :
- Ajoutez des métadonnées appropriées dans docusaurus.config.js 

![image](https://github.com/user-attachments/assets/c56f6d31-f0df-463b-b2db-b2a05d62a9d9)

![image](https://github.com/user-attachments/assets/110d2bc5-ab33-4caf-935f-916496f9ef9f)

### 5.3
```ssh
themeConfig: {
  metadata: [{name: 'keywords', content: 'devops, linux, docker, kubernetes, ansible, jenkins, terraform, gitops, helm'}],
  // ... autres configurations du thème
}
```

### 5.4

![image](https://github.com/user-attachments/assets/f4d0c375-a577-400f-8280-7ffb65678d76)

- Créez des pages placeholder pour chaque catégorie dans le dossier docs/. Par exemple :
  
![image](https://github.com/user-attachments/assets/f734a6ee-0436-416e-9175-46cb108e375b)



# Récap

![image](https://github.com/user-attachments/assets/0f4e4567-f525-47a6-a1b0-67efe0965d1b)




# Passer à l'action :

![image](https://github.com/user-attachments/assets/08122e57-5653-4db5-9269-ddafd9333be4)

# Résultat:

![image](https://github.com/user-attachments/assets/2b1ca008-2352-4800-b362-68781d39f260)



