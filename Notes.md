## Notes

- Nodes == Minions
---
- Basic `kubectl` commands-
```sh
    - kubectl run hello-minikube
    - kubectl cluster-info
    - kubectl get nodes
```

- Kubernetes introduced CRI(Container Runtime Interface) -> to allow any vendor to work as a container runtime for Kubernetes, as long as they adhere to the OCI(Open Container Initiative) standards.
- K8s introduced `dockershim` to support docker (outside of the container runtime interface) as docker was not CRI compliant.
- K8s in v1.24, it was decided to remove `dockershim` completely due to extra effort was required to maintain it, though `containerD` was there.
- ContainerD - `ctr` cli tool, mostly to `debug` containerD, `nerdctl` provides stable user experience.
- `Lazy pulling` is a technique of pulling container images aiming at the faster cold start. This allows container runtimes to startup containers without waiting for the entire image contents. Instead, the necessary chunks of contents (e.g. individual files) are fetched on-demand. This shortens the container startup latency from tens of seconds into a few seconds at the best.
- `crictl` CLI tool is a single interface used to interact with the CRI-compatible container runtime, mostly for `debugging` purpose.
---
