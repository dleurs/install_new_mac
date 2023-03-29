# Install new mac for mobile developper Flutter

### 1. Initial setup
   - Internet connexion established
   - FileVault is set up
      - Préférences Système > Sécurité et confidentialité > FileVault
   - [Latest stable macOs version](https://en.wikipedia.org/wiki/MacOS_version_history#Releases) installed
      - Préférences Système > Mise à jour de logiciels
   - Password setup
      - Préférences Système > Utilisateurs et groupes > Modifier le mot de passe...
### 2. [XCode](https://apps.apple.com/us/app/xcode/id497799835?mt=12)
   - Dans l'App Store, créer/se connecter à son identifiant Apple
   - Lancer [le téléchargement Xcode](https://developer.apple.com/xcode/resources/) via App Store (très long)
      - Lancer Xcode pour lancer l'install
   - ```sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer```
   - ```sudo xcodebuild -runFirstLaunch```
   - [Consider install previous Xcode version](https://xcodereleases.com/), but rename it to not replace up-to-date Xcode
      - To select the default Xcode for flutter : ```sudo xcode-select -s <path/to/>Xcode.app``` 
### 3.1 Settings
   - Préférences Système > Clavier > Méthodes de saisie > **Français - Numérique**
   - Préférences Système > TrackPad > Pointer et cliquer > **Toucher pour clicker** activé
   - Finder > Préférences > **Disques durs** activé
   - Terminal > Préférences > Profils > Police > Modifier -> 14,  SF Mono Regular 14pt
   - ***Right clic*** Dock > Préférences du Dock > **Masquer/afficher automatiquement le Dock** coché
   - If Mac with Apple chipset, create an Intel Terminal
      - Finder > Applications > Utilitaires > ***Clic droit*** Terminal > Duplicate
      - Remane Terminal Intel, ***Clic droit*** Terminal Intel > Lire les informations > Ouvrir avec Rosetta
      - Launch Terminal Intel > ```arch``` => ```i386```
   - Préférences Système > Clavier > Méthodes de saisie > **Français - Numérique**
   - Préférences Système > Son > Sortie > Afficher Son dans la barre des menus coché et **toujours**
   - Préférences Système > Bluetooth > Afficher Bluetooth dans la barre des menus coché
   - Cmd + Space > Simulateur > Lancer simulateur > Réglages > Clavier > Claviers > Français (France) en premier
   - Cmd + Space > Simulateur > Lancer simulateur > Réglages > Langue et région > Langue Français

### 3.2 Minor settings
   - QuickTime > Enregistrement de l'écran > Options > Afficher les clics de la souris
   - Préférences Système > Réseau > Wifi + Câble > Avancé > DNS > Add 1.1.1.1 & 1.0.0.1
### 4. Install [Firefox](https://www.mozilla.org/en-US/firefox/new/)
   - Do the sync with your account
   - Set Firefox default browser
   - Préférences Système > Sécurité et confidentialité > 
      - Enregistrement de l'écran > clic Cadenas > + > Application > Firefox
      - Appareil photo > clic Cadenas > + > Application > Firefox
      - Microphone > clic Cadenas > + > Application > Firefox
      - Service de localisation > clic Cadenas > + > Application > Firefox
### 5. Install [Chrome](https://www.google.com/chrome/)
   - Do the sync with your account
   - Préférences Système > Sécurité et confidentialité >
      - Enregistrement de l'écran > clic Cadenas > + > Application > Chrome
      - Appareil photo > clic Cadenas > + > Application > Chrome
      - Microphone > clic Cadenas > + > Application > Chrome
      - Service de localisation > clic Cadenas > + > Application > Chrome
### 6. On Terminal, install [brew](https://brew.sh/)
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
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
```
brew install python
brew install java
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
```
### 12. Install [Android Studio](https://developer.android.com/studio)
   - Launch Android Studio, install it with default settings
   - Android Studio > Preferences > Apparence & Behavior > System Settings > Android SDK > **SDK Tools**
      - **Android SDK Build-Tools** coché
      - **Android SDK Command-line Tools** coché
      - **Android SDK Plateform-Tools** coché
   - Press **Apply** 
   - Launch Android Studio > More Actions > Virtual Device Manager > Create Device
      - Pixel 4 > R ***download*** API 30 
      - Next > Show Advanced Settings > Internal Storage > **8 GB** > Finish
      - Mettre langue et clavier du simulateur à français

### 13. Setup SSH
```
git config --global user.name "Firstname LASTNAME"
git config --global user.name
```
```
git config --global user.email firstname.lastname@company.com
git config --global user.email
```
```
git config --global init.defaultBranch main
git config --global init.defaultBranch
```
```
ssh-keygen -t ed25519 -C "firstname.lastname@company.com"
```
- OR ```ssh-keygen -t rsa -b 4096 -C "firstname.lastname@company.com"```
```
cat ~/.ssh/id_ed25519.pub | pbcopy
```
- Paste the content inside Github/Gitlab > Security > Add an SSH Key, with tile **Macbook Pro 14" M1 2021 SERIAL_NUMBER_COMPUTER** 
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
flutter create first_helloworld
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

### 17. Install
   - [VLC](https://www.videolan.org/)
      - Pour modifier l'appli par défault pour mp3, mp4 et mkv, clic droit fichier > Lire les informations > Ouvrir avec > VLC > **Tout modifier**   
   - [Sublime Text](https://www.sublimetext.com/)
   - [Postman](https://www.postman.com/downloads/?utm_source=postman-home) or [Insomnia](https://insomnia.rest/download)
   - [Docker](https://docs.docker.com/desktop/install/mac-install/)
   - [act] ```brew install act``` (require docker)
### 18. Optionnal install
   - [Kubernetes](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
   - [Table Plus](https://tableplus.com/)
   - [Sourcetree](https://www.sourcetreeapp.com/)
   - [Vysor](https://www.vysor.io/)

### 19. Setup icons Dock
- ![Macbook Doc](/images/dock.png)

### 20. Download [Developer Tools](https://developer.apple.com/download/all/?q=Additional%20Tools) **Additional Tools for Xcode**, to simulate low connexion 
   - Hardware > double clic **Network Link Conditioner**
      - Préférences Système > Network Link Conditioner
      
### 21. Set profile picture
- Download profile picture in this repo inside dleurs > Images

### 22. Install mitmproxy
- ```brew install mitmproxy```
- S'assurer de n'avoir qu'une connexion wifi ou filaire (pas deux à la fois)
- Réglages Systèmes > Wifi ou filaire > Détails > Proxys > 
   - Proxy web : Serveur localhost / Port 8080
   - Proxy web sécurisé : Serveur localhost / Port 8080
- ```cd; cd Documents; mkdir Proxy```
- Via Chrome : mitm.it
- Téléchargez proxy macOS et iOS, déplacer vers ~/Documents/Proxy, renommez préfixe macOs et iOS
- Double clic certificat macOs, puis KeyChain > "mitm" > Toujours faire confiance
- On Firefox > Réglages > Vie privée et sécurité > Afficher les certificats > Autorité > Importer > certificat iOS
- On Chrome > proxy > utiliser proxy système
- Ouvrir simulateur iOS > drag drop certificat iOS dans simulateur > Réglages > Général > Informations > Réglages des certificats > mitmproxy checked

- ```mitmweb```
- Press z to clean history

### 23. AI 

(Tests were bad so you can avoid it)

- Intall [.dmg file](https://github.com/vincelwt/chatgpt-mac) ChatGPT
- Install [llama.cpp](https://github.com/ggerganov/llama.cpp)
   - [The install doc](https://til.simonwillison.net/llms/llama-7b-m2)
- Get the weights from [here](https://github.com/facebookresearch/llama/pull/73/commits/56de950af8a48c7cae221581e2e3e2c342b2ad82) 219Go required or select only 7B model / 12.55Gb folder with qBitTorrent
![image](https://user-images.githubusercontent.com/58068925/227500173-2621ef99-03e7-41e7-8e98-67167ab76beb.png)






# Transfer between macs

1. Bien récupérer les **local.properties** et **keystore** de TOUT les projets Android ou Flutter avec android
2. Toutes ses collections Insomnia (fichier)
3. Ses configs Android studio (fichier)
4. Son .zshrc ou .bashrc (fichier)
5. Ses configs VSCode (sync avec github)
6. Supprimer dossier .ssh (backup ?) 
7. L'export des certificats du Keychain Access
8. Déplacer son dossier ~/.kube ou Setup kube
9. Déplacer ou créer le fichier ```~/.gradle/gradle.properties``` avec ```jfrogUser="" jfrogApiKey=""```
10. Récupérer ```~/Library/MobileDevice/Provisioning\ Profiles```


# ZSHRC

### ZSHRC aliases
```
############### ALIASES ###############

alias gof="cd ~/Documents/Flutter"
alias goa="cd ~/Documents/Android"
alias goi="cd ~/Documents/iOS"
alias gor="cd ~/Documents/Readmes"
alias goai="cd ~/Documents/AI"

alias pip="pip3"
alias pyton="python3"

alias sublzsh="subl ~/.zshrc"
alias k="kubectl"
alias d="docker"

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

push() {
if [ $# -eq 0 ];
then
  echo "No arguments supplied. Example : push \"initial commit\" ";
else
  commitMessage=$1
  if [ "$commitMessage" = "" ]; 
  then
    echo "No commit message";
  else
    echo "\ngit status;\n";
    git status;
    echo "\ngit --no-pager diff;\n";
    git --no-pager diff;
    echo "\ngit add -A;\n";
    git add -A;
    echo "\ngit commit -m \"${commitMessage}\";\n";
    git commit -m $commitMessage;
    if [ $# -eq 1 ]; 
    then
      branch=$(git branch --show-current);
    else
      branch=$2
    fi
    for remote in $(git remote)
    do
      echo "\ngit push $remote $branch;\n";
      git push $remote $branch;
    done
  fi
fi
}

apush() { # Amend push
if [ $# -eq 0 ];
then
  commitMessage=$(git log -1 --pretty=%s | cat)  
  echo "No arguments supplied. Using lastest \"${commitMessage}\"";
else
  commitMessage=$1
fi
if [ "$commitMessage" = "" ]; 
then
  echo "No commit message";
else
  echo "\ngit status;\n";
  git status;
  echo "\ngit --no-pager diff;\n";
  git --no-pager diff;
  echo "\ngit add -A;\n";
  git add -A;
  echo "\ngit commit --amend -m \"${commitMessage}\";\n";
  git commit --amend -m $commitMessage;
  branch=$(git branch --show-current);
  for remote in $(git remote)
  do
    echo "\ngit push $remote $branch --force;\n";
    git push $remote $branch --force;
  done
fi
}

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


changeAuthor() {
  git config --global user.email firstname.lastname@company.com
  git commit --amend --reset-author --no-edit
}

rmDS_Store() {
  find . -name '.DS_Store' -type f -delete;
}

setnamespace() {
  kubectl config set-context --current --namespace=$1
}

llama () {
	if [ $# -eq 0 ]
	then
		~/Documents/AI/llama.cpp/main -m ~/Documents/AI/models/LLaMa/13B/ggml-model-q4_0.bin --interactive-first -n 512
	else
		~/Documents/AI/llama.cpp/main -m ~/Documents/AI/models/LLaMa/13B/ggml-model-q4_0.bin -n 512 -p $1
	fi
}


############ END FUNCTIONS ############
```

### ZSHRC Path

```
############# PATH EXPORTS ############

export PATH="$PATH:/Users/dleurs/fvm/versions/stable/bin"
export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
export PATH="$PATH:/Applications/Sublime Text.app/Contents/SharedSupport/bin"

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
