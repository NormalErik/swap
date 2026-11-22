# n-Tier Deployment

==🔴https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier==

The _n_-tier pattern represents a general distribution pattern where components of the application are separated across one or more servers. Commonly, you will choose a 2-tier, 3-tier, or 4-tier pattern as described in the following sections. While you will often locate all of the components of a layer on the same tier, this is not always the case. Layers do not have to be confined to a single tier—you can partition workloads across multiple servers if required. For example, you may decide to have side-by-side tiers that contain different aspects of your business logic [^3].

## 2-Tier Deployment
Consider the 2-tier pattern if you are developing a client that will access an application server, or a stand-alone client that will access a separate database server [^3].
![[2-tier_deployment.png]]

## 3-Tier Deployment
Consider the 3-tier pattern if you are developing an Intranet-based application where all servers are located within the private network or an Internet based application and security requirements do not prevent you from implementing business logic on the public facing Web or application server [^3].
![[3-tier_deployment.png]]

## 4-Tier Deployment
Consider the 4-tier pattern if security requirements dictate that business logic cannot be deployed to the perimeter network, or you have application code that makes heavy use of resources on the server and you want to offload that functionality to another server [^3].
![[4-tier_deployment.png]]