# Lesson 3: Introduction to Nutanix HCI

## Introduction to Nutanix Hyperconverged Infrastructure

1. The what and why of Nutanix HCI
2. The components of a cluster
3. The software components of a Nutanix cluster
4. How to work with the Prism interface

### Why Nutanix HCI?
Quick Review of the Legacy Infrastructure

There are a few reasons legacy infrastructure is not well suited to meet the increasing requirements of enterprise applications or the fast pace of modern business:

* The silos created by traditional infrastructure have become a barrier to change and progress, adding complexity to every step of the IT process from ordering to deployment to management.
* New business initiatives require cooperation from multiple teams. They also need organizations to predict IT infrastructure 3 to 5 years in advance. For context, this is pretty hard to get right.
* Vendor lock-in and rising licensing costs are significantly increasing budgets.

HCI addresses these pain points by combining standard datacenter hardware using locally attached storage resources with intelligent software to create flexible building blocks. These flexible building blocks can replace legacy infrastructure with separate servers, storage networks, and storage arrays.

Benefits of the Nutanix HCI

Nutanix provides the public cloud benefits that organizations want with the control that they need on-prem. There are six major benefits to Nutanix HCI specifically:

* Full-cloud: It’s a full-cloud stack that integrates all compute, storage, virtualization, and networking resources to run any application.

* One-click simplicity: This entire stack is managed via a single pane of glass that streamlines IT lifecycle management and makes hybrid and multi-cloud management easy .

* Deployed in minutes: The applications themselves can be deployed in minutes, instead of weeks or months. This is true for new infrastructure as well.

* Automation application management: Application management can also be automated, along with other common IT tasks. Application owners and developers can also be given on-demand IT services.

* Lower cloud costs: You can also reduce your datacenter TCO by up to 60%. This will help optimize your public cloud spend with lower cloud costs.

* True hybrid cloud: This refers to the ability for you to combine both public and private cloud operations with unified management.

### What is Nutanix HCI?

Nutanix HCI is fully software-defined, which is required from a true HCI solution. This means that the intelligence of the solution comes from the software, which runs on a variety of hardware platforms.

There are two key components to the software:

1. Acropolis: The data plane
2. Prism: The management plane

This software can be run on a number of different servers, from manufacturers such as Dell, Lenovo, HPE, Cisco, IBM, Inspur, and so on. In general, the hardware platforms themselves are structured as nodes, blocks, and clusters.

### Hardware Components: Nodes, Blocks, and Clusters

A node is an x86 server with compute and storage resources. A single Nutanix cluster can have an unlimited number of nodes. Different hardware platforms are available to address varying workload needs for compute and storage.

Each node in the cluster:
* Runs a standard hypervisor
* Contains processors, memory, and local storage such as SSDs and hard disks.
* A Nutanix Controller VM that enables the pooling of local storage from all nodes in the cluster.

All nodes in a Nutanix cluster converge to deliver a unified pool of tiered storage and present resources to VMs for seamless access. A global data system architecture integrates each new node into the cluster, allowing you to scale the solution to meet the needs of your infrastructure.

A block is a chassis that holds one to four nodes, and contains power, cooling, and the backplane for the nodes. The number of nodes and drives depends on the hardware chosen for the solution.

A cluster is a collection of multiple blocks. It refers to the physical servers, logically associated with one another, that deliver a unified pool of infrastructure resources. It can handle the failure of a single node when specific cluster conditions are met. In the case where multiple nodes in a block fail, guest VMs can continue to run because cluster configuration data has been replicated on other blocks.

A Sample Block
This graphic shows a 4-node block in which each node takes up one node position identified as A, B, C, or D. In this block chassis example, the node ports are accessible from the rear of the chassis and the storage is at the front. A Nutanix block is a rack-mountable enclosure that contains one to four Nutanix nodes. It can handle the failure of a single node when specific cluster conditions are met. In the case where multiple nodes in a block fail, guest VMs can continue to run because cluster configuration data has been replicated on other blocks.

Sample Cluster
What you see here is a visualization of a cluster, with both its physical and logical components highlighted. This particular example contains three nodes, each of which has a controller VM, locally attached storage, and has guest VMs running. All of the locally attached storage is presented as a single pool to the guest VMs, via the Controller VM.

### Software Components: Acropolis

Acropolis is a distributed data plane for either VMs or container-based applications that runs across a cluster of nodes delivering enterprise storage and virtualization services. Acropolis is also the foundation of an HCI solution that transforms HCI into a Hybrid Cloud OS.

Here are the main components:

* The Distributed Storage Fabric (DSF)
* The Acropolis Hypervisor (AHV)
* Scale-out storage services
* Advanced virtual networking

Let's take a look at each of these below!

Acropolis: Distributed Storage Fabric

Here is a representation of the Distributed Storage Fabric (DSF). The DSF simplifies storage and data management for virtual environments, by pooling flash and hard disk drive storage across a Nutanix cluster and exporting it as a data store to the virtualization layer as Small Computer Systems Interface (iSCSI), Network File System (NFS), and Server Message Block (SMB) which are all different ways of data sharing.

DSF offer capabilities:

* Snapshots
* Compression
* Cloning
* Data locality
* Deduplication
* Erasure coding
* Tiering
* Replication

Acropolis: AHV

Acropolis Hypervisor (or AHV) is a comprehensive virtualization solution that’s included as part of the Nutanix solution, bundled with Acropolis.

AHV is the virtualization layer in the illustration example. It enables a variety of key capabilities including:

* Backup
* Disaster recovery
* Host and VM high availability
* Dynamic scheduling

Acropolis: Scale-out Storage Services

Nutanix allows you leverage scale-out, fully software-defined storage services via Nutanix Files, Nutanix Volumes, and Nutanix Objects.

* Nutanix Files file services provides access to Microsoft Windows via SMB 2.1 and to Linux and Unix via the NFS v4 protocol. It also scales and load balances multiple nodes in the cluster, growing capacity and performance as needed.
* Nutanix Volumes block services provides iSCSI access to applications that require direct access to block storage. This can be non-virtualized systems, or virtual machines with specific requirements. Volumes uses the DSF to scale I/O across the entire cluster and can load balance and accelerate specified Volume Groups.
* Nutanix Buckets object storage services is a software-defined object storage solution that non-disruptively scales out while lowering overall costs. It supports an industry-standard S3-compatible REST API to handle petabytes of unstructured data.

Acropolis: Virtual Networking

Nutanix Flow:

* Delivers advanced networking and security services, providing visibility into the virtual network, application-centric protection from network threats and automation of common networking operations.
* Allows organizations to deploy software-defined virtual networking without having to install and manage additional products that have separate management and independent software maintenance requirements.
* Provides detailed visualization of communications between VMs, making it simple and straight-forward to set the right policies for the environment.
* Micro-segmentation provides granular control and governance of all traffic into and out of a VM, or groups of VMs. It ensures that only permitted traffic between application tiers or other logical boundaries is allowed and protects against advanced threats propagating within the virtual environment.
* Provides API-based notifications enabling third-party network devices to observe VM lifecycle events, such as the instantiation of a new VM into the Nutanix environment.

### Software Components: Prism
This is Prism, the single dashboard from which you can manage your entire Nutanix solution.

Prism is a distributed management plane that uses advanced data analytics and heuristics to simplify and streamline common workflows, eliminating the need for separate management solutions for servers, storage networks, storage, and virtualization. It provides a unified management interface that can generate actionable insights for optimizing virtualization, provides infrastructure management and everyday operations.

In Prism, Nutanix administrators can easily manage and operate their end-to-end virtual environments.

Just as Acropolis creates a data plane that spans the entire cluster for performance and resiliency, Prism creates the same resiliency for management and operational intelligence.

The information in Prism focuses on common operational tasks grouped into four areas:

* Infrastructure management
* Operational insight
* Capacity planning
* Performance monitoring

Prism is a single interface that eliminates the need for separate management solutions for servers, storage networks, storage, and virtualization. It generates actionable insights for optimizing virtualization, provides infrastructure management and everyday operations.

### Prism - Infrastructure Management: Cluster Management
Four Common Operational Areas
1. Infrastructure Management
2. Operational Insight
3. Capacity Planning
4. Performance Monitoring


Infrastructure management refers to cluster management, upgrades, storage management, virtual machine management, networking, data protection, entity management, user management, localization, and a handful of other key features.

Cluster management refers the overall view of your entire cluster that you see on the Prism home screen.

The Home dashboard is a summary overview of your Nutanix cluster:

* A count of blocks and hosts with model numbers
* A summary of storage
* VMs
* Hardware
* Cluster-wide controller IOPS
* Latency
* CPU usage
* Memory usage
* Alerts and events

Infrastructure Management
There are a lot of different dashboard available to you here depending on what type of information you'll need. We'll go through some of these dashboards during the course, but here's an opportunity to see what the options are. The Home drop down menu has a number of dashboards you can explore, each tailored around providing details on a specific area of your cluster.

### Prism - Infrastructure Management: Storage Management
Storage Dashboard: Overview
The Storage dashboard view shows you an overview of the storage environment, important performance charts, data reduction metrics, capacity summaries, and important alerts and warnings. If an administrator needs more details about certain storage services, then they can use the table view.

This screen provides three views that offer insight into the storage constructs within a cluster:

* Volume groups
* Containers
* Storage pools

The table view displays the configuration settings for each container, capacity metrics, and several performance charts.

The different views of the Storage dashboard are fundamentally the same, each view allows you to interact with and drill down into various components in different ways. The table view puts the storage containers, volume groups, and storage pools front and center. It provides a number of details at a glance about each of these components:

* Controller IOPS, total capacity, free and used capacity, status of various space optimization features, and more.
* Usage and performance summaries, as well as storage alerts and events.

The information you need from the Storage dashboard will determine which view you'll use and interact with.

From the Storage dashboard, you can also create new Storage Containers and new Volume Groups by filling in details in a simple form based on your requirements.

### Prism - Infrastructure Management: Virtual Machine Management
VM Dashboard: Table View
The VM Dashboard provides the same kind of overview summary that the cluster and storage management views offer.

* The VM summary delivers VM counts as well as VM power status.
* Highlighted CPU and memory usage statistics focus on provisioned amounts versus reserved amounts.
* You can also see the top VM consumers for IOPS, latency, memory usage, and CPU usage, enabling you to identify which VMs are using the most resources and detect any outliers.

VM Dashboard: Table View
Following the user experience in the other sections, the VM-focused view in Prism also offers a table-based layout for VM management. Similar to the detailed host data in the cluster view, the VM-based view provides a greater number of VM-focused data points.

This VM-focused view allows organizations to easily compare the CPU and memory settings configured versus the actual amounts of CPU and memory used. You can also access storage metrics for read versus write IOPS, combined IOPS, storage bandwidth, and latency. Prism tracks each of these data points on a per-VM basis to give a quick overview and locate potential issues faster.

### Prism - Infrastructure Management: Data Protection
While there are many other dashboards in Prism, the last one we’ll talk about in this section is the Data Protection dashboard. The data protection overview summarizes the number of remote sites and protection domains, giving you a quick look into the cluster’s data protection. Charts report replication data transfer bandwidth, as well as a list of the top remote sites by bandwidth consumption. This report lets an organization easily understand the bandwidth that replication is consuming, whether something is operating abnormally, and which sites use the most resources. Administrators also gain awareness of ongoing replication, pending replication, and successful replication tasks, so they can recognize if any tasks are being held up or simply verify that replication is completing successfully.

Data Protection Dashboard: Table View
The data protection table view summarizes the configuration, performance, and status of the protection domains that provide backup and disaster protection in your cluster. From this view you can see how many resources each protection domain consumes, what is contained within a protection domain, when taking a snapshot was last successful, and if there are any pending jobs. When you select a specific protection domain or remote site, a greater amount of data becomes available through additional charts and tables. These entity-specific data points provide extensive details on the contents, schedules, alerts, and metrics for each item.

Creating Protection Domains and Remote Sites
Again, creating protection domains and remote sites involves filling a form with details, after which both entities will be created for you. A protection domain is a set of policies that govern the local backup and remote replication functions for one or more VMs. A schedule attached to each protection domain controls the rate at which snapshots are taken and how long they are retained. This architecture allows you to create protection domains that can protect either a single VM or groups of VMs. The flexibility to use multiple protection domains within a cluster means that you can create different policies to protect diverse applications and groups of VMs, and control replication to different sites and clusters.

### Prism - Managing a Nutanix Cluster: Operational Insights
The second of the four key areas in which Prism helps organizations manage their Nutanix clusters is operational insights. Operational insights focus on providing administrators with alerts, metrics, and the ability to analyze data. As with infrastructure management, this also involves a number of different dashboard and Prism capabilities, including:

* Alerts and user-created alerts
* Alert-driven root cause analysis
* Analytics
* Analysis
* Network visualization

Operational Insights: Alerts Dashboard

Alerts Dashboard: Alerts View
Alerts in Prism provide administrators with information about informational, warning, and critical alerts. The Alerts dashboard has two views – Alerts and Events. The Alerts view presents all notifications and events in an easy-to-consume table format. The table presents each alert with a color-coded severity level, a description of the alert, a timestamp, which entities the alert involves, and cause and resolution guidance.

Alerts Dashboard: Events View
The Event view displays a list of event messages. Event messages describe cluster actions such as adding a storage pool or taking a snapshot. This view is read-only and you do not need to take any action like acknowledging or resolving generated events.

### Prism Operational Insights: Analysis Dashboard
The Analysis dashboard stacks multiple charts and lines them up in time sync.

Above the stack of charts, Prism adds all alerts and events, represented with colors and counts. This visual layout lets an administrator click on a chart at any point in time, placing a vertical line stretched through all charts for easy correlation. By focusing on a specific point and syncing all metrics, administrators can reduce the effort it takes to identify possible root causes. The rightmost column of the screen provides a summary of any alerts and events, so you don’t need to leave the analysis page.

The analysis view allows you to fully customize the number and size of the analytical charts you see and to add charts to your screen or remove them as needed. You can export each chart to a .csv or .json file.

### Prism Capacity Planning: Capacity Runway
Capacity planning is available as part of Prism and focuses on consumption from three resource buckets:

* Storage capacity
* CPU
* Memory

Capacity results are illustrated as a chart that shows the historical consumption for the capacity metric along with the estimated capacity runway. The capacity runway is the number of days remaining before the resource item is fully consumed. The Capacity Runway view provides overall and detailed runway information for each cluster managed by Prism Central. Clicking any of the clusters listed in the row will allow you to view more detailed information.

In this case, for example, we can see the total runway, and we can click to view:

* Specific storage
* CPU
* Memory details

On the Storage Runway view for DEMO-AHV, as seen here, we can view runway details either by usage or by storage container. On the CPU and memory pages, we can view details either as an overall view or by host.

Finally, hovering over the any point in the chart will show you projected capacity and runway information for that point in time. For example, as we’re seeing here, live usage has gone up from 1.07 TiB to 5 TiB, and Snapshot Usage has increased from 124.06 GiB to 282 GiB.

### Prism Capacity Planning: Scenarios
The other major capability of Prism’s Capacity Planning is scenario creation. Scenarios allow you to create projections and estimates of resource utilization over a period of time, if you were to add new workloads, or both.

Creating a Scenario
Creating a new scenario presents you with a number of different options. Here, we’re trying to create a scenario to determine resource utilization in 9 months, if no new workloads are added. As you can see, based on current utilization data, Prism projects that we’ll run out of storage well before that time.

In this case, clicking the Recommend button gives us suggestions for which nodes we could add, how many we should add, and what their configuration should be for us to meet our runway needs. This particular feature can be a powerful tool in understand what your current and future capacity needs are, and can empower you to make informed, incremental purchasing decisions.

### Prism Performance Monitoring: Dynamic Monitoring
We’ve already briefly touched upon this in the Operational Insights section, specifically when we discussed the Analysis dashboard. The Analysis dashboard is a key part of Prism’s performance monitoring capabilities, because it provides you with a single, holistic view of cluster data and allows you to drill down into details as required. However, what we haven’t yet discussed is how performance monitoring works in Prism.

Prism offers Dynamic Monitoring, using VM behavioral learning. The system learns the behavior of each VM and establishes a dynamic threshold as a performance baseline for each resource assigned to that VM. Each of the resource charts represents the baseline as a blue shaded range. If a given data point for a VM strays outside the baseline range (higher or lower), the system detects an anomaly and generates an alert. The anomaly is noted on the performance charts for easy reference and follow-up.

If the data point’s anomalous results persist over time, the system learns the VM’s new behavior and adjusts the baseline for that resource. With behavioral learning, performance reporting delivered via Prism helps organizations better understand their workloads and have early knowledge of issues that traditional static threshold monitoring would not otherwise discover.

### Prism Performance Monitoring: Creating Charts
In addition to the default charts that Prism presents you with, you can also create custom charts to monitor specific elements of your cluster. You can create two types of charts: metric or entity.

A metric chart monitors the performance of a single metric on one or more entities. For example, you can create a single chart that monitors the content cache hits for multiple hosts within a cluster.

An entity chart monitors the performance of one or more metrics for a single entity. For example, you can create a single metric chart that monitors a particular host, for metrics such as Disk I/O Bandwidth for Reads, Disk I/O Bandwidth for Writes, and Disk IOPS.

### Prism Performance Monitoring: Alert Emails
By default, Alert email notifications are enabled. This feature sends alert messages automatically to Nutanix customer support through customer-opened ports 80 or 8443. To receive email notification alerts, you need to ensure that nos-alerts and nos-asup recipients are added to the accepted domain of your SMTP server.

You can also customize your Alert emails. To aid in your cluster monitoring efforts, you can schedule the frequency of these Alert emails, the recipients, and the conditions under which an email will be sent.

You can also edit the contents of the email itself.

### Lesson Recap
* The hardware and software components of HCI
* Acropolis: AHV, DSF, Virtual Networking, Storage Services
* Prism: Infrastructure Management, Operational Insights, Capacity 
* Planning, and Performance Monitoring
