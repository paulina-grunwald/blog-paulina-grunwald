---
title: All you need to know about AWS Global Infrastructure
date: '2021-07-20T23:46:37.121Z'
layout: post
draft: false
path: '/posts/infrastructure-aws/'
category: 'AWS Cloud'
tags:
  - 'AWS'
  - 'infrastructure'
  - 'Cloud'
description: 'Intro about AWS Global Infrastructure (Regions, Availability Zones Edge Locations and Regional Edge Caches.'
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

<div>
  <table style="width:50%; text-align: justify">
    <tbody>
      <tr>
        <th>Code</th>
        <th>Name</th>
    </tr>
    <tr>
        <td><code class="code">us-east-2</code></td>
        <td>US East (Ohio)</td>
    </tr>
    <tr>
        <td><code class="code">us-east-1</code></td>
        <td>US East (N. Virginia)</td>
    </tr>
    <tr>
        <td><code class="code">us-west-1</code></td>
        <td>US West (N. California)</td>
    </tr>
    <tr>
        <td><code class="code">us-west-2</code></td>
        <td>US West (Oregon)</td>
    </tr>
    <tr>
        <td><code class="code">af-south-1</code></td>
        <td>Africa (Cape Town)</td>
    </tr>
    <tr>
        <td><code class="code">ap-east-1</code></td>
        <td>Asia Pacific (Hong Kong)</td>
    </tr>
    <tr>
        <td><code class="code">ap-south-1</code></td>
        <td>Asia Pacific (Mumbai)</td>
    </tr>
    <tr>
        <td><code class="code">ap-northeast-3</code></td>
        <td>Asia Pacific (Osaka-Local)</td>
    </tr>
    <tr>
        <td><code class="code">ap-northeast-2</code></td>
        <td>Asia Pacific (Seoul)</td>
    </tr>
    <tr>
        <td><code class="code">ap-southeast-1</code></td>
        <td>Asia Pacific (Singapore)</td>
    </tr>
    <tr>
        <td><code class="code">ap-southeast-2</code></td>
        <td>Asia Pacific (Sydney)</td>
    </tr>
    <tr>
        <td><code class="code">ap-northeast-1</code></td>
        <td>Asia Pacific (Tokyo)</td>
    </tr>
    <tr>
        <td><code class="code">ca-central-1</code></td>
        <td>Canada (Central)</td>
    </tr>
    <tr>
        <td><code class="code">eu-central-1</code></td>
        <td>Europe (Frankfurt)</td>
    </tr>
    <tr>
        <td><code class="code">eu-west-1</code></td>
        <td>Europe (Ireland)</td>
    </tr>
    <tr>
        <td><code class="code">eu-west-2</code></td>
        <td>Europe (London)</td>
    </tr>
    <tr>
        <td><code class="code">eu-south-1</code></td>
        <td>Europe (Milan)</td>
    </tr>
    <tr>
        <td><code class="code">eu-west-3</code></td>
        <td>Europe (Paris)</td>
    </tr>
    <tr>
        <td><code class="code">eu-north-1</code></td>
        <td>Europe (Stockholm)</td>
    </tr>
    <tr>
        <td><code class="code">me-south-1</code></td>
        <td>Middle East (Bahrain)</td>
    </tr>
    <tr>
        <td><code class="code">sa-east-1</code></td>
        <td>South America (São Paulo)</td>
    </tr>
     <tr>
        <td><code class="code">us-gov-east-1</code></td>
        <td>AWS GovCloud (US-East)</td>
    </tr>
     <tr>
        <td><code class="code">us-gov-west-1</code></td>
        <td>AWS GovCloud (US-West)</td>
    </tr>
  </tbody>
  </table>
</div>
## Edge Locations

- Edge Locations are **AWS sites deployed in major cities and highly populated areas across the globe**. They far outnumber the number of availability zones available.
- While Edge Locations are not used to deploy your main infrastructures such as [EC2 instances](https://cloudacademy.com/aws-ec2-instance-types-explained/), [EBS storage](https://cloudacademy.com/amazon-ebs-shink-volume/), VPCs, or RDS resources like AZs, they are used by AWS services such as **AWS CloudFront** and **AWS Lambda@Edge** (currently in Preview) **to cache data and reduce latency for end-user access by using the Edge Locations as a global Content Delivery Network (CDN)**.As a result, Edge Locations are primarily used by end users who are accessing and using your services.

## Regional Edge Cache

**_Lambda@Edge_** is a feature of Amazon CloudFront that lets you **_run code closer to users of your application_**, which improves performance and reduces latency. With Lambda@Edge, you don't have to provision or manage infrastructure in multiple locations around the world. You pay only for the compute time you consume - there is no charge when your code is not running

Lambda@Edge lets you run **_Node.js_** and **_Python Lambda_** functions to customize content that CloudFront delivers, executing the functions in AWS locations closer to the viewer. **_The functions run in response to CloudFront events_**, without provisioning or managing servers. You can use Lambda functions to change CloudFront requests and responses at the following points:

- After CloudFront receives a request from a viewer (viewer request)
- Before CloudFront forwards the request to the origin (origin request)
- After CloudFront receives the response from the origin (origin response)
- Before CloudFront forwards the response to the viewer (viewer response)

### Use Cases

With Lambda@Edge, you can build a variety of solutions, for example:

- **Inspect cookies to rewrite URLs to different versions of a site for A/B testing.**

- Send different objects to your users based on the `User-Agent` header, which contains information about the device that submitted the request. For example, you can send images in different resolutions to users based on their devices.
- Inspect headers or authorized tokens, inserting a corresponding header and allowing access control before forwarding a request to the origin.
- Headers modifications → Add, delete, and modify headers, and rewrite the URL path to direct users to different objects in the cache.
- Customize Generate new HTTP responses to do things like redirect unauthenticated users to login pages, or create and deliver static webpages right from the edge. For more information, see [Using Lambda functions to generate HTTP responses to viewer and origin requests](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/http-response-generation.html) in the *Amazon CloudFront Developer Guide*.
  ote: can't have Lambda@Edge without Cloudfront!

## References

- [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
