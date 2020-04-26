Setting up microk8s

# Neptune (master)

Install the snap:

```
$ sudo snap install microk8s --classic
$ sudo sudo usermod -a -G microk8s peter
$ sudo chown -f -R peter ~/.kube
```

(optional, should be done automatically, but can be damaged by me fiddling)

```
$ microk8s.config > /home/peter/.kube/config
```

Logout, login, then:
```
$ microk8s.start
$ microk8s.status
$ ...
$ microk8s.add-node
Join node with: microk8s join 192.168.0.3:25000/HqzLCQKBrvvdTYCEokhZbIevAxANYdLU
$ microk8s.add-node
Join node with: microk8s join 192.168.0.3:25000/CSqsETxKcjcpSOjEOShEzmbUIpGAIWnX
```

# Jupiter (slave)
```
$ microk8s join 192.168.0.3:25000/HqzLCQKBrvvdTYCEokhZbIevAxANYdLU
```

# Saturn (slave)
```
$ microk8s join 192.168.0.3:25000/CSqsETxKcjcpSOjEOShEzmbUIpGAIWnX
```
# Neptune (master)
```
$ microk8s.enable dns dashboard storage
$ microk8s kubectl port-forward -n kube-system service/kubernetes-dashboard 10443:443 --address 0.0.0.0 &
$ token=$(microk8s kubectl -n kube-system get secret | grep default-token | cut -d " " -f1)
$ microk8s kubectl -n kube-system describe secret $token
```
Use the displayed token to authenticate on https://neptune:10443
