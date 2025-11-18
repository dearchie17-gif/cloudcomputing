# cloudcomputing
cloud computing basics


Concepts of cloud computing, basics, related topics details 



# Cloud Computing 

Cloud computing is the delivery of computing services—including servers, storage, databases, networking, software, analytics, and intelligence—over the Internet ("the cloud"). This allows for faster innovation, flexible resources, and economies of scale.


 # Docker:-
Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run.
 
 Key features of Docker include:-;
1.Containerization:
Applications run in isolated environments, which makes them portable and easy to manage.

2. Images and Dockerfile:
Docker uses images as blueprints for containers. A Dockerfile is a script that contains instructions to build an image.

3. Docker Hub:
A cloud-based registry where users can share and distribute Docker image

How Docker works:-
Docker works by providing a standard way to run your code. Docker is an operating system for containers. Similar to how a virtual machine virtualizes .containers virtualize the operating system of a server. Docker is installed on each server and provides simple commands you can use to build, start, or stop containers.
# HOW TO INSTALL DOCKER:- 

To install Docker on a remote server using PuTTY, you'll first need to ensure you have access to a Linux server (like Ubuntu, CentOS, etc.) via SSH. Here's a step-by-step guide:

Step 1:Connect to Your Server


 Step 2: Update Your Package Index

Before installing Docker, it’s a good idea to update the package index:

```bash
sudo apt update
```


Step 3:Install Prerequisites

For Ubuntu, install the required packages:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

For CentOS, run:

```bash
sudo yum install -y yum-utils
```

Step 4: Add Docker’s Official GPG Key

For Ubuntu:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

For CentOS:

```bash
sudo rpm --import https://download.docker.com/linux/centos/gpg
```

Step 5: Set Up the Stable Repository
For Ubuntu:

```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```


For CentOS:

```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

Step 6: Install Docker

For Ubuntu:

```bash
sudo apt update
```

```bash
sudo apt install docker-ce
```

For CentOS:

```bash
sudo yum install docker-ce
```

Step 7: Start Docker

Enable and start the Docker service:


```bash
sudo systemctl start docker
```

```bash
sudo systemctl enable docker
```

 Step 8: Verify the Installation

Check if Docker is running:

```bash
sudo systemctl status docker
```

You can also run a test container:

```bash
sudo docker run hello-world
```

 Step 9: (Optional) Manage Docker as a Non-Root User

If you want to run Docker commands without sudo, add your user to the 

Docker group:

```bash
sudo usermod -aG docker $USER
```

After running this command, log out and back in for the changes to take effect.



You’ve successfully installed Docker using PuTTY! If you have any questions or run into issues, feel free to ask.


# container:-
A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

(in other and simple words )

Containers are an abstraction at the app layer that packages code and dependencies together. Multiple containers can run on the same machine and share the OS kernel with other containers, each running as isolated processes in user space. Containers take up less space than VMs (container images are typically tens of MBs in size), can handle more applications and require fewer VMs and Operating systems

Screenshot_2024_0918_124201

# NGINX:-

NGINX is a high-performance web server and reverse proxy server that is widely used for serving web applications, handling HTTP and HTTPS requests, and load balancing traffic. It is known for its speed, efficiency, and ability to handle a large number of concurrent connections with low resource usage.


# using EC2 in aws:-

First open aws search EC2 then Launch Instance and there select keypair in putty then download it

after that Launch it and run putty and paste public id on HOST NAME and open that downloaded key pair for putty in SSH then Auth then Credentials and open there

 after that run it and write username as ubuntu as selected os and then type following commands

```bash
sudo apt update
```


```bash
sudo apt install apache2
```

 to install a web server on ip then

```bash
sudo su
```

 for convert $ into # for getting admin role then

```bash
cd /var/www/html/
```

then

```bash
ls
```

 for list of html file in it

 then copy that html file name and write

```bash
rm index.html
```

```bash
rm means remove command
```

```bash
vi index.html
```

 this will open a notepad like and write html code there like (vi is editor) -

 then press ctrl+c then shift+colon then write wq and enter

 now copy your public ip and paste it on browser you will see the texts written by you (by using html above)

 congratulations you got it 👏🏻 🎉 


# USING CONTAINER IN VM and adding nginx server by Docker:- 

First open aws search EC2 then Launch Instance and there select keypair in putty then download it

after that edit network setting and click on add security group rule and select TCP,UDP,ALL TRAFFIC AND SELECT EVERYWHERE SOURCE TYPE IN THEM then Launch it and run putty and paste public id on HOST NAME and open that downloaded key pair for putty in SSH 


(SSH (Secure Shell) is a way to securely connect to another computer over a network. It's like a safe tunnel that allows you to control a remote computer and transfer files to it, without anyone else being able to listen in or interfere with the connection.)

then Auth then Credentials and open there

after that run it and write username as ubuntu as selected os and then type following commands

```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```

 this will install and run docker in your vm

```bash
newgrp docker
```

 this command will help us to use docker

```bash
docker ps
```

 this will list docker

```bash
docker --version
```

 this will display the version of docker installed

 now installing nginx

```bash
docker pull nginx
```

 You can download Nginx from a pre-built Docker image, with a default Nginx configuration, by above command. This downloads all the necessary components for the container.

```bash
docker run --name docker-nginx -p 80:80 nginx
```

Nginx installed, you can configure the container so that it’s publicly accessible as a web server.

 run is the command to create a new container

 The --name flag is how you specify the name of the container. If left blank, a generated name like nostalgic_hopper will be assigned.

 -p specifies the port you are exposing in the format of -p local-machine-port:internal-container-port. In this case, you are mapping port :80 in the container to port :80 on the server.

nginx is the name of the image on Docker Hub.

 now this will show this on your public ip

![Screenshot_2024_0923_210801](https://github.com/user-attachments/assets/12ed503f-9c71-4c80-bcb3-468c989c0258)

 In your terminal, enter CTRL+C to stop the container from running.

```bash
docker ps -a
```

 verify the container status with this command

```bash
docker rm docker-nginx
```

 Remove the existing container

```bash
docker run --name docker-nginx -p 80:80 -d nginx
```

 Create a new, detached Nginx container,By attaching the -d flag, you are running this container in the background.

```bash
docker ps
```
 this will obtain info about your container

```bash
docker stop docker-nginx
```

 Stop the container

```bash
docker rm docker-nginx
```

 remove the container

# Building a Web Page to Serve on Nginx

```bash
mkdir -p ~/docker-nginx/html
```

 Create a new directory for your website content within the home directory

```bash
cd ~/docker-nginx/html
```

 by this you navigate into this

```bash
vi index.html
```

 now press i and write your code in html like 


![Screenshot_2024_0923_211405](https://github.com/user-attachments/assets/7cd1afd2-b42e-43c1-94ed-86a1f1ebedf9)

 then press ctrl+c then shift+colon then write wq and enter

```bash
docker run --name docker-nginx -p 80:80 -d -v ~/docker-nginx/html:/usr/share/nginx/html nginx
```

Linking the Container to the Local Filesystem

 open your public ip in browser you will see as the content as your html code

 here you go 👏🏻

 Using Your Own Nginx Configuration File

```bash
cd ~/docker-nginx
```


```bash
docker cp docker-nginx:/etc/nginx/conf.d/default.conf default.conf
```

 Copy the Nginx config directory into your project folder

```bash
docker stop docker-nginx
```

```bash
docker rm docker-nginx
```

 to rebuild the container stop the container then remove it

```bash
docker run --name docker-nginx -p 80:80 -v ~/docker-nginx/html:/usr/share/nginx/html -v ~/docker-nginx/default.conf:/etc/nginx/conf.d/default.conf -d nginx
```

This command links the custom website pages to the container.

```bash
docker restart docker-nginx
```

 you need to restart your container to reflect changes on the associated pages.


# Kubernestes :-
Kubernetes (sometimes shortened to K8s with the 8 standing for the number of letters between the “K” and the “s”) is an open source system to deploy, scale, and manage containerized applications anywhere.

Kubernetes has built-in commands to handle a lot of the heavy lifting that goes into application management, allowing you to automate day-to-day operations. You can make sure applications are always running the way you intended them to run. 
# Main Function/Usage:
- Kubernetes manages containers, which package an application and its dependencies together to ensure it runs consistently across different environments. Containers are isolated units but lightweight compared to virtual machines.

**NODE**
A Node is the fundamental worker machine in a Kubernetes cluster. It can be either a physical machine or a virtual machine in a cloud environment. Each node runs the necessary services to support the containers it hosts, such as the container runtime (e.g., Docker), the Kubelet (which communicates with the Kubernetes control plane), and Kube-proxy (which manages networking for the pods).

TYPES OF NODES

Master Node- The master node is the brain of the Kubernetes cluster and handles scheduling, maintaining the desired state, and managing resources. It contains components like API Server,Scheduler,Controller Manager

Worker Node- Worker nodes are the machines where application workloads run. These nodes run the containers and host the pods that make up an application. They handle the execution of the actual tasks, networking, and storage management.

**PODS**
A Pod is the smallest and most basic deployable unit in Kubernetes (K8s). It represents a single instance of a running process in your cluster and can contain one or more containers that share the same network and storage resources. Typically, pods are used to run a single container, but there are cases where multiple containers need to work together closely, and in these cases, a pod will contain multiple tightly coupled containers.

Kubernetes Architecture
A Kubernetes environment consists of a control plane (master), a distributed storage system for keeping the cluster state consistent (etcd), and a number of cluster nodes (Kubelets).
![image](https://github.com/user-attachments/assets/0adc0296-4220-4d19-b0bb-a5b2807b1c9f)

# Minikube 
Minikube is a tool that sets up a Kubernetes environment on a local PC or laptop. This tool provides an easy means of creating a local Kubernetes environment on any Linux, Mac, or Windows system, where you can experiment with and test Kubernetes deployments. 

 # Orchestration
Orchestration is the automated coordination and management of complex tasks and processes, ensuring that different services and components work together effectively. In IT, it streamlines workflows and manages dependencies, especially in containerized environments.

**How to install minikube in dextop?**
Step 1: Set Up an AWS EC2 Instance
1.Log in to the AWS Management Console.
2.Launch an EC2 Instance:
Choose an Amazon Machine Image (AMI). For simplicity, a basic Ubuntu Server AMI (like Ubuntu 20.04) works well.

Select an instance type (e.g., t2.micro if you are using the free tier).

Configure security groups to allow SSH (port 22) and any other necessary ports (like 8443 for Kubernetes).

Launch the instance and download the key pair for SSH access.

Step 2: SSH into Your EC2 Instance
$ Use the key pair to SSH into your instance:

**ssh -i /path/to/your-key.pem ubuntu@your-ec2-instance-public-dns **

Step 3: Install Dependencies
Once you're logged in, update the package manager and install required packages:

sudo apt update sudo apt install -y curl wget apt-transport-https

Step 4: Install Minikube
Download Minikube
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 2. Install Minikube:

sudo install minikube /usr/local/bin/

Step 5: Install a Virtualization Driver
Minikube requires a virtualization driver to run. Since AWS does not support KVM, you can use Docker as the driver.

1. Install Docker
sudo apt install -y docker.io

2. Start Docker and enable it to run at startup
sudo systemctl start docker sudo systemctl enable docker

3. Add your user to the Docker group:
sudo usermod -aG docker $USER

Log out and back in for this change to take effect.

Step 6: Start Minikube
Now you can start Minikube using Docker as the driver:

minikube start --driver=docker

Step 7: Verify Installation
Check if Minikube is running:
minikube status

Step 8: Accessing Kubernetes Dashboard (Optional)
You can also access the Kubernetes dashboard:

minikube dashboard

Congratulations We achieved our Goal.

# KVM:- Kernel-based Virtual Machine

It is a technology that allows you to run multiple operating systems on a single physical machine. It turns the Linux kernel into a hypervisor, enabling virtual machines (VMs) to operate as if they were separate computers. 

# Openstack :-
OpenStack is an open-source platform that lets you create and manage cloud computing services. It allows users to control computing power, storage, and networking in a data center through a web interface. Essentially, it helps organizations build their own private or public clouds, making it easier to deploy and manage applications.



 **QEMU**
QEMU is an open-source emulator and virtualization tool that allows you to run different operating systems on a host machine.



 # VPC
Amazon Virtual Private Cloud (VPC) is a virtual network that allows users to launch AWS resources in a logically isolated environment. It's a foundational service of AWS that gives users complete control over their virtual networking environment.

What is the difference between EC2 and VPC?
•EC2 is a virtual server that you can run your software on. VPC is a virtual network that you use to connect your virtual servers, and other resources.

# NETWORKING IN CLOUD


Networking in the cloud is a critical aspect of cloud computing that enables communication between various resources, services, and applications hosted in cloud environments. Here are some key concepts and components involved in cloud networking:

1)Virtual Private Cloud (VPC)

A VPC allows you to create a logically isolated network within a cloud provider's infrastructure. You can define your own IP address range, subnets, route tables, and network gateways.

2)Subnets

Subnets are segments of a VPC that help organize and secure your cloud resources. They can be public (accessible from the internet) or private (accessible only from within the VPC).

3)Load Balancer

Load balancers distribute incoming traffic across multiple servers or resources, ensuring high availability and reliability of applications. They can be application-specific (Layer 7) or network-based (Layer 4).

4)VPN and Direct Connect

Virtual Private Networks (VPNs) create secure connections between your on-premises infrastructure and cloud resources. Direct Connect offers a dedicated network connection to the cloud provider, enhancing security and performance.

5)Firewalls and Security Groups

Cloud providers offer built-in firewalls and security groups to control inbound and outbound traffic. These tools help you define rules that specify which traffic is allowed or denied.

6)Content Delivery Networks (CDN)

CDNs cache content closer to users around the globe, improving access speed and performance for web applications.

7)DNS Services

Cloud-based DNS services manage domain names and route traffic efficiently to different resources, improving reliability and speed.

8)Network Monitoring and Management

Tools for monitoring network performance, tracking usage, and troubleshooting issues are essential for maintaining cloud network health

9)TTL

TTL, or Time to Live, in the context of cloud computing typically refers to the duration that data can exist in a cache or be considered valid before being refreshed or discarded. Here are a few contexts in which TTL is relevant:

-DNS Records: TTL determines how long a DNS resolver can cache a DNS record before it must query the authoritative server again. Shorter TTL values can lead to more frequent updates but increase the load on DNS servers.

-Caching: In cloud services (like AWS, Azure, or Google Cloud), TTL can define how long cached objects (such as those in a CDN or a caching layer) are considered fresh. This helps optimize performance by reducing the need to fetch data from the source frequently.

-Session Management: TTL can also be applied to session tokens or user sessions in web applications, dictating how long a session remains active before timing out for security reasons.

-Data Expiry: In databases or storage solutions, TTL can specify how long certain data should be retained before it is automatically deleted.

10)CNI


CNI stands for Container Network Interface. It's a specification and a set of libraries designed to facilitate the networking of containers in a cloud-native environment. CNI allows containers to communicate with each other and with external networks while ensuring network configuration is flexible and scalable.

Key Concepts of CNI: ---Plugins: CNI works through a series of network plugins that can be used to configure container networking. These plugins can handle tasks like assigning IP addresses, setting up routes, and configuring firewall rules.

-Decoupled Architecture: CNI separates network configuration from the container runtime, meaning that different container orchestrators (like Kubernetes, Mesos, or Docker Swarm) can use the same networking solutions.

-IP Address Management: CNI can allocate IP addresses to containers dynamically and manage their lifecycle, including handling IP address releases when containers are stopped.

-Network Isolation: CNI supports multiple network interfaces and allows for isolation between different applications or services by creating separate network namespaces.

-Integration with Orchestrators: Most modern container orchestration platforms, especially Kubernetes, utilize CNI to manage networking between pods.

Common CNI Plugins:

-Flannel: A simple overlay network that allows containers on different hosts to communicate.

-Calico: Offers both networking and network policy for containers.

-Weave Net: Provides a virtual network for containers that works across multiple hosts.

# MOVEMENT OF PACKETS


The movement of packets in the cloud involves several layers and processes, ensuring that data can travel efficiently from one point to another, whether it's within a single data center or across a global network. Here’s a breakdown of how packets move in a cloud environment:

1. Data Center Architecture:

Physical Layer: At the base, there are physical servers and networking hardware (switches, routers).

Virtualization Layer: Virtual machines (VMs) and containers are created on these physical servers, abstracting the hardware and allowing for resource allocation and management.

2. Networking Models:

Overlay Networks: Many cloud providers use overlay networking to abstract the underlying physical network, allowing for easier management and scalability.

Software-Defined Networking (SDN): This enables centralized control of network traffic, allowing for dynamic adjustments based on load and demand.

3. Packet Routing:

Ingress/Egress Points: Packets enter and exit the cloud network through designated ingress (entry) and egress (exit) points. This could involve load balancers that distribute traffic among multiple servers.

Routing Protocols: Inside the cloud, various routing protocols (like BGP, OSPF) are used to determine the most efficient path for packet delivery.

4. Transport Layer:

TCP/UDP: Data packets are transported using protocols like TCP (for reliable, ordered communication) or UDP (for faster, connectionless communication). The choice depends on the application’s requirements.

5. Security Measures:

Firewalls and Security Groups: Packets are filtered at various points to enforce security policies. This could include virtual firewalls or security groups that control inbound and outbound traffic.

Encryption: Data packets may be encrypted in transit, particularly when moving between data centers or to/from end users, using protocols like TLS.

6. Traffic Management:

Load Balancing: Load balancers distribute incoming traffic across multiple servers to ensure no single server becomes a bottleneck.



Content Delivery Networks (CDNs): For static content, CDNs cache data at various locations to minimize latency and speed up delivery to end users.

7. Monitoring and Logging:

Network Monitoring: Tools and services monitor the flow of packets, helping to identify issues and optimize performance.

Logging: Activity logs help track packet movements and diagnose problems.

8. Inter-Cloud Communication:

Peering and Interconnection: Different cloud providers can connect through peering arrangements, allowing packets to traverse multiple clouds.

APIs: Cloud services often expose APIs that allow for data transfer between different services and applications, which involves packet movement across networks.

# IPV4


IPv4, or Internet Protocol version 4, is one of the core protocols of the Internet Protocol Suite. It is primarily responsible for addressing and routing packets of data between devices on a network. Here are the key features and concepts related to IPv4:

Key Features of IPv4:

Addressing:

-32-bit Address Space: IPv4 uses a 32-bit address format, allowing for approximately 4.3 billion unique addresses (2^32). This is often represented in decimal as four octets (e.g., 192.168.1.1).

-Classes: IPv4 addresses are categorized into classes (A, B, C, D, and E) based on their leading bits, which affect the size of the network and host portions of the address.

Subnetting:

--Network and Host Portions: An IPv4 address consists of a network part (identifying the network) and a host part (identifying the specific device on that network). Subnetting allows for the division of a larger network into smaller, more manageable sub-networks.

-CIDR Notation: Classless Inter-Domain Routing (CIDR) allows for more flexible allocation of IP addresses. For example, 192.168.1.0/24 indicates a subnet with 256 addresses. Packet Structure:

An IPv4 packet consists of a header and a payload. The header includes information like the source and destination IP addresses, protocol type, and other control information. The maximum transmission unit (MTU) defines the largest packet size that can be sent over the network.

Routing:



Routers use IPv4 addresses to determine the best path for forwarding packets across interconnected networks. Routing protocols (like BGP, OSPF, and RIP) facilitate the dynamic exchange of routing information.

Address Allocation:

IPv4 addresses are managed and allocated by the Internet Assigned Numbers Authority (IANA) and regional Internet registries (RIRs). Address exhaustion has led to the adoption of strategies like Network Address Translation (NAT) and private addressing.

Private and Public Addresses:

Certain IPv4 address ranges are designated for private use (e.g., 10.0.0.0 to 10.255.255.255, 192.168.0.0 to 192.168.255.255), which can be used internally within organizations. Public addresses are routable on the Internet and are unique across the entire network.

Limitations of IPv4:

-Address Exhaustion: The finite address space has led to IPv4 address exhaustion, prompting the need for IPv6.

-Complexity with NAT: While NAT allows multiple devices to share a single public IP, it can complicate certain applications and protocols.

-Limited Security Features: IPv4 does not inherently include security features, leading to the need for additional protocols (like IPsec) for secure communication

-Transition to IPv6: Due to the limitations of IPv4, the Internet community has been transitioning to IPv6, which uses a 128-bit address space, vastly increasing the number of available addresses and incorporating features for improved security and efficiency.

---Cilium: Uses eBPF to provide advanced networking and security features.

# Key Concepts of a Bridge in Cloud Networking:


Network Connectivity:

A bridge connects two or more separate networks, allowing them to function as a single network. This can facilitate communication between virtual machines (VMs) in different subnets or virtual networks.

Layer 2 Functionality:

Bridges operate at Layer 2 of the OSI model (Data Link Layer). They use MAC addresses to forward packets to the appropriate destination within the connected networks, making decisions based on the data link layer information.

Virtual Network Bridging:

In a cloud environment, bridges can be used to link virtual networks created by different services or instances. For example, a bridge might connect a private network in a cloud provider's infrastructure with on-premises networks.

Network Segmentation:

Bridges can be used to segment traffic within a cloud environment, enhancing security and performance by isolating network segments while still allowing them to communicate when necessary. Common Use Cases:

Hybrid Cloud Connectivity:

In hybrid cloud architectures, bridges can facilitate communication between on-premises data centers and cloud resources, allowing for seamless integration of workloads and data. Microservices Communication:

In microservices architectures, different services might run in isolated environments. Bridges help connect these services, ensuring they can communicate effectively. Multi-Cloud Environments:

When using multiple cloud providers, bridges can help interconnect services across these clouds, allowing data and workloads to flow freely. VPN and Security:

Bridges can be part of a broader network security strategy, helping to connect secure networks or provide VPN access to resources in the cloud.

Implementation in Cloud Providers:
-AWS: AWS offers Virtual Private Cloud (VPC) Peering, which allows for the creation of isolated networks that can be connected with bridges.

-Azure: Azure Virtual Network Peering enables communication between Azure virtual networks.

-Google Cloud: Google Cloud's VPC allows for network segmentation and the ability to connect different projects through VPC peering.

# TUN AND TAP


TUN (Network TUNnel)
-Functionality: TUN devices operate at Layer 3 (the Network Layer) of the OSI model. They create virtual point-to-point connections, which means they handle IP packets.

-Use Case: Typically used in VPN applications. When a packet is sent to a TUN interface, it can be read by the application that created the TUN device. The application can then route these packets over a real network, encapsulating them as needed.

Example: A common use case is in OpenVPN, where TUN is used to tunnel traffic securely between the client and server.

TAP (Network TAP)
-Functionality: TAP devices operate at Layer 2 (the Data Link Layer) of the OSI model. They can handle Ethernet frames, allowing for more complex networking scenarios.

-Use Case: TAP is often used in scenarios where you need to simulate a full Ethernet network. This is particularly useful in applications that require Ethernet-level interactions, such as bridging two or more networks.

Example: TAP devices can be used in software-based routers or firewalls, or to connect virtual machines that require Ethernet-like behavior. Key Differences Layer:

TUN works with IP packets (Layer 3).

TAP works with Ethernet frames (Layer 2).

Use Cases:
1)TUN is ideal for point-to-point connections, like VPNs.

2)TAP is suitable for bridging or connecting virtual Ethernet networks.

Implementation

Both TUN and TAP can be configured using various tools and libraries, such as:

-iproute2: The ip command can be used to create and manage TUN/TAP devices.

-OpenVPN: For TUN-based connections.

-QEMU/KVM: For TAP devices in virtual machine networking.

# OVS(OPEN VIRTUAL SWITCH)


Open vSwitch is a powerful tool for building scalable and flexible networking solutions in virtualized and cloud environments. Its support for SDN and various network management protocols makes it a preferred choice for modern networking challenges.
