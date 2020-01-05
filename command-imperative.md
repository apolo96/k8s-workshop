# k8s deploy dockercoins

## Deploy microservices
```
kubctl create deploy redis --image redis
```
Deploy **rng**, **hasher**, **worker** and **webui**
```
kubctl create deploy rng --image dockercoins/rng
```

## Expose services
```
kubectl expose deploy redis --port 6379
```
Expose  **rng**, **hasher**, **worker** and **webui**
```
kubectl expose deploy rng --port 80
```
Expose external services
```
kubectl expose deploy webui --port 80 --type NodePort
```

## Scale worker service
```
kubectl scale deploy worker --replicas 10
```

## Rolling Update
```
kubectl set image deploy worker worker=dockercoins/worker:v0.2
```

```
kubectl rollout undo deploy worker
```

## Edit Rolling Update Strategy
```
kubectl edit deploy worker
```