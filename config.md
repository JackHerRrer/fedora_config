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
```bash
sudo dnf install tilix-nautilus-x.x.x
```

TODO Add configuration

### Fish Shell
#### Installation
Install Fish and set it as default shell
```bash
sudo dnf install fish
chsh -s /usr/bin/fish
```

#### Extension
Install extension manager
```bash
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
```

Install the extensions 
```bash
# Add colorization on man pages
fisher install decors/fish-colored-man
```

### Shell Prompt
#### Install starship
No need to install a font with ligature as specified in documentation
```bash
# install dependencies to build it
sudo dnf install cargo g++ cmake
# build/install starship
cargo install starship --locked
# Add binaries build with cargo in path
fish_add_path /home/max/.cargo/bin/
```

#### Source starship
In `~/.config/fish/config.fish` add:
```bash
# Use starship as prompt
starship init fish | source
```

#### Configure starship
Copy starship.toml at `~/.config/starship.toml`

### Fuzzy search
#### Install
```bash
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
# set user name and mail and default editor 
git config --global user.name "JackHerRrer"
git config --global user.email "my@mail.com"
git config --global core.editor 'code --wait'
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'
```

### Bat: colored cat
```
sudo dnf install bat 
```

### eza : ls replacement
```
sudo dnf install eza
```

### tldr: man replacement
```
sudo dnf install tldr
```

### zoxide: cd replacement
```
sudo dnf install zoxide
```

Add in `~/.config/fish/config.fish` the following abbreviations
```bash
# Add zoxide hotkeys 
zoxide init fish | source
```

### ranger
```
sudo dnf install ranger
```

TODO config

### Abreviations

Add in `~/.config/fish/config.fish` the following abbreviations
```bash
# abbreviations
abbr --add cat bat --style plain --paging never
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


## Bottles 
Its a wine GUI

## Gnome

### Add minimize / maximize button
```bash
gsettings set org.gnome.desktop.wm.preferences button-layout ":minimize,maximize,close"
```
### Plugins
Install the `extension manager`

Add the following plugins:
```
- clipboard indicator
- Tiling assistant
- Dash to panel
```

### Hotkeys
Setting -> keyboards -> customize hotkeys

```
navigation -> go to workspace on the right: ctrl + super + right
navigation -> go to workspace on the left: ctrl + super + left
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

## Wallpaper
https://backiee.com/static/wallpapers/7680x4320/219980.jpg

## Torrent 
- install qbitorrent
- install qbitorrent search plugins [explanations here](https://github.com/qbittorrent/search-plugins/wiki/Install-search-plugins) 
    - enable search view: `view -> search engine`  
    - Check updates in the search plugins (this enable default search engines)

- Add Jackett to have a way better search [explanations here](https://github.com/qbittorrent/search-plugins/wiki/How-to-configure-Jackett-plugin)
    - install jackett
        ```bash
        sudo dnf install dotnet

        # install jackett
        # from https://github.com/Jackett/Jackett#installation-on-linux-amdx64
        cd /opt && f=Jackett.Binaries.LinuxAMDx64.tar.gz && sudo wget -Nc https://github.com/Jackett/Jackett/releases/latest/download/"$f" && sudo tar -xzf "$f" && sudo rm -f "$f" && cd Jackett* && sudo chown $(whoami):$(id -g) -R "/opt/Jackett" && sudo ./install_service_systemd.sh && systemctl status jackett.service && cd - && echo -e "\nVisit http://127.0.0.1:9117"
        ```
    - Open the local server : http://127.0.0.1:9117
    - Add indexers
    - copy the jackett's api key
    - add the api key of jackett in qbitorrent conf `~/.var/app/org.qbittorrent.qBittorrent/data/qBittorrent/nova3/engines/jackett.json`


## To be explored
- pager : most/bat
- nvim
- notifications
- alias g git
- suggest aliases
- git config aliases
- https://github.com/jorgebucaran/awsm.fish?tab=readme-ov-file#plugins
- Nautilis extensions
- fd https://github.com/sharkdp/fd?tab=readme-ov-file
