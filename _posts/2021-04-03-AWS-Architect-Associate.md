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
* Dedicated Instances - No one else will share your hardware
* Dedicated Hosts - You book a entire host and control how instances are created. Get for a 3 year period. Useful for Bring your own license purpose.


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
