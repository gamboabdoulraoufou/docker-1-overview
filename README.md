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

![Docker archtecture](https://github.com/gamboabdoulraoufou/docker-1-overview/blob/master/img/docker_archi.png)

Service discovery is used so that containers can find out about the environment they have been introduced to without administrator intervention. They can find connection information for the components they must interact with, and they can register themselves so that other tools know that they are available. 

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

This basic level of networking is suitable for single-host or closely managed environments. However, the Docker ecosystem has produce a variety of projects that focus on expanding the networking functionality available to operators and developers. Some additional networking capabilities available through additional tools include:

Overlay networking to simplify and unify the address space across multiple hosts.
Virtual private networks adapted to provide secure communication between various components.
Assigning per-host or per-application subnetting
Establishing macvlan interfaces for communication
Configuring custom MAC addresses, gateways, etc. for your containers

Some projects that are involved with improving Docker networking are:
- flannel: Overlay network providing each host with a separate subnet.
- weave: Overlay network portraying all containers on a single network.
- pipework: Advanced networking toolkit for arbitrarily advanced networking configurations.

