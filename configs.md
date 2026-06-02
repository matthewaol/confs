.vimrc
```
set number
syntax on
set tabstop=4
set shiftwidth=4
set expandtab
set mouse=a
set showmatch
set relativenumber
```

sway conf
```
# Default config for sway
#
# Copy this to ~/.config/sway/config and edit it to your liking.
#
# Read `man 5 sway` for a complete reference.

exec mako

# for waybar 
exec_always {
    pkill -f xdg-desktop-portal
    sleep 1
    /usr/libexec/xdg-desktop-portal-wlr &
    /usr/libexec/xdg-desktop-portal &
}

### Variables
#
# Logo key. Use Mod1 for Alt.
set $mod Mod4
# Home row direction keys, like vim
set $left h
set $down j
set $up k
set $right l
# Your preferred terminal emulator
set $term foot

# Preferred browser
set $browser brave-browser

# Preferred file manager
set $file-manager thunar

# Your preferred application launcher
set $menu wmenu-run

include /etc/sway/config-vars.d/*

### Output configuration
#
# Default wallpaper (more resolutions are available in /usr/share/backgrounds/sway/)
# This is commented in Debian, because the Sway wallpaper files are in a separate
# package `sway-backgrounds`. Installing this package drops a config file to
# /etc/sway/config.d/
# output * bg /usr/share/backgrounds/sway/Kagutsuchi_Port_PM_16.45.webp fill
#
# Example configuration:
#
#   output HDMI-A-1 resolution 1920x1080 position 1920,0
#
# You can get the names of your outputs by running: swaymsg -t get_outputs

### Idle configuration
#
# Example configuration:
#
#exec swayidle -w \
#          timeout 300 'swaylock -f -c 000000' \
#          timeout 600 'swaymsg "output * power off"' resume 'swaymsg "output * power on"' \
#          before-sleep 'swaylock -f -c 000000'

# This will lock your screen after 300 seconds of inactivity, then turn off
# your displays after another 300 seconds, and turn your screens back on when
# resumed. It will also lock your screen before your computer goes to sleep.

### Input configuration
#
# Example configuration:
#
#   input "2:14:SynPS/2_Synaptics_TouchPad" {
#       dwt enabled
#       tap enabled
#       natural_scroll enabled
#       middle_emulation enabled
#   }
#
# You can get the names of your inputs by running: swaymsg -t get_inputs
# Read `man 5 sway-input` for more information about this section.

### Key bindings
#
# Basics:
#
    # Start a terminal
    bindsym $mod+Return exec $term

    # Start the file manager
    bindsym $mod+Shift+f exec $file-manager 

    # Kill focused window
    bindsym $mod+Shift+q kill

    # Start your launcher
    bindsym $mod+d exec $menu

    # Start your browser
    bindsym $mod+Shift+b exec $browser

    # back and forth between workspaces
    bindsym $mod+tab workspace back_and_forth

    # Lock the machine
    bindsym $mod+Shift+x exec swaylock -f -c 000000

    # Drag floating windows by holding down $mod and left mouse button.
    # Resize them with right mouse button + $mod.
    # Despite the name, also works for non-floating windows.
    # Change normal to inverse to use left mouse button for resizing and right
    # mouse button for dragging.
    floating_modifier $mod normal

    # Reload the configuration file
    bindsym $mod+Shift+c reload

    # Exit sway (logs you out of your Wayland session)
    bindsym $mod+Shift+e exec swaynag -t warning -m 'You pressed the exit shortcut. Do you really want to exit sway? This will end your Wayland session.' -B 'Yes, exit sway' 'swaymsg exit'

    # Toggle waybar

#
# Moving around:
#
    # Move your focus around
    bindsym $mod+$left focus left
    bindsym $mod+$down focus down
    bindsym $mod+$up focus up
    bindsym $mod+$right focus right
    # Or use $mod+[up|down|left|right]
    bindsym $mod+Left focus left
    bindsym $mod+Down focus down
    bindsym $mod+Up focus up
    bindsym $mod+Right focus right

    # Move the focused window with the same, but add Shift
    bindsym $mod+Shift+$left move left
    bindsym $mod+Shift+$down move down
    bindsym $mod+Shift+$up move up
    bindsym $mod+Shift+$right move right
    # Ditto, with arrow keys
    bindsym $mod+Shift+Left move left
    bindsym $mod+Shift+Down move down
    bindsym $mod+Shift+Up move up
    bindsym $mod+Shift+Right move right
#
# Workspaces:
#
    # Switch to workspace
    bindsym $mod+1 workspace number 1
    bindsym $mod+2 workspace number 2
    bindsym $mod+3 workspace number 3
    bindsym $mod+4 workspace number 4
    bindsym $mod+5 workspace number 5
    bindsym $mod+6 workspace number 6
    bindsym $mod+7 workspace number 7
    bindsym $mod+8 workspace number 8
    bindsym $mod+9 workspace number 9
    bindsym $mod+0 workspace number 10
    # Move focused container to workspace
    bindsym $mod+Shift+1 move container to workspace number 1
    bindsym $mod+Shift+2 move container to workspace number 2
    bindsym $mod+Shift+3 move container to workspace number 3
    bindsym $mod+Shift+4 move container to workspace number 4
    bindsym $mod+Shift+5 move container to workspace number 5
    bindsym $mod+Shift+6 move container to workspace number 6
    bindsym $mod+Shift+7 move container to workspace number 7
    bindsym $mod+Shift+8 move container to workspace number 8
    bindsym $mod+Shift+9 move container to workspace number 9
    bindsym $mod+Shift+0 move container to workspace number 10
    # Note: workspaces can have any name you want, not just numbers.
    # We just use 1-10 as the default.
#
# Layout stuff:
#
    # You can "split" the current object of your focus with
    # $mod+b or $mod+v, for horizontal and vertical splits
    # respectively.
    bindsym $mod+b splith
    bindsym $mod+v splitv

    # Switch the current container between different layout styles
    bindsym $mod+s layout stacking
    bindsym $mod+w layout tabbed
    bindsym $mod+e layout toggle split

    # Make the current focus fullscreen
    bindsym $mod+f fullscreen

    # Toggle the current focus between tiling and floating mode
    bindsym $mod+Shift+space floating toggle

    # Swap focus between the tiling area and the floating area
    bindsym $mod+space focus mode_toggle

    # Move focus to the parent container
    bindsym $mod+a focus parent
#
# Scratchpad:
#
    # Sway has a "scratchpad", which is a bag of holding for windows.
    # You can send windows there and get them back later.

    # Move the currently focused window to the scratchpad
    bindsym $mod+Shift+minus move scratchpad

    # Show the next scratchpad window or hide the focused scratchpad window.
    # If there are multiple scratchpad windows, this command cycles through them.
    bindsym $mod+minus scratchpad show
#
# Resizing containers:
#
mode "resize" {
    # left will shrink the containers width
    # right will grow the containers width
    # up will shrink the containers height
    # down will grow the containers height
    bindsym $left resize shrink width 10px
    bindsym $down resize grow height 10px
    bindsym $up resize shrink height 10px
    bindsym $right resize grow width 10px

    # Ditto, with arrow keys
    bindsym Left resize shrink width 10px
    bindsym Down resize grow height 10px
    bindsym Up resize shrink height 10px
    bindsym Right resize grow width 10px

    # Return to default mode
    bindsym Return mode "default"
    bindsym Escape mode "default" }
    bindsym $mod+r mode "resize"
#
# Utilities:
#
    # Special keys to adjust volume via wpctl (Pipewire)
    # Mute / unmute
    bindsym --locked XF86AudioRaiseVolume exec ~/.config/sway/scripts/volume.sh up
    bindsym --locked XF86AudioLowerVolume exec ~/.config/sway/scripts/volume.sh down
    bindsym --locked XF86AudioMute exec ~/.config/sway/scripts/volume.sh mute


    # Special keys to adjust brightness via brightnessctl
    bindsym --locked XF86MonBrightnessDown exec brightnessctl set 5%-
    bindsym --locked XF86MonBrightnessUp exec brightnessctl set 5%+

    # Special key to take a screenshot with grim
    # bindsym Print exec grim
    bindsym Print exec grimshot savecopy area


# Status Bar:

# Read `man 5 sway-bar` for more information about this section.
#bar {
    #position top

    # When the status_command prints a new line to stdout, swaybar updates.
    # The default just shows the current date and time.
    #status_command while date +'%Y-%m-%d %X'; do sleep 1; done

    #colors {
     #   statusline #ffffff
      #  background #323232
       # inactive_workspace #32323200 #32323200 #5c5c5c
    #}
#}

include /etc/sway/config.d/*

# switching out caps lock
exec_always --no-startup-id /usr/bin/setxkbmap -option "ctrl:nocaps"

# touchpad
input type:touchpad { 
	tap enabled 
	natural_scroll enabled
	pointer_accel 0.3
}

input type:keyboard { 
	xkb_options ctrl:nocaps
}

# night shift
exec_always wlsunset -t 2499 -T 2500 

# dark mode
exec_always gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
exec_always gsettings set org.gnome.desktop.interface gtk-theme 'Adwaita-dark'<D-r><D-r>

# waybar
bar swaybar_command waybar

# window styling
default_border pixel 2
default_floating_border normal

# font
font pango:Jetbrains Mono 9

# smart behavior
smart_borders on
smart_gaps on
hide_edge_borders smart
gaps outer 0
gaps inner 0

# colors
client.unfocused       #3b4252 #3b4252 #a3a3a3 #3b4252 #3b4252
client.focused         #683D8A #A25ED6 #1e1e1e #A25ED6 #A25ED6 
# scaling
exec_always gsettings set org.gnome.desktop.interface text-scaling-factor 1.3

# waybar visibility
bindsym $mod+backslash exec pkill -USR1 waybar
```

.bashrc
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# Fast exit for non-interactive shells
[[ $- != *i* ]] && return

export PATH="$HOME/.local/bin:/usr/local/bin:/usr/bin:/bin"

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
#[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=no
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;34m\][\u \[\033[01;33m\]\w\[\033[01;34m\]]\[\033[00m\] $ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
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
fi

# colored GCC warnings and errors
export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# more aliases
alias gohome='ssh matt@home'
alias gosleep='systemctl suspend && echo "Zzz.."'


# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

# ---- Poetry ---- 
export PATH="$HOME/.local/bin:$PATH"

complete -C /usr/bin/terraform terraform

# Homebrew (lazy)
brew() {
  unset -f brew
  eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
  brew "$@"
}

# nvm (lazy)
nvm() {
  unset -f nvm
  export NVM_DIR="$HOME/.nvm"
  source "$NVM_DIR/nvm.sh"
  nvm "$@"
}

# pyenv (lazy)
pyenv() {
  unset -f pyenv
  export PYENV_ROOT="$HOME/.pyenv"
  export PATH="$PYENV_ROOT/bin:$PATH"
  eval "$(pyenv init - bash)"
  pyenv "$@"
}

# cargo 
cargo() {
  unset -f cargo
  source "$HOME/.cargo/env"
  cargo "$@"
}

# colored ssh terminal
alias ssh='TERM=xterm-256color ssh'

# for java apps
export _JAVA_AWT_WM_NONREPARENTING=1

. "$HOME/.cargo/env
```

foot.ini
```
# -*- conf -*-

# shell=$SHELL (if set, otherwise user's default shell from /etc/passwd)
# term=xterm-256color 
# login-shell=no

# app-id=foot # globally set wayland app-id. Default values are "foot" and "footclient" for desktop and server mode
# title=foot
# locked-title=no

font=monospace:size=22
# font-bold=<bold variant of regular font>
# font-italic=<italic variant of regular font>
# font-bold-italic=<bold+italic variant of regular font>
# font-size-adjustment=0.5
# line-height=<font metrics>
# letter-spacing=0
# horizontal-letter-offset=0
# vertical-letter-offset=0
# underline-offset=<font metrics>
# underline-thickness=<font underline thickness>
# strikeout-thickness=<font strikeout thickness>
# box-drawings-uses-font-glyphs=no
# dpi-aware=no

# initial-window-size-pixels=700x500  # Or,
# initial-window-size-chars=<COLSxROWS>
# initial-window-mode=windowed
pad=5x5                             # optionally append 'center'
# resize-by-cells=yes
# resize-keep-grid=yes
# resize-delay-ms=100

# bold-text-in-bright=no
# word-delimiters=,│`|:"'()[]{}<>
# selection-target=primary
# workers=<number of logical CPUs>
# utmp-helper=/usr/lib/utempter/utempter  # When utmp backend is ‘libutempter’ (Linux)
# utmp-helper=/usr/libexec/ulog-helper    # When utmp backend is ‘ulog’ (FreeBSD)

[environment]
# name=value

[security]
# osc52=enabled  # disabled|copy-enabled|paste-enabled|enabled

[bell]
# system=yes
# urgent=no
# notify=no
# visual=no
# command=
# command-focused=no

[desktop-notifications]
# command=notify-send --wait --app-name ${app-id} --icon ${app-id} --category ${category} --urgency ${urgency} --expire-time ${expire-time} --hint STRING:image-path:${icon} --hint BOOLEAN:suppress-sound:${muted} --hint STRING:sound-name:${sound-name} --replace-id ${replace-id} ${action-argument} --print-id -- ${title} ${body}
# command-action-argument=--action ${action-name}=${action-label}
# close=""
# inhibit-when-focused=yes


[scrollback]
# lines=1000
# multiplier=3.0
# indicator-position=relative
# indicator-format=""

[url]
# launch=xdg-open ${url}
# label-letters=sadfjklewcmpgh
# osc8-underline=url-mode
# regex=(([a-z][[:alnum:]-]+:(/{1,3}|[a-z0-9%])|www[:digit:]{0,3}[.])([^[:space:](){}<>]+|\(([^[:space:](){}<>]+|(\([^[:space:](){}<>]+\)))*\)|\[([^]\[[:space:](){}<>]+|(\[[^]\[[:space:](){}<>]+\]))*\])+(\(([^[:space:](){}<>]+|(\([^[:space:](){}<>]+\)))*\)|\[([^]\[[:space:](){}<>]+|(\[[^]\[[:space:](){}<>]+\]))*\]|[^]\[[:space:]`!(){};:'".,<>?«»“”‘’]))

# You can define your own regex's, by adding a section called
# 'regex:<ID>' with a 'regex' and 'launch' key. These can then be tied
# to a key-binding. See foot.ini(5) for details

# [regex:your-fancy-name]
# regex=<a POSIX-Extended Regular Expression>
# launch=<path to script or application> ${match}
#
# [key-bindings]
# regex-launch=[your-fancy-name] Control+Shift+q
# regex-copy=[your-fancy-name] Control+Alt+Shift+q

[cursor]
# style=block
# color=<inverse foreground/background>
# blink=no
# blink-rate=500
# beam-thickness=1.5
# underline-thickness=<font underline thickness>

[mouse]
# hide-when-typing=no
# alternate-scroll-mode=yes

[touch]
# long-press-delay=400

[colors]
# alpha=1.0
# background=242424
# foreground=ffffff
# flash=7f7f00
# flash-alpha=0.5

## Normal/regular colors (color palette 0-7)
# regular0=242424  # black
# regular1=f62b5a  # red
# regular2=47b413  # green
# regular3=e3c401  # yellow
# regular4=24acd4  # blue
# regular5=f2affd  # magenta
# regular6=13c299  # cyan
# regular7=e6e6e6  # white

## Bright colors (color palette 8-15)
# bright0=616161   # bright black
# bright1=ff4d51   # bright red
# bright2=35d450   # bright green
# bright3=e9e836   # bright yellow
# bright4=5dc5f8   # bright blue
# bright5=feabf2   # bright magenta
# bright6=24dfc4   # bright cyan
# bright7=ffffff   # bright white

## dimmed colors (see foot.ini(5) man page)
# dim0=<not set>
# ...
# dim7=<not-set>

## The remaining 256-color palette
# 16 = <256-color palette #16>
# ...
# 255 = <256-color palette #255>

## Sixel colors
# sixel0 =  000000
# sixel1 =  3333cc
# sixel2 =  cc2121
# sixel3 =  33cc33
# sixel4 =  cc33cc
# sixel5 =  33cccc
# sixel6 =  cccc33
# sixel7 =  878787
# sixel8 =  424242
# sixel9 =  545499
# sixel10 = 994242
# sixel11 = 549954
# sixel12 = 995499
# sixel13 = 549999
# sixel14 = 999954
# sixel15 = cccccc

## Misc colors
# selection-foreground=<inverse foreground/background>
# selection-background=<inverse foreground/background>
# jump-labels=<regular0> <regular3>          # black-on-yellow
# scrollback-indicator=<regular0> <bright4>  # black-on-bright-blue
# search-box-no-match=<regular0> <regular1>  # black-on-red
# search-box-match=<regular0> <regular3>     # black-on-yellow
# urls=<regular3>

[colors]

# Solarized Light

# Core background / foreground
background=fdf6e3
foreground=657b83

# Optional UI colors
selection-background=eee8d5
selection-foreground=586e75

# Normal ANSI colors
regular0=073642    # black (base02)
regular1=dc322f    # red
regular2=859900    # green
regular3=b58900    # yellow
regular4=268bd2    # blue
regular5=d33682    # magenta
regular6=2aa198    # cyan
regular7=eee8d5    # white (base2)

# Bright ANSI colors
bright0=586e75     # bright black (base01)
bright1=cb4b16     # bright red (orange)
bright2=859900     # bright green
bright3=b58900     # bright yellow
bright4=6c71c4     # bright blue (violet)
bright5=d33682     # bright magenta
bright6=93a1a1     # bright cyan (base1)
bright7=fdf6e3     # bright white (base3)

[csd]
# preferred=server
# size=26
# font=<primary font>
# color=<foreground color>
# hide-when-maximized=no
# double-click-to-maximize=yes
# border-width=0
# border-color=<csd.color>
# button-width=26
# button-color=<background color>
# button-minimize-color=<regular4>
# button-maximize-color=<regular2>
# button-close-color=<regular1>

[key-bindings]
# scrollback-up-page=Shift+Page_Up Shift+KP_Page_Up
# scrollback-up-half-page=none
# scrollback-up-line=none
# scrollback-down-page=Shift+Page_Down Shift+KP_Page_Down
# scrollback-down-half-page=none
# scrollback-down-line=none
# scrollback-home=none
# scrollback-end=none
# clipboard-copy=Control+Shift+c XF86Copy
# clipboard-paste=Control+Shift+v XF86Paste
# primary-paste=Shift+Insert
# search-start=Control+Shift+r
# font-increase=Control+plus Control+equal Control+KP_Add
# font-decrease=Control+minus Control+KP_Subtract
# font-reset=Control+0 Control+KP_0
# spawn-terminal=Control+Shift+n
# minimize=none
# maximize=none
# fullscreen=none
# pipe-visible=[sh -c "xurls | fuzzel | xargs -r firefox"] none
# pipe-scrollback=[sh -c "xurls | fuzzel | xargs -r firefox"] none
# pipe-selected=[xargs -r firefox] none
# pipe-command-output=[wl-copy] none # Copy last command's output to the clipboard
# show-urls-launch=Control+Shift+o
# show-urls-copy=none
# show-urls-persistent=none
# prompt-prev=Control+Shift+z
# prompt-next=Control+Shift+x
# unicode-input=Control+Shift+u
# noop=none
# quit=none

[search-bindings]
# cancel=Control+g Control+c Escape
# commit=Return KP_Enter
# find-prev=Control+r
# find-next=Control+s
# cursor-left=Left Control+b
# cursor-left-word=Control+Left Mod1+b
# cursor-right=Right Control+f
# cursor-right-word=Control+Right Mod1+f
# cursor-home=Home Control+a
# cursor-end=End Control+e
# delete-prev=BackSpace
# delete-prev-word=Mod1+BackSpace Control+BackSpace
# delete-next=Delete
# delete-next-word=Mod1+d Control+Delete
# delete-to-start=Control+u
# delete-to-end=Control+k
# extend-char=Shift+Right
# extend-to-word-boundary=Control+w Control+Shift+Right
# extend-to-next-whitespace=Control+Shift+w
# extend-line-down=Shift+Down
# extend-backward-char=Shift+Left
# extend-backward-to-word-boundary=Control+Shift+Left
# extend-backward-to-next-whitespace=none
# extend-line-up=Shift+Up
# clipboard-paste=Control+v Control+Shift+v Control+y XF86Paste
# primary-paste=Shift+Insert
# unicode-input=none
# scrollback-up-page=Shift+Page_Up Shift+KP_Page_Up
# scrollback-up-half-page=none
# scrollback-up-line=none
# scrollback-down-page=Shift+Page_Down Shift+KP_Page_Down
# scrollback-down-half-page=none
# scrollback-down-line=none
# scrollback-home=none
# scrollback-end=none

[url-bindings]
# cancel=Control+g Control+c Control+d Escape
# toggle-url-visible=t

[text-bindings]
# \x03=Mod4+c  # Map Super+c -> Ctrl+c

[mouse-bindings]
# scrollback-up-mouse=BTN_WHEEL_BACK
# scrollback-down-mouse=BTN_WHEEL_FORWARD
# font-increase=Control+BTN_WHEEL_BACK
# font-decrease=Control+BTN_WHEEL_FORWARD
# selection-override-modifiers=Shift
# primary-paste=BTN_MIDDLE
# select-begin=BTN_LEFT
# select-begin-block=Control+BTN_LEFT
# select-extend=BTN_RIGHT
# select-extend-character-wise=Control+BTN_RIGHT
# select-word=BTN_LEFT-2
# select-word-whitespace=Control+BTN_LEFT-2
# select-quote = BTN_LEFT-3
# select-row=BTN_LEFT-4

# vim: ft=dosini
```

volume.sh
```
#!/bin/sh

STEP=5%
ACTION="$1"

case "$ACTION" in
  up)
    wpctl set-volume @DEFAULT_SINK@ ${STEP}+ ;;
  down)
    wpctl set-volume @DEFAULT_SINK@ ${STEP}- ;;
  mute)
    wpctl set-volume @DEFAULT_SINK@ 0 ;;
esac

# Show notification bar
VOL=$(wpctl get-volume @DEFAULT_SINK@ | awk '{print int($2*100)}')

notify-send \
  -h string:x-dunst-stack-tag:volume \
  -h int:value:$VOL \
  -u low \
  " "
```

