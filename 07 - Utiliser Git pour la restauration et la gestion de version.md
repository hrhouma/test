## Utiliser Git pour la restauration et la gestion de version

### Objectif :
Vous apprendre à gérer efficacement votre code avec **Git**, tout en explorant des scénarios réalistes et en adoptant des bonnes pratiques pour travailler avec des prompts ou des modifications risquées.

---

# **Étape 1 : Initialisation et premier commit**

1. **Initialiser un dépôt Git**  
   Tapez la commande suivante dans votre terminal à la racine de votre projet :
   ```bash
   git init
   ```
   Cela crée un dépôt Git local où vous pourrez suivre les changements de vos fichiers.

2. **Vérifiez l'état du dépôt :**
   ```bash
   git status
   ```
   Cette commande liste les fichiers ajoutés ou modifiés mais non suivis par Git.

3. **Ajoutez tous les fichiers au suivi :**
   ```bash
   git add .
   ```
   `.` signifie "ajouter tous les fichiers". C'est rapide, mais attention à ne pas ajouter accidentellement des fichiers non souhaités.

4. **Confirmez que les fichiers ont bien été ajoutés :**
   ```bash
   git status
   ```
   Vous verrez les fichiers prêts pour un commit.

5. **Créez votre premier commit :**
   ```bash
   git commit -m "Initialisation du projet avec tous les fichiers de base"
   ```
   ⚠️ **Astuce** : **Évitez les messages vagues comme "version1".** Donnez des descriptions significatives (par exemple : *"Ajout du système de base avec HTML et CSS"*).

6. **Consultez l’historique des commits :**
   ```bash
   git log
   ```
   Cela montre les détails complets des commits précédents.

7. **Utilisez une vue simplifiée de l’historique :**
   ```bash
   git log --oneline
   ```
   Utile pour un aperçu rapide des IDs de commit et des messages.

---

# **Étape 2 : Modifier le projet et vérifier le résultat**

1. **Exécutez votre prompt ou effectuez des modifications :**  
   Par exemple :
   ```bash
   Prompt : Change la couleur du background de l'ensemble du site à rouge.
   ```
   Appliquez le changement dans votre code source (par exemple, mettez `background-color: red;` dans votre fichier CSS).

2. **Tester votre site :**  
   Ouvrez votre site dans le navigateur pour vérifier le résultat.

---

# **Étape 3 : Restaurer un état précédent si nécessaire**

## **Cas 1 : Vous voulez annuler les changements récents avant un commit.**

- **Restaurer les fichiers à leur état précédent (non suivi par Git) :**
   ```bash
   git reset --hard HEAD
   ```
   **HEAD** fait référence au dernier commit. Tout changement non enregistré sera perdu.

## **Cas 2 : Vous voulez revenir à un état précis après plusieurs commits.**

1. **Listez l’historique des commits pour obtenir leurs IDs :**
   ```bash
   git log --oneline
   ```
   Par exemple, cela affichera :
   ```
   5d41402 Ajouter la fonctionnalité X
   7e3e21b Corriger le bug Y
   9c6fcd3 Initialisation du projet
   ```

2. **Revenir à un commit spécifique :**
   ```bash
   git reset --hard ID
   ```
   Par exemple :
   ```bash
   git reset --hard 5d41402
   ```

---

# **Étape 4 : Bonne pratique avant des modifications risquées**

Si vous vous apprêtez à exécuter un **prompt risqué** (comme *"Changer la logique métier"*), procédez avec prudence.

1. **Vérifiez l’état du dépôt :**
   ```bash
   git status
   ```

2. **Sauvegardez votre état actuel :**
   ```bash
   git add .
   git commit -m "Sauvegarde : Version stable avant le changement de la logique métier"
   ```
   Encore une fois, un message clair comme *"Version stable avant les modifications importantes"* est crucial.

3. **Exécutez le prompt dans votre outil (par exemple, Cursor.ai).**

---

# **Étape 5 : Annuler un prompt insatisfaisant**

1. **Vérifiez l’historique des commits :**
   ```bash
   git log --oneline
   ```

2. **Revenez au dernier état stable :**
   ```bash
   git reset --hard ID
   ```
   Utilisez l’ID du commit précédant les changements non satisfaisants.

---

# **Résumé des commandes utiles**

| **Commande**               | **Action**                                                                           |
|-----------------------------|---------------------------------------------------------------------------------------|
| `git init`                 | Initialise un dépôt Git                                                              |
| `git status`               | Affiche les fichiers modifiés et leur état                                           |
| `git add .`                | Ajoute tous les fichiers pour le prochain commit                                     |
| `git commit -m "message"`  | Crée un snapshot avec un message significatif                                        |
| `git log`                  | Montre l’historique complet des commits                                              |
| `git log --oneline`        | Affiche un aperçu rapide de l’historique                                             |
| `git reset --hard HEAD`    | Annule tous les changements non commités                                             |
| `git reset --hard ID`      | Revient à un commit précis                                                          |

---

# **Conclusion**

Avec Git, vous pouvez expérimenter en toute sécurité et revenir en arrière si nécessaire. Suivez ces étapes pour gérer vos changements de manière méthodique et efficace, surtout lorsque vous travaillez avec des prompts ou des modifications importantes.























Cela rétablit le dépôt à son dernier commit enregistré, supprimant les changements non commités.

*Revenir au dernier commit, deux commits en arrière , ...cinq commits en arrière*

```bash
# Revenir au dernier commit et annuler toutes les modifications non sauvegardées
git reset --hard HEAD

# Revenir deux commits en arrière et réinitialiser l'état du dépôt
git reset --hard HEAD~2

# Revenir trois commits en arrière et réinitialiser l'état du dépôt
git reset --hard HEAD~3

# Revenir quatre commits en arrière et réinitialiser l'état du dépôt
git reset --hard HEAD~4

# Revenir cinq commits en arrière et réinitialiser l'état du dépôt
git reset --hard HEAD~5
```

**Attention :** Ces commandes suppriment définitivement tous les commits plus récents et les modifications non commités. Soyez prudent lorsque vous utilisez ces commandes.





---
# Prompt 6 : prompt universel
---

"Améliore le design pour qu'il soit digne d'attirer et d'engager des millions d'utilisateurs. Assure-toi qu'il soit moderne, intuitif, visuellement captivant, et qu'il offre une expérience utilisateur exceptionnelle."
