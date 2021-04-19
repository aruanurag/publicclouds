---
layout: post
title: "AWS Certified Solution Architect Associate"
date: 2021-04-03 11:11:11 -0000
categories: AWSSolutionArchitectAssociate
---

## Table of Contents

1. [IAM](#IAM)
2. [EC2](#EC2)


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
