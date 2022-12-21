# k8s Learn

## k8s tutorial

<https://kubernetes.io/docs/tutorials/>

## k8s on docker desktop

<https://docs.docker.com/desktop/kubernetes/>

<https://docs.docker.com/get-started/kube-deploy/>

## run on wsl (KinD multinodes recommended)

<https://kubernetes.io/blog/2020/05/21/wsl-docker-kubernetes-on-the-windows-desktop/>

## online playground

<https://labs.play-with-k8s.com/>

## dashboard

<https://github.com/kubernetes/dashboard/>

### create service account

```bash
kubectl apply -f dashboard-service-acc.yaml
kubectl apply -f dashboard-cluster-role-binding.yaml
```

### generate token

```bash
kubectl -n kubernetes-dashboard create token admin-user
```

### remember to have `kubectl proxy` started

### go to <http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/>

### you can also disable dashboard auth

<https://andrewlock.net/running-kubernetes-and-the-dashboard-with-docker-desktop/>
