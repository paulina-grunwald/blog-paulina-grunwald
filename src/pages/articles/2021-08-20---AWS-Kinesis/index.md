---
title: AWS Kinesis
date: '2021-08-20T23:46:37.121Z'
layout: post
draft: false
path: '/posts/aws-kinesis/'
category: 'AWS'
tags:
  - 'AWS'
  - 'Kinesis'
description: 'Streaming data and AWS Kinesis Service'
---

# AWS Kinesis

Amazon Kinesis is the AWS solution for collecting, processing, and analyzing streaming data in the cloud. When you need “real-time” think Kinesis.

**Streaming data** is data that is generated continously by thousands of data sources , which typically send the data records simultaneously and in small sizes (order of Kilobytes).

There are three different types of Kinesis:

1.  Kinesis Streams
2.  Kinesis Firehose
3.  Kinesis Data Streams

- pucharse form online stores
- stock prices
- game data
- social network data
- geospacial data

## Kinesis Streams

Data are stored by default for 24 hours and maximum 7 days. You can
Kinesis Streams consists of shards. Each shard can process 5 transactions per second for reads and up to maximum total data rate of 2MB per second and up to 1,000 records per second writes. Maximum total data write rate is 1MB per second.

The data capacity of your stream is a function of the number of shards that you specify for your stream. The total capacity of stream is the sum of the capacities of its shards/

## Kinesis Firehose

In comparision to Kinesis Streams Kinesis Firehose doesn't have persistent storage and data have to be analysed when they arrive to the service. It's optional to have Lambda functions in Kinesis Firehose. For example as soon as the data comes in to Kinesis Firehose Lambda can process the data and then for example store it in S3.

#
