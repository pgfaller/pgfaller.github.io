---
layout: page
---

## SSH Cheatsheet

### Base Usage

```
$ ssh [user]@[host]
```

#### Use Specific Key

```
$ ssh -i ~/.ssh/id_rsa [user]@[host]
```

#### Use Alternative Port

```
$ ssh -i ~/.ssh/id_rsa -p [port] [user]@[host]
```

### Dynamic SOCKS Proxy

This can be used with proxychains to forward client traffic through the remote server.

```
$ ssh -D8080 [user]@[host]
```

### Local Port Forwarding

This will bind to [bindaddr]:[port] on the client and forward through the SSH server to the [dsthost]:[dstport]

```
$ ssh -L [bindaddr]:[port]:[dsthost]:[dstport] [user]@[host]
```

### Remote Port Forwarding

This will bind to [bindaddr]:[port] on the remote server and tunnel traffic through the ssh client side to [localhost]:[localport]

```
$ ssh -R [bindaddr]:[port]:[localhost]:[localport] [user]@[host]
```

### Establish VPN over SSH

The following options must be enabled on the server side.

```
PermitRootLogin yes
PermitTunnel yes
```

```
$ ssh [user]@[host] -w any:any
```

You can see the established tun interface by typing ifconfig -a

The interfaces and forwarding must still be configured. This assumes that we are going to forward 10.0.0.0/24 through the remote server. We are also assuming that the server’s main connection is through eth0, and both client/server stood up tun0. This may be different if you already have existing VPN connections.

#### Client

```
$ ip addr add 192.168.5.2/32 peer 192.168.5.1 dev tun0
# Once Server is setup, run the following to add routes
$ route add -net 10.0.0.0/24 gw 192.168.5.1
```

#### Server

```
$ ip addr add 192.168.5.1/32 peer 192.168.5.2 dev tun0
$ sysctl -w net.ipv4.ip_forward=1
$ iptables -t nat -A POSTROUTING -s 192.168.5.1 -o eth0 -j MASQUERADE
```

### Execute a One Liner

```
ssh -i ~/.ssh/id_rsa [user]@[host] "sudo apt-get update && sudo apt-get upgrade"
```

## Files

| File                   | Description                                                            |
| ---------------------- | ---------------------------------------------------------------------- |
| ~/.ssh/                | Directory for user-specific SSH configuration                          |
| ~/.ssh/authorized_keys | Lists public keys authorized for logging into this user                |
| ~/.ssh/config          | Per-user config file. Can specify how to connect, with which keys etc. |
| ~/.ssh/id\_\*          | Key files, both public and private                                     |
| ~/.ssh/known_hosts     | Contains list of public host keys known to user                        |
| /etc/ssh/ssh_config    | Global SSH client configuration                                        |
| /etc/ssh/sshd_config   | SSH server configuration                                               |

### Generating Keys

```
$ ssh-keygen
```

### Adding Authorized Keys

```
$ cat id_rsa.pub >> ~/.ssh/authorized_keys
```

The following will remotely copy your public key to authorized_keys on [host]

```
$ ssh-copy-id -i ~/.ssh/id_rsa [user]@[host]
```

### SSH Escape Sequences

Simply type the following combinations to escape SSH sessions.
| Escape Sequence | Description |
| --------------- | ------------|
| ~? | List all options |
| ~B | Send BREAK to remote host |
| ~R | Request Re-key |
| ~V/v | Decrease / Increase verbosity |
| ~^Z | Suspend SSH |
| ~# | List forwarded connections|
| ~& | background ssh |
| ~~ | Send the escape character instead of escaping the next char |

## SCP

SSH Copy utility for pushing and pulling files remotely

Copy from remote to local

Copy remote file.txt to /tmp/file.txt

```
$ scp [user]@[host]:file.txt /tmp/file.txt
```

Copy from local to remote

Copy local file.txt to remote /tmp/file.txt

```
$ scp file.txt [user]@[host]:/tmp/file.txt
```

Copy recursively (full directories)

The following will copy remote /home/ubuntu/.vim directory and all of its contents to ./vim.

```
$ scp -r [user]@[host]:/home/ubuntu/.vim ./vim
```

Use non-standard port

Uses -P instead of -p switch in regular SSH command. The following uses port 2222.

```
$ scp -P 2222 [user]@[host]:/home/ubuntu/test.py ./test.py
```
