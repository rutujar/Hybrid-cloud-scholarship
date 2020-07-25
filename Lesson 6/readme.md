# Lesson 6

## Managing Virtual Machines in the Hybrid Cloud
### Lesson Overview
* Introduction to VM management
* Working with Disc Images
* Creating and Managing VMs
* Understanding VM High Availability

Let’s start at the very beginning, with a simple question - what is a virtual machine? A virtual machine, or VM, is an emulation of a computer system. It’s based on computer architectures, is typically called an image, and provides the functionality of a physical computer.

As we’ve seen in previous lessons, it’s also a core part of a virtualized system since it’s created by abstracting the resources of a physical machine. VMs are used to provide the end users of a virtualized system with a familiar, comfortable substitute for a real machine.

And VM management refers to activities such as starting and stopping a VM, updating a VM’s configuration, and migrating, cloning, or deleting a VM. With Nutanix specifically, all of these activities are performed in Prism, and on the VM dashboard that we discussed briefly in lesson 2. So, before we move on to these operations, let’s quickly look at the VM dashboard again, but in a little more detail.

### The VM Dashboard
All of the VM management tasks that were listed earlier are performed here, on the table view of the VM dashboard. As you can see here, the Table view has three major sections – a table in the center of the screen that contains a list of all VMs on the cluster; a VM Summary box at the bottom left with information like total number of VMs, provisioned and reserved CPU and memory, etc.; and two tabs for VM performance summary and VM tasks respectively.

What we’re interested in right now is the VM table, which you’re seeing here. If you look below the table, you’ll see that there’s nothing of note – just the “Summary” heading and that’s it. However, if we were to select a VM from the table things look a little different.

As you can see, with Test VM 001 selected, we now have access to a variety of different management options. You can manage Nutanix Guest Tools, Launch the VM’s console, power the VM on or off, take a snapshot, and migrate, clone, update, or delete the VM.

So, now that you know how to access these options, let’s look at VM creation and management in more detail.

### Working with Images
The first step in creating virtual machines is learning how to work with images.

You can use Prism to import and configure operating system ISO and disk image files using the Image Service. This image service allows you to assemble a repository of image files in different formats including raw, vhd, vhdx, vmdk, vdi, iso, and qcow2. You can later use these images when creating virtual machines.

Adding an image to the image service is a fairly straightforward upload process. The upload process is performed on the Storage dashboard (not the VM dashboard). You simply select the image, name it, select the image type, and that’s it - your image is now in Prism and ready for use.

After you upload an image to Prism, there are several things you can do with it. You can use it to create a VM, you can leave it in the image service for use in future deployments and, if you no longer need that image at a later date, you can simply delete it from Prism.

Before we move on to an exercise in which you can practice uploading images, let’s watch a short video walkthrough of the process.

### Updating/Modifying a VM
Managing VMs involves a handful of tasks. Now, specifically, we’re going to be focusing on a few of them. Let’s start with modification. You can update or modify a VM at any point after you create it. And, you have access to the same dialog that’s used when creating a VM, so you can modify everything from CPU, memory, and storage to networking and host affinity details.

On the update VM dialog, change the VM’s configuration to suit your needs. In this case, we’ve updated the number of cores per vCPU to 2, and the memory from 8 GB to 16. When all your changes have been made, click Save.

### Cloning a VM
To clone a VM select it and then, from the row of option below the VM table, select Clone.

In the Clone VM dialog, you can change the configuration as required and specify the number of clones you want. If you want to create more than one clone – if you look at this example, we’re creating five – then you’ll also be prompted to specify a starting index number.

Once you’ve made all of your changes, click Save and your VM clones will be created.

### Deleting a VM
Deleting a VM is as straightforward as it sounds. Simply select the VM you want to delete and, from the row of options below the VM table,select Delete.

You’ll be prompted to confirm deletion. If the VM is powered on, as is the case here, the dialog will explicitly state that. You’ll also be asked if you want to delete all snapshots of this VM. Make your selections and, once you’re sure, click Delete to remove the VM from Prism.

### Migrating a VM
Like a lot of the capabilities we’ve talked about already, migrating a VM to a different host in the cluster also a one-click operation. If you need to migrate a VM, you can either choose the host yourself, or allow Prism to do it for you. Since the former is extremely straightforward, let’s look at a quick example of the latter.
On the Migrate VM screen, click the dropdown and select the host that you want to migrate to.
Here, we have 3 options – Demo 1, Demo 2, and the host that the VM is already on, Demo 3. Let’s move the VM to Demo 2. To do this, we just need to select DEMO-AHV-2 from the list and click Migrate.
Prism will take a few seconds to complete the process and, once it finishes, we can see the results. In the column to the right of the VM name, we can see that our test VM is now on DEMO-AHV-2.

### What is VM High Availability?
High availability refers to the ability of a system to run continuously without failure. This doesn’t mean that the system or components of it cannot fail; It just means that the system is designed to account for and compensate for failures when they happen. And, since VMs represent the interface with which end users interact with a virtualized system, being able to provide high uptime and strong tolerance for failure is especially important.

By default, Nutanix uses a system called best effort availability for VMs. Other options are available and can be manually turned on, but this one is on by default.

If a host fails, the VMs that were running on that host are restarted on any available space on other hosts in the cluster. One the failed host is up and running, VMs are migrated back to their original host. This type of VM high availability is implemented without reserving any resources. But because admission control is not enforced, there may not be enough resources to restart all VMs.

The other option is using host-based reservations.

In this method, the cluster is divided into segments to ensure enough space is reserved for any host failure. Each segment corresponds to the largest VM that is guaranteed to be restarted in case the failure occurs. The other factor is the number of host failures that can be tolerated. Using these inputs, the scheduler implements admission control to always have enough resources reserved so that the VMs can be restarted upon failure of any host in the cluster.

### Enabling VM High Availability
To enable VM HA, click the gear icon at the top right of the screen to open the Settings page.

As you can see here, HA Reservation is disabled by default. The dialog informs you that resources are not reserved, and in case of a failure VMs will be restarted based on the amount of resources that are available to the cluster. To enable VM HA, select the Enable HA Reservation checkbox.
The dialog updates to inform you that a certain amount of resources will be reserved to provide protection in case of a host failure. To save this change and enable VM HA, click Save.

### Lesson Recap
* Introduced you to VM management
* Worked with Disc Images
* Showed you how to create and manage VMs
* Discussed VM High Availability

### Glossary
* A virtual machine (or VM): An emulation of a computer system. It’s based on computer architectures, is typically called an image, and provides the functionality of a physical computer.
* High availability: Refers to the ability of a system to run continuously without failure.
