### docker-1-overview

> What is Docker?  

Containerization is the process of distributing and deploying applications in a portable and predictable way. It accomplishes this by packaging components and their dependencies into standardized, isolated, lightweight process environments called containers that can be easily deployed to distributed systems, allowing the system to scale easily and survive machine and application failures.  
Docker is the most common containerization software in use today.

![Docker archtecture](https://github.com/gamboabdoulraoufou/docker-1-overview/blob/master/img/docker_archi.png)

In this image, you can see how containers relate to the host system. Containers isolate individual applications and use operating system resources that have been abstracted by Docker. 

> Docker’s main advantages  

- Lightweight resource utilization: instead of virtualizing an entire operating system, containers isolate at the process level and use the host’s kernel.
- Portability: all of the dependencies for a containerized application are bundled inside of the container, allowing it to run on any Docker host.
- Predictability: The host does not care about what is running inside of the container and the container does not care about which host it is running on.  The interfaces are standardized and the interactions are predictable.

> Archi

