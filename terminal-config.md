# What it this?
Some common terminal setup I use on my devices


## ~/.gitconfig
Defines some git aliases.

### Contents:
```
[alias]
        l = log --date=short --pretty=format:'%C(bold blue)%cd %Creset%C(red)%h%Creset%C(auto)%d %Creset%C(normal)%s %Creset%C(bold blue)(%Creset%C(yellow)%an %Creset%C(bold blue)%cr)%Creset' --color --graph --decorate
        l-notes = log --date=short --pretty=format:'%C(normal)%s %C(red)%cd %Creset' --color --graph --decorate
        l-mine = log --oneline --all --author-date-order --committer 'Chris Skoblenick' --date short --pretty=format:'%C(bold blue)%ad%Creset %C(blue)%an%Creset %C(normal)%s%Creset' --author 'Chris Skoblenick'
```

## ~/.zshrc
Configures z shell

### Show git details:
```
# Show git information
# Reference: https://www.themoderncoder.com/add-git-branch-information-to-your-zsh-prompt/

# Load version control information
autoload -Uz vcs_info
precmd() { vcs_info }

# Include git info
# %b is the name of the current branch
zstyle ':vcs_info:git:*' formats '(%b)'

# Modify the prompt to include branch information
# Reference: https://www.makeuseof.com/customize-zsh-prompt-macos-terminal/
# NOTES:
# - %#   -->  show # if the shell is running with root (administrator) privileges, or % if it doesn’t.
# - %F{colour_name} ... %f  --> change the color between %F and %f. Supports black, white, yellow, green, red, blue, cyan, magenta. %F is foreground
# - %B ... %b  --> bold the contents
# - %S ... %s  --> highlight (background) colour

# Add the git details to the prompt
setopt PROMPT_SUBST
PROMPT='%B%F{cyan}${PWD/#$HOME/~}%f%b %F{red}${vcs_info_msg_0_}%f %# '
```
## Turn off mouse acceleration in OSX
```
defaults write .GlobalPreferences com.apple.mouse.scaling -1
```
