# What it this?
Some common terminal setup I use on my devices


## ~/.gitconfig

### How to modify
1. `nano ~/.gitconfig`
2. Add the contents into the file.

### Aliases
```
[alias]
        l = log --date=short --pretty=format:'%C(bold blue)%cd %Creset%C(red)%h%Creset%C(auto)%d %Creset%C(normal)%s %Creset%C(bold blue)(%Creset%C(yellow)%an %Creset%C(bold blue)%cr)%Creset' --color --graph --decorate
        l-notes = log --date=short --pretty=format:'%C(normal)%s %C(red)%cd %Creset' --color --graph --decorate
        l-mine = log --oneline --all --author-date-order --committer 'Chris Skoblenick' --date short --pretty=format:'%C(bold blue)%ad%Creset %C(blue)%an%Creset %C(normal)%s%Creset' --author 'Chris Skoblenick'
```
