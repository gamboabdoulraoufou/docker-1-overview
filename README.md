### Docker-1-overview

> What is Docker?  

Containerization is the process of distributing and deploying applications in a portable and predictable way. It accomplishes this by packaging components and their dependencies into standardized, isolated, lightweight process environments called containers that can be easily deployed to distributed systems, allowing the system to scale easily and survive machine and application failures.  
Docker is the most common containerization software in use today.

![Docker archtecture](https://github.com/gamboabdoulraoufou/docker-1-overview/blob/master/img/docker_archi.png)

In this image, you can see how containers relate to the host system. Containers isolate individual applications and use operating system resources that have been abstracted by Docker. 

> Docker’s main advantages  

- Lightweight resource utilization: instead of virtualizing an entire operating system, containers isolate at the process level and use the host’s kernel.
- Portability: all of the dependencies for a containerized application are bundled inside of the container, allowing it to run on any Docker host.
- Predictability: The host does not care about what is running inside of the container and the container does not care about which host it is running on.  The interfaces are standardized and the interactions are predictable.

> Service Discovery and Global Configuration Stores  

Service discovery is used so that containers can find out about the environment they have been introduced to without administrator intervention. They can find connection information for the components they must interact with, and they can register themselves so that other tools know that they are available. 

![Docker service discovery](https://github.com/gamboabdoulraoufou/docker-1-overview/blob/master/img/docker_service_discovery.png)

In the above image, you can see an example flow in which one application registers its connection information with the discovery service system. Once registered, other applications can query the discovery service to find out how to connect to the application

Some popular service discovery tools and related projects are:
- etcd
- consul
- zookeeper
- crypt
- confd

> Networking Tools

Docker's native networking capabilities provide two mechanisms for hooking containers together: 
- The first is to expose a container's ports and optionally map to the host system for external routing
- The other method is to allow containers to communicate by using Docker "links". A linked container will get connection information about its counterpart, allowing it to automatically connect if it is configured to pay attention to those variables.

This basic level of networking is suitable for single-host or closely managed environments. However, the Docker ecosystem has produce a variety of projects that focus on expanding the networking functionality:
- Overlay networking to simplify and unify the address space across multiple hosts.
- Virtual private networks adapted to provide secure communication between various components.
- Assigning per-host or per-application subnetting
- Establishing macvlan interfaces for communication
- Configuring custom MAC addresses, gateways, etc. for your containers

Some projects that are involved with improving Docker networking are:
- flannel: Overlay network providing each host with a separate subnet.
- weave: Overlay network portraying all containers on a single network.
- pipework: Advanced networking toolkit for arbitrarily advanced networking configurations.

> Scheduling, Cluster Management, and Orchestration  

Another component needed when building a clustered container environment is a scheduler. Schedulers are responsible for starting containers on the available hosts.

![Docker scheduler](https://github.com/gamboabdoulraoufou/docker-1-overview/blob/master/img/docker_scheduler.png)

The image above demonstrates a scheduling decision. The request is given through an API or management tool. From here, the scheduler evaluates the conditions of the request and the state of the available hosts. In this example, it pulls information about container density from a distributed data store / discovery service (as discussed above) so that it can place the new application on the least busy host.

This host selection process is one of the core responsibilities of the scheduler. Usually, it has functions that automate this process with the administrator having the option to specify certain constraints. Some of these constraints may be:

- Schedule the container on the same host as another given container.
- Make sure that the container is not placed on the same host as another given container.
- Place the container on a host with a matching label or metadata.
- Place the container on the least busy host.
- Run the container on every host in the cluster.
- The scheduler is responsible for loading containers onto relevant hosts and starting, stopping, and managing the life cycle of the process.

Because the scheduler must interact with each host in the group, cluster management functions are also typically included. These allow the scheduler to get information about the members and perform administration tasks. Orchestration in this context generally refers to the combination of container scheduling and managing hosts.

Some popular projects that function as schedulers and fleet management tools are:
- fleet: scheduler and cluster management tool.
- marathon: scheduler and service management tool.
- Swarm: scheduler and service management tool.
- mesos: host abstraction service that consolidates host resources for the scheduler.
- kubernetes: advanced scheduler capable of managing container groups.
- compose: container orchestration tool for creating container groups.


