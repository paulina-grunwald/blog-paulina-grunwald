---
title: All you need to know about AWS Global Infrastructure
date: "2020-05-22T23:46:37.121Z"
layout: post
draft: false
path: "/posts/infrastructure-aws/"
category: "AWS Cloud"
tags:
  - "AWS"
  - "infrastructure"
  - "Cloud"
description: "Intro about AWS Global Infrastructure (Regions, Availability Zones Edge Locations and Regional Edge Caches."
---

## Overview

Amazon Web Services (AWS) as the biggest global public cloud provider owns and maitanns truly global network of infrastructure that comprises of number of data centers around the world. In this article I will desctibe all components of AWS global infrastructure and how they tie togeher.


AWS infrastructure can be split in following components:

- **Regions**
- **Availability Zones (AZs)**
- **Edge Locations**
- **Regional Edge Caches**


## Regions
Each Region is complety independent and isolated from other AWS regions. If you for example launch EC2 instance in one Region, it will not be replicated in another region unless you set it up. Regions have multiple, isolated locations known as Availability Zones (min. of 2 per Region). AWS currently (as in May 2020 when this article was written) spans 76 Availability Zones within 24 geographic regions around the world, and has announced plans for nine more Availability Zones and three more AWS Regions in Indonesia, Japan, and Spain. 3 new AZs (Spain, Tokyo and Jakarta) are coming soon.

## Availability Zones

- Availability Zones and Regions are closely related.
- **AZs are essentially the physical data centers of AWS.** This is where the actual compute, storage, network, and database resources are hosted that we as consumers provision within our **Virtual Private Clouds (VPCs)**.
- **Multiple** data centres located close together form a single availability zone.
- Each AZ will always have at least one other AZ that is geographically located within the same area.
- Each AZ will be isolated from the others using separate power and network connectivity that minimises impact to other AZs should a single AZ fail.

## AZ's (Availbility Zones)

- Every Region will act independently of the others, and each will contain at least two Availability Zones.
- you could even connect different VPCs together in different regions. [Learn more from AWS about Multiple Region Multi-VPC Connectivity](https://aws.amazon.com/answers/networking/aws-multiple-region-multi-vpc-connectivity/).
- there are currently **16** Regions and **43** Availability Zones, with **4** Regions and 11 AZs planned.
- not all AWS services are available in every region.
- The current Regions available at the time of this post are:

**US East:** N. Virginia, Ohio**US West:** N. California, Oregon**Asia Pacific:** Mumbai, Seoul, Singapore, Sydney, Tokyo**Canada:** Central**China:** Beijing**Europe:** Frankfurt, Ireland, London**South America:** São Paulo

- AWS GovCloudAlthough regions are grouped together in this way, every single region in this list is independent from other regions.The AWS GovCloud is an isolated region in the U.S. that is only available to U.S. government agencies.

<table style="width:50%; text-align: justify">
  <tr>
    <th>Name</th>
    <th>Code</th>
  </tr>
  <tr>
    <td>US East (N.Virginia)</td>
    <td>us-east-1</td>
  </tr>
  <tr>
    <td>US East (Ohio)</td>
    <td>us-east2</td>
  </tr>
  <tr>
    <td>US West (N.California)</td>
    <td>us-west-1</td>
  </tr>
   <tr>
    <td>US West (Oregon)</td>
    <td>us-west-2</td>
  </tr>
  <tr>
    <td>Canada (Central)</td>
    <td>ca-central-1</td>
  </tr>
  <tr>
    <td>EU (Ireland)</td>
    <td>eu-west-1</td>
  </tr>
  <tr>
    <td>EU (Frakfurt)</td>
    <td>eu-central-1</td>
  </tr>
   <tr>
    <td>EU (London)</td>
    <td>eu-west-2</td>
  </tr>
   <tr>
    <td>Asia Pacific (Tokyo)</td>
    <td>ap-northeast-1</td>
  </tr>
    <tr>
    <td>Asia Pacific (Seoul)</td>
    <td>ap-northeast-2</td>
  </tr>
  <tr>
    <td>Asia Pacific (Sinpagore)</td>
    <td>ap-southeast-1</td>
  </tr>
  <tr>
    <td>Asia Pacific (Sydney)</td>
    <td>ap-southeast-2</td>
  </tr>
   <tr>
    <td>Asia Pacific (Mumbai)</td>
    <td>ap-south-1</td>
  </tr>
   <tr>
    <td>South America (Sao Paulo)</td>
    <td>sa-east-1</td>
  </tr>
</table>


## Edge Locations

## Regional Edge Cache

Cheers,

Paulina


## References
- [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
