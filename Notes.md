## Notes

### Query K8s doc instead going to google!!!!

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
- ContainerD `ctr` cli tool, mostly to `debug` containerD, `nerdctl` provides stable user experience.
- `Lazy pulling` is a technique of pulling container images aiming at the faster cold start. This allows container runtimes to startup containers without waiting for the entire image contents. Instead, the necessary chunks of contents (e.g. individual files) are fetched on-demand. This shortens the container startup latency from tens of seconds into a few seconds at the best.
- `crictl` CLI tool is a single interface used to interact with the CRI-compatible container runtime, mostly for `debugging` purpose.
---
- Pods usually have a `one-to-one` relationship with containers running your application.
- To scale up, you create new Pods and to scale down, you delete existing Pod. You do not add additional containers to an existing Pod to scale your application.
- Though a single Pod can have multiple containers, except for the fact that they're usually not multiple containers of the `same kind`.
---
## YAML
- Kubernetes uses YAML files as inputs for the creation of objects such as `pods, replicas, deployments, services, et cetera.`
- A Kubernetes definition file always contains four top level fields: `The API version, kind, metadata, and spec.` These are the top level or `root level` properties. These are also `required` fields so you must have them in your configuration file.
- `apiVersion`: This is the version of the Kubernetes API we are using to `create` the object.
- `kind`: The kind refers to the type of object we are trying to create, which in this case happens to be a `pod`, so we will set it as pod. Some other possible values here could be `replica` set or `deployment` or `service`.
- `metadata`: The metadata is data about the object like its name, labels, et cetera. This is in the form of a `dictionary`.
- `spec`: `Specification` section which is written as spec. Depending on the object we are going to create, this is where we would provide additional information to Kubernetes pertaining to that object. It is a `dict`.
---
## REPLICA SETS, Controller, Replication Controller
- Even if you have a single pod the replication controller can help by automatically bringing up a new pod when the existing one fails.
- Thus, the replication controller ensures that the specified number of pods are running at all times even if it's just one or hundred.
- Another reason we need replication controller is to create multiple pods to share the load across them.
- The replication controller spans across multiple nodes in the cluster. It helps us balance the load across multiple pods on different nodes as well as scale our application when the demand increases.
- Note that there are two similar terms `replication controller` and `replica set`. Both have the same purpose, but they're not the same.
- Replication controller is the older technology that is being replaced by replica set.
- Replica set is the new recommended way to set up replication.
- Replica set requires a `selector` definition. The selector section helps the replica set identify what pods fall under it.
- Need for selector is because replica set can also manage pods that were not created as part of the replica set creation.
- Selector is one of the `major differences` between replication controller and replica set. The selector is not a required field in case of a replication controller but it is still available.
---