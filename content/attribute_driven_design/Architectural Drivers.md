Before commencing design with a design method, you need to think about what you are doing and why [^1]. We categorize these “what” and “why” questions as architectural drivers [^1]. These drivers include a design purpose, quality attributes, primary functionality, architectural concerns, and constraints [^1]. These considerations are critical to the success of the system and, as such, they drive and shape the architecture [^1].
## Design Purpose
You need to be clear about the purpose of the design that you want to achieve, because this has impact on the design itself. The purpose includes things like, when and why but also the business goals of the organization.

**Project proposal** as architecture design purpose would be one example. It is not uncommon that, as part of determining project feasibility, schedule, and budget, an initial architecture is created. Such an architecture would not be very detailed; its purpose is to understand and break down the architecture in sufficient detail that the units of work are understood and hence may be estimated.

**Exploratory Prototype** would be another option. In this case, the purpose of the architecture design process is not so much to create a releasable or reusable system, but rather to explore the domain, to explore new technology, to place something executable in front of a customer to elicit rapid feedback, or to explore some quality attribute (such as performance scalability or failover for availability).

**Architecture during development** would be a third option. This could be for an entire new system, for a substantial portion of a new system, or for a portion of an existing system that is being refactored or replaced. In this case, the purpose is to do enough design work to satisfy requirements, guide system construction and work assignments, and prepare for an eventual release.

The purposes varies for greenfield systems in mature domains, for greenfield systems in novel domains, and for brownfield system. 

In a **mature domain** the architect can reuse existing systems as examples and confidently make estimates based on analogy. 

In **novel domains** processes will be far more complex and risky, and may have highly variable results. In these circumstances, a prototype of the system, or a key part of the system, may need to be created to mitigate risk and reduce uncertainty. In many cases, this architecture may also need to be quickly adapted as new requirements are learned and embraced. 

In **brownfield systems**, while the requirements are better understood, the existing system is itself a complex object requirements are better understood, the existing system is itself a complex object that must be well understood for planning to be accurate.

Finally, the development organization’s goals during development or maintenance may affect the architecture design process. For example, the organization might be interested in designing for reuse, designing for future extension or subsetting, designing for scalability, designing for continuous delivery, designing to best utilize existing project capabilities and team member skills, and so forth. Or the organization might have a strategic relationship with a vendor. Or the CIO might have a specific like or dislike and wants to impose it on your project.
## Quality Attributes

> Quality attrivutes are defined as being measurable or testable properties of a system that are used to indicate how well the system satisfies the needs of its stakeholders. Because quality tends to be a subjective concept in itself, these properties allow quality to be expressed succinctly and objectively.

The best way to discuss, document, and prioritize quality requirements is a set of scenarios., which is practically describes the system's response to some stimulus. You can use the following template to write them down:

| No  | Entry            | Explanation                                                                 |
| --- | ---------------- | --------------------------------------------------------------------------- |
| 1.  | Stimulus source  | Origin of stimulus (person(role), system, etc.)                             |
| 2.  | Stimulus         | Type of stimulus (specific event)                                           |
| 3.  | Artifact         | What (part) needs to react to the stimulus (whole system, certain function) |
| 4.  | Environment      | Context factors that influence the fulfillment of the requirements          |
| 5.  | Response         | Type of response                                                            |
| 6.  | Response Measure | Measurement as foundation for determining whether quality is fulfilled      |
An example for the quality characteristic "Availability" could be:

| No  | Entry            | Explanation                                                                                                                                                |
| --- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.  | Stimulus source  | (network connection) DB-server                                                                                                                             |
| 2.  | Stimulus         | A DB-server is no longer reachable / does not reply                                                                                                        |
| 3.  | Artifact         | Persistent data                                                                                                                                            |
| 4.  | Environment      | Normal operation                                                                                                                                           |
| 5.  | Response         | The error is identified and logged, remaining servers are used. Recovery of relevant customer data from backups is initiated.                              |
| 6.  | Response Measure | Customers who did not have their data stored on this server are not impacted, other customers experience an interruption of availability of max 5 minutes. |

### Quality attribute scenario

As with other requirements, scenarios should be prioritized. This can be achieved by considering two dimensions that are associated with each scenario and that are assigned a rank of importance: 
- The first dimension corresponds to the importance of the scenario with respect to the success of the system. This is ranked by the customer. 
- The second dimension corresponds to the degree of technical risk associated with the scenario. This is ranked by the architect. 

The following example is a quality attribute scenario from a Network Management System [^3]

| ID   | Quality Attribute      | Scenario                                                                                                                                                                                | Associated use case                | Priority |
| ---- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- | -------- |
| QA-1 | Performance            | Several network devices send traps to the management system at peak load. 100% of the traps are successfully processed and stored.                                                      | Detect network device fault (UC-2) | H, H     |
## Primary Functionality

When designing an architecture, you need to consider at least the primary functionality. Primary functionality is usually defined as functionality that is critical to achieve the business goals that motivate the development of the system. Other criteria for primary functionality might be that it implies a high level of technical difficulty or that it requires the interaction of many architectural elements. As a rule of thumb, approximately 10 percent of your use cases or user stories are likely to be primary.

You need to think how functionality will be allocated to elements (usually modules) to promote modifiability or reusability, and also to plan work assignments.

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
