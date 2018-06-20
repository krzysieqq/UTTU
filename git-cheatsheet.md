#Useful Git aliases

```bash
git aliases # <- show aliases

# ---> Add to Global Config
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status

```
```bash
# ---> File: .gitconfig or .git/config <--- 
[alias]
  a = add
  pu = push -u
  cm = commit -m
  cam = commit -a -m
  st = status -s
  co = checkout
  cob = checkout -b
  als = !git config --get-regexp 'alias.*' | colrm 1 6 | sed 's/[ ]/ = /' | sort
  vl = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
  ls = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
  ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
  l = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short
  # la = "!git config -l | grep alias | cut -c 7-"
  wip = commit -am "WIP"
  undo = reset HEAD~1 --mixed
  #up = !git pull --rebase --prune $@ && git submodule update --init --recursive
  # Rename [branch] to done-[branch] -> done = "!f() { git branch | grep "$1" | cut -c 3- | grep -v done | xargs -I{} git branch -m {} done-{}; }; f"

```

```bash
# ---> .git/hooks/pre-commit <---
git diff HEAD^ | flake8 --diff --ignore=E501 --exclude=.svn,CVS,.bzr,.hg,.git,__pycache__,.tox,.eggs,*.egg,version.py,*.yml,*.csv,*.json
```