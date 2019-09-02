# kubernetes_installation_with_ansible

### Step 1: Create host file where IP address for MASTER and WORKER nodes are present.

```
[root@linux kube-cluster]# pwd
/root/kube-cluster
[root@linux kube-cluster]# cat hosts
[masters]
master ansible_host=192.168.100.202 ansible_user=root

[workers]
worker1 ansible_host=192.168.100.187 ansible_user=root
worker2 ansible_host=192.168.100.234 ansible_user=root
[root@linux kube-cluster]#
```

### Step 2: Run on your own machine from where all the MASTER and WORKER nodes are reachable.
Note: Make sure that SSH password less login is already established from the node where ansible playbook will be running.

```
[root@linux kube-cluster]# ansible-playbook -i hosts ~/kube-cluster/kube-dependencies.yml
```

### Step 3: Run master.yml which will do configuration on MASTER node

```
[root@linux kube-cluster]# ansible-playbook -i hosts ~/kube-cluster/master.yml
```
### Step 4: Run worker.yml which will do configuration on WORKER nodes

```
[root@linux kube-cluster]# ansible-playbook -i hosts ~/kube-cluster/worker.yml
```
