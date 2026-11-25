Authentication can be enforced at different layers of a system's architecture [^6]. This cheat sheet compares the main patterns, where verification happens in each, and what that means for trust boundaries:
- **Service-Level:** each service verifies identity itself, or delegates it to a proxy tightly coupled to it.
- **Edge-Level:** authentication is centralized in a shared component at the system boundary.

Each Section contains a short description, a diagram and the architectural drivers that you can compare to.
### Service-Level Embedded Authentication
In this pattern, each service handles primary authentication itself: it manages identities and credentials, verifies them, and implements the authentication workflows, typically with username/password or API keys. All authentication logic and subject data storage live inside the service, in custom code or built-in libraries. If you have to maintain such a service, the credential handling must follow the [Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) and the [Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html).

![[service-level_embedded_authentication.png]]

| Quality Attribute               | Priority | Explanation                                                                                                                                |
| ------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Modifiability (Maintainability) | Low      | Changing authentication methods requires updates across all affected services; Adding multi-principal subjects adds significant complexity |
| Scalability (Flexibility)       | Low      | Each service manages its own identities                                                                                                    |
| Non-repudiation (Security)      | Low      | Risk of complicated audits because of duplicated authentication code across services                                                       |
| Integrity (Security)            | Low      | Risk of vulnerabilities because of duplicated authentication code across services                                                          |
| Authenticity (Security)         | Low      | Risk of Leakage and unauthorized access using the same authentication data for external actors and internal services                       |
| Resistance (Security)           | Low      | Coordinated detection and response his hindered w/o centralized monitoring                                                                 |
- Internal requirement: The authentication of the system should be simple. Each service should be self-contained and no external authentication infrastructure is needed.
- Internal requirement: Services have many different service-specific requirements to adapt to

### Service-Level Code-Mediated Authentication
This pattern addresses key limitations of [Service-Level Embedded Authentication](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Patterns_Cheat_Sheet.html#service-level-embedded-authentication): fragmented identity management, duplicated credential stores, and lack of SSO. The service no longer verifies credentials directly. Instead, an external Identity Provider (IdP) authenticates the subject and issues authentication proofs; the service verifies these itself and extracts identity attributes for request processing.

![[service-level_code-mediated_authentication.png]]

| Quality Attribute                    | Priority | Explanation                                                                                                                                       |
| ------------------------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Modifiability (Maintainability)      | Medium   | Each service must implement and maintain logic for authentication proof verification and protocol-specific behavior                               |
| Integrity (Security)                 | Medium   | Centralized authentication reduces the attack surface (of credential handling); Incorrect verification logic, can introduce severe security risks |
| Authenticity (Security)              | Low      | Risk of Leakage and unauthorized access using the same authentication data for external actors and internal services.                             |
| Operability (Interaction Capability) | Medium   | Consistent authentication flows and session handling across services                                                                              |
| Interoperability (Compatibility)     | High     | OIDC and SAML provide broad and flexible integration possibilities via IdPs                                                                       |
- Internal requirement : The authentication of the system should support Single-Sign-On
- Internal requirement: Services have many different service-specific requirements to adapt to
### Service-Level Proxy-Mediated Authentication
This pattern builds on the [previous pattern](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Patterns_Cheat_Sheet.html#service-level-code-mediated-authentication) but moves authentication logic out of the service into a dedicated proxy deployed as a sidecar alongside it. The proxy sits in front of the application, verifies authentication proofs with the Identity Provider (IdP), injects identity context into the request (typically as headers), and forwards it locally to the service.

![[service-level_proxy-mediated_authentication.png]]
### Edge-Level Authentication
In this pattern, authentication is handled at the system boundary by a shared component such as an API gateway or ingress proxy. This component authenticates incoming requests from external clients before they reach internal services. It uses [OIDC](https://openid.net/specs/openid-connect-core-1_0.html) or [SAML](https://www.oasis-open.org/standard/saml/) with an identity provider for user authentication, validates [OAuth 2.0](https://www.rfc-editor.org/rfc/rfc6749) access tokens for API access, or uses [mTLS](https://www.rfc-editor.org/rfc/rfc8446) for certificate-based client authentication. It propagates verified identity information, typically via headers, to downstream services.

![[edge-level_authentication.png]]
