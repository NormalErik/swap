A Web application is an application that can be accessed by the users through a Web browser or a specialized user agent [^2]. The browser creates HTTP requests for specific URLs that map to resources on a Web server [^2]. 

![[web_applications.excalidraw]]
Figure 1: Web application architecture with common components grouped by different areas of concern. Based on [^2]
# Specific Design Issues
The following sections provide guidelines to help you avoid the common issues in each area:
- Authentication
- Authorization
- Caching
- Exception Management
- Logging and Instrumentation
- Navigation
- Page Layout
- Page Rendering
- Session Management
- Validation
## Application Request Processing
Regardless of the request processing strategy you choose, you should ensure separation of concerns by implementing the request processing logic and application logic separately from the UI. Several patterns help achieve this. In general, the Model-View-Presenter (MVP) or similar patterns can be used in a Web Forms post back approach to help provide a clean separation of concerns. The Model-View-Controller (MVC) pattern is typically used in a REST-full request processing approach [^2].
### Post back Approach
The post back approach typically allows a forms-based development experience, and uses rich server-side controls that render the corresponding HTML, associated view state, and interaction logic to the browser [^2]. E.g.: You fill out a form on a website and click “Submit.” The browser sends your data to the server and reloads the page with a confirmation message. This round trip from client to server and back is a postback [^1].

>Rapid application development (RAD) is a software development methodology that encourages speed, iterative development and user feedback rather than detailed upfront planning [^3]. Agile development has overlap typically optimized for adaptive, sustainable software development [^3].

**When to use?**
Consider this approach if you developing a forms-based Web application and require a rapid application development (RAD) experience [^2].
### REST-full Approach
The REST-full approach typically allows finer-grained control over the UI of your application, and provides more flexibility in terms of navigation, testability, and separation of concerns [^2].

**When to use?**
Consider using this approach if your application requires flexible navigation, fine control over its UI, may use alternate UI rendering technologies, or if you are using a test-driven development approach [^2].

> Test-driven development (TDD) is an approach to software development in which software tests are written before their corresponding functions [^4].

### ==🔴ALTERNATIVES==

## Authorization

https://openstax.org/books/introduction-computer-science/pages/11-1-modern-web-applications-architectures

---

[^1]: https://medium.com/@najamhassan569/understanding-callback-vs-postback-whats-the-difference-and-why-it-matters-b39e8f2fe391

[^2]: https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ee658099(v=pandp.10)

[^3]: https://www.ibm.com/think/topics/rapid-application-development

[^4]: https://www.ibm.com/think/topics/test-driven-development
