---
title: AWS S3
date: '2021-07-14T23:46:37.121Z'
layout: post
draft: false
path: '/posts/aws-s3/'
category: 'AWS'
tags:
  - 'AWS'
  - 'S3'
  - 'Data storage'
description: 'Storing data using S3.'
---

# AWS S3

## General Overview

- **Object storage**❗
- S3 Object consists:
  - **_Key_** (name of the object)
  - **_Value_** (data of the object is made of)
  - **_Version ID_** (important for versioning)
  - **_Metadata_** (data about the data, set of key/value pairs)
  - **_Subresources e.g torrent_**
- Data is spread across multiple devices and facilities
- Built for **99.99% availability**
- **99.99999% durability** for S3 information
- Tiered Storage available
- Lifecycle Managmnet
- Versioning & Encryption
- **Tags** can be used to organize buckets
- Buckets are placed in the region.
- S3 is a flat structure, there is no hierarchy like you would see in a typical file system.
- Object management through life-cycle policies
- Origin for cloud front cdn
- file sharing and backup/archiving for hybrid networks (via AWS storage gateway)
- **Objects stay within an AWS region and are synced across all AZ's.**
- ALL regions support **read-after-write consistency for PUTS** of new objects into S3.→ Objects are immediately available after putting the object in S3.
- All regions use **eventually consistency for PUTS overwriting existing objects and DELETES** of objects.
- **All objects by default are private.** Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects.

**You can't delete the bucket if there are files inside.** If you use **CloudFormation** to tare down the stack you can trigger lambda function on stack delete to recursively go thorough the bucket and delete all files.

## S3 Bucket Policies and ACLs

S3 ACLs are legacy access control mechanism. AWS recommends using IAM Policies and S3 Bucket Policies. If you need to apply policies on an object itself, then you can use S3 ACL.

Note: Bucket Policies can be only applied at the bucket level where S3 ACLs can be applied to individual files (S3 objects).

## CORS

- **_Cross-origin resource sharing (CORS)_** defines a way for client web applications that are loaded in one domain to interact with resources in a different domain.
- To configure your bucket to allow cross-origin requests, you create a CORS configuration.
- The CORS configuration is a document with rules that identify the origins that you will allow to access your bucket, the operations (HTTP methods) that will support for each origin, and other operation-specific information.
- You can add up to **100 rules** to the configuration.
- You can add the CORS configuration as the cors subresource to the bucket.

If you are configuring CORS in the S3 console, you must use JSON to create a CORS configuration

- In the CORS configuration, you can specify the following values for the `AllowedMethod` element.
  - GET
  - PUT
  - POST
  - DELETE
  - HEAD

```xml
<CORSConfiguration>
 <CORSRule>
   <AllowedOrigin>http://www.example1.com</AllowedOrigin>

   <AllowedMethod>PUT</AllowedMethod>
   <AllowedMethod>POST</AllowedMethod>
   <AllowedMethod>DELETE</AllowedMethod>

   <AllowedHeader>*</AllowedHeader>
 </CORSRule>
 <CORSRule>
   <AllowedOrigin>http://www.example2.com</AllowedOrigin>

   <AllowedMethod>PUT</AllowedMethod>
   <AllowedMethod>POST</AllowedMethod>
   <AllowedMethod>DELETE</AllowedMethod>

   <AllowedHeader>*</AllowedHeader>
 </CORSRule>
 <CORSRule>
   <AllowedOrigin>*</AllowedOrigin>
   <AllowedMethod>GET</AllowedMethod>
 </CORSRule>
</CORSConfiguration>
```

### **AllowedOrigin element**

In the `AllowedOrigin` element, you specify the origins that you want to allow cross-domain requests from, for example, `http://www.example.com`. The origin string can contain only one `*` wildcard character, such as `http://*.example.com`. You can optionally specify `*` as the origin to enable all the origins to send cross-origin requests. You can also specify `https` to enable only secure origins.

### **AllowedHeader element**

The `AllowedHeader` element specifies which headers are allowed in a preflight request through the `Access-Control-Request-Headers` header. Each header name in the `Access-Control-Request-Headers` header must match a corresponding entry in the rule. Amazon S3 will send only the allowed headers in a response that were requested.

Each AllowedHeader string in the rule can contain at most one _ wildcard character. For example, `<AllowedHeader>x-amz-_</AllowedHeader>` will enable all Amazon-specific headers.

### **ExposeHeader element**

Each `ExposeHeader` element identifies a header in the response that you want customers to be able to access from their applications (for example, from a JavaScript `XMLHttpRequest` object).

### **MaxAgeSeconds element**

The `MaxAgeSeconds` element specifies the time in seconds that your browser can cache the response for a preflight request as identified by the resource, the HTTP method, and the origin.

Important to keep in mind:

- You can't delete the bucket if there are files inside. If you use CloudFormation to tare down the stack you can trigger lambda function on stack delete to recursively go thorough the bucket and delete all files.

## Providing cross-account access to objects that are in Amazon S3 buckets?

Use one of the following methods to grant cross-account access to objects that are stored in S3 buckets:

- **Resource-based policies and AWS Identity and Access Management (IAM) policies** for programmatic-only access to S3 bucket objects
- **Resource-based Access Control List (ACL) and IAM policies** for programmatic-only access to S3 bucket objects
- **Cross-account IAM roles** for programmatic and console access to S3 bucket objects

## References

- [Cross-account S3 access](https://aws.amazon.com/premiumsupport/knowledge-center/cross-account-access-s3/)
