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

# dockerfile:
```
FROM python:3.6.0-alpine
RUN mkdir /app
COPY app/homework.html /app
WORKDIR /app
EXPOSE 8000
USER 1001
CMD ["python3", "-m", "http.server", "8000"]
```
# docker build -t veter9/python36 .
```
Sending build context to Docker daemon  3.584kB
Step 1/7 : FROM python:3.6.0-alpine
 ---> cb178ebbf0f2
Step 2/7 : RUN mkdir /app
 ---> Using cache
 ---> 6a7319ce90a0
Step 3/7 : COPY app/homework.html /app
 ---> ad85545f8e06
Step 4/7 : WORKDIR /app
 ---> Running in 8588a2a2ca13
Removing intermediate container 8588a2a2ca13
 ---> 2301922b3d4a
Step 5/7 : EXPOSE 8000
 ---> Running in 9834d67ae4a1
Removing intermediate container 9834d67ae4a1
 ---> 5fdcf59be36b
Step 6/7 : USER 1001
 ---> Running in ad93e039d8e4
Removing intermediate container ad93e039d8e4
 ---> ca434c909a6f
Step 7/7 : CMD ["python3", "-m", "http.server", "8000"]
 ---> Running in 262ab92c3eb9
Removing intermediate container 262ab92c3eb9
 ---> adf8f262f6cf
Successfully built adf8f262f6cf
Successfully tagged veter9/python36:latest
```

# sudo docker login
```
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: veter9
Password: 
WARNING! Your password will be stored unencrypted in /root/snap/docker/384/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```
# sudo docker push veter9/python36
``` 
The push refers to repository [docker.io/veter9/python36]
f6d8a0b2b184: Pushed 
d42244823e3c: Pushed 
7def4548bbc9: Mounted from library/python 
d13764a9eea3: Mounted from library/python 
af4997faab5b: Mounted from library/python 
9f8566ee5135: Mounted from library/python 
latest: digest: sha256:c68f6bdac3170e81306b70bbe1d608e62025bdf4a098dec7d63b45e13516a642 size: 1570
```
# kubectl apply -f web-pod.yaml 
```
pod/web created
```
# kubectl get pod
```
NAME   READY   STATUS    RESTARTS   AGE
web    1/1     Running   0          74s
```
# kubectl get pod web -o yaml
```
apiVersion: v1
kind: Pod
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","kind":"Pod","metadata":{"annotations":{},"labels":{"key":"web"},"name":"web","namespace":"default"},"spec":{"containers":[{"image":"veter9/python36","name":"web","resources":{"limits":{"cpu":"400m","memory":"512Mi"},"requests":{"cpu":"200m","memory":"256Mi"}}}]}}
  creationTimestamp: "2019-07-15T06:18:27Z"
  labels:
    key: web
  name: web
  namespace: default
  resourceVersion: "7594"
  selfLink: /api/v1/namespaces/default/pods/web
  uid: 49af49cc-f9a5-4ade-bb15-6e4f62e30d47
spec:
  containers:
  - image: veter9/python36
    imagePullPolicy: Always
    name: web
    resources:
      limits:
        cpu: 400m
        memory: 512Mi
      requests:
        cpu: 200m
        memory: 256Mi
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-48fgr
      readOnly: true
  dnsPolicy: ClusterFirst
  enableServiceLinks: true
  nodeName: minikube
  priority: 0
  restartPolicy: Always
  schedulerName: default-scheduler
  securityContext: {}
  serviceAccount: default
  serviceAccountName: default
  terminationGracePeriodSeconds: 30
  tolerations:
  - effect: NoExecute
    key: node.kubernetes.io/not-ready
    operator: Exists
    tolerationSeconds: 300
  - effect: NoExecute
    key: node.kubernetes.io/unreachable
    operator: Exists
    tolerationSeconds: 300
  volumes:
  - name: default-token-48fgr
    secret:
      defaultMode: 420
      secretName: default-token-48fgr
status:
  conditions:
  - lastProbeTime: null
    lastTransitionTime: "2019-07-15T06:18:27Z"
    status: "True"
    type: Initialized
  - lastProbeTime: null
    lastTransitionTime: "2019-07-15T06:19:13Z"
    status: "True"
    type: Ready
  - lastProbeTime: null
    lastTransitionTime: "2019-07-15T06:19:13Z"
    status: "True"
    type: ContainersReady
  - lastProbeTime: null
    lastTransitionTime: "2019-07-15T06:18:27Z"
    status: "True"
    type: PodScheduled
  containerStatuses:
  - containerID: docker://d5e8d59c869c12a0e200c9994eafa1548259d480cf0c3830df1cf5f673ed4650
    image: veter9/python36:latest
    imageID: docker-pullable://veter9/python36@sha256:c68f6bdac3170e81306b70bbe1d608e62025bdf4a098dec7d63b45e13516a642
    lastState: {}
    name: web
    ready: true
    restartCount: 0
    state:
      running:
        startedAt: "2019-07-15T06:19:12Z"
  hostIP: 10.0.2.15
  phase: Running
  podIP: 172.17.0.2
  qosClass: Burstable
  startTime: "2019-07-15T06:18:27Z"
```

# kubectl port-forward --address 0.0.0.0 pod/web 8000:8000
```
Forwarding from 0.0.0.0:8000 -> 8000
Handling connection for 8000
Handling connection for 8000
```
