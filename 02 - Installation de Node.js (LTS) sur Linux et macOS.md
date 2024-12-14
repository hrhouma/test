# Installation de Node.js (LTS) sur Linux et macOS

Après avoir vu comment installer Node.js sur Windows, découvrons maintenant comment l’installer sur **Linux** et **macOS**, en utilisant la méthode recommandée avec **nvm (Node Version Manager)**. Cette méthode est simple, flexible, et permet de gérer plusieurs versions de Node.js.

---

## **1. Installation sur Linux (Ubuntu/Debian)**

#### Étape 1 : Mettre à jour votre système

Avant de commencer, mettez à jour vos paquets pour éviter les erreurs :  
```bash
sudo apt update -y
```

#### Étape 2 : Installer `curl` (si ce n'est pas déjà fait)

`curl` est utilisé pour télécharger le script d'installation de `nvm` :  
```bash
sudo apt install curl -y
```

#### Étape 3 : Installer `nvm` (Node Version Manager)

1. Téléchargez et installez `nvm` avec cette commande :  
   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
   ```
2. Chargez `nvm` dans votre terminal :  
   ```bash
   source ~/.bashrc
   ```
   (Si vous utilisez `zsh`, remplacez `.bashrc` par `.zshrc`.)

3. Vérifiez que `nvm` est bien installé :  
   ```bash
   nvm --version
   ```
   Si vous voyez une version (par exemple `0.39.5`), l’installation a réussi.

#### Étape 4 : Installer Node.js via `nvm`

1. Listez les versions disponibles de Node.js :  
   ```bash
   nvm ls-remote
   ```
   Cela affichera toutes les versions disponibles.

2. Installez la version LTS (stable) :  
   ```bash
   nvm install --lts
   ```

3. Activez la version installée :  
   ```bash
   nvm use --lts
   ```

4. Assurez-vous que Node.js et npm sont bien installés :  
   ```bash
   node -v
   npm -v
   npx -v
   ```

---

## **2. Installation sur macOS**

### Méthode 1 : Installation via Homebrew (recommandée)

#### Étape 1 : Installer Homebrew (si ce n’est pas encore fait)

1. Ouvrez votre terminal.
2. Installez Homebrew avec la commande suivante :  
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

#### Étape 2 : Installer Node.js avec Homebrew

1. Installez Node.js :  
   ```bash
   brew install node
   ```
2. Vérifiez que Node.js, npm et npx sont bien installés :  
   ```bash
   node -v
   npm -v
   npx -v
   ```

---

### Méthode 2 : Installation via `nvm` (alternative)

Suivez exactement les mêmes étapes que celles décrites pour **Linux** dans la section précédente pour installer Node.js avec `nvm` sur macOS.

---

## **3. Tester Node.js sur Linux et macOS**

#### Étape 1 : Tester Node.js

Dans le terminal, exécutez :  
```bash
node -v
```
Cela affichera la version de Node.js.

#### Étape 2 : Tester npm

Ensuite, testez `npm` :  
```bash
npm -v
```

#### Étape 3 : Tester npx

Pour tester `npx` :  
```bash
npx -v
```

#### Étape 4 : Exécuter un programme simple en Node.js

1. Lancez l’environnement interactif Node.js :  
   ```bash
   node
   ```
2. Tapez :  
   ```javascript
   console.log("Hello from Node.js!");
   ```
   Appuyez sur Entrée. Si tout fonctionne, vous verrez :  
   `Hello from Node.js!`
3. Quittez avec :  
   ```bash
   .exit
   ```

---

## **4. Résolution des problèmes courants**

1. **Commandes introuvables après installation** :
   - Si Node.js ou npm ne sont pas reconnus après l’installation avec `nvm`, exécutez :  
     ```bash
     source ~/.bashrc
     ```
   - Sur macOS avec zsh :  
     ```bash
     source ~/.zshrc
     ```

2. **Permission refusée lors de l’installation globale de paquets avec npm** :
   - Si vous rencontrez des erreurs de permissions avec npm, exécutez :  
     ```bash
     npm config set prefix ~/.npm-global
     ```
   - Ajoutez ensuite ce chemin dans votre fichier `.bashrc` ou `.zshrc` :
     ```bash
     export PATH=$PATH:~/.npm-global/bin
     ```

3. **Problème avec Homebrew** :  
   Si Homebrew affiche une erreur, vérifiez que votre macOS est à jour et réinstallez Homebrew.

