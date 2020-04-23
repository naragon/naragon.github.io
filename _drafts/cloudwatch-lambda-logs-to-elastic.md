---
layout: post
title: Sending AWS ClouWatch Logs to Elasticsearch with Functionbeat
categories: aws cloudwatch lambda elasticsearch
---

Recently, I was watching the excellent course on AWS Lambda - [Production-Ready Serverless](https://www.manning.com/livevideo/production-ready-serverless) - by Yan Cui. Although the course is starting to become a little dated, it's still very useful. One of the lessons in the course shows how to send CloudWatch logs for Lambda functions to a hosted Elasticsearch solution - [Datadog](https://https://www.datadoghq.com/), specifically. The solution involved writing a custom Lambda function to send the CloudWatch log events to Datadog using an API key.

Since I already run my Elastic Stack, I was looking for a way to send the information to a self-hosted ELK stack.

I came across the following posts:

- [Streaming AWS CloudWatch Logs to your own ELK logging solution](https://medium.com/@sohit_kumar/streaming-aws-cloudwatch-logs-to-your-own-elk-logging-solution-2bbd32f25100)

- [Lambda Logs in ELK](https://medium.com/bbc-design-engineering/lambda-logs-in-elk-e4d924757249)

Eventually, I decided to use [Functionbeat](https://www.elastic.co/beats/functionbeat) for a simpler way to send CloudWatch logs to Elasticsearch. Functionbeat is free.

![](https://static-www.elastic.co/v3/assets/bltefdd0b53724fa2ce/blt6237966c22b17d95/5c94fa6e3baf7a5933ef5636/diagram-functionbeat-architecture.svg)

Functionbeat works by deploying a Lambda function (written in Go) to your AWS account that listens for CloudWatch events.

Pre-requisites:

- **ELK Stack with an Elasticsearch endpoint** - by the way if you're looking for a good tutorial on how to set this up, I recommend the one from [Digital Ocean](), which shows how to set up ELK on an Ubuntu server.
