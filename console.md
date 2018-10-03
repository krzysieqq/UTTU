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

# K8S
```bash
kubectl config set-context $(kubectl config current-context) --namespace=<insert-namespace-name-here>
# Validate it
kubectl config view | grep namespace:
kubeadm init --pod-network-cidr=192.168.10.0/16 --apiserver-advertise-address=192.168.10.172
kubectl get nodes
kubectl get pods --all-namespaces -o wide
kubectl create deployment apache --image=apache
kubectl get deployments
kubectl get deploy,svc,pods,pvc
kubectl describe deployment apache
kubectl create service nodeport apache --tcp=80:80
kubectl get svc # list out current services
kubectl cluster-info
kubectl expose deployment ms1 --type=NodePort --name=ms1-service
kubectl expose deployment nginx --type=NodePort --name=nginx-service
kubectl exec web -c <container-name> date
kubectl logs --tail=50 mytestserver # Print most recent 50 lines
kubectl logs --since=3h mytestserver # Print last 3 hours logs
KUBE_EDITOR=”vim” kubectl edit pod mytestserver1
cat mypod.json | kubectl apply -f -
kubectl config set-context my-context --namespace=mystuff
kubectl exec -it <pod-name> -- bash
kubectl cp <pod-name>:/path/to/remote/file /path/to/local/file

```

#Other
```bash
ssh-copy-id demo@198.51.100.0 #copy ssh key to server
```