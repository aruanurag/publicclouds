---
layout: post
title: "AWS Certified Solution Architect Associate"
date: 2021-04-03 11:11:11 -0000
categories: AWSSolutionArchitectAssociate
---

## Table of Contents

1. [IAM](#iam)
2. [EC2](#ec2)
3. [Security Groups](#security-groups)
4. [Elastic Network Interface](#elastic-network-interface)
5. [Load Balancer](#load-balancer)


## IAM

AWS Identity and Access Management solution. Like 
**Azure Service**: Azure Active Directory

* **USERS**
  * Physical Person/Users
* **Groups**
  * Group of users. Grouping can be done by Teams , tasks etc
* **Roles**
  * Internal usage within AWS 
  * Used by AWS resources to get access to other resources
* **IAM Policies**
  * Predefined/Managed Policies
* **IAM federation**

## EC2

**Azure Service**: Azure Virtual Machine
EC2 is the virtual machine offering from AWS. It has various capabilities -

* Storing data on virtual drives. (EBS)
* Load balancing across multiple instances (ELB)
* Auto scaling horizontally by increasing the number of instances (ASG)

### AMI
- Amazon Machine Image
- Can be customized with custom software as needed.
- Custom/Private AMI needs to be managed by us.

### User Data

* Use custom scripts to bootstrap your EC2 instances.
* Scripts provided are like startup instructions. 
* At the time of creating a EC2 instance provide the script that you want to run at the time of 
bootstraping

### Instance Launch Type

* On Demand - Most commonly used. Used for shorter durations eg. POC's
* Reserved - 
  * When the usage is for a minimum 1 year , reserved instances can be used.
  * Convertible Reserved - Can be used if the duration is long and a flexible size is needed. The instance type can be changed.
  * Scheduled Reserved - Available on specific schedules. Require compute only for a fraction of time.
* Spot Instances - short workloads , very cheap and less reliable.
 * Cheapest option
 * You bid for a price and at any time if your max price is less than the current spot price you loose the instance
 * More suitable for workloads which are unaffected by failures. 
* Spot Fleets - Set of On demand + Spot Instances
  * Try to meet the capacity with cost restraint.
* Dedicated Instances - No one else will share your hardware
* Dedicated Hosts - You book a entire host and control how instances are created. Get for a 3 year period. Useful for Bring your own license purpose.

### Placement Groups

* This option lets you configure the placemnt of the EC2 instances in the underlying hardware.
* **Cluster** Clustered together for minmimizing the latency
* **Spread**  The EC2 instances are spread across the underlying hardware (max 7 per group). Can spread across Availability Zones
* **Partition** EC2 instances are spread across different racks .

### EC2 Hibernate
- When a EC2 instance is stopped the data on the disk is retained 
- When terminated the dat is also lost
- With EC2 hibernate all the inMemory (RAM) state is preserved which makes the restart really fast

### EBS Volume
- Elastic Block Store
- Network drive that can be attached to the EC2 instance
- They are netork drive so there is some network latency
- Can only be assigned to one at a time, but can be detached and attached to other one.
- Bind to one Availabilty Zone
- Can take a EBS Snapshot which is basically a backup
- EBS RAID -

### EC2 instance store
- Attached to the EC2 instance. So high perfomance and no latency.
- Are ephemeral in nature so data goes away with EC2 instance.

### EFS _ Elastic File System
- Managed File System
- Network File System
- Can be shared by multiple instances
- Expensive but pay only for the usage
- Works with EC2 across multiple instances

## Security Groups 

**Azure Service**: Network Security Groups (NSG)

* Network Security component to control traffic flow.
* Collection of In and Out rules to control Ingress and Egress. Rules are defined using:
  * Type - SSH/HTTP
  * Protocol - TCP
  * Port Range - 80, 443, 22 etc
  * CIDR range for IP addresses - 10.1.1.0/24
* By default all ingress is blocked and egress is allowed.
* Can be attached to multiple EC2 instances and one EC2 instance can have multiple Security groups
* DNS names can not be used in a security group.
* One security group can refrence other security group

## Elastic Network Interface

**Azure Service**  Azure Network Interface

1. Virtual Network Card
2. Gives EC2 instances network Access
3. Attributes:
  - 1 Public Ip
  - 1 Private IP
  - One or More security groups



** Load Balancer


***Classic Load Balancer***


***Application Load Balancer***


***Network Load Balancer***


***Gateway Load Balancer***

***More Concepts**

1. Stickiness
2. Cross Zone Load balancing