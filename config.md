# My configuration for fedora

## dnf config
### Set 'Yes' as  default install choice
In `/etc/dnf/dnf.conf` add:
```
defaultyes=True
```

### Enable parallel download
In `/etc/dnf/dnf.conf` add:
```
max_parallel_downloads=10 
```

### Enable fastest mirrors
In `/etc/dnf/dnf.conf` add:
```
fastestmirror=True
```

## Terminal configuration
### Terminal emulator
```
sudo dnf install tilix-nautilus-x.x.x
```

### Shell
Install Fish and set it as default shell
```bash
sudo dnf install fish
chsh -s /usr/bin/fish
```

### Shell Prompt
#### Install starship
No need to install a font with ligature as specified in documentation
```bash
sudo dnf install cargo
sudo dnf install g++
sudo dnf install cmake
cargo install starship --locked
fish_add_path /home/max/.cargo/bin/
```

#### Source starship
In `~/.config/fish/config.fish` add:
```bash
starship init fish | source
```

#### Configure starship
Copy starship.toml at `~/.config/starship.toml`

### Fuzzy search
#### Install
```
sudo dnf install fzf
```
#### Integration with fish
```bash
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
sudo dnf install bat
sudo dnf install fd-find
fisher install PatrickF1/fzf.fish
```
/!\ Not fully working

### Git and Github
#### SSH key for github
[How to generate the key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

```bash
# create the key and put it the following path: ~/.ssh/github_key
ssh-keygen -t ed25519 -C "your_email@example.com"
# ssh-agent is started by default on fedora 40
# Add the key to the ssh-agent
ssh-add ~/.ssh/github_key
# Add the public key to github
# Try the connection to github
ssh -T git@github.com
```
#### config
```bash
# set user name and mail
git config --global user.name "JackHerRrer"
git config --global user.mail "my@mail.com"
```

### Bat: colored cat

### eza : ls replacement
```
sudo dnf install eza
```

### Abreviations

Add in `~/.config/fish/config.fish` the following abbreviations
```bash
# abbreviations
abbr --add cat batcat --style plain --paging never
abbr --add ip ip -c
abbr --add ip6 ip -c -6
abbr --add grep grep --color=auto
abbr --add fgrep fgrep --color=auto
abbr --add egrep egrep --color=auto
abbr --add ll eza -alh --git --icons=always 
abbr --add l eza --icons=always 
abbr --add install sudo dnf install
```

Then source it 
```bash
source ~/.config/fish/config.fish
```

## Firefox
### Plugins
- ublock origin
- Google Search Maps Button

## VsCode
https://code.visualstudio.com/docs/setup/linux

## Gnome
### Plugins
Install the `extension manager`

Add the following plugins:
```
- clipboard indicator
- Tiling assistant
- Dash to panel
```

#### Dash to panel configuration 
position
    Panel on the left
    bouton activités caché

style
    style de l'indicateur d'activité (application active) -> Traits 
        surligner l'application active
        opacité du surlignement -> 40
    style de l'indicateur d'activité (application inaactive) -> traits 
    remplacer l'opacité du panneaur 
    opacité du fond du panneau -> 60

comportement
    afficher les apercu de fenêtre lors du survol
        taille des prévisualisation de fenêtre -> 500
    Isoler les espaces de travail


## To be explored
- firaCode
- pager : most
- nvim
- notifications
- alias g git
- suggest aliases
- git config aliases
- https://github.com/jorgebucaran/awsm.fish?tab=readme-ov-file#plugins
- ranger command
- tldr command
- Nautilise extensions


