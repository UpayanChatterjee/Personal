In this document I will be making a comprehensive guide to my gnu/linux setup, mostly for my personal future reference but also for anyone else who might be interested :)

## Change default shell to zsh
While the default shell in most cases - bash - is pretty good, I prefer the zsh mostly because of its support of plugins (auto-suggest and syntax-highlighting).
```
sudo pacman -S zsh
```
After this I like to install `oh-my-zsh` framework:
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" # install oh-my-zsh for some cool themes
```
I like to use the `powerlevel10k` theme for which some fonts are prerequisite:
- [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
- [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
- [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
- [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)
Now go to the settings of the terminal application and force it to use the MesloLGS font(otherwise the `powerlevel10k` theme has trouble with the symbols and unicode(?) characters).
Then,
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
and set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.

Run `exec zsh` and proceed with the rest of the customisation in `powerlevel10k`.

-   autosuggesions plugin
    
    `git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions`


-   zsh-syntax-highlighting plugin
    
    `git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting`


-   zsh-fast-syntax-highlighting plugin
    
    `git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting`


-   zsh-autocomplete plugin
    
    `git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete`

Now add the plugins to your `.zshrc` :
`plugins=(git zsh-autosuggestions zsh-syntax-highlighting fast-syntax-highlighting zsh-autocomplete)`

I like to use  `alt + enter` to accept the autosuggestion. To do that, add  `bindkey '^[ ' autosuggest-accept` to your `.zshrc`.
*Warning:* Make sure you disable any `alt + enter` shortcut that might be set by default by your desktop environment (In KDE Plasma, you can find it in Global Shortcut section in settings, in GNOME you can find it in Keyboard section in settings, fiddle around with other desktop environment to find settings to disable the shortcut :)

## Installing nix package manager
Although I have only recently learnt about the nix package manager, I was quickly drawn to it because of its underlying philosophy and ease of use. 

