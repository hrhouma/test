# Utiliser Cursor AI avec Prompt Engineering pour développer un projet existant

**Objectif :**  
Exploiter **Cursor AI** pour organiser, développer, et enrichir un projet éducatif basé sur **Docusaurus**, sans toucher manuellement aux fichiers.


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

---


---
# **Prompt 1 : Configuration de base du projet**  
---

**Objectif :**  
Créer une structure de base pour la plateforme éducative en utilisant **Docusaurus**. La page d’accueil doit présenter les catégories principales sous forme de blocs carrés ou tuiles dynamiques. Chaque bloc doit être cliquable et rediriger vers une page placeholder pour la catégorie.  

**Prompt :**  
> Configurez une plateforme avec Docusaurus :  
> - Installez un projet Docusaurus classique.  
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
# **Prompt 2 : réorganiser les catégories selon leur ordre d'apprentissage en DevOps** 
---

**Prompt :**  
"Réorganise les catégories suivantes selon un ordre logique d'apprentissage dans le domaine DevOps, en partant des concepts de base vers les concepts avancés : Introduction to DevOps, Linux, Ansible, Terraform, Kubernetes, Helm, GitOps, Jenkins. L'ordre doit refléter une progression naturelle pour un apprenant débutant dans le domaine DevOps."


  ```bash
   npm start
   ```

---
# **Prompt 3 : Ajout des modules et sous-catégories dans chaque catégorie**  
---

**Objectif :**  
Organiser chaque catégorie en modules, avec des sous-catégories et des leçons fictives pour tester la navigation.  

**Prompt :**  
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

