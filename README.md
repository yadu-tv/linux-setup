
# Guide to how I setup linux system

## Initial setup

* Updating the system
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```

  ```bash
  sudo apt-get dist-upgrade -y
  ```

* Installing necessary applications
  ```bash
  sudo apt install git curl vlc ffmpeg build-essential nautilus vim neovim htop neofetch thefuck gparted p7zip-rar ntfs-config usbmount cmake ssh openssh-server gedit-latex-plugin -y
  ```

* Initialise thefuck
    ```bash
    # Thefuck plugin
    eval $(thefuck --alias)
    # You can use whatever you want as an alias, like for Mondays:
    eval $(thefuck --alias FUCK)
    ```

## Setting up Github SSH Key

* Generating new ssh key
    ```bash
    ssh-keygen -t ed25519 -C "your_email@gmail.com"
    ```

* Start ssh agent
    ```bash
    eval "$(ssh-agent -s)"
    ```

* Add ssh private key
    ```bash
    ssh-add ~/.ssh/id_ed25519
    ```

* Add ssh public key
    * Copy public key
        ```bash
        cat ~/.ssh/id_ed25519.pub
        ```
    * Navigate to [Keys](https://github.com/settings/keys)

    * Click new SSH key and paste the value

* Check the connection using
    ```bash
    git -T git@github.com
    ```

## Installing required development applications
### Installing Node Version Manager(NVM)
* Run installer
    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
    ```

* Initialise NVM 
    ```bash
    export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
    ```

### Installing Node using nvm
* To install a particular version
    ```bash
    nvm install <NODE_VERSION>
    ```
* To use a particular version
    ```bash
    nvm use <NODE_VERSION>
    ```

### Installing PyEnv
* Run installer
    ```bash
    curl https://pyenv.run | bash
    ```

* Initialise PyEnv
    ```bash
    export PYENV_ROOT="$HOME/.pyenv"
    [[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
    eval "$(pyenv init -)"
    ```

### Installing Python using pyenv
* To install a particular version
    ```bash
    pyenv install <PYTHON_VERSION>
    ```
* To default a particular version for the whole system
    ```bash
    pyenv global <PYTHON_VERSION>
    ```
* To default a particular version for the user
    ```bash
    pyenv local <PYTHON_VERSION>
    ```
### Installing Anaconda for python

* Installing prerequisites
    ```bash
    apt-get install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
    ```

* Choose installer version from [archive](https://repo.anaconda.com/archive/)

* Replace INSTALLER_VERSION with the correct version and run the command below
    ```bash
    curl -O https://repo.anaconda.com/archive/Anaconda3-<INSTALLER_VERSION>-Linux-x86_64.sh
    ```

* To run the installer
    ```bash
    bash ~/Downloads/Anaconda3-<INSTALLER_VERSION>-Linux-x86_64.sh
    ```

* Enter “yes” to initialize Anaconda Distribution by running ```conda init```

### Using conda to create python environment

* Creating an env
    ```bash
    conda create -n "ENV_NAME" python="PYTHON_VERSION"
    ```

* Using an env
    ```bash
    conda activate "ENV_NAME"
    ```

* Deactivating an env
    ```bash
    conda deactivate
    ```

### Installing JDK

* Find the version of JDK
    ```bash
    apt search openjdk
    ```

* Enter this command to install JDK
    ```bash
    sudo apt install openjdk-<JDK_VERSION>-jdk -y
    ```

* Add the following to the shell file
    ```bash
    export JAVA_HOME=/usr/lib/jvm/java-<JDK_VERSION>-openjdk
    ```

## Other Applications

[VS Code](https://code.visualstudio.com/download)

[Google Chrome](https://www.google.com/intl/en_in/chrome/)

[Sublime Text 3](https://www.sublimetext.com/3)

The following DPKG applications above can be installed by using the command below

```bash
sudo dpkg -i /path/to/file
```

## Cleaning
```bash
sudo apt-get autoclean
```