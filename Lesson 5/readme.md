# Lesson 5

## Networking
### Lesson Overview
* Introduction to Physical and Virtual Networking
* Components of AHV Networking
* Working with VLANs

What is Networking?
Networking is the practice in which nodes transport and exchange data over a shared medium.

It is commonly associated with the design, construction, and use of a network. Networking also includes the management, maintenance, and operation of the network’s physical infrastructure. It also involves all the associated software and policies.

In this lesson we’re going to be focusing on two specific topics – physical networking and virtual networking.

### Introduction to Networking: Physical Networking
Physical networking is about the network topology – the devices, their location, and the physical cables that connect those devices to each other. The network is a key component in ensuring high performance and availability, and successful deployments combine the right physical switches with the right physical designs.

A Nutanix environment should use datacenter switches designed for transmitting large amounts of server and storage traffic at low latency.

Datacenter switches have the following characteristics:

* Line rate: Ensures that all ports can simultaneously achieve advertised throughput.
* Low latency: Minimizes port-to-port latency, measured in microseconds or nanoseconds.
* Large per-port buffers: Handle speed mismatch from uplinks without dropping frames.
* Nonblocking, with low or no oversubscription: Reduces chance of drops during peak traffic periods.
* 10 Gbps or faster links for Nutanix CVM traffic: Only use 1 Gbps links either for additional user VM traffic or when 10 Gbps connections are not available, such as in a ROBO deployment. Limit Nutanix clusters using 1 Gbps links to eight nodes.

Once you’ve found the right switch, that’s one big decision dealt with. The other is which networking design to use. And whether you’re designing a new network or transitioning an older network into cloud-scale architecture, it is important to know the differences and characteristics of two prominent network topologies: Core-Aggregation-Access networking, which is also called 3-Tier networking, and Leaf-Spine architecture.

### Physical Networking Topology: Core-Aggregation-Access (3-Tier)
This architecture contains three layers: Core, Aggregation, and Access.

The core layer provides fast transport between distribution layer switches. The core layer provides routing services to other parts of the data center, as well as to services outside of the data center such as the Internet, geographically separated data centers and other remote locations. The network core delivers routing services, making complex routing decisions for optimized networking traffic, advertises routes, stores network configurations, and provides a gateway for all networks to communicate internally and externally.

The aggregation layer has redundant connections to access layer switches and connects to the core layer.

The access layer is where host devices are connected to the network. It plays a vital role in meeting server requirements such as NIC teaming, clustering, and broadcast containment.

In the Core-Aggregation-Access networking model, devices are connected to each other within a layer, as well as across layers for redundancy. This model scales somewhat well, but it is subject to bottlenecks if uplinks between layers are oversubscribed. This can come from latency incurred as traffic flows through each layer and from blocking redundant links. Also, the cost per port is fairly high. The hardware and logic contained within core switches made them cost-prohibitive to scale.

### Using 3-Tier in a Nutanix Deployment
The core-aggregation-access (or three-tier) design is a modular layout that allows you to upgrade and scale layers independently.

However, there’s one important best practice that you need to consider and that’s the three-switch-hop rule.

Nutanix nodes send storage replication traffic to each other in a distributed fashion over the top-of-rack network. One Nutanix node can therefore send replication traffic to any other Nutanix node in the cluster. The network should provide low and predictable latency for this traffic. So, it’s important to ensure that there are no more than three switches between any two Nutanix nodes in the same cluster.

Essentially, when using Core-Aggregation-Access, you need to ensure that all nodes in a Nutanix cluster share the same aggregation layer to meet the three-switch-hop rule.

Scaling the three-tier network design may require adding another aggregation and access layer to the core. In this case, there would be more than three switch hops between the two access layers. To continue to align with the three-switch-hop rule, ensure that you add Nutanix nodes in separate aggregation and access layers to separate clusters. In the example you’re seeing here, Cluster 1 connects to one aggregation layer and Cluster 2 connects to another.

However, since there are many ways to connect switches in the core-aggregation-access design, your deployment may look a little different from this one.

### Physical Networking Topology: Leaf-Spine
The leaf-spine network design is popular in new datacenter deployments because it’s easy to deploy and easy to scale after deployment. A leaf-spine topology requires at least two spine switches and two leaf switches. Every leaf connects to every spine using uplink ports. There are no connections between the spine switches or between the leaf switches in the conventional leaf-spine design. This architecture maintains consistent performance without any reduction in throughput.

Spine switches contain the routing, switching, and network services required for core network functions. Leaf switches exclusively provide high port density for network communications and extend the network configuration of the core out to the endpoints. Leaf-Spine switching focuses on east-west traffic, capitalizing on the fact that a majority of network communication now relies upon communication within the LAN to other adjacent servers and services. Spine leaf provides a high-bandwidth, low latency alternative to 3-tiered architecture, as any given network node is simply one hop away from any adjacent node through the leaf switches.

Spine and leaf architecture provides consolidated management and scale-out networking in a simplified network design. Scaling the architecture normally involves adding a single leaf, enabling the new switch in the fabric, and then cabling the endpoints as needed.

### Leaf Spine: Using Leaf-Spine in a Nutanix Deployment
Nutanix recommends a leaf-spine network architecture to ensure true linear scaling. Other best practices include using uplinks that are a higher speed than the edge ports to reduce uplink oversubscription. To increase uplink capacity, add spine switches or uplink ports as needed.

### Introduction to Networking: Virtual Networking
To understand virtual networking, we need to first take a quick step back and understand network virtualization. And although they sound similar – and that’s because they’re related – they do mean slightly different things.

Network virtualization involves combining hardware and software network resources, along with network functionality, into a single, software-based administrative entity. The elements that can be combined include switches, network adapters, firewalls, load balancers, virtual LANs, and so on. The outcomes of this – the single, software-based entity – is a virtual network.

And virtual networking, to put it very simply, facilitates communication between virtual machines. It’s based on physical networking principles, but its functions are software-driven. For example, a virtual switch contains the same packet forwarding logic that a physical switch does, but as software.

There are four major components that we need to talk about: virtual switches, bridges, ports, and bonds.

This virtual switch controls and directs communication between the existing physical network and virtual parts of the network, like virtual machines. A virtual network adapter allows VMs to connect to a network, and allows the VMs on a LAN to connect to a larger network as well.

### Virtual Networking: Virtual Switches
As we discussed earlier, virtual switches allow communication between virtual machines. More specifically, they intelligently direct communication on a network by checking data packets before sending them along to their destination.

Using virtual switches simplifies the complexity that comes with configuring and managing a network. This is because virtual switches help reduce the number of switches that need to be managed after factoring in the size of the network, data packets, and architecture. Because they’re entirely software-based, it’s easier to roll out new functionality for virtual switches as compared to physical, hardware-based ones.

Nutanix AHV uses Open vSwitch, or OVS, to manage the network across all nodes in the Nutanix cluster. OVS is an open source software switch implemented in the Linux kernel and designed to work in a multi-server virtualization environment. By default, OVS behaves like a layer-2 learning switch that maintains a MAC address table. The hypervisor host and VMs connect to virtual ports on the switch.

OVS supports many popular switch features, including VLAN tagging, Link Aggregation Control Protocol (LACP), port mirroring, and quality of service (QoS), to name a few. Each AHV node maintains an OVS instance, and all OVS instances combine to form a single logical switch. Constructs called bridges manage the switch instances residing on the AHV hosts.

Let's break down some of these virtual networking components that make up Nutanix AHV.

### Virtual Networking: Bridges
Bridges act as virtual switches that manage network traffic between physical and virtual network interfaces.

The default AHV configuration includes an OVS bridge called br0 and a native Linux bridge called virbr0. The virbr0 Linux bridge carries management and storage communication between the CVM and AHV host. All other storage, host, and VM network traffic flows through the br0 OVS bridge. The AHV host, VMs, and physical interfaces use ports for connectivity to the bridge. Next, let's discuss ports.

### Virtual Networking: Ports
Ports are logical constructs created in a bridge that represent connectivity to the virtual switch. Nutanix uses several port types, including internal, tap, VXLAN, and bond.

* An internal port provides access for the AHV host.

* Tap ports act as bridge connections for virtual NICs presented to VMs.

* VXLAN ports are used for the IP address management functionality provided by Acropolis.

* Bonded ports provide NIC teaming for the physical interfaces of the AHV host.

### Virtual Networking: Bonds
It is possible to balance traffic across bond uplinks, via one of three bond modes: active-backup, balance-slb, and LCAP with balance-tcp. Let’s take a quick look at each of these bond modes next.

### Bond Modes: active-backup
With the active-backup bond mode, one interface in the bond carries traffic and other interfaces in the bond are used only when the active link fails. Active-backup is the simplest bond mode, easily allowing connections to multiple upstream switches without any additional switch configuration. The active-backup bond mode requires no special hardware and you can use different physical switches for redundancy.

### Bond Modes: Balance-slb
To take advantage of the bandwidth provided by multiple upstream switch links, you can use the balance-slb bond mode. The balance-slb bond mode in OVS takes advantage of all links in a bond and uses measured traffic load to rebalance VM traffic from highly used to less used interfaces.

When the configurable bond-rebalance interval expires, OVS uses the measured load for each interface and the load for each source MAC hash to spread traffic evenly among links in the bond. Traffic from some source MAC hashes may move to a less active link to more evenly balance bond member utilization.

Perfectly even balancing may not always be possible, depending on the number of source MAC hashes and their stream sizes. Each individual VM NIC uses only a single bond member interface at a time, but a hashing algorithm distributes multiple VM NICs’ multiple source MAC addresses across bond member interfaces.

As a result, it is possible for a Nutanix AHV node with two 10 GB interfaces to use up to 20 Gbps of network throughput. Individual VM NICs have a maximum throughput of 10 Gbps, the speed of a single physical interface. A VM with multiple NICs could still have more bandwidth than the speed of a single physical interface, but there is no guarantee that the different VM NICs will land on different physical interfaces.

The default rebalance interval is 10 seconds, but Nutanix recommends setting this interval to 30 seconds to avoid excessive movement of source MAC address hashes between upstream switches. Nutanix has tested this configuration using two separate upstream switches with AHV. If the upstream switches are interconnected physically or virtually, and both uplinks allow the same VLANs, no additional configuration, such as link aggregation is necessary.

### Bond Modes: balance-tcp
Taking full advantage of bandwidth provided by multiple links to upstream switches, from a single VM, requires dynamically negotiated link aggregation and load balancing using balance-tcp. Nutanix recommends dynamic link aggregation with LACP instead of static link aggregation due to improved failure detection and recovery.

With link aggregation negotiated by LACP, multiple links to separate physical switches appear as a single layer-2 link. A traffic-hashing algorithm such as balance-tcp can split traffic between multiple links in an active-active fashion. Because the uplinks appear as a single L2 link, the algorithm can balance traffic among bond members without any regard for switch MAC address tables. Nutanix recommends using balance-tcp when using LACP and link aggregation, because each TCP stream from a single VM can potentially use a different uplink in this configuration.

With link aggregation, LACP, and balance-tcp, a single guest VM with multiple TCP streams could use up to 20 Gbps of bandwidth in an AHV node with two 10 GB adapters.

### VLAN
A virtual LAN, or VLAN, is a subgroup of a network, which combines multiple networking devices into a single domain and partitions them off from the rest.

VLANs offer a number of benefits over their more physical-based counterparts: Better network speed and performance More efficient traffic routing between domains More control over network devices and traffic Security benefits by isolating data within a VLAN No need to add cabling or make significant infrastructure changes

AHV supports two different ways to provide VM connectivity: managed and unmanaged networks.

### Unmanaged Networks
With unmanaged networks, VMs get a direct connection to their VLAN of choice. Each virtual network in AHV maps to a single VLAN and bridge. All VLANs allowed on the physical switch port to the AHV host are available to the CVM and guest VMs. Acropolis binds each virtual network it creates to a single VLAN. During VM creation, you can create a virtual NIC and associate it with a network and VLAN. Or, you can provision multiple virtual NICs each with a single VLAN or network.

### Managed Networks
A managed network is a VLAN plus IP Address Management. IPAM is the cluster capability to function like a DHCP server, to assign an IP address to a VM that sits on the managed network. Administrators can configure each virtual network with a specific IP subnet, associated domain settings, and group of IP address pools available for assignment.

The Acropolis Master acts as an internal DHCP server for all managed networks. The OVS is responsible for encapsulating DHCP requests from the VMs in VXLAN and forwarding them to the Acropolis Master. VMs receive their IP addresses from the Acropolis Master’s responses. The IP address assigned to a VM is persistent until you delete the VNIC or destroy the VM.

The Acropolis Master runs the CVM administrative process to track device IP addresses. This creates associations between the interface’s MAC addresses, IP addresses and defined pool of IP addresses for the AOS DHCP server.

### Lesson Recap
* Physical and Virtual Networking
* Components of AHV Networking
* How to work with VLANs

## Glossary
* Physical networking: The network topology including the devices, their location, and the physical cables that connect those devices to each other.
* Core layer: Provides fast transport between distribution layer switches. The core layer provides routing services to other parts of the data center, as well as to services outside of the data center such as the Internet, geographically separated data centers and other remote locations.
* Aggregation layer: Has redundant connections to access layer switches and connects to the core layer.
* Access layer: Where host devices are connected to the network. It plays a vital role in meeting server requirements such as NIC teaming,clustering, and broadcast containment.
* Core-aggregation-access (or three-tier) design: A modular layout that allows you to upgrade and scale layers independently.
* Leaf-spine network design: Popular in new datacenter deployments because it’s easy to deploy and easy to scale after deployment. A leaf-spine topology requires at least two spine switches and two leaf switches. Every leaf connects to every spine using uplink ports. There are no connections between the spine switches or between the leaf switches in the conventional leaf-spine design. This architecture maintains consistent performance without any reduction in throughput.
* Spine switches: Contain the routing, switching, and network services required for core network functions.
* Leaf switches: Exclusively provide high port density for network communications and extend the network configuration of the core out to the endpoints.
* Virtual networking: Facilitates communication between virtual machines. It’s based on physical networking principles, but its functions are software-driven.
* Virtual switch: Controls and directs communication between the existing physical network and virtual parts of the network, like virtual machines.
* Virtual network adapter: Allows VMs to connect to a network, and allows the VMs on a LAN to connect to a larger network as well. Open vSwitch (OVS): Manages the network across all nodes in the Nutanix cluster. OVS is an open source software switch implemented in the Linux kernel and designed to work in a multi-server virtualization environment.
* Bridges: Act as virtual switches that manage network traffic between physical and virtual network interfaces.
Ports: Logical constructs created in a bridge that represent connectivity to the virtual switch.
* Active-backup: The simplest bond mode, easily allowing connections to multiple upstream switches without any additional switch configuration.
* Balance-slb: Bond mode in OVS that takes advantage of all links in a bond and uses measured traffic load to rebalance VM traffic from highly used to less used interfaces.
* Balance-tcp: A traffic-hashing algorithm that can split traffic between multiple links in an active-active fashion. Because the uplinks appear as a single L2 link, the algorithm can balance traffic among bond members without any regard for switch MAC address tables.
* A virtual LAN (VLAN): A subgroup of a network, which combines multiple networking devices into a single domain and partitions them off from the rest.
* Unmanaged networks: VMs get a direct connection to their VLAN of choice.
* A managed network: A VLAN plus IP Address Management.
