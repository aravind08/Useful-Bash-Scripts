# Useful-Bash-Scripts

### Short-hands

    alias ..='cd ../'                           # Go back 1 directory level
    alias ...='cd ../../'                       # Go back 2 directory levels
    alias .3='cd ../../../'                     # Go back 3 directory levels    
    alias .4='cd ../../../../'                  # Go back 4 directory levels
    alias .5='cd ../../../../../'               # Go back 5 directory levels
    alias .6='cd ../../../../../../'            # Go back 6 directory levels
    alias f='open -a Finder ./'                 # f:  Opens current directory in MacOS Finder
    alias path='echo -e ${PATH//:/\\n}'         # path:  Echo all executable Paths
    alias c='clear'                             # Clear terminal


### Show hidden files (Mac OS)
    alias show_hidden_file='defaults write com.apple.finder AppleShowAllFiles -bool TRUE && killall Finder'
    alias show_hidden_file='defaults write com.apple.finder AppleShowAllFiles -bool FALSE && killall Finder'


### Get external IP
    alias my_ip='curl ipecho.net/plain; echo'


### Git commands
    alias gf='git fetch'                        # Git pull branches 
    alias gs='git status'                       # Git check status
    alias gd='git diff'                         # Git diff
    alias gb='git branch'                       # Git branch
    alias gc='git commit -m $1'                 # Git commit with message
    alias ga='git add .'                        # Git safe-add all
    alias gg='git push'                         # Git push all branches
    alias go='git checkout $1'                  # Git checkout to existing branch


### Git current branch in prompt.
    parse_git_branch() {
        git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
    }
    export PS1="\u@\h \W\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
