---
layout: post
title: Sending AWS Lambda Clouwatch Logs to Elasticsearch
categories: aws cloudwatch lambda elasticsearch
---

Recently, I've been watching the excellent course on AWS Lambda - [Production-Ready Serverless](https://www.manning.com/livevideo/production-ready-serverless) - by Yan Cui. The course is a little dated, but it's still useful nonetheless.

One of the lessons in the course involves sending Lambda function logs to a hosted Elasticsearch solution, Datadog, in this case.

I didn't want to sign up for a hosted Elasticsearch service,  as I already run my own Elastic Stack server, so I Googled for articles on how to go about doing this.

The posts I came across included the following:

[Article1](https://example.com)

[Article 2](https://example.com)

Instead, I decided to leverage [Functionbeat](https://www.elastic.co/beats/functionbeat) to do this.

Functionbeat works by deploying a Lambda function (written in Go) to your AWS account that listens for CloudWatch events.

Pre-requisites:

* ELK Stack with an Elasticsearch endpoint




