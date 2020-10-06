+ Getting Start with Kubernets 2e
+ Hands on Kubernets
+ Certified Kubernetes Application Developer(CKAD)
+ Certified Kubernetes Administrator(CKA)

Container Solutions

+ LXC offers Linux-native containers and has been around for a long time
+ Systemd-nspawn offers Systemd integrated containers
+ Docker started in 2013 and has made containers the success it currently is
+ Podman is offered in recent versions of Red Hat Enterprise Linux and offers a more secure and Lightweight solution to run containers


Corporate container Requirements

+ Automated rollouts and rollback
+ Container Archestration
+ Storage archestration
+ Service discovery and load balancing
+ Self-healing
+ High-availability
+ Scalability
+ batch execution


> Large-scale cluster management Bog
> https://research.google/pubs/pub43438/


# Kubernetes Ecosystem

+ Kubernetes is the core project, managed by CNCF
+ the Kubernetes conference Kubecon is a major event about the current and  future status of Kubernetes projects twice a year
+ A new release of Kubernetes is published every 3 months


# Understanding CNCF Projects

+ Different CNCF projects exists and make Kubernetes an easy-to-extend solution
  + CR-O - a Kubernetes Container Runtime
  + CNI - the common network interface
  + Jaeger: an Operator, that eases packaging, deploying and managing applications
  + rook - a storage archstrator for Kubernetes
  + and many more
+ Notice that Kubernetes itself is also "just" a CNCF project

## Unerstanding Project Status

+ Project status is determined by the CNCF
  + Sandbox: the project is new and used by innovators only
  + Incubating: adoption of the project is becoming more wid-spread
  + Graduated: the project is part of the core Kubernetes environment
+ For current project status, see https://www.cncf.io/projects/

## Understanding Kubernetes Solutions

+ CNCF is owner of the Kubernetes code
+ Different commercial and open source distributions are available to work with Kubernetes
  + Rancher
  + Red Hat OpenShift Container Platform
  + SUSE Containers as a Service(Caas)
+ Kubernetes can be used on-premise, but also as a managed solution in public cloud
  + AKS is the Azure Kubernetes service
  + EKS is the Amazon Kubernetes platform
  + google GKE is offered by Google


## Understanding Kubernetes Certification

+ Certified Kubernetes Application Developer(CKAD) is a performanced-based exam wherre candidates can prove they are capable of running applications in Kubernetes
  + Consider CKAD an entry-level exam that test Kubernetes basic skills
  + It is NOT exclusively targeted at developers and no programming skills are required to take it
+ Certified Kubernetes Administrator(CKA) is a performance-based exam where candidate are tested on their ability to run applications in Kubernetes clusters, as well as test and manage Kubernetes clusters
  + It is recommended to take CKAD before taking CKA



## Selecting a Container Distribution

+ fedora Atomic
+ CoreOS



> docker inspect --format="{{.NetworkSettings.IPAddress}}" containername


> https://github.com/yaowenqiang/cinf
> http://containerz.info/


## Understanding Docker Networking

+ bridge: the default network driver, used when applications run in standalone containers that need to communicate
+ host: only in Docker swarm: used for standalone containers, where the container connects to the host network directly
+ overlay: used in docker swarm to connect multiple Docker daemons together
+ macvlan: used with legacy applications: where a MAC address can be assigned to a continer to have it appear as a physical device on the network
+ None: disables networking, which is useful if a custom network driver is used.



> cat /proc/net/fib_trie  get ip without any command
> /var/lib/docker/overlay2/18d108988b28884ea83d8ff7a224aeedd65ce478769da17fcd703a761427fb29/diff/root/hello
/var/lib/docker/overlay2/18d108988b28884ea83d8ff7a224aeedd65ce478769da17fcd703a761427fb29/merged/root/hello
/var/lib/docker/aufs/diff/161d4c89734c99195af973c1b3edead3978e9c5ad47793d3856bdddb10ab443b/hello

> ps -fax


docker run --rm -v /dev/log:/dev/log fedora  logger "message from the container"
> journalctl | grep container # centos host
>  cat /var/log/syslog | grep container # ubuntu host

> kubectl explain
> kubectl explain pod
> kubectl explain pod.spec
> kubectl explain pod.spec.containers
> kubectl get <resources> -o yaml > mresource.ymln
> kubectl api-resources
> kubectl api-versions

> https://kubernetes.io/docs/home/

> use the search function

> kubectl get all  --selector k8s-app=nginx  --show-labels



> kubectl create ns will crate a Nmespace

with kubectl, use --all-namespaces to show resources in all Namespaces

the optional kubectx package can be used to used to make switching between Namespaces easier; it contains kbectx to switch between context, and kubens to switch between Namespaces


# Understanding Context

+ The context consists of the clustername and namespace that the current user connects to
+ Context is set in the user settings, use kubectl config get to show current context
+ If multiple clusters are available to a Kubernetes client, switching context is relevant
+ If multiple namespaces exist withing a cluster, switching context is relevant
+ kubens provides a shell script that makes switching between namespaces easier

## Installing kubens

> https://github.com/ahmetb/kubectx

> kubectl get pods -A 
> kubectl get pods  --all-namespaces


# Managing Application Scalability

+ kubectl scale allows you to modify the number of replicas for a current application
> kubectl edit allows you to edit the current Etcd configuration to modify the number of replicas for a current application

> kubectl scale --replicas=3 -f foo.yaml


## Understanding Deployment History

> kubectl rollout history
> kubectl rollout undo

> kubectl rollout undo daemonset/abc --to-revision=3


> kubectl explain deploy.spec.strategy


