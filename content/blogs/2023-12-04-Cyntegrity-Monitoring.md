---
title: "2023 12 04 Cyntegrity Monitoring"
date: 2023-12-04T09:24:09-05:00
draft: false
author: "Bishoy"
tags: ["technical", "private"]
image:
description:
toc:
---

Cyntegrity has tasked me with a monitoring project which hasn't been completed until now. Here's the progress so far and the road blockers that have stopped me from getting ahead in this project.

## Current State of the World:

As per the Person responsible for IT. This is the current state:

> on the Application side RD team implemented the APM with Applications insights, and on the Backend it Mongo Atlas Native Monitoring and Alerting.

Up until now, I haven't been granted access to such environments, nor have I been told what parameters are being monitored. This is all despite asking both the product owner and the IT manager.

It also seems that MongoDB atlas is lacking a good way to collect and store logs.

## Suggested Route:

The 2 personas that are affected by the project should be:
- The Product Manager: A non technical, or not so technical, person who only needs to see what is happening in their environment and whether customers are able to use the tool in a productive manner or not.
- The Technical Personnel: The more hands-on people that need to get more parameters about what is happening in their environment and where the bottle neck is.

**The ultimate goal is to provide a comprehensive dashboard where both personas can find their way around, and be able to keep the production environment alive.**

In order to achieve such goal, all monitoring aspects (metrics, logs, and traces) should be tracked in the same place with persona-oriented dashboards.

For the current environment, there are 3 possible ways to achieve this:

### 1. Using Native Monitoring Tools

This will mean building on top of the current dashboards in Azure, as well as moving the Mongo Monitoring to Azure.

Problems with that approach:

1. Azure monitoring is still young and harder to maintain.
2. As of the time of writing, MongoDb Atlas doesn't provide a native way to push metrics and logs to Azure, which will require us to build and maintain a tool that is to be used to move the logs and traces out of Mongo.

### 2. Using tools that are more oriented towards observability

This will include deploying industry leading tools (listed below) and have all the metrics, traces, and logs passed over to them, then create persona-based dashboards.

The tools that are most suited for the job, as of the time of writing, are:
1. Prometheus: A high performance, light-weight database that can collect and store Metrics.
2. Elastic: A database for logs.
3. Grafana: The Dashboarding tool.

Pros:
- Industry Standards.
- Highly Scalable.
- Already compatible with MongoDb, no need to build a new tool.
- Easier to maintain and extend with dashboards.

Cons:
- Will require approvals from Security board.
- Will Require maintenance.

By far, this is the choice I would go with.

### 3. Using 3rd parties providers that can handle observability

This will include pushing monitoring parameters to 3rd party tools like [Datadog](https://www.datadoghq.com/) in the cloud. Such tools have already established themselves as market leaders in observability.

Pros:
- Same outcome as option number 2, but without the maintenance aspect.
- Easier to use, less steep learning curve.

Cons:
- Metrics data are stored in a different cloud, which could mean harder compliance.
- This is a paid service which can have bigger financial impact on Cyntegrity.


## Current Road blocks:

Unfortunately, until now there has been many blockers as to why this project is not taking off. The most important are:

- Lack of clear problem statement from the customer side. This has been making the solution almost impossible, and harder to push through IT.
- Lack of cooperation from the IT manager side. Even when trying to go down the first solution which is the one that is suggested by the IT manager, there has been minimum to no help from the IT manager with communications left unanswered or lately answered. There seems to be a lot of push back against implementing virtually any solutions citing problems like security, budget without suggesting any clear paths to solve such issues.
