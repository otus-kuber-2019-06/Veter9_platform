# Veter9_platform
Veter9 Platform repository


# вывод первой команды
alex@lapbook:~/Desktop/Veter9_platform$ kubectl cluster-info
Kubernetes master is running at https://192.168.99.100:8443
KubeDNS is running at https://192.168.99.100:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

# заходим на миникуб виртуальную машину и удаляем контейнеры
```
alex@lapbook:~/Desktop/Veter9_platform$ minikube ssh
                         _             _            
            _         _ ( )           ( )           
  ___ ___  (_)  ___  (_)| |/')  _   _ | |_      __  
/' _ ` _ `\| |/' _ `\| || , <  ( ) ( )| '_`\  /'__`\
| ( ) ( ) || || ( ) || || |\`\ | (_) || |_) )(  ___/
(_) (_) (_)(_)(_) (_)(_)(_) (_)`\___/'(_,__/'`\____)

$ docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS               NAMES
21cca2c10daf        eb516548c180           "/coredns -conf /etc…"   12 minutes ago      Up 12 minutes                           k8s_coredns_coredns-5c98db65d4-gdrm8_kube-system_cb625da6-f4ef-4c8c-90a9-ed6cd99a5fca_3
f56d75722f6b        eb516548c180           "/coredns -conf /etc…"   12 minutes ago      Up 12 minutes                           k8s_coredns_coredns-5c98db65d4-5w8zk_kube-system_5e5e63b7-4a70-47ea-836e-6e90b339467e_3
5050991c974b        4689081edb10           "/storage-provisioner"   12 minutes ago      Up 12 minutes                           k8s_storage-provisioner_storage-provisioner_kube-system_3890b0cd-e9e1-4097-8009-e5e7d830b35a_3
dc1786fda289        d235b23c3570           "/usr/local/bin/kube…"   13 minutes ago      Up 13 minutes                           k8s_kube-proxy_kube-proxy-cv2jm_kube-system_cf5dd86d-9638-4e6e-82ff-11babe516062_1
8ea2924d67fe        k8s.gcr.io/pause:3.1   "/pause"                 13 minutes ago      Up 13 minutes                           k8s_POD_storage-provisioner_kube-system_3890b0cd-e9e1-4097-8009-e5e7d830b35a_1
e70c7e1f41e1        k8s.gcr.io/pause:3.1   "/pause"                 13 minutes ago      Up 13 minutes                           k8s_POD_coredns-5c98db65d4-gdrm8_kube-system_cb625da6-f4ef-4c8c-90a9-ed6cd99a5fca_1
74f0a674ff85        k8s.gcr.io/pause:3.1   "/pause"                 13 minutes ago      Up 13 minutes                           k8s_POD_coredns-5c98db65d4-5w8zk_kube-system_5e5e63b7-4a70-47ea-836e-6e90b339467e_1
830e9f803665        k8s.gcr.io/pause:3.1   "/pause"                 13 minutes ago      Up 13 minutes                           k8s_POD_kube-proxy-cv2jm_kube-system_cf5dd86d-9638-4e6e-82ff-11babe516062_1
9047debc7cea        2d3813851e87           "kube-scheduler --bi…"   14 minutes ago      Up 13 minutes                           k8s_kube-scheduler_kube-scheduler-minikube_kube-system_31d9ee8b7fb12e797dc981a8686f6b2b_1
ebd1e74ea65a        8328bb49b652           "kube-controller-man…"   14 minutes ago      Up 13 minutes                           k8s_kube-controller-manager_kube-controller-manager-minikube_kube-system_676a8a1e3e146d0c0f7c4f6e1e96b578_1
3f444f9104a4        201c7a840312           "kube-apiserver --ad…"   14 minutes ago      Up 14 minutes                           k8s_kube-apiserver_kube-apiserver-minikube_kube-system_e0f883122ef4b18e9fbea5c005bca446_1
27c4d6c0853f        119701e77cbc           "/opt/kube-addons.sh"    14 minutes ago      Up 13 minutes                           k8s_kube-addon-manager_kube-addon-manager-minikube_kube-system_65a31d2b812b11a2035f37c8a742e46f_1
7ac024fc2471        2c4adeb21b4f           "etcd --advertise-cl…"   14 minutes ago      Up 14 minutes                           k8s_etcd_etcd-minikube_kube-system_89f36d1de777528a3e8b9a2534a41af4_1
bdc8de8815a8        k8s.gcr.io/pause:3.1   "/pause"                 14 minutes ago      Up 14 minutes                           k8s_POD_kube-apiserver-minikube_kube-system_e0f883122ef4b18e9fbea5c005bca446_1
57f8f3a1e200        k8s.gcr.io/pause:3.1   "/pause"                 14 minutes ago      Up 14 minutes                           k8s_POD_kube-controller-manager-minikube_kube-system_676a8a1e3e146d0c0f7c4f6e1e96b578_1
1147f1d9911b        k8s.gcr.io/pause:3.1   "/pause"                 14 minutes ago      Up 14 minutes                           k8s_POD_kube-addon-manager-minikube_kube-system_65a31d2b812b11a2035f37c8a742e46f_1
4723cb3284f5        k8s.gcr.io/pause:3.1   "/pause"                 14 minutes ago      Up 14 minutes                           k8s_POD_kube-scheduler-minikube_kube-system_31d9ee8b7fb12e797dc981a8686f6b2b_1
9a44e4c5e02c        k8s.gcr.io/pause:3.1   "/pause"                 14 minutes ago      Up 14 minutes                           k8s_POD_etcd-minikube_kube-system_89f36d1de777528a3e8b9a2534a41af4_1
$ docker rm -f $(docker ps -a -q)
21cca2c10daf
f56d75722f6b
5050991c974b
c51c86aec1cf
0d3feedb0c8b
4c5be2253839
dc1786fda289
8ea2924d67fe
e70c7e1f41e1
74f0a674ff85
830e9f803665
9047debc7cea
ebd1e74ea65a
3f444f9104a4
27c4d6c0853f
7ac024fc2471
bdc8de8815a8
57f8f3a1e200
1147f1d9911b
4723cb3284f5
9a44e4c5e02c
17c5df78e27e
a2b519cf01c0
85268fc47569
8fc4b1fe2fee
dd74fbc5716f
6660434fffad
6ee23f8bb0d2
b0b20d4c2770
a6e1b7306f18
56fcbf2c3daa
98231cb77312
60446e691693
$ 
```

# kubectl get pods -n kube-system
```
NAME                               READY   STATUS    RESTARTS   AGE
coredns-5c98db65d4-5w8zk           1/1     Running   1          4d1h
coredns-5c98db65d4-gdrm8           1/1     Running   1          4d1h
etcd-minikube                      1/1     Running   0          4d1h
kube-addon-manager-minikube        1/1     Running   0          4d1h
kube-apiserver-minikube            1/1     Running   2          4d1h
kube-controller-manager-minikube   1/1     Running   2          4d1h
kube-proxy-cv2jm                   1/1     Running   0          4d1h
kube-scheduler-minikube            1/1     Running   0          4d1h
storage-provisioner                1/1     Running   1          4d1h
```
# kubectl delete pod --all -n kube-system 
```
pod "coredns-5c98db65d4-5w8zk" deleted
pod "coredns-5c98db65d4-gdrm8" deleted
pod "etcd-minikube" deleted
pod "kube-addon-manager-minikube" deleted
pod "kube-apiserver-minikube" deleted
pod "kube-controller-manager-minikube" deleted
pod "kube-proxy-cv2jm" deleted
pod "kube-scheduler-minikube" deleted
pod "storage-provisioner" deleted
```
# kubectl get cs
```
NAME                 STATUS    MESSAGE             ERROR
controller-manager   Healthy   ok                  
scheduler            Healthy   ok                  
etcd-0               Healthy   {"health":"true"}   
```
# 