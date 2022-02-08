# SSH config for ssh with Cloudflare for `~/.ssh/config`

```
Host aws.hostname
        HostName aws.hostname
        User ec2-user
        ProxyCommand /usr/local/bin/cloudflared access ssh --hostname %h
```
