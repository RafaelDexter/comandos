# .bashrc

```
export EDITOR=/usr/bin/vim

# Colors
C1="\[\033[0;30m\]"  # Black
C2="\[\033[1;30m\]"  # Dark Gray
C3="\[\033[0;31m\]"  # Red
C4="\[\033[1;31m\]"  # Light Red
C5="\[\033[0;32m\]"  # Green
C6="\[\033[1;32m\]"  # Light Green
C7="\[\033[0;33m\]"  # Brown
C8="\[\033[1;33m\]"  # Yellow
C9="\[\033[0;34m\]"  # Blue
C10="\[\033[1;34m\]" # Light Blue
C11="\[\033[0;35m\]" # Purple
C12="\[\033[1;35m\]" # Light Purple
C13="\[\033[0;36m\]" # Cyan
C14="\[\033[1;36m\]" # Light Cyan
C15="\[\033[0;37m\]" # Light Gray
C16="\[\033[1;37m\]" # White
C17="\[\033[0;41m\]" # Teste
P="\[\033[0m\]" # Neutral

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
# PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
  PS1="$C5 Dexter $C8[$C10\$PWD$C8]\\$ $P"
    ;;
*)
    ;;
esac


# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
  test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
  alias ls='ls --color=auto'
  alias dir='dir --color=auto'
  alias vdir='vdir --color=auto'
  alias grep='grep --color=auto'
  alias fgrep='fgrep --color=auto'
  alias egrep='egrep --color=auto'
  alias rm='rm -vi'
  alias cp='cp -ivb'
  alias mv='mv -iv'
  alias l='ls -alrts --color=auto' 
  alias ll='ls -l'
  alias la='ls -A'
fi
```
