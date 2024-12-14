# Installation de **Cursor AI** sur Linux et macOS

---

### **Installation sur Linux**

#### Étape 1 : Télécharger l'exécutable pour Linux

1. **Accédez au site officiel de Cursor AI** :
   - Ouvrez votre navigateur et allez sur 👉 [https://getcursor.com](https://getcursor.com) ou sur leur page officielle GitHub.

2. **Téléchargez l'exécutable** :
   - Recherchez la section "Downloads" ou "Releases".
   - Téléchargez le fichier correspondant à Linux, généralement nommé :  
     `CursorAI-x.x.x.AppImage`.

---

#### Étape 2 : Rendre l'exécutable utilisable

1. **Ouvrez un terminal** et allez dans le dossier où le fichier `.AppImage` a été téléchargé, par exemple :  
   ```bash
   cd ~/Downloads
   ```

2. **Rendre le fichier exécutable** :
   - Exécutez cette commande pour donner les permissions nécessaires :  
     ```bash
     chmod +x CursorAI-x.x.x.AppImage
     ```

3. **Lancer Cursor AI** :
   - Une fois le fichier rendu exécutable, lancez Cursor AI :  
     ```bash
     ./CursorAI-x.x.x.AppImage
     ```

---

#### Étape 3 : Ajouter Cursor AI au menu des applications (optionnel)

Si vous souhaitez accéder à Cursor AI via le menu des applications :
1. Créez un fichier de raccourci :  
   ```bash
   nano ~/.local/share/applications/cursor-ai.desktop
   ```

2. Ajoutez ce contenu dans le fichier (remplacez les chemins si nécessaire) :
   ```ini
   [Desktop Entry]
   Name=Cursor AI
   Exec=/path/to/CursorAI-x.x.x.AppImage
   Icon=/path/to/icon.png
   Type=Application
   Categories=Development;
   ```

3. Enregistrez (Ctrl + O, puis Entrée) et quittez (Ctrl + X).  

---

### **Installation sur macOS**

#### Étape 1 : Télécharger l’exécutable pour macOS

1. **Accédez au site officiel de Cursor AI** :
   - Rendez-vous sur 👉 [https://getcursor.com](https://getcursor.com) ou leur page GitHub.

2. **Téléchargez l’exécutable macOS** :
   - Recherchez la version pour macOS, souvent nommée :  
     `CursorAI-x.x.x.dmg`.

---

#### Étape 2 : Installer Cursor AI

1. **Ouvrir le fichier .dmg** :
   - Double-cliquez sur le fichier téléchargé pour monter l’image disque.

2. **Glisser-déposer l’application dans le dossier Applications** :
   - Une fenêtre s’ouvrira, vous demandant de glisser l’icône de Cursor AI dans le dossier **Applications**.

---

#### Étape 3 : Lancer Cursor AI

1. **Ouvrez Cursor AI** :  
   - Dans le **Finder**, accédez à Applications et double-cliquez sur **Cursor AI**.

2. Si une alerte de sécurité macOS s’affiche :  
   - Allez dans **Préférences Système** > **Sécurité et confidentialité** > **Général**.
   - Cliquez sur **"Ouvrir quand même"**.

---

### **Étape Finale : Résolution des problèmes communs**

#### Sur Linux :
- Si le fichier `.AppImage` ne s'exécute pas :
  - Assurez-vous que toutes les dépendances nécessaires sont installées. Par exemple :  
    ```bash
    sudo apt install libfuse2
    ```

#### Sur macOS :
- Si macOS bloque l'application pour des raisons de sécurité :  
  - Ouvrez l'application en maintenant **Ctrl** tout en cliquant sur l'icône, puis sélectionnez **"Ouvrir"**.


