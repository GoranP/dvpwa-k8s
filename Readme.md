Deployment of secured dvpwa
===========================


In directory dvpwa is helm chart that will deploy dvpwa application and all its dependencies.
Dependencies are defined in Chart.yaml. There is one dependency chart named "db-backend".
Dependency chart installs secured postgres and redis as prerequisites for dvpwa app.

Postgres statefulset will create 1GB disk and volume template forr postgres data. 

Solution is tested on Docker Desktop (Mac) versinon `4.8.2 (79419)` with Kubernetes engine enabled.

Preprequisites
==============

Install Helm with following [installation instructions](https://helm.sh/docs/intro/install/) and kubectl with [following instructions](https://kubernetes.io/docs/tasks/tools/) on local machine. 

Test that `kubectl`is working with local kubernetes. Eg: run `kubectl get pods -A `

Deploy app
==========

Execute following from root directory of this repo:
```code
helm install dvpwa dvpwa/
```

Wait until everything is deployed. 
Command `kubectl get pods` should reture someting like this:

```code
NAME                     READY   STATUS    RESTARTS   AGE
dvpwa-7857f77c46-fs5nd   1/1     Running   0          69s
postgres-0               1/1     Running   0          69s
redis-bfbc66d6c-5g6tg    1/1     Running   0          69s
```

Access application with browser on [localhost:8080](http://localhost:8080)