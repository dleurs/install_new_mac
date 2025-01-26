# Install new mac for mobile developper Flutter

### 1. Initial setup
   - Internet connexion established
   - FileVault is set up
      - Réglages Système > Confidentialité et sécurité > FileVault
   - [Latest stable macOs version](https://en.wikipedia.org/wiki/MacOS_version_history#Releases) installed
      - Réglages Système > Mise à jour de logiciels
   - Password setup
      - Réglages Système > Utilisateurs et groupes > Modifier le mot de passe...
### 2. [XCode](https://apps.apple.com/us/app/xcode/id497799835?mt=12)
   - Create [Apple ID](https://appleid.apple.com/). **Be careful if you should use ESN email or client company email.**
   - Dans l'App Store, créer/se connecter à son identifiant Apple
   - Lancer [le téléchargement Xcode](https://developer.apple.com/xcode/resources/) via App Store (très long)
      - Lancer Xcode pour lancer l'install
   - ```sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer```
   - ```sudo xcodebuild -runFirstLaunch```
   - [Consider install previous Xcode version](https://xcodereleases.com/), but rename it to not replace up-to-date Xcode
      - To select the default Xcode for flutter : ```sudo xcode-select -s <path/to/>Xcode.app```
   - ```open /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app```
      - Simulator > Settings... > **coché** Show single touches et **coché** Show pinch gestures
      - (Dans le simulateur) Réglages/Settings > Clavier > Claviers > Français (France) en premier
      - (Dans le simulateur) Réglages/Settings > Langue et région > Langue Français
     
### 3.1 Settings
   - Réglages Système > Clavier > Méthodes de saisie > **Français - Numérique**
   - Réglages Système > TrackPad > Pointer et cliquer > **Toucher pour clicker** activé
   - Ouvrir Finder > Réglages > **Disques durs** activé
   - Ouvrir Terminal > Réglages > Profils > Police > Modifier -> 14,  SF Mono Regular 14pt
   - ***Right clic*** Dock > Préférences du Dock > **Masquer/afficher automatiquement le Dock** coché
   - If Mac with Apple chipset, create an Intel Terminal
      - Finder > Applications > Utilitaires > ***Clic droit*** Terminal > Duplicate
      - Remane Terminal Intel, ***Clic droit*** Terminal Intel > Lire les informations > Ouvrir avec Rosetta
      - Launch Terminal Intel > ```arch``` => ```i386```
   - Réglages Système > Son > Sortie > Émettre un son au démarrage **désactivé**
   - Réglages Système > Son > Sortie > Émettre un son lorsque le volume est modifié **activé**
   - Centre de contrôle > Son > **Toujours affcher dans la barre de menu**
   - Centre de contrôle > Bluetooth > **Toujours affcher dans la barre de menu**
   - Centre de contrôle > Batterie > Afficher le pourcentage **activé**

### 3.2 Minor settings
   - QuickTime > Nouvel enregistrement de l'écran > Options > Afficher les clics de la souris
   - Réglages Système > Réseau > Wifi + Câble > Avancé > DNS > Add DNS https://yggland.fr/FAQ-Tutos/ (could be 1.1.1.1 & 1.0.0.1 & 2606:4700:4700::1111 & 2606:4700:4700::1001)
   - Préférences Sytème > Confidentialité et sécurité > Accès complet au disque > Terminal
      - Pour accéder à ls depuis ~/.Trash
### 4. Install [Firefox](https://www.mozilla.org/en-US/firefox/new/)
   - Do the sync with your account
     - Réglages Système > Bureau et Dock > Navigateur par défaut > Firefix
   - Set Firefox default browser
   - Réglages Système > Confidentialité et sécurité > 
      - Enregistrement de l'écran > clic Cadenas > + > Application > Firefox
   - Installer extension uBlock Origin (devrais être automatique)
### 5. Install [Chrome](https://www.google.com/chrome/)
   - Do the sync with your account
   - Réglages Système > Confidentialité et sécurité >
      - Enregistrement de l'écran > clic Cadenas > + > Application > Chrome
### 6. On Terminal, install [brew](https://brew.sh/)
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
```
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/dleurs/.zprofile
```
```
eval "$(/opt/homebrew/bin/brew shellenv)"
```
### 7. On Terminal, install [zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH) 
```
brew install zsh
```
```
chsh -s /usr/local/bin/zsh
```
### 8. On Terminal install [Oh My Zsh](https://ohmyz.sh/)
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
### 9. Setup environment
```
cd ;
cd Documents;
mkdir Flutter;
mkdir Android;
mkdir iOS;
mkdir Readmes;
mkdir AI;
```
- <img width="176" alt="Capture d’écran 2022-09-20 à 00 09 15" src="https://user-images.githubusercontent.com/58068925/191128920-4821519a-8712-4dab-9e0a-f407c5725a8d.png">
### 10. Setup tools

```
brew tap leoafarias/fvm
brew install fvm
fvm install stable
```
```
export PATH="$PATH:/Users/dleurs/fvm/versions/stable/bin" 
# Inside zshrc after
```
```
brew install cocoapods
```
- Optionnals
```
brew install trash
```
Les dossiers ne seront pas visibles dans la poubelle mac, il faudra ```cd ~/.Trash; ls; mv```
```
brew install python
```
```
brew install java #or java11
```
```
export JAVA_HOME="/opt/homebrew/opt/openjdk@20" # Next inside .zshrc
```
### 11. Install [VSCode](https://code.visualstudio.com/download)
   - Code > Preferences > Turn on Settings Sync... > GitHub
   - Launch VSCode > Preferences > Settings
```
dart.devToolsBrowser > chrome
```
```
dart.devToolsLocation > external
```
```
dart.lineLength > 80
# Dans la plupart des projets flutter on mettra 120
```
### 12. Install [Android Studio](https://developer.android.com/studio)
   - Launch Android Studio, install it with default settings
   - Android Studio > Preferences > Language & Framework > Android SDK > **SDK Tools**
      - **Android SDK Build-Tools** coché
      - **Android SDK Command-line Tools** coché
      - **Android SDK Plateform-Tools** coché
   - Press **Apply** 
   - Launch Android Studio > More Actions > Virtual Device Manager > Create Device
      - Pixel 5 > R ***download*** API 30 
      - Next > Show Advanced Settings > Internal Storage > **6 GB** 
      - Studio-managed > **6 GB** > Finish
      - Mettre langue et clavier du simulateur à français

# For adb
```
brew install android-platform-tools
```

### 13. Setup SSH
```
git config --global user.name "Firstname LASTNAME"
```
```
git config --global user.email firstname.lastname@company.com
```
```
git config --global init.defaultBranch main
```
```
ssh-keygen -t ed25519 -C "firstname.lastname@company.com"
```
- OR ```ssh-keygen -t rsa -b 4096 -C "firstname.lastname@company.com"```
```
cat ~/.ssh/id_ed25519.pub | pbcopy
```
- Paste the content inside Github/Gitlab/Hetzner > Security > Add an SSH Key, with tile **Macbook Pro 14" M1 2021 SERIAL_NUMBER_COMPUTER** 
 - Add your key to agent without need to enter passphrase every time:
```
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
# Then inside ~/.zshrc
```

### 14. Setup GPG, to sign commits to avoid impersonation
```
brew install gnupg pinentry-mac
```
```
gpg --full-gen-key
```
      - 9 ```ECC (sign and encrypt)```
      - 1 ```Curve 25519```
      - 0 ```La clef n'expire pas```
      - ```Firstname LASTNAME```
      - ```firstname.lastname@company.com```
      - ```Macbook Pro 14" M1 2021 SERIAL_NUMBER_COMPUTER```
```
echo "pinentry-program $(brew --prefix)/bin/pinentry-mac" > ~/.gnupg/gpg-agent.conf && chmod 0600 ~/.gnupg/gpg-agent.conf
```
```
$ gpg --list-keys --keyid-format LONG
$ [...]pub   ed25519/2B6*********9F4 2021-09-27 [SC][...]
```
```
git config --global user.signingkey 2B6*********9F4
```
```
git config --global commit.gpgsign true
```
```
gpgconf --kill gpg-agent
```
```
git log --show-signature
```
```
gpg --armor --export 2B6*********9F4 | pbcopy
```
Paste to github/gitlab
- https://github.com/settings/keys
- https://gitlab.com/-/profile/gpg_keys

Verify email address inside 
- https://github.com/settings/emails
- 
   
### 15. Setup ```~.zshrc``` like [below](https://github.com/dleurs/install_new_mac/blob/main/README.md#zshrc), copy elements of **ZSHRC** chapter

### 16. Setup Flutter and check it is working fine
```
flutter doctor --android-licenses
``` 
```
flutter doctor -v
```
- Go to where you save your Flutter projects, ```gof```
```
flutter create first_helloworld --org uniqueidhelloworld.leurs.dev
```
```
cd first_helloworld
```
```
fvm use stable
```
```
code first_helloworld
```
```
mkdir .vscode; cd .vscode;
```
```
touch launch.json
```
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "program": "lib/main.dart",
            "name": "First Helloworld",
            "request": "launch",
            "type": "dart"
        }
    ]
}
```
```
touch settings.json
```
```
{
    "dart.flutterSdkPath": ".fvm/flutter_sdk",
    // Remove .fvm files from search
    "search.exclude": {
      ".fvm/**": true
    },
    // Remove from file watching
    "files.watcherExclude": {
      ".fvm/**": true
    }
}
```
  - Below blue bar > **macOS** > launch iOS simulator > wait for simulator to be launched
    - Inside vscode > ```fn + F5``` > Check it is running > close running task clicking red square inside VSCode
  - Below blue bar > **iPhone 14** > Pixel 4 API 30 > wait for simulator to be launched 
    - Inside vscode > ```fn + F5``` > Check it is running > close running task clicking red square inside VSCode
  - Below blue bar > **iPhone 14** > Chrome
    - Inside vscode > ```fn + F5``` > Check it is running > close running task clicking red square inside VSCode
  
  - Create a new Github/Gitlab project **Test Upload Helloworld** to see if you can ```git push```, and commit user info is correct

  - Also run on real device, check https://support.apple.com/fr-fr/HT204460 for iOS

### 17. Install
   - [VLC](https://www.videolan.org/)
      - Pour modifier l'appli par défault pour mp3, mp4 et mkv, clic droit fichier > Lire les informations > Ouvrir avec > VLC > **Tout modifier**
   - [Vysor](https://www.vysor.io/)
   - [Sublime Text](https://www.sublimetext.com/)
   - [Postman](https://www.postman.com/downloads/?utm_source=postman-home) or [Insomnia](https://insomnia.rest/download)
   - Giphy, inside App Store
      - Réglages Systèmes > Confidentialité et sécurité > Enregistrement de l'écran > + Giphy
   - [Table Plus](https://tableplus.com/)
   - [Flashlight](https://docs.flashlight.dev/) ```curl https://get.flashlight.dev | bash```
   - [Logitech G Hub](https://www.logitechg.com/fr-fr/innovation/g-hub.html)
   - [NextCloud](https://nextcloud.com/fr/install/)
   - [gcloud command](https://cloud.google.com/storage/docs/gsutil_install?hl=fr)
     
### 18. Optionnal install
   - [Very Good Cli](https://pub.dev/packages/very_good_cli)
      - ```dart pub global activate very_good_cli```
   - [Zoom](https://support.zoom.us/hc/fr/articles/4415294177549-T%C3%A9l%C3%A9charger-le-Zoom-desktop-client-et-la-Zoom-mobile-app)
      - Réglages Systèmes > Confidentialité et sécurité > Enregistrement de l'écran > + Zoom
   - [Microsoft Teams](https://www.microsoft.com/fr-fr/microsoft-teams/download-app)
      - Réglages Systèmes > Confidentialité et sécurité > Enregistrement de l'écran > + Microsoft Teams
   - [Sourcetree](https://www.sourcetreeapp.com/)
   - [Docker](https://docs.docker.com/desktop/install/mac-install/)
      - Launch and connect
   - [Kubernetes](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
   - [Android File Transfer](https://www.android.com/filetransfer/)
   - [LibreOffice](https://fr.libreoffice.org/download/telecharger-libreoffice/?type=mac-aarch64&version=24.8.2&lang=fr)
   - [qBitTorrent](https://www.qbittorrent.org/) 
      - Changer Settings > Download folder default : /Users/dleurs/Movies/videos_personnel_privee
      - Extraire piste sous titre : https://subler.org/
        - Instruction extraction srt : https://www.journaldulapin.com/2023/05/25/recuperer-les-sous-titres-dans-un-fichier-mkv/
        -  

### 19. Setup icons Dock
- ![Macbook Doc](/images/dock.png)

### 20. Download [Developer Tools](https://developer.apple.com/download/all/?q=Additional%20Tools) **Additional Tools for Xcode**, to simulate low connexion 
   - Hardware > double clic **Network Link Conditioner**
      - Réglages Système > Network Link Conditioner
      
### 21. Set profile picture
- Download profile picture in this repo inside dleurs > Images

### 22. Proxy
- Use dart devtools

### 23. Other
- Download a PDF, open it with default Preview, then Presentation > tick 'Vignettes' so it will always open with vignettes
- Cmd + Space > Preview > Ajouter sa signature
- Add SSH key to console.hetzner.cloud
```
cat ~/.ssh/id_ed25519.pub | pbcopy
```


# À penser avant de donner son mac

1. Bien récupérer les **local.properties** et **keystore** de TOUS les projets Android ou Flutter avec android
2. Toutes ses collections Insomnia / Postman (fichier)
3. ? Ses configs Android studio (fichier) 
4. Check sync VSCode Github OK
5. L'export des certificats du Keychain Access
6. Déplacer les fichiers .gitignored, comme ```~/.gradle/gradle.properties``` avec ```jfrogUser="" jfrogApiKey=""```
7. Avec la suppression clé ssh et gpg, retirer de github
8. Récupérer ```~/Library/MobileDevice/Provisioning\ Profiles```
9. Certains bouts de code à conserver ?

# Git autofixup
```
brew install fzf
```
```
subl ~/.gitconfig
```

```
[alias]
  # Amend into a past commit using fzf
  # Stage your changes `git add -p`, then run `git autofixup` and choose the target commit
  autofixup = "!f() { \
    COMMIT_HASH=$(git log --pretty=oneline | fzf | awk '{print $1}'); \
    git commit --fixup $COMMIT_HASH; \
    GIT_SEQUENCE_EDITOR=: git rebase --autostash --autosquash -i $COMMIT_HASH^; \
    }; f"
```

# ZSHRC

### ZSHRC aliases
```
############### ALIASES ###############

alias sshcloud="ssh root@XXX"

alias gof="cd ~/Documents/Flutter"
alias goa="cd ~/Documents/Android"
alias goi="cd ~/Documents/iOS"
alias gor="cd ~/Documents/Readmes"

alias simulateur="open /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app"

alias pip="pip3"
alias pyton="python3"

alias sublzsh="subl ~/.zshrc"
alias sublgit="subl ~/.gitconfig"
alias k="kubectl"
alias d="docker"

alias gitskip="git update-index --skip-worktree"
alias gitunskip="git update-index --no-skip-worktree"
# git autofixup   inside ~/.gitconfig

alias rm="echo 'FAILURE : better user trash, or /bin/rm'"

############# END ALIASES ############# 

```

### ZSHRC keys

```

################ KEYS #################

ssh-add --apple-use-keychain ~/.ssh/id_ed25519

############## END KEYS ###############
```

### ZSHRC functions

```
############## FUNCTIONS ##############

pull() {
  branch=$1
  initialBranch=$(git branch --show-current)
  if [ "$branch" = "" ]; 
  then
    branch=$(git branch --show-current);
  else
    git checkout $branch
  fi
  git fetch;
  git pull origin $branch; 
  git status;
  if [ "$branch" = "" ]; 
  then
  else
    git checkout $initialBranch
  fi
}

push() {
  # Récupérer la branche Git actuelle
  current_branch=$(git rev-parse --abbrev-ref HEAD 2>/dev/null)
  
  # Vérifier si on est bien dans un dépôt Git
  if [ -z "$current_branch" ]; then
    echo "Erreur : Ce répertoire n'est pas un dépôt Git."
    return 1
  fi

  # Si un argument est donné avec "--force-with-lease", ajouter cette option
  if [[ "$1" == "--force-with-lease" ]]; then
    echo "Poussée avec 'force-with-lease' pour la branche : $current_branch"
    git push origin "$current_branch" --force-with-lease
  else
    echo "Poussée pour la branche : $current_branch"
    git push origin "$current_branch"
  fi
}

cleanIos() {
  cd ios
  trash Pods
  trash .symlinks
  trash Flutter/Flutter.framework
  trash Flutter/Flutter.podspec
  trash Podfile.lock
  arch -x86_64 pod repo update
  arch -x86_64 pod install
  cd ..
}

changeAuthor() {
  git config --global user.email firstname.lastname@company.com
  git commit --amend --reset-author --no-edit
}

generate() {
  fvm dart run build_runner build --delete-conflicting-outputs
  fvm flutter gen-l10n
}

deleteDsStore() {
  find . -name '.DS_Store' -type f -delete;
}

############ END FUNCTIONS ############
```

### ZSHRC Path

```
############# PATH EXPORTS ############

export PATH="$PATH:/Users/dleurs/fvm/versions/3.22.2/bin"
export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
export PATH="$PATH:/Applications/Sublime Text.app/Contents/SharedSupport/bin"
export PATH="$PATH":"$HOME/.pub-cache/bin"
export PATH="$PATH":"/opt/homebrew/opt/openjdk/bin"
export JAVA_HOME="/opt/homebrew/opt/openjdk"

########### END PATH EXPORTS ##########
```

# ZSHRC info
```
################# INFO ################

infoGitlavCleanComments='
Gitlab clear code comments
    
<details><summary>Mon code</summary>
  <pre>
    1+1=2
  </pre>
</details>
'

infoGitTag='
git tag -a 1.4.0 -m "my version 1.4"
'

############### END INFO ##############
```
