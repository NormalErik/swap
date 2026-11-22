Authentication can be enforced at different layers of a system's architecture [^6]. This cheat sheet compares the main patterns, where verification happens in each, and what that means for trust boundaries:
- **Service-Level:** each service verifies identity itself, or delegates it to a proxy tightly coupled to it.
- **Edge-Level:** authentication is centralized in a shared component at the system boundary.
### Service-Level Embedded Authentication

In this pattern, each service handles primary authentication itself: it manages identities and credentials, verifies them, and implements the authentication workflows, typically with username/password or API keys. All authentication logic and subject data storage live inside the service, in custom code or built-in libraries. If you have to maintain such a service, the credential handling must follow the [Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) and the [Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html).

Pros:
- **Simplicity:** Each service is self-contained and needs no external authentication infrastructure.
- **Customization freedom:** Authentication behavior can be adapted to service-specific requirements without external constraints.
- **Support for external and internal actors:** Because the service controls all authentication functionality, it can orchestrate different authentication contexts (internal services and external users), at the price of significant complexity (see the authentication orchestration con below).
Cons:
- **Inconsistency:** Authentication behavior, credential storage, and flows differ across services, which fragments the system, degrades the user experience, and rules out Single Sign-On (SSO).
- **Security risk:** Authentication code is duplicated across services, increasing the risk of vulnerabilities and complicating audits.
- **Maintenance burden:** Changing authentication methods (for example, introducing multi-factor authentication (MFA)) requires updates across all affected services.
- **Limited scalability:** Each service manages its own identities, which does not scale to service-to-service authentication across a large system.
- **Limited observability and governance:** Without centralized monitoring, credential reuse, account compromise, or brute-force attacks against one service remain invisible to the others, hindering coordinated detection and response.
- **Authentication orchestration:** Supporting multi-principal subjects (multiple authentication configurations, protocol chaining, and subject-specific variations for contexts such as first- and third-party access, or external clients next to service-to-service calls) adds significant complexity.
- **Coupling of external authentication data with internal trust assumptions:** Using the same authentication data for external clients and internal services increases the risk of leakage and unauthorized access. If an internal service is exposed through a misconfiguration, or an attacker gains internal access, the leaked authentication data grants access to sensitive resources.

### Service-Level Code-Mediated Authentication

### Service-Level Proxy-Mediated Authentication

### Edge-Level Authentication