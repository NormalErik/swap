Applications of this type typically support connected scenarios and can support different browsers running on a range of operating systems and platforms [^2].

The core of a Web application is its server-side logic. This logic may be comprised of many distinct layers. A typical example is a three-layered architecture comprising presentation, business, and data layers, as shown in Figure 5 [^2].

A Web application is an application that can be accessed by the users through a Web browser or a specialized user agent [^2]. The browser creates HTTP requests for specific URLs that map to resources on a Web server [^2]. 

![[web_application_archetype.png]]

Figure 1: Web application architecture with common components grouped by different areas of concern. Based on [^2]
# Specific Design Issues
You must consider several common issues as you develop your design. These issues can be categorized into specific areas of the design. common issues in each area are [^2]:
- [[#Request-Response Patterns]]
- [[#Authentication]]
- Authorization
- Caching
- Exception Management
- Logging and Instrumentation
- Navigation
- Page Layout
- Page Rendering
- Session Management
- Validation
## Request-Response Patterns

You should choose REST or GraphQL if you are looking for a synchronous client-browser communication. Synchronous is also SOAP, but it is more of a legacy enterprise standard, and RPC/gRPC, but it has limited browser client support (gRPC-Web).

The complete guide for API communication patterns can be found [here](https://blog.blackwell-systems.com/posts/api-communication-patterns-guide/?utm_source=chatgpt.com).
### REST 
Representational State Transfer (REST) is an architectural style for building API's using HTTP and standard methods [^5]. 

```
# Get all users
GET https://api.example.com/users
Response: 200 OK
[
  {"id": 1, "name": "Alice"},
  {"id": 2, "name": "Bob"}
]

# Get specific user
GET https://api.example.com/users/1
Response: 200 OK
{"id": 1, "name": "Alice", "email": "alice@example.com"}

# Create user
POST https://api.example.com/users
Body: {"name": "Charlie", "email": "charlie@example.com"}
Response: 201 Created
{"id": 3, "name": "Charlie", "email": "charlie@example.com"}

# Update user
PUT https://api.example.com/users/3
Body: {"name": "Charles", "email": "charlie@example.com"}
Response: 200 OK
{"id": 3, "name": "Charles", "email": "charlie@example.com"}

# Delete user
DELETE https://api.example.com/users/3
Response: 204 No Content
```

You should choose REST if you have the following quality attributes, architectural concerns and constraints.

| Quality Attribute               | Priority | Explanation              |
| ------------------------------- | -------- | ------------------------ |
| Modifiability (Maintainability) | Low      | Fixed response structure |
| Analysability (Maintainability) | High     | Simpler than REST        |
- Specific concern: The system must use **simple** data structures
- Specific concern: The system must allow only **simple** data requests
- Specific concern: The system must have **HTTP Caching out of the box**
### GraphQL
GraphQL is a query language that lets clients request exactly the data they need. You should choose GraphQL if you have the following quality attributes, architectural concerns and constraints.

```
# Client specifies exactly what it needs
query {
  user(id: 123) {
    name
    email
    posts(limit: 5) {
      title
      createdAt
      comments(limit: 3) {
        author
        text
      }
    }
  }
}

```

| Quality Attribute               | Priority | Explanation             |
| ------------------------------- | -------- | ----------------------- |
| Modifiability (Maintainability) | High     | Client specifies fields |
| Analysability (Maintainability) | Medium   | More complex than REST  |
- Specific concern: The system must enable **complex, nested** data structures
- Specific concern: The system must enable **complex, nested** data requests
- Specific concern: The system must enable for **minimal data transfer**
- Specific concern: The system must enable multiple clients needing **different data shapes**
- Specific concern: The system must prevent **Over-fetching**
- Specific concern: The system must prevent **Under-fetching**
## Authentication
The possible [[Authentication]] patterns applicable depend on the amount of services, which again are dependend on the amount of tiers. For example in the case of an 4 tier deployment, planing one service on the web server and one on the application server then deciding for the Service-Level Embedded Authentication would mean a maintenance burden because both services need to be updated and maintained individually. When you have only 3 tier deployment with one service there is no maintenance burden because there is only one service.

More about the Authentication patterns can be found

## Authorization

---

[^1]: https://medium.com/@najamhassan569/understanding-callback-vs-postback-whats-the-difference-and-why-it-matters-b39e8f2fe391

[^2]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ee658099(v=pandp.10)

[^3]: https://www.ibm.com/think/topics/rapid-application-development

[^4]: https://www.ibm.com/think/topics/test-driven-development

[^5]: https://blog.blackwell-systems.com/posts/api-communication-patterns-guide/?utm_source=chatgpt.com

https://openstax.org/books/introduction-computer-science/pages/11-1-modern-web-applications-architectures

[^6]: https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Patterns_Cheat_Sheet.html#service-level-embedded-authentication
