Before commencing design with a design method, you need to think about what you are doing and why [^1]. We categorize these “what” and “why” questions as architectural drivers [^1]. These drivers include a design purpose, quality attributes, primary functionality, architectural concerns, and constraints [^1]. These considerations are critical to the success of the system and, as such, they drive and shape the architecture [^1].
## Design Purpose

## Quality Attributes

### Quality attribute scenario

As with other requirements, scenarios should be prioritized. This can be achieved by considering two dimensions that are associated with each scenario and that are assigned a rank of importance: 
- The first dimension corresponds to the importance of the scenario with respect to the success of the system. This is ranked by the customer. 
- The second dimension corresponds to the degree of technical risk associated with the scenario. This is ranked by the architect. 

The following example is a quality attribute scenario from a Network Management System [^3]

| ID   | Quality Attribute      | Scenario                                                                                                                                                                                | Associated use case                | Priority |
| ---- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- | -------- |
| QA-1 | Performance            | Several network devices send traps to the management system at peak load. 100% of the traps are successfully processed and stored.                                                      | Detect network device fault (UC-2) | H, H     |

### Quality characteristics
The product quality model defined in ISO/IEC 25010 comprises the nine quality characteristics shown in the following figure [^2]:

![[software_quality_characteristics.png]]

#### Functional Suitability
- **Functional completeness -** Degree to which the set of functions covers all the specified tasks and intended users' objectives.
- **Functional correctness -** Degree to which a product or system provides accurate results when used by intended users.
- **Functional appropriateness -** Degree to which the functions facilitate the accomplishment of specified tasks and objectives.
#### Performance Efficiency
- **Time behaviour -** Degree to which the response time and throughput rates of a product or system, when performing its functions, meet requirements.
- **Resource utilization -** Degree to which the amounts and types of resources used by a product or system, when performing its functions, meet requirements.
- **Capacity -** Degree to which the maximum limits of a product or system parameter meet requirements.
#### Compatibility
- **Co-existence -** Degree to which a product can perform its required functions efficiently while sharing a common environment and resources with other products, without detrimental impact on any other product.
- **Interoperability -** Degree to which a system, product or component can exchange information with other products and mutually use the information that has been exchanged.
#### Interaction Capability
- **Appropriateness recognizability -** Degree to which users can recognize whether a product or system is appropriate for their needs.
- **Learnability -** Degree to which the functions of a product or system can be learnt to be used by specified users within a specified amount of time.
- **Operability -** Degree to which a product or system has attributes that make it easy to operate and control.
- **User error protection.** Degree to which a system prevents users against operation errors.
- **User engagement -** Degree to which a user interface presents functions and information in an inviting and motivating manner encouraging continued interaction.
- **Inclusivity -** Degree to which a product or system can be used by people of various backgrounds (such as people of various ages, abilities, cultures, ethnicities, languages, genders, economic situations, etc.).
- **User assistance -** Degree to which a product can be used by people with the widest range of characteristics and capabilities to achieve specified goals in a specified context of use.
- **Self-descriptiveness -** Degree to wich a product presents appropriate information, where needed by the user, to make its capabilities and use immediately obvious to the user without excessive interactions with a product or other resources (such as user documentation, help desks or other users).
#### Realiability
- **Faultlessness -** Degree to which a system, product or component performs specified functions without fault under normal operation.
- **Availability -** Degree to which a system, product or component is operational and accessible when required for use.
- **Fault tolerance -** Degree to which a system, product or component operates as intended despite the presence of hardware or software faults.
- **Recoverability -** Degree to which, in the event of an interruption or a failure, a product or system can recover the data directly affected and re-establish the desired state of the system.
#### Security
- **Confidentiality -** Degree to which a product or system ensures that data are accessible only to those authorized to have access.
- **Integrity -** Degree to which a system, product or component ensures that the state of its system and data are protected from unauthorized modification or deletion either by malicious action or computer error.
- **Non-repudiation -** Degree to which actions or events can be proven to have taken place so that the events or actions cannot be repudiated later.
- **Accountability -** Degree to which the actions of an entity can be traced uniquely to the entity.
- **Authenticity -** Degree to which the identity of a subject or resource can be proved to be the one claimed.
- **Resistance -** Degree to which the product or system sustains operations while under attack from a malicious actor.
#### Maintainability
- **Modularity -** Degree to which a system or computer program is composed of discrete components such that a change to one component has minimal impact on other components.
- **Reusability -** Degree to which a product can be used as an asset in more than one system, or in building other assets.
- **Analysability -** Degree of effectiveness and efficiency with which it is possible to assess the impact on a product or system of an intended change to one or more of its parts, to diagnose a product for deficiencies or causes of failures, or to identify parts to be modified.
- **Modifiability -** Degree to which a product or system can be effectively and efficiently modified without introducing defects or degrading existing product quality.
- **Testability -** Degree of effectiveness and efficiency with which test criteria can be established for a system, product or component and tests can be performed to determine whether those criteria have been met
#### Flexibility
- **Adaptability -** Degree to which a product or system can effectively and efficiently be adapted for or transferred to different hardware, software or other operational or usage environments.
- **Scalability -** Degree to which a product can handle growing or shrinking workloads or to adapt its capacity to handle variability.
- **Installability -** Degree of effectiveness and efficiency with which a product or system can be successfully installed and/or uninstalled in a specified environment.
- **Replaceability -** Degree to which a product can replace another specified software product for the same purpose in the same environment.
#### Safety
- **Operational constraint -** Degree to which a product or system constrains its operation to within safe parameters or states when encountering operational hazard.
- **Risk identification -** Degree to which a product can identify a course of events or operations that can expose life, property or environment to unacceptable risk.
- **Fail safe -** Degree to which a product can automatically place itself in a safe operating mode, or to revert to a safe condition in the event of a failure.
- **Hazard warning -** Degree to which a product or system provides warnings of unacceptable risks to operations or internal controls so that they can react in sufficient time to sustain safe operations.
- **Safe integration -** Degree to which a product can maintain safety during and after integration with one or more components.
## Primary Functionality

## Architectural Concerns

### General concerns
These are “broad” issues that one deals with in creating the architecture, such as establishing an overall system structure, the allocation of functionality to modules, the allocation of modules to teams, organization of the code base, startup and shutdown, and supporting delivery, deployment, and updates.
### Specific concerns
These are more detailed system-internal issues such as exception management, dependency management, configuration, logging, authentication, authorization, caching, and so forth that are common across large numbers of applications. Some specific concerns are addressed in reference architectures (see Section 2.5.1), but others will be unique to your system. Specific concerns also result from previous design decisions. For example, you may need to address session management if you previously decided to use a reference architecture for the development of web applications. 
### Internal requirements
These requirements are usually not specified explicitly in traditional requirement documents, as customers usually seldom express them. Internal requirements may address aspects that facilitate development, deployment, operation, or maintenance of the system. They are sometimes called “derived requirements”.
### Issues
These result from analysis activities, such as a design review (see Section 8.6), so they may not be present initially. For instance, an architectural evaluation may uncover a risk that requires some changes to be performed in the current design.

## Constraints
You need to catalog the constraints on development as part of the architectural design process. These constraints may take the form of mandated technologies, other systems with which your system needs to interoperate or integrate, laws and standards that must be complied with, the abilities and availability of your developers, deadlines that are non-negotiable, backward compatibility with older versions of systems, and so on. An example of a technical constraint is the use of open source technologies, whereas a nontechnical constraint is that the system must obey the Sarbanes-Oxley Act or that it must be delivered by December 15. A constraint is a decision over which you have little or no control as an architect. Your job is, as we mentioned in Chapter 1, to satisfice: to design the best system that you can, despite the constraints you face. Sometimes you might be able to argue for loosening a constraint, but in most cases you have no choice but to design around the constraints

---

[^1]: https://repo.darmajaya.ac.id/3948/1/Designing%20Software%20Architectures_%20A%20Practical%20Approach%20%28%20PDFDrive%20%29.pdf

[^2]: https://iso25000.com/index.php/en/iso-25000-standards/iso-25010

[^3]: https://www.youtube.com/watch?v=d_gRoI3oHag
