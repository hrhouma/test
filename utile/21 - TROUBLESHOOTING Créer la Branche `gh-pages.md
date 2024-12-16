
# Créer la Branche `gh-pages` et Forcer le Push"

- L'utilisation ou non de la section "Créer la Branche `gh-pages` et Forcer le Push" dépend de la méthode choisie pour déployer notre site sur GitHub Pages. 
- Voici ce qui est **correct** selon la méthode utilisée :

---

## **1. Avec GitHub Actions et le workflow peaceiris/actions-gh-pages**
- Si vous utilisez **GitHub Actions** avec `peaceiris/actions-gh-pages`, **vous n'avez PAS besoin de créer manuellement la branche `gh-pages`**. 
- Le workflow s'occupe de tout automatiquement.

Dans ce cas :
- La branche `gh-pages` sera créée par le workflow lors de l'exécution, si elle n'existe pas déjà.
- Vous n'avez pas besoin de la section "Créer la Branche `gh-pages` et Forcer le Push".

**Ce qui est correct** :
- Supprimez complètement cette section et concentrez-vous sur la configuration du fichier `deploy.yml`.

---

## **2. Sans GitHub Actions (manuellement avec Git uniquement)**
Si vous ne voulez pas utiliser GitHub Actions et que vous souhaitez configurer GitHub Pages **manuellement**, alors **vous devez créer et gérer la branche `gh-pages` vous-même**.

Dans ce cas, la section "Créer la Branche `gh-pages` et Forcer le Push" est **nécessaire**. Voici les étapes exactes corrigées :

**Créer et déployer sur la branche `gh-pages` :**
1. **Créer une branche `gh-pages` orpheline (sans historique)** :
   ```bash
   git checkout --orphan gh-pages
   ```

2. **Supprimer tous les fichiers de cette nouvelle branche** :
   ```bash
   git rm -rf .
   ```

3. **Créer un fichier `index.html` de base** (si ce n'est pas déjà fait) :
   ```bash
   touch index.html
   echo "<h1>Bienvenue sur mon site GitHub Pages</h1>" > index.html
   ```

4. **Commiter le fichier** :
   ```bash
   git add index.html
   git commit -m "Initial gh-pages commit"
   ```

5. **Pousser la branche vers GitHub** :
   ```bash
   git push origin gh-pages
   ```

6. **Configurer GitHub Pages** :
   - Allez dans les **Settings** de votre dépôt.
   - Dans l'onglet **Pages**, sélectionnez la branche `gh-pages` comme source et cliquez sur **Save**.

---

## **Conclusion**
- **Avec GitHub Actions** : **Pas besoin** de créer ou gérer manuellement `gh-pages`. Configurez simplement le fichier `deploy.yml`.
- **Sans GitHub Actions** : **Nécessaire** de créer et forcer le push de la branche `gh-pages` manuellement.

# Annexe 01

   ```bash
     git checkout --orphan gh-pages
     git rm -rf .
     touch index.html
     git add index.html
     git commit -m "Initial gh-pages commit"
   ```
