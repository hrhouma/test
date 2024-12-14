# Installation de Node.js LTS sur Windows

---

Bonjour à tous ! Aujourd'hui, nous allons apprendre **comment installer Node.js sur Windows** en utilisant la version LTS (Long-Term Support). Node.js est un environnement JavaScript très puissant, et il est essentiel pour exécuter des applications modernes. Nous allons également tester son installation à la fin.

---

### Étape 1 : Télécharger Node.js (Version LTS)

1. **Ouvrez votre navigateur web**.
2. Rendez-vous sur le site officiel de Node.js :  
   👉 [https://nodejs.org](https://nodejs.org)
3. Sur la page d'accueil, vous verrez deux options de téléchargement :  
   - **LTS (Recommandé pour la majorité des utilisateurs)**  
   - **Current (Pour les développeurs avancés)**  
   **Cliquez sur le bouton vert `LTS`** pour télécharger la version stable.
4. Une fois le fichier téléchargé (généralement nommé `node-vXX.X.X-x64.msi`), passez à l'étape suivante.

---

### Étape 2 : Installer Node.js via l’exécutable `.msi`

1. **Double-cliquez sur le fichier téléchargé** (`node-vXX.X.X-x64.msi`) pour lancer l'installation.
2. **Suivez ces étapes dans l’assistant d’installation** :
   - **Cliquez sur "Next"** (Suivant).
   - **Acceptez les termes du contrat de licence** en cochant la case, puis cliquez sur "Next".
   - Laissez le **chemin d’installation par défaut** (par exemple, `C:\Program Files\nodejs`), puis cliquez sur "Next".
   - À l'étape "Custom Setup", **laissez toutes les options cochées**, surtout "npm package manager". Cela installera également **npm**, un gestionnaire de paquets indispensable.
   - Cliquez sur "Next", puis sur **"Install"** pour démarrer l'installation.
3. Une fois terminé, cliquez sur **"Finish"**.

---

### Étape 3 : Tester l'installation de Node.js

Après l'installation, vous devez vérifier que Node.js fonctionne correctement. Voici comment procéder :

1. **Ouvrez l’invite de commandes Windows** :  
   - Appuyez sur **`Win + R`**, tapez `cmd`, puis appuyez sur Entrée.  
   OU  
   - Cherchez "Invite de commandes" dans le menu Démarrer.
   
2. **Testez Node.js** :
   - Dans l'invite de commandes, tapez :  
     ```bash
     node -v
     ```
     Cela affichera la version de Node.js installée, par exemple :  
     `v18.17.1` (ou la version LTS que vous avez installée).

3. **Testez npm** :  
   - Tapez :  
     ```bash
     npm -v
     ```
     Cela affichera la version de npm (le gestionnaire de paquets). Exemple :  
     `9.6.7`.

4. **Testez npx** :  
   - Tapez :  
     ```bash
     npx -v
     ```
     Cela affichera la version de npx. Exemple :  
     `9.6.7`.

5. **Exécutez un simple test Node.js** :  
   - Toujours dans l’invite de commandes, tapez :  
     ```bash
     node
     ```
     Cela ouvrira un environnement interactif Node.js.
   - Essayez de taper cette ligne :  
     ```javascript
     console.log("Hello, Node.js!");
     ```
     Ensuite, appuyez sur Entrée.  
     Si tout fonctionne, vous verrez apparaître :  
     `Hello, Node.js!`
   - Pour quitter l’environnement Node.js, tapez :  
     ```bash
     .exit
     ```

---

### Étape 4 : Résolution des problèmes courants

- **Erreur "commande introuvable"** :  
   Si les commandes `node`, `npm`, ou `npx` ne fonctionnent pas, cela peut être dû à un problème de **variable d'environnement**. Redémarrez votre ordinateur et réessayez. Si cela persiste :
   - Ouvrez l'Explorateur Windows.
   - Cliquez avec le bouton droit sur "Ce PC" > "Propriétés" > "Paramètres système avancés".
   - Cliquez sur **"Variables d’environnement"**.
   - Dans "Variables système", sélectionnez `Path` et cliquez sur "Modifier".
   - Vérifiez que le chemin `C:\Program Files\nodejs\` est bien présent. Sinon, ajoutez-le manuellement.

