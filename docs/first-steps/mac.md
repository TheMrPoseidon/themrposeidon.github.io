---
icon: lucide/apple
title: ... on Mac
---

# First Steps on Mac
You've got a new mac or installed a fresh OS on it. :thumbsup:

## Finder
There are several things I like configured in the `Finder`:

- I want to see all objects on my desktop including interal drives and conntected servers
- Opening a new window should show my home folder 
- The sidebar should show my computer with all its drives, disks and servers (not scriptable)
- Name-Suffix should be shown
- Sorting should clip folders above files
- Objects should be deleted after 30 days moving to the trash

And because doing this manual every time here is command line settings for all of that:

```bash
# Desktop: Show all objects (internal and external drives, servers)
defaults write com.apple.finder ShowHardDrivesOnDesktop -bool true
defaults write com.apple.finder ShowMountedServersOnDesktop -bool true

# Finder: New window opens in Home folder
defaults write com.apple.finder NewWindowTarget -string "PfHm"
defaults write com.apple.finder NewWindowTargetPath -string "file://${HOME}/"

# Extensions: Show file extensions
defaults write com.apple.finder ShowAllNameExtensions -bool true

# Sorting: Show folders above files
defaults write com.apple.finder _FXSortFoldersFirst -bool true

# Trash: Delete items after 30 days
defaults write com.apple.finder FXRemoveOldTrashItems -bool true

killall Finder
```

## Terminal
### Brew
The holy grail of package management on mac.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Oh my zsh
Thanks to one of my collegues here for showing it to me. Since I've seen I don't want to miss it. [Oh My ZSH](https://ohmyz.sh/) is an extension to the zsh interpreter which add some fancy support. On top of that I've added powerlevel10k, a flavour and theme that adds some fancy color to it.

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
curl --output MesloLGS_NF_Regular.ttf https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Regular.ttf
curl --output MesloLGS_NF_Bold.ttf https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Bold.ttf
curl --output MesloLGS_NF_Italic.ttf https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Italic.ttf
curl --output MesloLGS_NF_Bold_Italic.ttf https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/MesloLGS%20NF%20Bold%20Italic.ttf
open *.ttf &
brew install powerlevel10k
```

After installing you should set your font `MesloLGS NF` inside your Terminal. Then: 

```bash
p10k configure
```

### Additional Command Line Tools
I want different terminal tools to be present on my my here is the current list of them and what they do.

- uv: Simplifing a virtual python environment by creating a distinct folder structure, managing a list of installed dependencies (compareable to a requirements.txt), allow for different python versions
- kubectl: Managing kubernetes cluster
- python: I want the latest python interpreter present on my mac

```bash
brew install uv kubectl python
```

## Apps
I want different apps to be present on my mac. Here is the current list of them:

- Visual Studio Code: Editor for source code, with integrated Git, expandable with extensions
- Firefox: Privacy Oriented Browser
- Joplin: Tool to take notes in Markdown
- KeepassXC: Password Manager
- Spotifiy: Musik Streaming
- drawio: Tool to create diagrams for different topics
- Affinity: IMHO the perfect replacement for the Adobe suite (Photoshop, Indesign and Illustrator)
- Virtualbuddy: A simple way to have a VM for Linux or macOS
- Podman Desktop: A container engine

```bash
# Must
brew install visual-studio-code firefox joplin keepassxc spotify

# Optional
brew install drawio affinity virtualbuddy podman-desktop
```