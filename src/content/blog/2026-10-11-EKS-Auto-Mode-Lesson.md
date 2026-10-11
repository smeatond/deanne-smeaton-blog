---
title: 'Why I Moved Away From EKS Auto Mode'
description: 'Why I moved away from AWS EKS Auto Mode after issues. My experience moving to Node Groups, taking more control of infrastructure.'
pubDate: 'Oct 11 2026'
heroImage: '../../assets/network.jpg'
tags:
  - AWS
  - EKS
  - Kubernetes
  - DevOps
---

Some lessons you have to learn twice. This is the story of one I learned the hard way on AWS EKS Auto Mode, and what I changed afterwards. 

## The First Warning 

I am working on an application in AWS using the EKS auto mode in a production cluster. In the past we have had unexpected costs around “DataProcessing-Bytes". When it first happened, I will say I was unaware for some time and to AWS’s credit their support was amazing. They helped us set up alerts for if it happened again. Which yes, it did happen again. Through my investigation I found that the nodes had changed to different zones, and I forced them to a single zone with a task to further investigate best practices on my to-do-list. I dedicated some of my time looking into this, but my team is small and had other higher priorities to do.  
 
## It Happened Again 

About 6 months went past, we had just finished a new release and updated the application. Everything looked ok at first. Then at the end of the week, problems started. First, an email from budget anomalies said that something was increasing costs per day. If you haven’t got this set up in your environment, you should now! That and budget alerts.  Something similar to what we had 6 months earlier. I checked the EKS nodes and yes, they had moved to a different zone which was causing a lot of cross-AZ traffic.  I made some changes to force the nodes in the same zone. The reason behind this is that the application did not actually need the benefits of multi zones at this stage. I then added a task for me to remove auto mode once my current priorities were completed. I had the plan and documented a full run book. 

## Moving Away From Auto Mode 
 
By the end of the week, the environment became unstable. My EKS cluster was reporting that everything was ok. But one of the nodes was obviously not happy and was not properly joining the cluster. All the pods on that node were running but had a big restart count, and ingress would not run. As the application was down, I took the opportunity to move away from Auto Mode and start using Node Groups. As I had already moved my dev cluster a month earlier away from Auto Mode to Node Groups, I was confident of doing this now for the production cluster. This was so I could properly control which zone the nodes would be created in, reduce overall AWS costs and improve odd stability issues that Auto Mode was causing. I documented the change properly with the incident report attached. 

## What I Had to Recreate 

Making the move to Node Groups does mean I now have to be more hands on. It also meant somes core add-ons were now missing which I had to add: 
- **CoreDNS** – the default DNS server in Kubernetes 
- **kube-proxy** – core networking service that manages network rules and communication between pods 

I also had to recreate the storage class I was using as it was now missing. For this application, the PVC was to store Redis cache, low-priority RabbitMQ messages and logs which I assessed were ok to completely remove. For other applications you would need to look at proper backup. So, I deleted and recreated the PVC by redeploying the application. 

## What I Learned 

The application has been running well since, and with much lower costs. I chose Auto Mode at the beginning as at the time I was a developer first and only starting to do increasingly more DevOps work. But as AWS has cornered me, it doesn’t really allow for set-and-forget. I now want that control, and I see the benefit of having more granular control over the infrastructure I deploy on. A lot of this was cost-driven, but it is also about stability, and having control gives you more confidence that it is doing what you would expect.  

So, what did I change? I moved to Node Groups so I control where nodes run, I have cost anomaly alerts and budgets in place, and I try to avoid leaving root-cause fixes sitting on a to-do list. Control costs me more hands-on work, but I’d rather have that than surprises. 

**A note on node affinity:** I tested it on dev to keep nodes in one zone, but it didn’t address the wider cost concerns, so I went with Node Groups. 
 
----
If you haven’t set up alerts, follow these AWS guides today: 
- [Setting up your anomaly detection](https://docs.aws.amazon.com/cost-management/latest/userguide/settingup-ad.html) 
- [Create a Budget](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-create.html) 

