---
title: "Declarative API"
date: 2020-12-08T22:53:58+05:30
draft: false
author: "Bishoy"
tags:
  - Kubernetes
  - Infrastructure
  - Technical
image: /images/post.jpg
description: "declarative and imerative apis comparison"
toc: 
---

- I came across the term declarative Api when trying to understand Kubernetes CRDs, and controllers
- Declarative focuses on the what, while imperative focuses on the how

## Still what does that even mean?

- The above explanation didn't convince me that much, So I dug a little deeper.
- A very nice example to describe is Car's climate control vs old AC systems.
  - In an older car, you'd manually determine if you need AC or heater. Then make sure you have the
    correct fan power and also correct air flow. Hence, you are manually defining **how** the system
    should work.
  - Climate Control systems are declarative; that means that you tell the system that you need the
    car's inside to feel like it is 23 degrees, and then the system decides whether to use the AC or
    the heater, and how much power it needs on the fans in order to apply your order. Hence, you are
    telling the system **what** you want and then the system decides on **how** to make that happen.

