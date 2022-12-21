# kubectl commands

## kubectl get nodes

## kubectl get namespaces

## kubectl get pods

`--all-namespaces`

`-n <name>`

## kubectl get deployments

## kubectl create deployment `<name>` --image=`<source>`

## kubectl scale deployments/`<name>` --replicas=`<number>`

eg: kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1

### gcloud repo: <https://console.cloud.google.com/gcr/images/google-samples/>

## kubectl proxy

check proxy is available:

```bash
curl http://localhost:8001/version
```

## Find your deployment app's pod details

```bash
curl http://localhost:8001/api/v1/namespaces/default/pods/<POD_NAME>/
```

similar to

```bash
kubectl describe pods <POD_NAME>
```

## Find containers inside your pod

```bash
kubectl get pods <POD_NAME> -o jsonpath='{.spec.containers[*].name}'
```

## Logs, shell etc... Similar to docker containers

```bash
kubectl logs <POD_NAME>
```

```bash
kubectl exec -it kube-demo-54cd547f5c-zrr5x -- bash
```

## Expose a service

```bash
kubectl expose deployment/<DEPLOYMENT_NAME> --type="NodePort" --port 8080
```

Services will be automatically used by k8s load balancer on deployments with multiple replicas!

Should be then displayed under:

```bash
kubectl get services
```

Details again, under:

```bash
kubectl describe services/<DEPLOYMENT_NAME>
```

Look for: `NodePort:                 <unset>  31910/TCP`
(31910 is an example, this is randomly allocated)

## Update a deployment

```bash
kubectl set image deployments/<NAME> <CONTAINER_NAME>=<source>:v2
```

If you want to update from local docker image add `--image-pull-policy=Never`

```bash
kubectl rollout status deployments/<NAME>
```

```bash
kubectl rollout undo deployments/<NAME>
```

## Apply a configuration file

```bash
kubectl apply -f <path/to/file>
```

## Useful flags for multiple commands

`-o yaml` sets output to yaml for a command

`--dry-run` won't submit your command
