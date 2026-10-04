Experiment 1: Hypervisor Analysis
1. Problem Statement
To study and analyze Type-1 and Type-2 hypervisors by creating and configuring virtual machines, understanding their architectures, verifying the virtualized environment, and performing basic CPU performance analysis.

The experiment uses Proxmox VE as the Type-1 hypervisor and VMware Workstation as the Type-2 hypervisor.

2. Objectives
To understand virtualization and the concept of hypervisors.
To study Type-1 and Type-2 hypervisor architectures.
To create and configure a virtual machine using Proxmox VE.
To create and configure a virtual machine using VMware Workstation.
To verify CPU, memory, and storage resources available to the virtual machine.
To perform CPU performance testing using Sysbench.
To record and compare the obtained performance and architectural characteristics.
3. Requirements
Hardware
Computer or server capable of supporting hardware virtualization.
Sufficient CPU, RAM, and storage.
Network connectivity where required.
Software
Software	Purpose
Proxmox VE	Type-1 Hypervisor
VMware Workstation	Type-2 Hypervisor
Ubuntu	Guest Operating System
Sysbench	CPU Benchmarking
4. Introduction to Hypervisors
A hypervisor is a software layer that enables multiple virtual machines to share the resources of a physical computer.

Hypervisors are broadly classified into two types.

Type-1 Hypervisor
A Type-1 hypervisor runs directly on the physical hardware without requiring a conventional host operating system between the hardware and the hypervisor.

Example used in this experiment: Proxmox VE.

Type-2 Hypervisor
A Type-2 hypervisor runs as an application on top of a host operating system and provides virtualization to guest virtual machines.

Example used in this experiment: VMware Workstation.

5. Architecture
5.1 Type-1 Hypervisor Architecture
Physical Hardware
        ↓
    Proxmox VE
  (Type-1 Hypervisor)
        ↓
   Virtual Machine
        ↓
    Ubuntu OS
        ↓
Applications / Benchmark
In a Type-1 architecture, the hypervisor operates directly on the physical hardware and manages the virtual machines and their allocated resources.

5.2 Type-2 Hypervisor Architecture
Physical Hardware
        ↓
  Host Operating System
        ↓
 VMware Workstation
  (Type-2 Hypervisor)
        ↓
   Virtual Machine
        ↓
    Ubuntu OS
        ↓
Applications / Benchmark
In a Type-2 architecture, the hypervisor runs as an application above the host operating system and provides virtualization to the guest virtual machine.

6. Type-1 Hypervisor — Proxmox VE
6.1 Introduction
Proxmox VE is used as the Type-1 hypervisor in this experiment.

An Ubuntu virtual machine is created and configured in the Proxmox environment. The VM configuration and system resources are verified.

6.2 Configuration
Parameter	Configuration
Hypervisor	Proxmox VE
Hypervisor Type	Type-1
Guest Operating System	Ubuntu
Virtual Machine	Ubuntu VM
Benchmark Tool	Sysbench
6.3 Procedure
Access the Proxmox VE environment.
Open the Proxmox web interface.
Create a new virtual machine.
Select the Ubuntu ISO image.
Allocate CPU, memory and storage resources.
Configure the network adapter.
Start the virtual machine.
Install Ubuntu.
Log in to the Ubuntu guest operating system.
Verify the allocated system resources.
Install and execute Sysbench.
Record the obtained results.
6.4 System Verification Commands
CPU
lscpu
Memory
free -h
Storage
lsblk
df -h
Operating System
hostnamectl
6.5 CPU Benchmark
The CPU benchmark can be performed using:

sysbench cpu --cpu-max-prime=20000 run
6.6 Type-1 Evidence
Proxmox Dashboard
Proxmox Dashboard

Proxmox VM Configuration
Proxmox VM Configuration

Ubuntu VM Running
Proxmox Ubuntu VM Running

Ubuntu Console
Proxmox Ubuntu Console

These screenshots document the Type-1 virtualization environment, VM configuration and Ubuntu guest execution.

7. Type-2 Hypervisor — VMware Workstation
7.1 Introduction
VMware Workstation is used as the Type-2 hypervisor in this experiment.

An Ubuntu virtual machine is created and configured using VMware Workstation. The guest system configuration is verified.

7.2 Configuration
Parameter	Configuration
Hypervisor	VMware Workstation
Hypervisor Type	Type-2
Host Operating System	Windows
Guest Operating System	Ubuntu
Virtual Machine	Ubuntu VM
Benchmark Tool	Sysbench
7.3 Procedure
Open VMware Workstation on the host operating system.
Create a new virtual machine.
Select the Ubuntu ISO image.
Configure the virtual CPU.
Allocate memory.
Configure the virtual disk.
Configure the network adapter.
Start the virtual machine.
Install Ubuntu.
Log in to the Ubuntu guest operating system.
Verify the system configuration.
Perform CPU benchmarking using Sysbench when the VMware environment is available.
7.4 System Verification Commands
hostnamectl
lscpu
free -h
lsblk
df -h
7.5 CPU Benchmark
The same benchmark command is used for a fair comparison:

sysbench cpu --cpu-max-prime=20000 run
7.6 Type-2 Evidence
VMware VM Configuration
VMware VM Configuration

VMware VM Running
VMware VM Running

VMware System Configuration
VMware System Configuration

These screenshots document the Type-2 virtualization environment, VMware VM configuration, VM execution and guest system configuration.

8. Type-1 vs Type-2 Hypervisor Comparison
Feature	Type-1 Hypervisor	Type-2 Hypervisor
Example Used	Proxmox VE	VMware Workstation
Hypervisor Location	Directly on physical hardware	Runs above a host operating system
Host OS Dependency	Does not require a conventional host OS	Requires a host operating system
Guest OS	Ubuntu	Ubuntu
Hardware Access	More direct hardware access	Hardware access through the host OS
Performance Overhead	Generally lower	Generally higher due to host OS layer
Resource Management	Hypervisor directly manages resources	Resources are managed through the host OS and hypervisor
Isolation	Strong VM isolation	VM isolation with host OS dependency
Typical Usage	Servers, data centers and cloud infrastructure	Desktop virtualization, development and testing
Example Platform	Proxmox VE	VMware Workstation
Experiment Activity	VM creation, configuration and verification	VM creation, configuration and verification
9. Performance Analysis
The CPU benchmark is performed using Sysbench.

The same command should be used in both environments:

sysbench cpu --cpu-max-prime=20000 run
The main parameters that can be compared are:

Parameter	Type-1: Proxmox	Type-2: VMware
Total Time	From Sysbench result	From Sysbench result
Total Events	From Sysbench result	From Sysbench result
Events per Second	From Sysbench result	From Sysbench result
Average Latency	From Sysbench result	From Sysbench result
The Type-2 benchmark values should be entered only from an actual VMware Sysbench result. No assumed values are used.

10. Result
The experiment successfully demonstrated the concepts of Type-1 and Type-2 virtualization.

Type-1
Proxmox VE was used as the Type-1 hypervisor to create and run an Ubuntu virtual machine. The VM configuration and guest system resources were verified.

Type-2
VMware Workstation was studied as the Type-2 hypervisor. The VMware virtual machine was configured and executed with Ubuntu as the guest operating system.

The comparison table demonstrates the architectural and operational differences between Type-1 and Type-2 hypervisors.

11. Conclusion
This experiment provided practical understanding of virtualization and hypervisors.

Type-1 virtualization was studied using Proxmox VE, while Type-2 virtualization was studied using VMware Workstation. Ubuntu was used as the guest operating system.

The experiment demonstrated virtual machine creation, configuration, resource verification and CPU benchmarking using Sysbench.

The comparison shows that Type-1 hypervisors operate directly on physical hardware, whereas Type-2 hypervisors depend on a host operating system. This makes Type-1 hypervisors more suitable for server and cloud environments, while Type-2 hypervisors are commonly useful for desktop virtualization, development and testing.

12. Reproducibility Guide
Type-1 — Proxmox VE
Prepare a system capable of running Proxmox VE.
Access or install Proxmox VE.
Open the Proxmox web interface.
Create a new virtual machine.
Select an Ubuntu ISO.
Allocate CPU, memory, storage and network resources.
Install Ubuntu.
Log in to the guest operating system.
Verify the system using hostnamectl, lscpu, free -h, lsblk and df -h.
Install Sysbench.
Run the CPU benchmark.
Record the output.
Type-2 — VMware Workstation
Prepare a system with VMware Workstation.
Open VMware Workstation.
Create a new virtual machine.
Select an Ubuntu ISO.
Allocate CPU, memory, storage and network resources.
Install Ubuntu.
Log in to the guest operating system.
Verify the system configuration.
Install Sysbench.
Run the same CPU benchmark.
Record the output.
Compare the result with the Type-1 environment.
13. Important Commands
System Information
hostnamectl
lscpu
free -h
lsblk
df -h
Sysbench
sudo apt update
sudo apt install sysbench -y
sysbench --version
sysbench cpu --cpu-max-prime=20000 run
14. Repository Structure
01-Hypervisor-Analysis/
│
├── README.md
│
└── screenshots/
    │
    ├── type1/
    │   ├── 01-proxmox-dashboard.png
    │   ├── 02-proxmox-vm-configuration.png
    │   ├── 03-proxmox-vm-running.png
    │   └── 04-proxmox-ubuntu-console.png
    │
    └── type2/
        ├── 01-vmware-vm-configuration.png
        ├── 02-vmware-vm-running.png
        └── 03-vmware-system-configuration.png

