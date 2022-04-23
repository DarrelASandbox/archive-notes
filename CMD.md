#### GitHub & Git

```sh
# "Undo" pushed commit to GitHub.
git push -f origin HEAD~1:main
git reset --soft HEAD~1
# Discard commit, keep changes in staging area & changes in working directory.

#Revert initial git commit
git update-ref -d HEAD

# Reduce Git repository size.
git reflog expire --all --expire=now
git gc --prune=now --aggressive
```

#### UNIX

```sh
# List of open network ports.
netstat -anvp tcp | awk 'NR<3 || /LISTEN/'
sudo lsof -PiTCP -sTCP:LISTEN
```

```sh
# Kill port
kill -9 <PID>
```

#### Homebrew

```sh
# List information about all managed services for the current user (or root).
brew services
```
