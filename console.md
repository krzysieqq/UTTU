#tmux
```bash

tmux	[-2Cluv] [-c shell-command] [-f file] [-L socket-name] [-S socket-path] [command [flags]]
tmux new -s [name_session]
tmux rename-session -t 0 database
tmux ls
tmux attach -t 0
tmux a -t [name of session]
tmux a # <- go to the last created session
tmux kill-session -t [name of session] <- Kill named session
tmux kill-server <- Kill tmux server, along with all sessions


Ctrl+b then [ ] then you can use your normal navigation keys to scroll around 
        (eg. Up Arrow or PgDn)
        Press q to quit scroll mode.
Ctrl+b d - detach

```
## windows (tabs)
```
c  create window
w  list windows
n  next window
p  previous window
f  find window
,  name window
&  kill window
```

## panes (splits)

```
%  vertical split
"  horizontal split

o  swap panes
q  show pane numbers
x  kill pane
+  break pane into window (e.g. to select text by mouse to copy)
-  restore pane from window
⍽  space - toggle between layouts
<prefix> q (Show pane numbers, when the numbers show up type the key to goto that pane)
<prefix> { (Move the current pane left)
<prefix> } (Move the current pane right)
<prefix> z toggle pane zoom
```