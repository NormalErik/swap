Layered architectures are said to be the most common and widely used architectural framework in software development [^1]. It is also known as an n-tier architecture and describes an architectural pattern composed of several separate horizontal layers that function together as a single unit of software [^1]. A layer is a logical separation of components or code [^1].

> Baeldung is an informational and educational Website that help developers explore the Java ecosystem with guides and courses, with a strong focus on web applications, Spring, Spring Security, and RESTful APIs [^4].

Baeldung presents the following advantages and disadvantages of the layered Architecture[^1]:

**Advantages**
- The framework is simple and easy to learn and implement.
- There is reduced dependency because the function of each layer is separate from the other layers.
- Testing is easier because of the separated components, each component can be tested individually.
- Cost overheads are fairly low.
**Disadvantages**
- Scalability is difficult because the structure of the framework does not allow for growth.
- They can be difficult to maintain. A change in a single layer can affect the entire system because it operates as a single unit.
- There is interdependence between layers since a layer depends on the layer above it to receive data.
- Parallel processing is not possible.
 
Which means you should choose the layered architecture if your requirements are suggesting the following quality attributes, architectural concerns and constraints.

| Quality Attribute                       | Priority | Explanation                                                                           |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------- |
| Modularity (Maintainability)            | High     | Logical separation of components                                                      |
| Analysability (Maintainability)         | Medium   | Reduced dependency between layers, but lower layers still depend on the higher layers |
| Modifiability (Maintainability)         | Low      | Change in a single layer can affect the entire system                                 |
| Testability (Maintainability)           | High     | Each component can be tested individually                                             |
| Scalability (Flexibility)               | Low      | Structure does not allow for growth                                                   |
| Time behaviour (Performance Efficiency) | Low      | Parallel processing is not possible                                                   |

+ Internal requirement (Architectural Concern): The architectural framework must be simple & easy to learn & implement because the application needs to be built **quickly** and the developers are **missing architectural knowledge** or **cant decide** which architecture to use
+ Constraint: The ongoing **operating expenses should be as small as possible** relative to the revenue
# Microsoft Application Archetypes
The Microsoft Application Architecture Guide helps understanding capabilities, features, benefits, and liabilities of common application archetypes [^6]. These archetypes are using a layer architecture. The guide contains following archetypes:
- [[Web Applications]]
- Rich Client Applications
- Rich Internet Applications
- Mobile Applications
- Service Applications

> The Microsoft Application Architecture Guide (2nd Edition, October 2009) is intended to help developers and solution architects design and build effective, high quality applications. It provides guidance for using architecture principles, design principles, and patterns [^5].

# Deployment

A layered architecture can be combined with an [[N-Tiered Architecture]].


---
[^1]: https://www.baeldung.com/cs/layered-architecture

[^2]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ee658104(v=pandp.10)

[^3]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ee658120(v=pandp.10)

[^4]: https://www.baeldung.com/about

[^5]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ff650706(v=pandp.10)

[^6]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ee658107(v=pandp.10)
