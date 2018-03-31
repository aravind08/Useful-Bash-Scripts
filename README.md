# Useful-Bash-Scripts

### Short-hands

    alias ..='cd ../'                           # Go back 1 directory level
    alias ...='cd ../../'                       # Go back 2 directory levels
    alias ....='cd ../../../'                   # Go back 3 directory levels    
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
    alias gg='git pull'                         # Git pull & merge all branches 
    alias gs='git status'                       # Git check status
    alias gd='git diff'                         # Git diff
    alias gb='git branch'                       # Git branch
    alias gc='git commit -m $1'                 # Git commit with message
    alias ga='git add .'                        # Git safe-add all
    alias gp='git push'                         # Git push all branches
    # Git print all files in conflicted state
    alias gconf='git ls-files -u | awk '{print $4}' | sort -u'
    # Git delete the local branches that have been merged into the HEAD
    alias gdel='git branch -d $(git branch --merged | grep -v '^*' | tr -d '\n')'


### Git current branch in prompt.
    parse_git_branch() {
        git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
    }
    export PS1="\u@\h \W\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
