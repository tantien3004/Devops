### What is difference between network default bridge and network bridge be created by user?

	In the context of virtualization and networking, a network bridge is a software component that connects two or more networks, enabling communication between them at the data link layer (Layer 2) of the OSI model. Network bridges are typically used to connect virtual machines (VMs) to host system's network and to each other.

	There are two type of network bridge you may encounter:
 	1. Network Default Bridge: This is the predefined, automatically created bridge provided by the virtualization software (such as VirtualBox, KVM, or Docker). The default bridge is usually created when the virtualization software is installed or when a new virtual network is initialized. The default bridge typicallyu assigins IP addresses to VMs connected to it, using a built-in DHCP server. VMs connected to the default bridge can communicate with each other and with the host system, as well as access the external network (if the host system is connected to one).

	2. User-created Network Bridge: This is a custom bridge created by the user for a specific purpose. A user-created bridge might be necessary when the default bridge does not meet the user's requirements, such as when cofiguring VLANs, isolating network traffic, or setting up custom DHCP configurations. User-created bridges can be tailored to specific use cases, including assigning static IP addresses, setting up custom firewall rules, or enabling advances networking features.


	In summary, the main differences between a network default bridge and a user-created network bridge are:
  + The default bridge is automaticcally created and managed by the virtualization software, while the user-created bridged bridge is configured and managed by the user.
  + The default bridge typically has built-in DHCP and NAT functionalities, while a user-created bridge can be customized to meet specific networking requirements.	
