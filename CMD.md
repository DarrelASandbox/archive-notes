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

# Pull Request (After forking and cloning to local)
git branch branchname
git checkout branchname
git add .
git commit -m 'branchname feature'
git push
# Open Pull Request on GitHub & Create
# Sync with Master Repo
git checkout main
git remote add upstream https://github.com/some-url
git fetch upstream
git merge upstream/main
# See remote branches
git remote -v
# Remove previously incorrect remote
git remote rm upstream
```

#### NPM

```sh
# List all the Node.js modules linked with npm
npm ls --link --global
```

#### VS Code

```sh
# https://stackoverflow.com/questions/35773299/how-can-you-export-the-visual-studio-code-extension-list
# Export from Machine A
code --list-extensions > extensions.list
# Install on Machine B
cat extensions.list |% { code --install-extension $_}
```

#### Homebrew

```sh
# List information about all managed services for the current user (or root).
brew services
```

#### Anaconda

```sh
# To keep everything consistent, use "conda update anaconda", as Anaconda is the consistent set of packages for each Anaconda release.
conda update anaconda

# Skip dependency checking altogether, use the '--no-deps' option
conda install --no-deps #package

# Create env
conda create --name basic
conda activate basic

# Make exact copy of an environment
conda create --clone basic --name temp

# Check envs
conda env list

# Activate the new environment to use it
source activate base

# Delete an environment and everything in it
conda env remove --name temp_env

# List the history of each change to the current environment
conda list --revisions
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
