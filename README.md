## Team "K8C"
### Team members:
- Dandamaev Gadji
- Smolkin Mikhail
- Tsaturyan Konstantin
- Tsurkan Daniel

## Product requirements:
### Self-documenting API gateway
A typical ingress implementation in k8s forwards incoming traffic to a particular application. An improved API Gateway would integrate Single Sign-On, automatic OpenAPI schema generation, request validation and response caching. The goal of the project is to develop such a Kubernetes operator to extend existing ingress implementations to API Gateway. The project should provide means to define API schema using Custom Resource Definitions in K8s directly and generate them from the source code following a set of conventions.

### Stakeholders
- Anton Sergeevich Kheintankov
- Kaspersky Lab
- Yandex

### Features
- Request routing  
Implements K8s ingress reverse proxy functionality. The reverse proxy forwards incoming traffic from external clients to appropriate service within K8s service. Configure the reverse proxy via Custom Resource Definitions for dynamic rules update.  
- Audit (traffic logging)  
Logging of incoming requests and responses. Availability for collecting metrics. K8s operator for configuration of the logs level and logs path.
- Load balancing  
Integration with K8s native load balancing to improve perfomance of the system overall and make it scalable. Configuration is provided in CRDs.
- Single Sing-On  
Integration with SSO protocols and support of the different auth methods. Store session tickets securely and clear on expiration.
- OpenAPI scheme generation  
Automated generation of the OpenAPI scheme based on the source code. Use CRDs to allow API scheme generation on the K8s level.
- Request Validation  
Validation of the requests for corresponding to OpenAPI scheme. Rules are defined in CRDs. Invalid requests are rejected with an corresponding error.
- Response Caching  
Caching response via key, using defined time-to-live. Implement cache invalidation mechanisms to ensure that cached content is not outdated
- Errors handling and response customization  
Availability for customization of error pages for different HTTP error codes or responses.

### Constrains/Implementation rules/Non-functional requirements
- Up-to-date documentation
- Custom Resource Definition (with yaml configuration)
- HTTP IPv4 network stack
- Support at least 1000 request per second
- Session ticket usage
- Response timeout: 5s
- Cache expiration time: 2h
- Session expiration: 8h
- Testing coverage not less than 80%
- Successfull load testing
- Logs are stored for 30 days
