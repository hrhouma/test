# Utiliser Git pour la restauration et la gestion de versions pour projets dynamiques

## Objectif:  

- *Ce tutoriel  combine théorie et pratique pour vous permettre d'utiliser **Git** efficacement, en particulier dans des contextes où vous travaillez avec des prompts ou effectuez des modifications complexes.*
- *Apprendre à gérer vos fichiers, sauvegarder des versions stables et restaurer un état antérieur en toute sécurité avec Git, tout en travaillant avec des prompts qui modifient le design ou la logique métier de votre projet.*

---

## **Étape 1 : Initialisation et premier commit**

### 1. Créez un dépôt Git
- Accédez au dossier contenant vos fichiers :
   ```bash
   cd Skillr1
   ```
- Initialisez un dépôt Git :
   ```bash
   git init
   ```
   **Explication :** Cette commande crée un espace Git où tous vos changements seront suivis et enregistrés.

### 2. Vérifiez l'état de vos fichiers
   ```bash
   git status
   ```
   **Explication :** Vous pouvez voir quels fichiers ont été modifiés ou ajoutés, mais ne sont pas encore suivis par Git.

### 3. Ajoutez les fichiers au suivi
   ```bash
   git add .
   ```
   **Astuce :** Si vous ne voulez ajouter qu’un fichier spécifique, utilisez :
   ```bash
   git add fichier_specifique
   ```

### 4. Créez votre premier commit
   ```bash
   git commit -m "Initialisation du projet avec tous les fichiers de base"
   ```
   **Bonne pratique :** Donnez un message descriptif pour documenter clairement les changements.

### 5. Consultez l’historique des commits
   - **Version détaillée :**
     ```bash
     git log
     ```
   - **Version simplifiée :**
     ```bash
     git log --oneline
     ```

**Vous avez maintenant une version stable de votre projet enregistrée.**

---

## **Étape 2 : Effectuer des modifications et tester**

### 1. Travaillez sur votre projet ou exécutez un prompt
- Exemple de prompt :
   ```bash
   Prompt : Change la couleur du background de l'ensemble du site à rouge.
   ```
   Appliquez ce changement dans vos fichiers, ou utilisez un outil comme Cursor AI.

### 2. Testez vos modifications
- Chargez votre projet dans un navigateur pour vérifier si le résultat correspond à vos attentes.

---

## **Étape 3 : Restauration en cas de besoin**

### Cas 1 : Annuler des changements récents (non commités)
- Revenir à l’état initial du dernier commit :
   ```bash
   git reset --hard HEAD
   ```
   **Explication :** Cela supprime tous les changements non enregistrés et revient à la dernière version stable.

---

### Cas 2 : Revenir à une version spécifique
1. Listez les commits pour identifier leur ID (SHA) :
   ```bash
   git log --oneline
   ```
   Exemple de sortie :
   ```
   5d41402 Ajout d’une fonctionnalité d’authentification
   7e3e21b Correction du bug dans le formulaire de contact
   9c6fcd3 Initialisation du projet
   ```

2. Revenez à un commit précis :
   ```bash
   git reset --hard [ID]
   ```
   Exemple :
   ```bash
   git reset --hard 7e3e21b
   ```
   **Attention :** Tout commit plus récent sera supprimé.

---

## **Étape 4 : Sauvegarder avant des modifications risquées**

### Pourquoi sauvegarder avant d’exécuter des prompts "dangereux" ?
Si vous travaillez sur des modifications importantes ou complexes (ex. : *"Changer la logique métier"*), une sauvegarde préalable est essentielle pour éviter de perdre une version stable.

1. Vérifiez l'état de vos fichiers :
   ```bash
   git status
   ```

2. Sauvegardez vos modifications actuelles :
   ```bash
   git add .
   git commit -m "Sauvegarde : Version stable avant le changement de logique"
   ```

3. **Exécutez le prompt :**
   ```bash
   Prompt : Change le site pour en faire une boutique de vêtements de sport.
   ```

---

## **Étape 5 : Restaurer après un échec**

Si le résultat du prompt n’est pas satisfaisant, procédez ainsi :

1. Listez l’historique des commits pour identifier une version stable :
   ```bash
   git log --oneline
   ```

2. Revenez à cette version stable :
   ```bash
   git reset --hard [ID]
   ```

---

## **Bonus : Revenir plusieurs commits en arrière**

Si vous souhaitez revenir en arrière par rapport au dernier commit, vous pouvez utiliser des raccourcis :
```bash
git reset --hard HEAD~1  # Revenir au dernier commit
git reset --hard HEAD~3  # Revenir trois commits en arrière
```

---

## **Prompt universel pour améliorer votre site**

**Exemple :**
```bash
Prompt : Améliore le design pour qu'il soit moderne, intuitif et visuellement captivant, tout en optimisant l'expérience utilisateur.
```

- Avant d’exécuter ce prompt :
   ```bash
   git add .
   git commit -m "Sauvegarde avant optimisation du design"
   ```

- En cas d’insatisfaction :
   ```bash
   git reset --hard HEAD
   ```

---

## **Résumé des commandes importantes**

| **Commande**               | **Action**                                                                           |
|-----------------------------|---------------------------------------------------------------------------------------|
| `git init`                 | Initialise un dépôt Git                                                              |
| `git status`               | Affiche les fichiers modifiés et leur état                                           |
| `git add .`                | Ajoute tous les fichiers pour le prochain commit                                     |
| `git commit -m "message"`  | Crée un snapshot avec un message significatif                                        |
| `git log`                  | Montre l’historique complet des commits                                              |
| `git log --oneline`        | Affiche un aperçu rapide de l’historique                                             |
| `git reset --hard HEAD`    | Annule tous les changements non commités                                             |
| `git reset --hard [ID]`    | Revient à un commit précis                                                          |

---

## **Conclusion**

Git est votre meilleur allié pour expérimenter sans peur de perdre vos fichiers. En combinant des sauvegardes fréquentes avec une bonne gestion des versions, vous pouvez explorer librement, tester des prompts audacieux et restaurer votre projet à tout moment. **Adoptez ces bonnes pratiques pour un workflow fluide et sécurisé !**






















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
