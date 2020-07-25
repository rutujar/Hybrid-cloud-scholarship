# Lesson 7

## Data Protection
### Lesson Overview
* The state of data protection
* The complexities of data protection in a hybrid cloud world
* Data protection trends
* Data protection in the hybrid cloud

Businesses of all sizes are modernizing IT with the goal of:

* Reducing costs
* Increasing productivity
* Addressing digital transformation needs.

However, not all businesses are paying the same amount of attention to changing requirements for data protection, nor have they made the same investments for data protection as they have for other areas of IT. At the same time, uptime and availability of critical applications is becoming increasingly important. The result is a steadily widening gap between the amount of data protection being delivered, and the level of protection needed.

### The Cost of a Disaster
Disaster risks are growing on many fronts. Over the last several years, there has been a steady increase in both natural and man-made disasters. In 2018 alone, U.S. climate disasters cost the nation around $91 billion dollars.

Unplanned outages due to system failure, cybercrime, and simple human error are also on the rise. In March 2019, Facebook had a massive day-long meltdown caused by a routine maintenance operation that triggered a bug. No company is immune.

According to Gartner, the average cost that large businesses incur due to downtime is 300 thousand dollars per hour. Organizations need to review their business continuity practices. But, at the same time, a number of factors make comprehensive data protection more challenging than ever.

### Data Protection Challenges
The amount and type of stored data continues to grow. The diversity of places where data is being stored – such as desktops, SAN and NAS storage, and multiple clouds – also continues to grow.

At the same time, the widespread adoption of the hybrid cloud is changing the way data protection is being implemented. In many cases, the cloud is seen as the preferred target for backup and Disaster Recovery, in short: DR. Backup as a Service and DR as a Service are rising as popular alternatives to traditional approaches.

On top of that, businesses are seeking higher levels of protection. Recovery Time Objectives, or RTO, and Recovery Point Objectives, or RPO, are all shrinking. This makes for a challenge: as the amount of data increases, the time for backup tasks continues to decrease. For many applications, the backup window has effectively shrunk to zero.

### Data Protection Trends
Many of the trends in data protection are a direct response to the challenges that we just discussed. Broadly, we’re interested in three specific trends:

* Application-centric protection: Applications often have their own data protection and disaster recovery methods. While this can be attractive in terms of level of protection for a given application, it can also result in additional silos of software and hardware that add to overall complexity.
* Automation: Because of the complexity and importance of data protection and disaster recovery workflows, significant efforts have been made to automate tasks and simplify orchestration of custom workflows to: reduce administrative overhead, accelerate recovery, and eliminate the chance of operator error.
* Copy data management: This refers to the rapidly proliferating number of full data copies that must be stored and managed for, for instance, backup, replication, and development. Solutions are emerging to control and manage this growth.

### RTO and RPO
Before we move on to data protection in the hybrid cloud, let’s take a minute to go over two terms that were just introduced – Recovery Time Objective, or RTO, and Recovery Point Objective, or RPO.

Both parameters are extremely important to data protection because, in many ways, RPO and RTO are the foundation of data protection and disaster recovery decisions that many businesses make.

Recovery Time Objective refers to the time allowed to restore normal operations when an IT failure or disruption occurs, in order to avoid unacceptable consequences associated with a break in business continuity. An RTO of one hour means an application or a data-set will be back online within one hour after a failure occurs.

Recovery Point Object refers to the quantity of data that a business can lose, before the amount of data lost during that period, exceeds a maximum allowable threshold which would result in unacceptable consequences associated with a break in business continuity.

### Data Protection in the Hybrid Cloud
Businesses of all sizes are discovering that hybrid cloud with Nutanix – which is built with web-scale engineering and consumer-grade design – simplifies IT, increases availability, and accelerates the entire IT environment, including data protection and Disaster Recovery.

Nutanix combines a highly resilient, scale-out infrastructure with efficient snapshot, cloning, and replication technologies, as well as intelligent software to provide a higher level of protection with less complexity and lower cost.

As a result, the Nutanix hybrid cloud brings six major capabilities to data protection.

Six Major Capabilities
* Application-centric automation: With Nutanix, you can quickly and easily group application VMs, and protect them together, as a set.
Multi- and cross-hypervisor support: VMware vSphere, Microsoft Hyper-V, and Nutanix AHV.
* Not only can you use data protection functionality with all three hypervisors, you can also perform cross-hypervisor replication to optimize costs.
* Simple Management: Data protection with multiple solutions, devices, and interfaces – can be a problem. Prism can be used to manage all Nutanix data protection and DR functionality.
* Policy-based data protection: Data protection and DR are based on policies you define up front, allowing you to deliver the right protections for every application and workload with ease.
* API-driven automation: Nutanix provides a full set of REST APIs to facilitate automation. Every action that can be performed from the Prism UI, through PowerShell, or using application programs.
* Copy efficient protection: Nutanix data protection and data reduction help you minimize the number of full data copies and the bandwidth needed for replication. This saves on space and cost, providing complete data protection, while allowing you to quickly provision clones for analytics, development, and testing.

### Infrastructure Resilience
Infrastructure resiliency is the first line of defense for your data and applications. One of the things that differentiates Nutanix from conventional infrastructure with separately sourced servers, storage, and storage networks is that the platform is fault resistant, with no single point-of-failure or bottlenecks.

The system uses a shared-nothing architecture with data, metadata, and services distributed across all nodes within a cluster. It is designed to detect, isolate, and recover from failures in order to survive system malfunctions and maintain data availability should there be any hardware unavailability, software glitches, or hypervisor issues.

With respect to infrastructure resilience, it is important to understand 4 key capabilities that Nutanix provides:

* Tunable redundancy
* Erasure coding
* Integrity checks
* Availability domains

### Infrastructure Resilience: Tunable Redundancy
Tunable redundancy, replaces traditional, hardware-centric RAID. Each Nutanix data container, which is the equivalent of a VM datastore, has a data Replication Factor, or “RF”, of 2 or 3. This means that either two or three copies of data are maintained at all times.

In this image, you can see how RF2 allows a cluster to survive the failure of one node or drive, while RF3 allows a cluster to survive two simultaneous failures of the same components.

If a node or drive fails, the copy of that data is automatically read from another node in the cluster. If the node does not come back online, all data on the affected node is automatically reconstructed to ensure full redundancy and data protection.

Because the workload is spread across the cluster, the performance impact is small. The larger the cluster is, the faster the data is reconstructed, and the smaller the impact of a failure. The system returns to full redundancy quickly and without intervention.

Next, we’ll discuss erasure coding, which provides the same level of data resilience while removing storage capacity overhead.

### Infrastructure Resilience: Erasure Coding
Let’s take a closer look at Erasure Coding, or “EC-X”.

Erasure Coding encodes a strip of data blocks that reside on different nodes in the cluster, and calculates parity using software, instead of physical disk controllers.

With the parity blocks in place, the second and/or third copies of the original data are then removed. In the event of a disk or node failure, parity blocks are used to re-calculate missing data blocks. Each data block in a strip is on a different node and belongs to a different vDisk. The number of data and parity blocks in a strip is dynamic, it's configuration based on the number of nodes in the cluster and the chosen data replication factor.

Erasure coding increases usable capacity over 50%. EC-X also reduces data storage capacity, and therefore capacity cost without taking away any of the resiliency benefits, and with no impact on write performance.

### Infrastructure Resilience: Integrity Checks
Nutanix integrity checks are a combination of features that proactively identify and fix issues related to data consistency, data integrity, and hard disk corruption.

There are three items that are worth calling out specifically. These are:

* The system scans data in the background and verifies it against stored checksums in the distributed metadata store. If an error is detected, bad data is overwritten using a good copy.

* A checksum is computed for all data being read, and compared with stored checksums. This essentially provides automatic data integrity checks for every read operation.

* If a drive fails, the system automatically replicates all data that is no longer redundant, to ensure fault tolerance. During the failure and recovery process, both data and access to it are preserved.

### Infrastructure Resilience: Availability Domains
Availability domains, our final discussion point under infrastructure resilience, offers even greater protection from hardware failures than we’ve talked about already. It allows a cluster to survive the failure of a node, a block, or even a datacenter rack. The three types we’re going to discuss are:

* Node Awareness: Exactly how a cluster survives node failures without losing access to its data.
* Block Awareness: Block awareness takes node awareness a step further, by distributing data replicas across multiple blocks. A block, incidentally, is a multi-node enclosure that can contain up to four nodes. In the case of block awareness, if a block fails, there is always at least one replica of all data on the node of another block.
* Rack Awareness: Rack awareness builds on block awareness in the same way, and provides data availability in case of a rack-level failure, for instance a power outage.

### Backups Overview
Regular backups are the second line of defense in data protection, and the only protection against user, administrator, and application errors that result in data being deleted or corrupted. The Nutanix hybrid cloud provides three levels of backup:

* Converged local backup with snapshots
* Integrated remote backup
* Cloud backups

Using these capabilities, you can easily implement disk-to-disk, disk-to-cloud, or disk-to-disk-to-cloud backup models. For any of these modes you can tailor the number of retained backups to your exact needs.

### Converged Local Backup with Nutanix Snapshot
Backup remains one of the biggest challenges in enterprise IT environments. With Nutanix, you can create unlimited local backups with VM-level and application-level consistency, allowing you to recover data instantly to meet a wide range of backup and data protection requirements.

Nutanix snapshots provide production-level data protection without sacrificing performance. A redirect-on-write algorithm dramatically improves system efficiency. Once a snapshot has been created, it can be accessed without affecting production activity.

You can backup a snapshot to tape for long-term retention, replicate it to another Nutanix cluster, or replicate it to the cloud.

### Integrated Remote Backup
Nutanix can efficiently replicate snapshots of individual VMs from a primary system to one or more secondary systems at different sites.

Replication is flexible and bi-directional, enabling: one-to-one, one-to-many, many-to-one, and many-to-many topologies. By supporting fan-out, fan-in, and multi-way replication, Nutanix allows you to create a flexible multi-master virtualization environment.

VM snapshots can be asynchronously replicated or backed up to another datacenter through a user-defined schedule. Only changes between snapshots of VMs, the byte-level delta, are sent over the network to the remote cluster, and data is compressed to minimize Wide-Area-Network, or “WAN”, bandwidth consumption.

Deduplicated data sent to remote sites can effectively cut the bandwidth requirement by more than 50% when compared with host-based, full-copy backup solutions.

Replication, like other system functions, is fully distributed across the nodes in a cluster, ensuring maximum replication performance.

Prism provides a simplified view of all local and remote snapshots, allowing administrators to restore a VM from a snapshot with a single click. In case of disaster, you can failover using the backed up data-copy at a secondary datacenter, providing a single replication stream for backup.

### Cloud Backups
Nutanix allows you to use public cloud services, such as Amazon Web Services, as a backup destination for all types of workloads, making the public cloud a logical extension of your own datacenter. You can backup to, and recover from, the public cloud with just a few clicks, similar to backing up to a remote physical Nutanix cluster.

You can snapshot an individual VM, or a collection of VMs, to multiple geographically dispersed regions, utilizing Nutanix Xi Leap cloud services. Recovery is the same as from a remote Nutanix site. Data transfer is WAN optimized, reducing the storage footprint and network bandwidth by more than 50%.

### Lesson Recap
* The state of data protection
* The complexities of data protection in a hybrid cloud world
* Data protection trends
* Data protection in the hybrid cloud
