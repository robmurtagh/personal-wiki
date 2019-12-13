# Kubernetes, Helm and Docker

- Launch with terminal and custom entry point:

```sh
docker run -it --entrypoint=/bin/bash flyway/flyway:latest
```

- Work on dev machine:

```sh
kname dev-triage
kexec devmachine
```

- Deploy a yaml file with Kubernetes:

```sh
k create -f box.yaml
```

## Helm

- Helm deploy current directory chart:

```sh
helm install --name mysqltest2 .
helm install --name mysqltest2 --dry-run --debug .
```

```sh
helm repo list
helm repo update
helm search s3-mysqlrestore

helm plugin install https://github.com/chartmuseum/helm-push
helm push ./ https://dev-charts.k8s.corp.beno.ai
```

```sh
docker run -it --entrypoint bash gitlab.beno.ai:4567/ai/hypgen/biograph/aws:0.0.3
```
