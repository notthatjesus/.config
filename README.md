# New computer configuration
## Scope
The scope of this project is to cover the applications and configurations required to setup a new working environment on both Windows 11 and Ubuntu 22.04

## Ubuntu
- __Version__: 22.04
- __Desktop__: GNOME

## Apps to install
[Here is the list](apps.md)

## Configuration
### Copy SSH keys
Get your ssh keys from 1Password and then store them into `$HOME/.ssh`.
```shell
echo '[YOUR PRIVATE KEY]' > $HOME/.ssh/id_rsa
echo '[YOUR PUBLIC KEY]' > $HOME/.ssh/id_rsa.pub
chmod 0700 $HOME/.ssh/id_rsa
chmod 0700 $HOME/.ssh/id_rsa.pub
```

### Install Git
```shell
sudo apt install git
```
### Shell
```bash
$ sudo apt install zsh
```
Run `zsh` and choose option (2) to create ~/.zshrc. Exit ZSH.

__Install Nerd Fonts (Meslo)__
```shell
git clone --filter=blob:none --sparse git@github.com:ryanoasis/nerd-fonts
cd nerd-fonts
git sparse-checkout add patched-fonts/
./install Meslo
```
After installing the fonts, open a new terminal and change the profile to use Meslo LGS font.

__Install powerlevel10k__<br>
Powerlevel10k is a shell customization with lots of features.
```shell
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

Run `zsh` and connifure the console options. Configuration file is stored here:
- [.zshrc](.zshrc)
- [.p10k.zsh](.p10kzsh)

__Make ZSH the default shell__
```shell
chsh -s $(which zsh)
```
After logout your session, if you open a new terminal, ZSH should be used by default.

### Shell tools

__AWS CLI__
```shell
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
Now you can run `aws configure` to setup AWS KEY ID and AWS KEY SECRET.

The tools below are applications used for different purposes, mainly covering devops topics. To install these tools we will use `brew`. 

Install brew:
```shell
cd $HOME
mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
eval "$(homebrew/bin/brew shellenv)"
brew update --force --quiet
chmod -R go-w "$(brew --prefix)/share/zsh"
```
__Kubernetes tools__
```shell
brew install kubectl kubectx k9s
brew install minikube
```

__Biometric Authentication (XPS laptops)__

!! This does not work!!
Kudos to [this guy](https://www.reddit.com/r/Dell/comments/ixwgm0/xps_15_9500_ubuntu_popos_fingerprint_howto/)

```shell
sudo apt install libfprint-2-tod1

```
Download and install the package [here](http://dell.archive.canonical.com/updates/pool/public/libf/libfprint-2-tod1-goodix/)

```shell
sudo dpkg -i [PACKAGE_NAME]
```

Restart and edit user settings to use biometric auth.

__Howdy(Windows hello)__
This somewhat works for console but not initial login
https://github.com/boltgolt/howdy

```shell
sudo add-apt-repository ppa:boltgolt/howdy
sudo apt update
sudo apt install howdy
```


__Screen Casting(Miracast)__

```shell
sudo apt-get install build-essential debhelper gnome-pkg-tools libglib2.0-dev libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstrtspserver-1.0-dev libgtk-3-dev libnm-dev libpulse-dev libx264-dev meson wpasupplicant desktop-file-utils appstream-util lib-avahi-client-dev lib-avahi-gobject-dev

git clone https://gitlab.gnome.org/GNOME/gnome-network-displays.git
cd gnome-network-displays
meson build
cd build
meson install
```


### Customization
__Configure secondary screen resolution__
__Notes on performance__ <br>
Wayland works nice with multiple screens but on single one looks bit blurry. Something to look at.
Normal Ubuntu (GNOME) works better on a single screen but it's slower.

## IDE Setup
### Pycharm plugins
> - .env files support (2022.1)
> - .ignore (4.3.0)
> - Big Data Tools (212.4037.95)
> - CSV (2.19.0)
> - Datalore (0.1.14-212)
> - EnvFile (3.2.2)
> - GitToolBox (212.9.7)
> - Ideolog (203.0.30.0)
> - Monokai Pro Theme (1.8.1)
> - Mypy (0.14.0)
> - Poetry (1.1.5-212)
> - Database Tools and SQL (212.5712.39)
> - Docker (212.5712.39)
> - FTP/SFTP Connectivity (ex. Remote Hosts Access) (212.5712.39)
> - Puppet (212.5712.39)
> - Vagrant (212.5712.39)
> - HTML Tools (212.5712.39)
> - IDE Settings Sync (212.5712.39)
> - Settings Repository (212.5712.39)
> - Angular and AngularJS (212.5712.39)
> - CoffeeScript (212.5712.39)
> - JavaScript and TypeScript (212.5712.39)
> - JavaScript Debugger (212.5712.39)
> - JavaScript Intention Power Pack (212.5712.39)
> - TSLint (212.5712.39)
> - Gherkin (212.5712.39)
> - GNU GetText files support (*.po) (212.5712.39)
> - Ini (212.5712.39)
> - Markdown (212.5712.39)
> - Properties (212.5712.39)
> - Shell Script (212.5712.39)
> - YAML (212.5712.39)
> - CSS (212.5712.39)
> - Less (212.5712.39)
> - Sass (212.5712.39)
> - Stylus (212.5712.39)
> - Haml (212.5712.39)
> - Windows 10 Light Theme (212.5712.39)
> - ChangeReminder (212.5712.39)
> - Git (212.5712.39)
> - GitHub (212.5712.39)
> - Mercurial (212.5712.39)
> - Perforce Helix Core (212.5712.39)
> - Subversion (212.5712.39)
> - Code With Me (212.5712.39)
> - Copyright (212.5712.39)
> - Diagrams (212.5712.39)
> - EditorConfig (212.5712.39)
> - File Watchers (212.5712.39)
> - Grazie (212.5712.39)
> - HTTP Client (212.5712.39)
> - IDE Features Trainer (212.5712.39)
> - IDE Features Trainer: Git Lessons (212.5712.39)
> - IntelliLang (212.5712.39)
> - Machine Learning Code Completion (212.5712.39)
> - Performance Testing (212.5712.39)
> - ReStructuredText (212.5712.39)
> - Shared Project Indexes (212.5712.39)
> - Space (212.5712.39)
> - Task Management (212.5712.39)
> - Terminal (212.5712.39)
> - TextMate Bundles (212.5712.39)
> - Time Tracking (212.5712.39)
### DataLore
> - Plugins TBD

# Setup configuration

- Install 1Password
    - Configure 1Password
- Python installation
    - 3.7
    - 3.10
- Shell
    - Install ZSH
    - Install powerlevel10k and configure
    - SAVE CONFIGURATION FILES
    - Install AWS CLI
    - Copy SSH keys
    - Copy AWS keys
    - Install Hyper on Windows
    - Install that thing similar to powerlevel10k for powershell
    - Install nerdfonts
- IDE
    - Install Pycharm
    - Install VS Code
    - Install Data Grip
    - Configure options for all of them
    - SAVE CONFIGURATION FILES TO Github
- Tools
    - Install Docker
    - Install Kubectl
    - Install kubectx
    - Install k9s
    - Install terraform
    - Install terragrunt
    - Install pg14 client
- Browsers
    - Install Firefox
    - Install Chrome
- Communication
    - Install Discord
    - Install Slack
    - Install Whatsapp
    - Install Messenger
    - 

- Install Icedrive


