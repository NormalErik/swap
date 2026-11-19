Layered architectures are said to be the most common and widely used architectural framework in software development [^1]. It is also known as an n-tier architecture and describes an architectural pattern composed of several separate horizontal layers that function together as a single unit of software. A layer is a logical separation of components or code.

The Microsoft Application Architecture Guide is presenting different Application Archetypes. 

## Web Application
Applications of this type typically support connected scenarios and can support different browsers running on a range of operating systems and platforms [^2].

The core of a Web application is its server-side logic. This logic may be comprised of many distinct layers. A typical example is a three-layered architecture comprising presentation, business, and data layers, as shown in Figure 5 [^2].
![[web_application_archetype.png]]

## Service Archetype
 Services expose shared business functionality and allow clients to access them from a local or a remote system. Service operations are called using message passed over a transport channel. The goal of this type of application is to achieve loose coupling between the client and the server [^2].

![[service_application_archetype.png]]

# n-Tier Deployment
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

---
[^1]: https://www.baeldung.com/cs/layered-architecture

[^2]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ee658104(v=pandp.10)

[^3]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ee658120(v=pandp.10)
