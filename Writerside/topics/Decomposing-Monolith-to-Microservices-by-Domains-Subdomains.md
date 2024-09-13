# Decomposing Monolith to Microservices by Domains/Subdomains

## Domain-Driven Design (DDD) as a Foundation

A domain is the business context or the problem space your application operates in. Decomposing by domain requires **Domain-Driven Design (DDD)**, which focuses on dividing the problem space into smaller, manageable **domains** and **subdomains**.

### Key Concepts of Domain-Driven Design (DDD)
- **Domain**: A high-level business area, like e-commerce, customer management, or inventory.
- **Subdomain**: A smaller, more specific area within a domain, like order management or payment processing.
- **Bounded Context**: The boundaries within which a domain model is defined and applicable.
- **Ubiquitous Language**: A shared vocabulary that the development team and business stakeholders use to communicate within a particular domain.

With these DDD concepts, you can systematically break a monolithic application into microservices that closely reflect your business structure.

## Steps for Decomposing Monolith by Domains/Subdomains

### 1. Analyze the Business Domain
Start by understanding the high-level business domain. In this step, you'll identify the **core domains**, which are central to the business, and the **supporting domains**, which are auxiliary but necessary.

#### Types of Domains
- **Core Domain**: The essential business functions that differentiate your business (e.g., order processing for an e-commerce system).
- **Supporting Domain**: Non-core but still essential functions like billing, user authentication, or logging.
- **Generic Domain**: Common functionalities shared across different domains, such as logging, notifications, or monitoring.

Conduct workshops, interviews, or **event storming** sessions with business stakeholders and technical teams to map out the core and supporting domains.

### 2. Identify and Define Subdomains
Each domain often contains multiple subdomains. A **subdomain** is a smaller, more granular piece of functionality within a larger domain. For example:
- **E-Commerce Domain**: May include subdomains like product catalog, inventory, shopping cart, checkout, and order management.
- **Customer Domain**: May include subdomains like customer profile, authentication, and support tickets.

Using techniques like **context mapping** and DDD practices, break the monolith into clear subdomains. These subdomains will serve as the basis for your microservices.

### 3. Map Monolith Components to Domains/Subdomains
After defining your domains and subdomains, analyze your monolithic codebase and map existing functionality to the corresponding domain/subdomain. Identify which parts of the monolith relate to each subdomain, and whether they are tightly coupled or share common dependencies.

#### Questions to Ask:
- Which code modules handle which business functions?
- Can the module be independently deployed?
- What are the dependencies between modules?

This mapping exercise is critical to understanding which areas of the monolith can be separated out as independent services.

### 4. Define Bounded Contexts
Each subdomain should be assigned a **bounded context**, which refers to the boundary where a particular model is valid. The bounded context allows different models and data representations to coexist without overlap.

For instance, the **Customer Profile** subdomain could have its own bounded context where the customer entity is represented. This entity might differ from the customer representation used in the **Order Management** subdomain.

#### Example of Bounded Contexts:
- **Customer Profile Bounded Context**: Manages customer data, addresses, and preferences.
- **Order Management Bounded Context**: Handles customer orders and order history.

### 5. Prioritize Decomposition by Core Domains
Not all domains need to be extracted at once. Begin with **core domains** that represent the most critical business functions. These areas are likely to benefit the most from being scalable, independently deployable, and maintainable.

#### Prioritization Criteria:
- **Business Impact**: Start with domains that have the most impact on your business operations.
- **Technical Complexity**: Extract less complex domains first to gain experience before tackling more challenging areas.
- **Change Frequency**: Services that undergo frequent changes should be decomposed earlier to gain flexibility.

### 6. Implement Service Boundaries and API Contracts
After identifying your domains and subdomains, define **service boundaries** for each microservice. Each microservice should focus exclusively on its domain/subdomain. At this stage, you'll need to design clear API contracts between services to handle inter-service communication.

#### Best Practices for Service Boundaries:
- Ensure loose coupling between services.
- Avoid shared databases between services; each service should own its data.
- Create well-defined APIs for inter-service communication.

### 7. Handle Inter-Service Communication
Microservices will need to communicate, especially when domains are split across multiple services. The two primary methods are:
- **Synchronous Communication**: Use REST APIs or gRPC for real-time communication.
- **Asynchronous Communication**: Use messaging systems like Kafka or RabbitMQ for event-driven architecture, where services communicate via events.

In an e-commerce system, the **Order Service** might publish an event when an order is placed, which the **Inventory Service** listens to in order to update stock levels.

### 8. Ensure Data Consistency Across Services
In a monolithic application, transactions can span multiple parts of the system. In microservices, maintaining this kind of consistency becomes more difficult due to the distributed nature of data.

#### Techniques for Maintaining Consistency:
- **Saga Pattern**: Manage distributed transactions by breaking them into smaller, compensatable steps. If one step fails, previous steps are rolled back.
- **Eventual Consistency**: Accept that data will not be immediately consistent across services, but changes will propagate over time.
- **CQRS** (Command Query Responsibility Segregation): Separate the responsibility for writing and reading data, allowing each service to own its data while synchronizing updates through events.

### 9. Test and Validate Microservices
Once decomposition has begun, thorough testing is essential to ensure the microservices work together correctly. **Contract testing** is useful here, allowing services to be tested against their expected API contracts.

#### Testing Strategies:
- **Unit Testing**: For individual microservices.
- **Integration Testing**: Ensures that multiple services work together as intended.
- **Contract Testing**: Validates that service APIs conform to their agreed contract.

### 10. Continuously Deploy and Monitor
Microservices should be designed for **Continuous Integration/Continuous Deployment (CI/CD)**. This enables frequent, reliable releases with less risk of system-wide failure. Implement monitoring tools to track the health and performance of each microservice.

#### Monitoring Best Practices:
- **Centralized Logging**: Tools like ELK Stack (Elasticsearch, Logstash, Kibana) for aggregating logs from different services.
- **Distributed Tracing**: Tools like Jaeger or Zipkin to trace requests across multiple services.
- **Health Checks**: Regular health checks for individual services to ensure they are functioning correctly.

## Conclusion

Decomposing a monolithic application into microservices by domains and subdomains is an effective way to align your architecture with your business structure. By focusing on **core domains**, **subdomains**, and **bounded contexts**, you can incrementally break down a monolith into smaller, manageable, and scalable services. This approach enables faster development cycles, independent deployments, and better scalability, ultimately improving the flexibility and resilience of your system.
