# Tmux Cheat Sheet

```
All commands start with :, use Ctrl-b followed by :
In tmux, press Ctrl-b then other key.
```

## Setting
.tmux.conf
```
setw -g mode-keys vi
set-option -sg escape-time 10
set-option -g default-terminal "screen-256color"
set -g mouse on

bind \ split-window -h -c '#{pane_current_path}'
bind - split-window -v -c '#{pane_current_path}'

set -g history-limit 20000
bind r source-file ~/.tmux.conf \; display "Reloaded!"

set -g base-index 1       # Numbering of windows
set -g pane-base-index 1  # Numbering of panes

bind C-h select-pane -L     # Switch to Pane Left
bind C-j select-pane -D     # Switch to Pane Down
bind C-k select-pane -U     # Switch to Pane Up
bind C-l select-pane -R     # Switch to Pane Right

setw -g monitor-activity on      # Activity Alerts
set -g visual-activity on
set -g status-fg white           # Status line Colors
set -g status-bg black
```

Bind key
```
unbind r
bind r source-file ~/.tmux.conf
```

Force reload of config file
```
:source-file ~/.tmux.conf
```

## Session
New session by command line
```
$ tmux new-session -s work
```
Attach to a Session
```
$ tmux attach
$ tmux attach -t work
```
Detach from a session
```
d
```
List all Session
```
$ tmux ls
```
Switch between sessions
```
(   previous
)   next
L   last
s   choose from a list
```
Rename current session
```
$
```

## Windows
Create Windows
```
c
```
Swtich Windows
```
number   0,1,2,...
p     previous
n     next
l     last
w     choose from a list
```

Swap/Move Windows
```
:swap-window -s 3 -t 1
:swap-window -t 0
:move-window -t 0
```

Rename current window
```
,
```
Kill Window
```
&
```

## Pane
Create pane
```
"     split vertically (top/bottom)
%     split horizontally (left/right)
```
Switch panes
```
left/right/up/down
o     next
;     last
```
Move panes
```
{ / }   to previous/next position
!     pane -> window
:move-pane -t 3.2    window 3 pane 2->pane
z     toggle pane zoom
```
Change layout
```
space
```
Resize Pane
```
M-up/down/left/right      resize by 5
C-up/down/left/right      resize by 1
```
Others Pane Commands
```
x     kill pane
q     Display Pane Number
```

## Copy/Paste
### Copy/Paste in terminal
when follwing otpions is set
* mouse-select-pane
* mouse-select-window

Hold the **shift** key, then use mouse to selsect text.

### Copy/Paste in tmux
```
C-b [ - enter copy mode
space - start to select
enter - copy to tmux clipboard
C-b ] - paste in tmux
```
