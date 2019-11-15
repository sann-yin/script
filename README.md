# script
centos bash界面中文配置

yum -y install kde-l10n-Chinese && yum -y reinstall glibc-common
localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
export LC_ALL=zh_CN.utf8

vim /etc/locale.conf
LC_ALL="zh_CN.UTF-8"

vim /etc/sysconfig/i18n
LANG="zh_CN.UTF-8"
LC_ALL="zh_CN.UTF-8"
source    /etc/sysconfig/i18n

vim /etc/locale.conf
LANG="zh_CN.UTF-8"
source   /etc/locale.conf

vim /etc/environment
LC_ALL=zh_CN.UTF_8
LANG=zh_CN.UTF_8


# 配置好看的bash和alias
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

# User specific environment and startup programs

PATH=$PATH:$HOME/bin

export PATH
# alias
alias l="clear"
alias ll="ls -ahl"

export PATH=$PATH:/usr/local/bin

# enables colorin the terminal bash shell export
export CLICOLOR=1
# sets up the color scheme for list export
export LSCOLORS=gxfxcxdxbxegedabagacad
# sets up git aware prompt
export GITAWAREPROMPT=~/.bash/git-aware-prompt
source "${GITAWAREPROMPT}/main.sh"
# sets up theprompt color (currently a green similar to linux terminal)
#export PS1='\[\033[01;32m\]\u:\[\033[01;36m\]\w\[\033[00m\]\$ '
export PS1="\[\033[01;32m\]\u:\[\033[01;36m\]\w \[$txtred\]\$git_branch \[\033[00m\]\$ "

export GREP_OPTIONS="--color=auto"

# tmux
[ -z "$TMUX" ] && export TERM=xterm-256color

# alias
alias ll='ls -lah'
alias vi='vim'

# ssh agent
# eval $(ssh-agent)
# ssh-add


# Vim
export EDITOR=vim

# bash-completion
#[ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion

# Minikube
KUBECONFIG="${KUBECONFIG:-$HOME/.kube/config}"

alias killgunicorn="ps aux | grep gunicorn | awk '{print $2;}' | xargs kill -9 2>/dev/null"
