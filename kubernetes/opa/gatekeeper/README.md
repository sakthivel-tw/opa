# Gatekeeper

Install gatekeeper from helm chart

```bash
helm repo add gatekeeper https://open-policy-agent.github.io/gatekeeper/charts
helm install gatekeeper gatekeeper/gatekeeper
```

1. Create namespace
```bash
kubectl create ns gatekeeper-system
```

1. Apply config
```bash
kubectl apply -f label/sync.yaml
```


kubectl apply -f label/constraint_template.yaml
kubectl apply -f label/constraint_ns.yaml

kubectl apply -f label/dobby_ns.yaml
kubectl apply -f label/dobby_patch_ns.yaml

# Usage of Gatekeeper in Namespace


1. Apply constraint template

```bash
kubectl apply -f label/constraint_template.yaml
```

2. Apply constraint for namespace - to have gatekeeper label as string

```bash
kubectl apply -f label/constraint_ns.yaml
```

3. Create namespace without label

```bash
kubectl apply -f label/dobby_ns.yaml
```

4. Create namespace with label

```bash
kubectl apply -f label/dobby_patch_ns.yaml
```

# Usage of Gatekeeper in Pod


1. Apply constraint - to have gatekeeper label as string

```bash
kubectl apply -f label/constraint_pod.yaml
```

3. Deploy sample application without label

```bash
kubectl apply -f label/dobby_pod.yaml
```

4. Check deployment

```bash
kubectl get deploy -o wide

kubectl get rs -o wide
kubectl describe rs
```

5. Patch sample application with label

```bash
kubectl patch deployment dobby --patch "$(cat label/dobby_patch.yaml)"
```

6. Check deployment

```bash
kubectl get rs -o wide
kubectl describe rs dobby
```