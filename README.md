# Dotfiles 

## Usage 

- Clone the repository : 

```shell    
git clone git@github.com:patrickdeville/dotfiles.git ~/dotfiles 
```

- Create a symlink for .zshrc 

```shell
ln -s ~/dotfiles/.zshrc ~/.zshrc
```

## ZSH 

- Install ZSH 

```shell
sudo apt install zsh 
```

- Set ZSH as the default shell 

```shell
chsh -s $(which zsh) 
```

- Install [Oh my zsh](https://ohmyz.sh/)

```shell
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Config

- Install zsh-syntax-highlighting and zsh-autosuggestions plugins 

```shell 
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

- Open up `~/.zshrc` 
```shell
nano ~/.zshrc
```

- Add the desired plugins to the plugins variable 

```
plugins=(git docker zsh-syntax-highlighting zsh-autosuggestions)
```

- Set the [desired theme](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) by editing the `ZSH_THEME` variable. 

## Manage LOG files
### Largest top 10 log files and directories in /var/lib/docker
```shell
sudo find /var/lib/docker/ -name '*.log' -type f -printf '%s %p\n'| sort -nr | head -10
```
### Purge log files in /var/lib/docker
```shell
sudo find /var/lib/docker/ -name '*.log' | sudo awk '{print "echo -n > "$1}' | sudo sh
```

