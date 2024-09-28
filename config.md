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

## Font with ligatures
https://www.nerdfonts.com/font-downloads
FiraCode Nerd Font, regular
(Not used)

## gnome plugin
TODO

## Terminal configuration
### Terminal emulator
tilix

### Shell
Install Fish and set it as default shell
```
sudo dnf install fish
chsh -s /usr/bin/fish
```

### Shell Prompt
#### Install starship
```
sudo dnf install cargo
sudo dnf install g++
sudo dnf install cmake
cargo install starship --locked
fish_add_path /home/max/.cargo/bin/
```

#### Source starship
In `~/.config/fish/config.fish` add:
```
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
```

```

### SSH key
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

TODO ssh-agent

### Bat: colored cat

### colored IP


## Firefox
### Plugins
- ublock origin
- Google Search Maps Button

## VsCode
https://code.visualstudio.com/docs/setup/linux

## To be explored
- firaCode



