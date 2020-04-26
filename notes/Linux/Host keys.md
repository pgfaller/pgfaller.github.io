Host keys

## Host Key Fingerprints

Actually, that is a public key "fingerprint", not the entire key. You can view your server's fingerprints by running the following commands:

Code:

```
$ ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub

$ ssh-keygen -l -f /etc/ssh/ssh_host_dsa_key.pub

$ ssh-keygen -l -f /etc/ssh/ssh_host_key.pub
```
