### ***Introduction***

 **Kubernetes**, a container #orchestration system, has become the *overwhelming standard for managing complex container workloads in production environments*.

> **Container orchestration** is a term for software that allows operators to run groups of containers across multiple hosts. These systems coordinate with container runtimes to manage the life cycle of containerized workloads and operate an entire supporting environment for containers to create a scalable platform for deployment.
>  In short, **container orchestration** systems are designed to create a complete management environment that takes care of the hard work of operating containers with production requirements.
>  **Container orchestration** grew out of the need for an additional layer of management above individual container runtimes.

**Kubernetes** is, by far, the most popular and feature rich container orchestration system in the world. It grew out of an internal Google cluster system called Borg which was used to operate and scale workloads across the organization starting in 2003. In 2014, after transitioning internally to a new system, Google released Kubernetes as an open-source version of Borg.


### Health Checks and Self-Healing

Kubernetes takes responsibility for knowing about and responding to changes in the health of your containers. *If a container fails to start properly, Kubernetes will try to start it again. Similarly, if a container exits prematurely, Kubernetes will notice and reschedule it to reach the previous level of availability.* **While this is happening, it will also automatically adjust the networking to make sure no new traffic is forwarded to the unhealthy containers.**

Kubernetes provides mechanisms for defining your own criteria for container health, which it will then monitor for you. Kubernetes can check for healthy behavior by executing a command within the container itself, by looking for a specific response to an HTTP request at a specific endpoint, or by attempting a TCP connection to a certain port. This allows you to define the exact behavior of a healthy component so that Kubernetes can take action if it deviates.


### Workload-Specific Management Features

Kubernetes is great at managing containers, but it does so by building and working with more complex objects on top of the container paradigm. This layering comes with additional capabilities as more specific use cases are targeted.

For example,***Kubernetes wraps all containers within an object it calls Pods***, **which is its smallest unit of management**. *To enable horizontal scaling, Pods are managed by ReplicaSets. To add roll out and rollback features, ReplicaSets are managed by Deployments.* Each additional abstraction adds new features, guarantees, and capabilities without much additional complexity. Different abstractions exist to run one-off Pods, to run Pods on every node in the cluster, and to run Pods that require special storage management.

### Network Management, Service Discovery, and Load Balancing

Kubernetes pays **special attention to the communication requirements of running different types of applications in a clustered environment.** Connectivity needs to be configurable, secure, and reliable by default. Kubernetes provides ***robust*** *networking capabilities out of the box* but also allows for other projects to enhance or modify the networking features available. This allows administrators to tailor their network environment to meet their requirements.

Beyond basic connectivity, Kubernetes also provides application-related network features. *Service discovery is built into the platform*, **allowing applications and components to easily find and route traffic to one another.** Similarly, ***load balancing is available out of the box, allowing you to route requests to an entire pool of containers from a single endpoint.***

### Separate Secret and Configuration Management

By design, Kubernetes embraces the software development best practices by providing mechanisms for managing configuration separate from applications themselves. The workload definitions that are used by Kubernetes can reference configuration values that can be stored and managed separately. This allows you to standardize your application definitions while retaining flexibility, allowing you to adjust variable data to match the needs of the current environment.

Similarly, Kubernetes offers a separate category for data that should be **considered secret.** *Separating sensitive data from regular configuration data allows organizations to allow access to important information without negatively impacting the security of the system. ***Secrets in Kubernetes can be protected by handling them through separate, more closely guarded processes.***

### ***How Kubernetes Works***

Now that you understand some of the benefits that Kubernetes offers, let’s talk briefly about how Kubernetes works. This will be a simple explanation as later guides will cover the Kubernetes architecture and workloads in more depth.

The basic idea behind Kubernetes is to provide a resilient platform for containerized workloads. On an architecture level, **Kubernetes is a clustered system comprised of master (or control plane) nodes, responsible for the orchestration logic, resource management, scheduling, etc., and worker nodes, responsible for running assigned container workloads and reporting back to the control plane.** These systems work in unison to provide a stable platform managed through an ***API server***, **which is used by tools like `kubectl`, the standard Kubernetes command line client.**

Kubernetes not only manages the life cycle of containers, it also helps with what is in some ways a trickier task: managing the connectivity between containers and hosts. As containers are created and destroyed, interfaces between components need to be refreshed with up-to-date information about how to communicate with each other and how to receive outside requests. Kubernetes takes care of a lot of this complexity by providing a stable, self-updating service model on top of groups of applications to route traffic appropriately and to expose the correct interfaces to the outside world.

### ***Main Components of K8s***

Kubernetes (K8s) consists of several key components that work together to manage and orchestrate containerized applications. Here are the main components of a Kubernetes cluster:

1. Master Components:
    
    - API Server: Acts as the front-end for the Kubernetes control plane. It exposes the Kubernetes API, which clients use to interact with the cluster.
    - etcd: Distributed key-value store that stores the cluster's configuration data, state, and metadata. It provides reliable and consistent storage for Kubernetes.
    - Scheduler: Assigns pods (groups of containers) to nodes based on resource requirements, constraints, and other policies.
    - Controller Manager: Manages various controllers that handle different aspects of the cluster, such as replication, endpoints, service accounts, and more.
    
2. Node Components:
    
    - kubelet: Runs on each node and communicates with the master components. It manages the containers, starts and stops them, and reports their status to the master.
    - kube-proxy: Manages network connectivity between services within the cluster by setting up and maintaining network rules and forwarding traffic.
    - Container Runtime: The underlying software responsible for running containers, such as Docker, containerd, or CRI-O. It pulls container images and starts containers.
    
3. Add-Ons and Supporting Components:
    
    - DNS Service: Provides DNS-based service discovery and enables communication between services using their names.
    - Ingress Controller: Manages inbound network traffic to services within the cluster, typically by acting as a reverse proxy and applying routing rules.
    - Dashboard: A web-based graphical user interface (GUI) for managing and monitoring the Kubernetes cluster.
    - Metrics Server: Collects resource utilization data from nodes and pods and exposes it as metrics in the Kubernetes API.
    - Persistent Volumes: Abstraction layer that allows pods to request and use durable storage. It decouples storage from the lifecycle of pods.
    - Service Mesh (e.g., Istio): Provides advanced networking and observability capabilities, including traffic management, load balancing, and monitoring.
	

These components work together to provide the core functionalities of Kubernetes, including container orchestration, scaling, automated deployment, service discovery, and load balancing. Each component has a specific role in managing the lifecycle of containers and ensuring the desired state of the cluster.

