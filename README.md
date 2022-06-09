# Beginner friendly kubernetes workshop

inspired and update from : https://www.magalix.com/blog/deploying-an-application-on-kubernetes-from-a-to-z

## Step 1 : containerize application

```bash
cd step1/
docker build -t sample-api .
```

## Requirement before starting wotking with K8s

check context : 

```bash
kubectl config get-contexts
```

select context: 

```bash
kubectl config set-context docker-desktop
```

Create a namespace :

```bash
kubectl create namespace frontend
```

Change Namespace :
```
kubectl config set-context --current --namespace=frontend
# Validate it
kubectl config view --minify | grep namespace:
```

## Step 2 : Create a deployment

```bash
cd step2/
kubectl apply -f deployment.yaml
```

## Step 3 : Expose application 

### Step 3.1 : create service

```bash
cd step3/
kubectl apply -f frontend-svc.yaml
```

### Step 3.2 (optional) : create ingress using Nginx Controller

Install Nginx ingress controller:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.0/deploy/static/provider/cloud/deploy.yaml

kubectl apply -f step3/ingress.yaml

```

### step 3.3 : port forward

```bash
kubectl port-forward services/frontend-svc 3000:3000  
```

## Step 4 : Configure application using configMap

Creat a configmap:

```bash
cd step4/
kubectl apply -f configmap.yml
```

## Step 5 : Use secrets to secure confidential data

```bash
kubectl create secret generic redis-password --from-literal=redis-password=password123
```

Note : uncomment and redeploy deployment in step 2, then check its status. You did it!

## Step 6 (Bonus) : Add HTML Content to the Application
## Step 7 (Bonus) : Deploy Backend storage (Redis)
## Step 8 (Bonus) : use Helm or kustomize

