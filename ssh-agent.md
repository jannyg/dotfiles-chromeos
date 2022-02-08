etting up ssh-agent in Linux/Crostini on Chromebook

* Create your user systemd directory:
```
$ mkdir -p .config/systemd/user
```
* Edit the unit file `.config/systemd/user/ssh-agent.service`:
```
[Unit]
Description=SSH key agent

[Service]
Type=simple
Environment=SSH_AUTH_SOCK=%t/ssh-agent.socket
ExecStart=/usr/bin/ssh-agent -D -a $SSH_AUTH_SOCK

[Install]
WantedBy=default.target
```
* Enable the service:
```
$ systemctl --user enable ssh-agent
```
* Add setting of SSH_AUTH_SOCK to end of `.bashrc`:
```
export SSH_AUTH_SOCK=$XDG_RUNTIME_DIR/ssh-agent.socket
```
