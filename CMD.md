- [Git](#git)
- [VS Code](#vs-code)
- [Homebrew](#homebrew)
- [Conda](#conda)
- [UNIX](#unix)
- [Neovim](#neovim)

## Git

```sh
# "Undo" pushed commit to GitHub.
git push -f origin HEAD~1:main
git reset --soft HEAD~1
# Discard commit, keep changes in staging area & changes in working directory.

# Revert initial git commit
git update-ref -d HEAD

# https://stackoverflow.com/questions/18393498/gitignore-all-the-ds-store-files-in-every-folder-and-subfolder/19299889#19299889
# Make a global .gitignore file somewhere
echo .DS_Store >> ~/.gitignore_global
# Now tell git to use it for all repositories:
git config --global core.excludesfile ~/.gitignore_global

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

# Combining repositories while keep commit histories (Using branch)
git clone https://github.com/<your_username>/<old_repository>.git
git clone https://github.com/<your_username>/<new_repository>.git
cd <new_repository>
git checkout -b merging_branch
git remote add old_repo ../<old_repository> # Local directory
git fetch old_repo
git merge old_repo/main --allow-unrelated-histories
git push origin merging_branch
# Handle pull request on GitHub after pushing
# Delete old branch on GitHub
git remote remove old_repo

# Combining repositories while keep commit histories (Directly to main)
git clone https://github.com/<your_username>/<new_repository>.git
cd <new_repository>
git remote add old_repo https://github.com/<your_username>/<old_repository>.git
git fetch old_repo
git merge old_repo/main --allow-unrelated-histories
git push
git remote remove old_repo
```

&nbsp;

---

&nbsp;

## VS Code

```sh
# https://stackoverflow.com/questions/35773299/how-can-you-export-the-visual-studio-code-extension-list
# Export from Machine A
code --list-extensions > extensions.list
# Install on Machine B
cat extensions.list |% { code --install-extension $_}
```

&nbsp;

---

&nbsp;

## Homebrew

```sh
# List information about all managed services for the current user (or root).
brew services

# List all packages dependencies:
brew deps --tree --installed
# List one package dependencies:
brew deps --tree --installed go
# List all formulas that aren't dependents of any other formulas (leaves), and for each of them lists all of its dependencies.
brew leaves | xargs brew deps --formula --for-each | sed "s/^.*:/$(tput setaf 4)&$(tput sgr0)/"
```

&nbsp;

---

&nbsp;

## Conda

```sh
# https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

# Skip dependency checking altogether, use the '--no-deps' option
conda install --no-deps #package

# Create env
conda create --name basic
conda activate basic

# Make exact copy of an environment
conda create --clone base --name temp

# Check envs
conda env list

# Activate the new environment to use it
conda activate base

# Delete an environment and everything in it
conda env remove --name temp_env

# Update all packages
conda update --all

# List the history of each change to the current environment
conda list --revisions

# To "reset" env
conda install --rev 1
```

&nbsp;

---

&nbsp;

## UNIX

```sh
# List of open network ports.
netstat -anvp tcp | awk 'NR<3 || /LISTEN/'
sudo lsof -PiTCP -sTCP:LISTEN

# nmap identify the services running on ports
dnf install nmap
# `-sT` lists open ports
# `-O` option is for operating system detection
nmap -sT -O localhost

# Port forwarding setup
# Configure port forwarding for your router
# Instruction varies from router to router
# On remote server (Rocky Linux)
systemctl status firewalld
firewall-cmd --add-port=YOUR_PORT/tcp --permanent
firewall-cmd --reload
firewall-cmd --list-all
while true; do nc -l 443 -c 'echo -e "HTTP/1.1 200 OK\n\nHello, world!"'; done
# On client server (MacOS)
nc -zv hostname port

# Generate csr
openssl genrsa -out private.key 4096
mv private.key
mv private.key .ssh/private.key
cd .ssh
openssl req -new -key private.key -out csr.pem -subj "/CN=your_domain.com"

# List Open Files
# `-i`: Select the listing of files any of whose Internet address matches the address specified in i.
# `-P`: inhibits the conversion of port numbers to port names for network files.
# `-n`: inhibits the conversion of network numbers to host names for network files.
lsof -i -P -n
lsof -i :8080 -P -n
```

&nbsp;

---

&nbsp;

## Neovim

```sh
# runtimepath
:help rtp
```

&nbsp;

---

&nbsp;
