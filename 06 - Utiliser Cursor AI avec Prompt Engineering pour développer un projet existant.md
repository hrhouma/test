# Utiliser Cursor AI avec Prompt Engineering pour développer un projet existant ( les trois premiers prompts)

**Objectif :**  
- Exploiter **Cursor AI** pour organiser, développer, et enrichir un projet éducatif basé sur **Docusaurus**, sans toucher manuellement aux fichiers.
- Utilisation des trois premiers prompts pour poser les bases, structurer l'organisation, et enrichir les fonctionnalités du projet.


# Introduction 
---

🚀 **Bienvenue à cette session**  
- Dans cette session, je vais vous guider à travers un exemple de prompt, **structuré en étapes numérotées (Prompt 1, Prompt 2, etc.)**, avec une attention minutieuse à chaque détail.  

🎯 **Notre objectif**  
- Concevoir une plateforme à la fois fonctionnelle et engageante, qui capte l'attention dès les premiers instants.  


---

# **1. Accéder au projet existant**

1. **Naviguer vers le projet :**
   - Accédez à votre projet existant via le terminal :
     ```bash
     cd Skillr1
     ```

2. **Lancer Cursor AI :**
   - Exécutez la commande suivante pour ouvrir le projet dans Cursor AI :
     ```bash
     cursor
     ```

3. **Vérifiez que Cursor AI est correctement initialisé :**
   - Une fois ouvert, vous devriez voir la structure de votre projet (fichiers, répertoires, etc.) dans l'interface Cursor.


4. **⚠️ Ouvrir le terminal de Composer**

- 🖥️ **Naviguer dans le menu :**  
  `View` ➡️ `Open View` ➡️ `Composer`  

### 4.1. Choisir  `View` ➡️ `Open View` :

![image](https://github.com/user-attachments/assets/932e7fb6-61ad-405d-97bc-1613944f5331)

### 4.2. Choisir Composer :

![image](https://github.com/user-attachments/assets/1a53f83b-e6f3-4fdc-b15c-50173ab25316)

### 4.3. Cliquez sur l'onglet Composer :

![image](https://github.com/user-attachments/assets/fc39bdd3-a7e7-4fa2-b079-216d930e62fa)



---
# **Prompt 1 : 🚧 Configuration de base du projet**  
---

🔑 **Étape clé** : Posez les fondations solides pour votre projet.  
⚙️ **Ce que vous allez faire** : Configurer les éléments essentiels pour démarrer rapidement et efficacement.  
📋 **Objectif** : Assurer une structure structure de base pour la plateforme éducative en utilisant **Docusaurus**. La structure doit être claire et prête à évoluer 🚀. La page d’accueil doit présenter les catégories principales sous forme de blocs carrés ou tuiles dynamiques. Chaque bloc doit être cliquable et rediriger vers une page placeholder pour la catégorie.  



⚠️ **Prompt à copier et coller dans Composer :**  
> Refacorisez le projet Docusaurus existant pour effectuer les tâches suivantes:  
> - Créez une page d’accueil avec des blocs représentant les catégories principales suivantes :  
>   - **Linux**  
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

**Instructions de test :**  
1. **Installation de Docusaurus :**  
   - Exécutez les commandes suivantes :

   ```bash
   cd test1
   npm install
   npm start
   ```

   - Lancez le projet avec `npm start` et ouvrez `http://localhost:3000`.  


1. **Vérification des blocs :**  
   - Vérifiez que les blocs des catégories apparaissent correctement sur la page d’accueil.  
   - Assurez-vous que chaque bloc redirige bien vers une page placeholder.  

2. **Design initial :**  
   - Vérifiez que les blocs sont alignés et clairement lisibles.  



---
# **Prompt 2 : 📚 Réorganiser les catégories selon leur ordre d'apprentissage en DevOps**  
---

🔍 **Ce que vous allez faire** : Structurer un chemin d'apprentissage clair et progressif dans le domaine du DevOps.  
📈 **But** : Guider un débutant à travers les concepts, des bases solides jusqu'aux outils avancés.  

⚠️ **Prompt à copier et coller dans Composer :**  
"Réorganise les catégories suivantes selon un ordre logique d'apprentissage dans le domaine DevOps, en partant des concepts de base vers les concepts avancés : Introduction to DevOps, Linux, Ansible, Terraform, Kubernetes, Helm, GitOps, Jenkins. L'ordre doit refléter une progression naturelle pour un apprenant débutant dans le domaine DevOps."


  ```bash
   npm start
   ```

---
# **Prompt 3 : 🗂️ Ajout des modules et sous-catégories dans chaque catégorie**  
---

🎯 **Objectif** : Structurer chaque catégorie en modules clairs, avec des sous-catégories et des leçons fictives pour tester l'expérience utilisateur et la navigation.  

💡 **Ce que vous allez faire** :  
- Décomposer chaque catégorie en modules bien définis.  
- Ajouter des sous-catégories pertinentes pour une organisation optimale.  
- Créer des leçons fictives pour simuler une navigation fluide et engageante.  


⚠️ **Prompt à copier et coller dans Composer :**  

> Ajoutez des modules pour chaque catégorie.
> Configurez chaque module avec des sous-catégories et leçons comme suit :  
> - **Modules de Linux** : Introduction, Administration Système, Sécurité, Réseau, etc.  
> - Pour chaque module, ajoutez des leçons fictives en fichiers Markdown (ex. `Leçon001.md`).  
> - Configurez une navigation où :  
>   - Cliquer sur une catégorie affiche ses modules.  
>   - Cliquer sur un module affiche les leçons correspondantes.  

**Livrable attendu :**  
Une structure navigable où chaque catégorie contient des modules, et chaque module affiche ses leçons.  

**Instructions de test :**  
1. **Vérification des modules :**  
   - Cliquez sur une catégorie et confirmez que les modules s’affichent.  

2. **Navigation des leçons :**  
   - Cliquez sur un module et assurez-vous que les leçons s’affichent correctement.  

3. **Markdown :**  
   - Vérifiez que les fichiers Markdown des leçons sont bien rendus.  

