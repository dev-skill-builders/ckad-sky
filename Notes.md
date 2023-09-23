## Notes

- Nodes == Minions

- Basic `kubectl` commands-
```sh
    - kubectl run hello-minikube
    - kubectl cluster-info
    - kubectl get nodes
```

- Kubernetes introduced CRI(Container Runtime Interface) -> to alllow any vendor to worknas a container runtime for Kubernetes, as long as they adhere to the OCI(Open Container Initiative) standards.

- K8s introduced `dockershim` to support docker as docker was not CRI compliant. dsfdsf