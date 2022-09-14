# Install new mac

0. Check
   - FileVault is set up
      - Préférences Système > Sécurité et confidentialité > FileVault
   - [Latest LRS macOs version](https://en.wikipedia.org/wiki/MacOS_version_history#Releases) installed
      - Préférences Système > Mise à jour de logiciels
1. XCode
   - Dans l'App Store, créer/se connecter à son identifiant Apple
   - Lancer le téléchargement Xcode via App Store (très long)
2. 
1. Install Firefox, 
   - Do the sync with your account
   - Set Firefox default browser
2. Install Chrome
   - Do the sync with your account
3. On Terminal, install [brew](https://brew.sh/)
   - ```/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"```
4. On Terminal, install [zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH) 
   - ```brew install zsh```
   - ```chsh -s /usr/local/bin/zsh```
5. On Terminal install [Oh My Zsh](https://ohmyz.sh/)
   - ```sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"```
6. 
6. Setup environment
```
cd ;
cd Documents;
mkdir Flutter;
mkdir Android;
mkdir iOS;
mkdir Readmes;
```
7. Setup tools
```
brew install trash
```
8. Install [vscode](https://code.visualstudio.com/download)
   - Code > Preferences > Turn on Settings Sync... > GitHub
9. Install [Android Studio](https://developer.android.com/studio)
   - 

12. Install
   - [VLC](https://www.videolan.org/)
   - [Sublime Text](https://www.sublimetext.com/)



8. Download [developer tools](https://developer.apple.com/download/more/?=for%20Xcode) for mac, to simulate low connexion 



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

alias sublzsh="subl ~/.zshrc"
alias k="kubectl"
alias d="docker"

alias rm="echo 'FAILURE : better user trash, or /bin/rm'"

############# END ALIASES ############# 
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
  git config --global user.email dimitri.leurs@numberly.com
  git commit --amend --reset-author --no-edit
}

rmDS_Store() {
  find . -name '.DS_Store' -type f -delete;
}

setnamespace() {
  kubectl config set-context --current --namespace=$1
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