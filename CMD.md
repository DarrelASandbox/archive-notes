#### UNIX

- List of open network ports

```sh
netstat -anvp tcp | awk 'NR<3 || /LISTEN/'
sudo lsof -PiTCP -sTCP:LISTEN
```

- Kill port

```sh
kill -9 <PID>
```

#### Homebrew

- List information about all managed services for the current user (or root).

```sh
brew services
```
