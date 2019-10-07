# Kubernetes and Helm

- Work on dev machine:

```sh
kname dev-triage
kexec devmachine
```

- Deploy a yaml file with Kubernetes:

```sh
k deploy -f box.yaml
```

## Helm

- Helm deploy current directory chart:

```sh
helm install --name mysqltest2 .
helm install --name mysqltest2 --dry-run --debug .
```
