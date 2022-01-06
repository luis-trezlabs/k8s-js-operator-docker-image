# K8S Typescript based operator

# Steps to build the project
```bash
  # Clone the project to your local machine
  git clone https://github.com/luis-trezlabs/operator-k8s-js.git
```

```bash
  # Change to cronjob-operator branch
  git checkout cronjob-operator
```

```bash
  # Install the ts-operator-chart chart
  helm install ts-operator-chart ts-operator-chart/

  # Output
  NAME: ts-operator-chart
  LAST DEPLOYED: Wed Jan  5 12:48:08 2022
  NAMESPACE: default
  STATUS: deployed
  REVISION: 1
  TEST SUITE: None
```

Now, the operator is running in our cluster

We can check if everything work as spectated 

```bash
  # Get cronjobs in defined namespace
  kubectl get cronjob -n ts-operator

  # output
  NAME          SCHEDULE    SUSPEND   ACTIVE   LAST SCHEDULE   AGE
  ts-operator   0 * * * *   False     0        4m59s           16m
```

```bash
  # Get pods in our namespace
  kubectl get pods -n ts-operator

  # output
  NAME                            READY   STATUS      RESTARTS   AGE
  ts-operator-27356820--1-wh7zs   0/1     Completed   0          6m3s
```

Our cronjob is working

```bash
  # We can check the out information doing
  kubectl logs <pod-name> -n ts-operator

  kubectl logs ts-operator-27356820--1-wh7zs -n ts-operator

  # output
  NAME                            READY   STATUS      RESTARTS   AGE
  ts-operator-27356820--1-wh7zs   0/1     Completed   0          6m3s
```

Also we can view the out file doing the following

```bash
  # Connect to minikube
  minikube ssh

  # read file
  cat /pod-logs/pods.txt
  
  # output similar to this
  -------------------------
  Time                     Pod Name
  1/5/2022, 8:00:02 PM    coredns-78fcd69978-rfz62
  1/5/2022, 8:00:02 PM    etcd-minikube
  1/5/2022, 8:00:02 PM    kube-apiserver-minikube
  1/5/2022, 8:00:02 PM    kube-controller-manager-minikube
  1/5/2022, 8:00:02 PM    kube-proxy-9pdqd
  1/5/2022, 8:00:02 PM    kube-scheduler-minikube
```
