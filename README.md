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

### Step 3.2 : create ingress using Nginx Controller

Install Nginx ingress controller:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.0/deploy/static/provider/cloud/deploy.yaml
```

## Step 4 : Configure application using configMap

## Step 5 : Use secrets to secure confidential data

## Step 6 (Bonus) : Deploy Backend storage (Redis)
## Step 7 (Bonus) : Add HTML Content to the Application
## Step 8 (Bonus) : use Helm or kustomize