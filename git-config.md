# .gitconfig
Here are the aliases I use:
```
[alias]
        lad = log --date=short --pretty=format:'%C(bold blue)%cd %Creset%C(red)%h%Creset%C(auto)%d %Creset%C(normal)%s %Creset%C(bold blue)(%Creset%C(yellow)%an %Creset%C(bold blue)%cr)%Creset' --color --graph --decorate --all --author-date-order
        lg = log --graph --pretty=format:'%Cred%h%Creset - %s %Cgreen(%cr) %C(bold blue)<%an>%C(yellow)%d%Creset' --abbrev-commit --date=relative
        l = log --date=short --pretty=format:'%C(bold blue)%cd %Creset%C(red)%h%Creset%C(auto)%d %Creset%C(normal)%s %Creset%C(bold blue)(%Creset%C(yellow)%an %Creset%C(bold blue)%cr)%Creset' --color --graph --decorate
        lr = log --date=short --pretty=format:'%C(normal)%s %C(red)%cd %Creset' --color --graph --decorate
        lts = log --oneline --all --author-date-order --committer 'Chris Skoblenick' --date short --pretty=format:'%C(bold blue)%ad%Creset %C(blue)%an%Creset %C(normal)%s%Creset' --author 'Chris Skoblenick'
```
