# 🏗️ Database Architecture, Tiers & User Management

> How database systems are organized, how applications communicate with databases, and who is responsible for using, designing, and managing them.

---

# Part 1 — 🧱 Database Architecture

## 1. What Is Database Architecture?

**Database architecture** refers to the overall organization of a database system, including its components, how they communicate, how data is stored, and how database operations are performed.

Architecture influences:

- **Performance:** How efficiently data can be accessed and processed.
- **Scalability:** How well the system handles increasing workloads.
- **Reliability:** How well the system continues operating when components fail.
- **Security:** How access to data and system operations is controlled.
- **Maintainability:** How easily the system can be updated and managed.

The appropriate architecture depends on the system's size, workload, number of users, network requirements, budget, and reliability needs.

## 2. 🧭 Four Database Architecture Models

Database systems can be organized in different ways depending on where processing takes place and how data is managed.

The four models covered in this chapter are:

1. Centralized database architecture.
2. Client-server database architecture.
3. Parallel database architecture.
4. Distributed database architecture.

These models describe different aspects of system organization. They are not necessarily mutually exclusive: for example, a distributed database system may use parallel processing.

---

## 3. 🖥️ Centralized Database Architecture

### Definition

A **centralized database architecture** manages the database through a central system or server. Data and database management are concentrated at one main location, although users may connect from different locations.

### How It Works

1. Data is stored in the central database.
2. Users or applications send requests to the central system.
3. The central DBMS processes those requests.
4. Results are returned to the requesting users or applications.

### Example

A small company maintains one central database for its HR, sales, and purchasing departments. Employees in different departments access the information they are authorized to use.

### Advantages

- Centralized administration and maintenance.
- Easier enforcement of consistent data rules.
- Reduced duplication when departments share one authoritative data source.
- Simpler backup and access management in relatively small systems.

### Disadvantages

- The central server can become a performance bottleneck.
- If the central system fails and no suitable redundancy exists, database services may become unavailable.
- Expanding capacity can require upgrading the central system.
- Remote users depend on network connectivity.

### Common Uses

- Small business databases.
- Departmental information systems.
- Small administrative systems.
- Applications where centralized control is more important than geographically distributed processing.

💡 **Remember:** Centralized architecture means the database is managed around a central point. Remote users may still access it over a network.

---

## 4. 🔌 Client-Server Database Architecture

### Definition

**Client-server architecture** separates the client applications from the database server.

The client handles user interaction and may perform some application processing. The database server manages database operations and responds to client requests.

### How It Works

1. A user interacts with a client application.
2. The client sends a request to the database server.
3. The server processes the request.
4. The server returns the required results to the client.

### Example

A library installs management software on staff computers. Each computer connects to a shared database server containing book, member, and loan records.

### Advantages

- Multiple clients can access a shared database.
- Data can be centrally managed.
- Processing and storage responsibilities are separated.
- The server can be upgraded independently of individual client devices.

### Disadvantages

- Clients depend on network connectivity.
- Direct database connections require careful security configuration.
- A heavily loaded server can become a bottleneck.
- Administration becomes more complex as the number of clients grows.

### Common Uses

- Library management systems.
- Internal business applications.
- School administration software.
- Client applications connected to shared database servers.

💡 **Remember:** In a client-server database system, clients communicate with a database server over a network.

---

## 5. ⚡ Parallel Database Architecture

### Definition

A **parallel database architecture** uses multiple processors or processing nodes to perform database work simultaneously.

Instead of completing every operation sequentially on a single processor, the system divides suitable tasks so that several processors can work at the same time.

### How It Works

A large task may be divided into smaller subtasks. Multiple processors execute those subtasks, and their results are combined.

Parallelism can be used for:

- Query processing.
- Data loading.
- Large-scale data analysis.
- Data-intensive calculations.

### Common Configurations

| Configuration | Basic Idea |
|---|---|
| Shared-memory | Multiple processors share main memory. |
| Shared-disk | Processing nodes have separate memory but access shared storage. |
| Shared-nothing | Each node has its own memory and storage, and data or work is distributed across nodes. |
| Hierarchical / hybrid | Combines multiple organization models. |

### Example

A data warehouse processes millions of sales records. Multiple processors analyze separate portions of the workload simultaneously, reducing the time required for suitable operations.

### Advantages

- Can improve performance through concurrent processing.
- Can handle large workloads.
- Can increase processing capacity by adding resources.
- Supports large-scale analytics and data warehousing.

### Disadvantages

- Requires coordination between processors or nodes.
- Work distribution and result combination introduce complexity.
- Performance gains depend on the workload and the amount of parallelizable work.
- Specialized infrastructure can increase cost.

### Common Uses

- Data warehouses.
- Business intelligence.
- Scientific computing.
- Large-scale analytics.
- High-performance computing.

⚠️ **Important:** Parallel processing does not automatically guarantee fault tolerance or high availability. These depend on the design and failure-handling mechanisms.

---

## 6. 🌍 Distributed Database Architecture

### Definition

A **distributed database architecture** stores or manages data across multiple interconnected computers or locations while providing coordinated access to that data.

The system may distribute data geographically, divide it among nodes, maintain copies at multiple sites, or combine these approaches.

### How It Works

A distributed database may:

1. Receive a request from a user or application.
2. Determine which nodes contain the required data.
3. Send relevant operations to those nodes.
4. Process the operations locally or remotely.
5. Coordinate and combine results before returning a response.

The exact process depends on the distributed DBMS.

### Important Techniques

**Data partitioning:** Divides a dataset into portions distributed across different nodes.

**Data fragmentation:** Divides a database relation or dataset into smaller logical pieces. These pieces may be placed at different sites.

**Replication:** Maintains copies of data on multiple nodes.

**Location transparency:** Allows users or applications to access data without needing to manage its physical location directly, to the extent supported by the system.

### Types of Distributed Systems

**Homogeneous distributed database**

The participating sites use the same DBMS software or a compatible common database environment.

**Heterogeneous distributed database**

The participating sites may use different DBMS products, data models, or technologies. Integration requires mechanisms to handle differences in formats, interfaces, and behavior.

### Example

An international organization operates across several countries. Its database services are distributed across multiple locations to support regional operations and users.

### Advantages

- Can support geographically distributed users.
- Can increase capacity by distributing workloads and data.
- Replication can improve availability and access speed when designed appropriately.
- Can reduce dependence on one physical site.

### Disadvantages

- Coordination between sites is complex.
- Network latency can affect performance.
- Replicated data may become inconsistent if updates are not coordinated correctly.
- Security, monitoring, backup, and recovery require careful planning.
- Network failures can disrupt communication between nodes.

### Common Uses

- Global business systems.
- Cloud database platforms.
- Geographically distributed applications.
- Large internet services.
- Systems requiring data access across multiple locations.

💡 **Remember:** Distributed architecture focuses on managing data across multiple nodes or sites. Parallel architecture focuses on using multiple processors or nodes to perform work simultaneously. A system can use both.

---

## 7. ⚖️ Comparing the Four Architecture Models

| Feature | Centralized | Client-Server | Parallel | Distributed |
|---|---|---|---|---|
| Main focus | Central management | Separation of clients and server | Simultaneous processing | Data and services across sites |
| Processing | Concentrated around a central system | Shared between clients and server | Multiple processors work together | Distributed across nodes as designed |
| Scalability | Can be limited by central capacity | Can support multiple clients | Can increase processing capacity | Can scale across nodes and sites |
| Main challenge | Central bottlenecks and failure risk | Network and server management | Coordination and workload distribution | Network coordination and consistency |
| Example | Small company's central database | Library software and database server | Large analytical workload | Global multi-site database |

There is no universal ranking in which one architecture is always the fastest, safest, or most reliable. Actual performance and reliability depend on workload, implementation, redundancy, configuration, and operational practices.

---

# Part 2 — 🪜 Tier-Based Application Architecture

## 8. What Is a Tier?

A **tier** is a logical or physical division of an application's responsibilities.

In database applications, the main responsibilities are commonly divided into:

- **Presentation tier:** Displays information and accepts user input.
- **Application tier:** Processes requests and applies business rules.
- **Database tier:** Stores, retrieves, and manages data.

The number of tiers indicates how these responsibilities are separated, not necessarily how many physical computers are used.

---

## 9. 🖥️ 1-Tier Architecture

### Definition

In a **1-tier architecture**, the user interface, application logic, and database functionality operate together in a single local environment.

The user works directly with a local or embedded database system.

### Basic Structure

`User Interface + Application Logic + Database`

### Workflow

1. The user performs an operation locally.
2. The application or database processes it on the same machine.
3. The result is displayed to the user.

### Example

A student uses a local database application on a personal computer to practice database concepts.

### Advantages

- Simple to set up.
- Easy to use for local experiments and learning.
- Little or no network communication is required.
- Suitable for small standalone applications.

### Disadvantages

- Sharing data among multiple users is less straightforward.
- Centralized management can be difficult when many separate copies exist.
- The system may not meet the security, concurrency, and availability requirements of a larger application.

### Common Uses

- Learning and experimentation.
- Personal database applications.
- Local prototypes.
- Small standalone tools.

⚠️ **Clarification:** One-tier architecture is not inherently unsuitable for production. It can be appropriate for certain standalone applications. The important question is whether it meets the application's requirements.

---

## 10. 🔌 2-Tier Architecture

### Definition

In a **2-tier architecture**, a client application communicates directly with a database server.

The presentation and much of the application logic reside on the client, while the database resides on the server.

### Basic Structure

`Client Application ↔ Database Server`

### Workflow

1. The user interacts with the client application.
2. The client sends a database request directly to the server.
3. The server processes the request.
4. The server returns the result to the client.

### Example

A school's administrative desktop application connects directly to a shared database server containing student and course records.

### Advantages

- Straightforward client-server design.
- Multiple clients can share a central database.
- Data management is centralized.
- Can be effective for controlled internal applications.

### Disadvantages

- Database connectivity and credentials must be managed securely on clients.
- Business logic may be duplicated across client applications.
- Many direct connections can increase the database server's workload.
- Clients depend on network connectivity.

### Common Uses

- Internal desktop applications.
- Small and medium-sized client-server systems.
- Library or school management applications.

---

## 11. 🌐 3-Tier Architecture

### Definition

A **3-tier architecture** separates the application into three layers: presentation, application logic, and database management.

An application server sits between the client and the database server.

### Basic Structure

`Presentation Tier ↔ Application Tier ↔ Database Tier`

### The Three Tiers

**1. Presentation Tier — User Interface**

This is the interface through which users interact with the application.

Examples include a web browser, a mobile application, or a desktop interface.

Responsibilities:

- Display information.
- Accept user input.
- Send requests to the application tier.
- Present the returned results.

**2. Application Tier — Business Logic**

This layer processes application requests and coordinates database access.

Responsibilities may include:

- Authentication and authorization checks.
- Input validation.
- Business rules and calculations.
- Request coordination.
- Communicating with the database.
- Formatting responses.

**3. Database Tier — Data Management**

This layer stores and manages the application's data.

Responsibilities include:

- Storing records.
- Processing database operations.
- Enforcing database constraints.
- Managing transactions and data integrity.
- Returning requested data to authorized application components.

### Workflow: University Student Portal

1. A student opens the portal in a browser.
2. The browser sends a request to the application server.
3. The application server checks the request and applies relevant rules.
4. It communicates with the database to retrieve the student's academic information.
5. The database returns the relevant data.
6. The application server prepares the response.
7. The browser displays the information.

### Advantages

- Separates user interaction, business logic, and data management.
- Helps keep database credentials and direct database access away from end-user devices.
- Makes it easier to maintain application logic centrally.
- Can support independent scaling of application and database resources.
- Supports consistent validation and authorization when implemented correctly.

### Disadvantages

- Requires additional components and configuration.
- Can increase deployment and maintenance complexity.
- The application server can become a bottleneck if not designed to handle the workload.
- A failure in a critical tier can disrupt the application unless suitable redundancy exists.

### Common Uses

- Online banking.
- E-commerce websites.
- University portals.
- Enterprise web applications.
- Applications with substantial security or concurrency requirements.

💡 **Remember:** In a three-tier application, end-user devices should normally communicate with the application tier rather than connect directly to the database server.

---

## 12. ⚖️ Comparing 1-Tier, 2-Tier, and 3-Tier Architectures

| Feature | 1-Tier | 2-Tier | 3-Tier |
|---|---|---|---|
| Main structure | Local, combined environment | Client and database server | Client, application server, database server |
| Database access | Local or embedded | Direct from client | Through application tier |
| Business logic | Local application | Mostly client-side, depending on design | Central application tier |
| Complexity | Usually lowest | Moderate | Usually highest |
| Centralized business rules | Limited | Possible, but often distributed across clients | Easier to centralize |
| Typical use | Standalone tools | Internal desktop systems | Web and enterprise systems |

### How to Choose

Choose **1-tier** when a simple local environment meets the requirements.

Choose **2-tier** when clients need direct access to a shared database and the application can safely manage that arrangement.

Choose **3-tier** when separating business logic, centralizing request handling, or supporting broader scaling and security requirements is valuable.

---

# Part 3 — 👥 Database User Management and Roles

## 13. Who Uses a Database System?

A database ecosystem includes people with different responsibilities and levels of technical expertise.

Some users interact with ready-made applications, some write software, some design database structures, and others manage or analyze the underlying data.

These categories describe roles, not necessarily separate people. One person may perform multiple roles in a small organization.

---

## 14. 👤 Naive Users / Parametric End Users

### Definition

**Naive users**, also called **parametric end users**, interact with databases through predefined application interfaces rather than composing database operations themselves.

They generally need little knowledge of the DBMS.

### Examples

- Bank tellers processing routine transactions.
- Railway reservation clerks.
- Office staff entering records.
- Employees using a standard administrative form.

### Responsibilities

- Enter information through predefined forms.
- Retrieve information through established application functions.
- Perform routine operations according to their responsibilities.

**Key idea:** They use existing database applications rather than designing or administering the database.

---

## 15. 💻 Application Programmers

### Definition

**Application programmers** develop software that interacts with a database.

They create applications, user interfaces, and the logic needed to retrieve, process, and update data.

### Responsibilities

- Develop application features.
- Implement database connectivity.
- Integrate database operations into software.
- Validate inputs and handle errors.
- Develop interfaces such as forms and reports.
- Apply appropriate application-level access controls.

### Examples

A Java developer creates a student registration application that communicates with a database backend.

Application programmers need relevant programming and database knowledge. Their database permissions should be limited to the operations required by their applications.

---

## 16. 📊 Sophisticated Users

### Definition

**Sophisticated users** understand database systems well enough to interact with them directly using query tools, analytical tools, or other specialized interfaces.

They may not need a separate custom application for every task.

### Examples

- Business analysts.
- Engineers.
- Researchers.
- Data analysts.
- System analysts who directly investigate database information.

### Responsibilities

- Retrieve and analyze relevant data.
- Construct queries using supported tools.
- Investigate trends or operational issues.
- Produce reports and support decision-making.

**Key idea:** Sophisticated users interact more directly with database capabilities than ordinary end users, but they are not necessarily database administrators.

---

## 17. 🧪 Specialized Users

### Definition

**Specialized users** develop or use database applications designed for specialized data or tasks that go beyond routine business processing.

They may work with complex data models, domain-specific algorithms, or specialized application environments.

### Examples

- Computer-aided design (CAD) systems.
- Knowledge-based and expert systems.
- Scientific or environmental modeling.
- Applications involving complex graphics, audio, or other specialized data.

### Responsibilities

Their work depends on the application but may involve developing specialized data structures, algorithms, or database-based systems for a particular domain.

**Key idea:** Specialized users focus on non-routine, domain-specific database applications.

---

## 18. 🕒 Casual Users

### Definition

**Casual users** access a database occasionally and use it as needed rather than performing the same predefined operations continuously.

They may use menus, reports, forms, or query tools.

### Examples

- A manager checking a monthly sales report.
- An executive reviewing performance information.
- A supervisor retrieving records for a particular decision.

### Responsibilities

- Retrieve information when needed.
- Review reports.
- Perform occasional permitted operations.

### Casual vs. Naive Users

| Casual Users | Naive / Parametric Users |
|---|---|
| Access the database occasionally | Perform routine, repeated operations |
| May use different reports or queries | Usually follow predefined workflows |
| Examples: managers reviewing reports | Examples: clerks processing standard records |

A person can be a casual user in one system and a sophisticated user in another.

---

## 19. 🛡️ Database Administrator (DBA)

### Definition

A **Database Administrator (DBA)** is responsible for administering and maintaining the database environment.

The DBA helps ensure that the database remains secure, available, efficient, and properly managed.

### Responsibilities

- Manage database accounts and privileges.
- Configure authorization and access controls.
- Monitor database performance and resource usage.
- Plan and verify backups and recovery procedures.
- Maintain database software and configuration.
- Monitor storage capacity and system health.
- Support availability, security, and operational reliability.

### Example

A DBA creates appropriate database accounts, limits permissions, monitors resource usage, and verifies that backup and recovery procedures work.

**Key idea:** The DBA manages the database environment, its operational health, and access privileges.

⚠️ A DBA should not automatically grant every user unrestricted access. Permissions should follow the principle of least privilege: each account receives only the access it needs.

---

## 20. 🧭 System Analysts

### Definition

A **system analyst** studies user and organizational requirements and determines how a proposed information system should satisfy them.

### Responsibilities

- Gather and analyze user requirements.
- Identify functional and non-functional requirements.
- Assess technical and economic feasibility.
- Analyze existing workflows.
- Help define system behavior and specifications.
- Coordinate between stakeholders and technical teams.

### Example

A system analyst interviews university staff to determine how course registration, student records, and grade reporting should work.

**Key idea:** System analysts help determine what the system must do and whether the proposed solution is feasible.

---

## 21. 🧩 Database Designers

### Definition

**Database designers** determine how information should be structured and related within a database.

They translate data requirements into an appropriate database design.

### Responsibilities

- Identify entities and their attributes.
- Define relationships between data structures.
- Select suitable keys.
- Define integrity constraints.
- Design tables, views, and indexes where appropriate.
- Consider redundancy, consistency, and data integrity.
- Ensure the design supports the requirements of different user groups.

### Example

A database designer determines how Students, Courses, and Enrollments should be represented and related in a university database.

**Key idea:** Database designers decide how data should be organized; DBAs focus on operating and administering the database environment. Their responsibilities can overlap depending on the organization.

---

## 22. 🤖 Data Scientists

### Definition

A **data scientist** uses statistical methods, computational techniques, and analytical models to extract insights from data.

Their work may involve structured data, unstructured data, or both.

### Responsibilities

- Explore and prepare datasets.
- Apply statistical analysis.
- Develop predictive or classification models.
- Use machine learning when appropriate.
- Interpret findings.
- Communicate insights that support decisions.

### Examples of Tools

Python, R, and machine-learning libraries may be used for analysis and modeling.

### Example

A university data scientist analyzes historical enrollment patterns to estimate future course demand.

**Key idea:** Data scientists focus on extracting knowledge and predictive insights from data, rather than primarily administering the database.

---

## 23. ⚖️ Comparing Database User Roles

| Role | Primary Responsibility | Typical Interaction |
|---|---|---|
| Naive / parametric user | Routine data operations | Predefined forms and interfaces |
| Application programmer | Build database-connected software | Code, APIs, database interfaces |
| Sophisticated user | Direct data retrieval and analysis | Query and analytical tools |
| Specialized user | Domain-specific database applications | Specialized software and models |
| Casual user | Occasional information access | Reports, forms, query tools |
| DBA | Administration, permissions, performance, recovery | Administrative tools |
| System analyst | Requirements and feasibility | Interviews, analysis, specifications |
| Database designer | Logical data organization and constraints | Data models and schema design |
| Data scientist | Statistical analysis and predictive insights | Analytical tools and modeling |

### Common Role Confusions

- **DBA vs. database designer:** The designer focuses on data structure; the DBA focuses on administration and operation.
- **System analyst vs. programmer:** The analyst investigates requirements; the programmer implements software. They collaborate closely.
- **Sophisticated user vs. data scientist:** Sophisticated users may query and analyze data; data scientists typically apply deeper statistical or computational modeling when their work requires it.
- **Casual vs. naive user:** Casual users access information occasionally; naive users often perform predefined routine tasks.

---

# Part 4 — 🔄 Workflows and Real-World Applications

## 24. Request Flow in Different Tier Architectures

### 1-Tier Request Flow

`User → Local Application / Database → Result`

The user performs an operation within the local environment. Processing occurs locally without requiring a remote database server.

### 2-Tier Request Flow

`Client Application → Database Server → Client Application`

The client sends a request directly to the database server. The server processes the request and returns the result to the client.

### 3-Tier Request Flow

`Client → Application Server → Database Server → Application Server → Client`

The application server receives the client request, applies the relevant rules, accesses the database, and returns an appropriate response.

### Why the Difference Matters

Each architecture places responsibilities in different locations. These decisions influence security, deployment, maintenance, network communication, and scaling.

---

## 25. 🌍 Distributed Query Processing

A distributed database may store the information required for a task across multiple sites.

A distributed query may therefore require the system to:

1. Determine which data and sites are relevant.
2. Break the work into suitable subtasks.
3. Execute those subtasks at the relevant nodes.
4. Coordinate operations and handle communication.
5. Combine the results.
6. Return the final response.

The system may use partitioning, fragmentation, replication, or a combination of these techniques.

**Example:** A company wants a report combining sales information from several regional offices. A distributed system may retrieve the relevant regional data and combine the results into one report.

The exact strategy depends on where the data resides, how it is replicated, and the DBMS's query-processing capabilities.

---

## 26. 🧪 Real-World Architecture Scenarios

### Scenario A — Small Company Database

A small business maintains one central database for its staff, inventory, and sales.

**Possible choice:** Centralized architecture.

**Reason:** Central administration may be simple and appropriate for the workload. Backup, access control, and server availability still need attention.

### Scenario B — Library Management System

Staff members use desktop software connected directly to a shared database server.

**Possible choice:** Two-tier client-server application.

**Reason:** Client applications can communicate with a common database, while data remains centrally managed.

### Scenario C — Online Banking

Customers use a browser or mobile application to access banking services.

**Possible choice:** Three-tier application architecture.

**Reason:** The application tier can validate requests, apply banking rules, coordinate transactions, and mediate access to the database.

### Scenario D — University Student Portal

Students access registration and academic records through a web interface.

**Possible choice:** Three-tier architecture.

**Reason:** Presentation, application logic, and data management can be maintained separately, with access controls enforced across the system.

### Scenario E — Large-Scale Data Warehouse

An organization processes a very large amount of historical sales data.

**Possible choice:** A parallel database architecture, potentially combined with distributed storage.

**Reason:** Large analytical workloads may benefit from dividing processing across multiple processors or nodes.

### Scenario F — International Organization

An organization has offices in several countries and needs database services across different regions.

**Possible choice:** Distributed database architecture.

**Reason:** Data and services can be placed across multiple locations to support regional access and operational needs.

These are common design choices, not mandatory rules. A real system may combine multiple architectures.

---

## 27. 🔐 Security and Reliability Considerations

Architecture alone does not guarantee security or reliability.

A well-designed database application should consider:

- **Authentication:** Verifying who is making a request.
- **Authorization:** Determining which operations the user may perform.
- **Least privilege:** Giving each user or application only the permissions required.
- **Input validation:** Rejecting invalid or unexpected inputs.
- **Network security:** Protecting communication between components.
- **Backups and recovery:** Preparing for data loss or system failure.
- **Redundancy:** Providing backup components or replicas where required.
- **Monitoring:** Detecting performance problems and operational failures.

### Important Distinctions

- A centralized system can be highly reliable if it has effective redundancy and recovery mechanisms.
- A distributed system can still suffer outages or data inconsistency.
- A three-tier application can improve separation of responsibilities, but it must be configured securely.
- A database server should not be exposed directly to end users merely because the application uses a web interface.

---

## 28. 📝 Quick Revision Sheet

| Concept | Main Idea |
|---|---|
| Database architecture | Overall organization of database components and processing |
| Centralized architecture | Database management concentrated around a central system |
| Client-server architecture | Clients communicate with a database server |
| Parallel architecture | Multiple processors or nodes work on tasks simultaneously |
| Distributed architecture | Data or database services are spread across multiple sites or nodes |
| 1-tier architecture | User interface, application logic, and database operate together locally |
| 2-tier architecture | Client application communicates directly with the database server |
| 3-tier architecture | Application server separates the client from the database |
| Naive / parametric user | Performs routine operations through predefined interfaces |
| Application programmer | Builds applications that use a database |
| Sophisticated user | Interacts directly with database or analytical tools |
| Specialized user | Develops or uses domain-specific database applications |
| Casual user | Accesses information occasionally |
| DBA | Administers permissions, performance, maintenance, and recovery |
| System analyst | Analyzes requirements and system feasibility |
| Database designer | Designs data structures and relationships |
| Data scientist | Extracts insights using statistics and computational methods |

---

## ✅ Self-Check

Try answering these without looking at the notes.

1. What is database architecture, and why does it matter?
2. How does centralized architecture differ from distributed architecture?
3. What is the main purpose of parallel database processing?
4. Explain the difference between parallel and distributed architectures.
5. What is a tier in application architecture?
6. Describe the three tiers of a three-tier application.
7. Compare one-tier, two-tier, and three-tier architectures.
8. Why might an organization choose a three-tier application?
9. What is the difference between a DBA and a database designer?
10. How does a system analyst contribute to database development?
11. Differentiate between casual and naive users.
12. What distinguishes sophisticated users from specialized users?
13. What is the purpose of replication in a distributed system?
14. Why does distributed data management require careful coordination?
15. Does a three-tier architecture automatically guarantee security? Explain.
16. Which architecture might suit a large analytical workload, and why?

---

## 🎯 Chapter Summary

Database architecture defines how database components, processing, and data storage are organized. Centralized systems concentrate management, client-server systems separate clients from servers, parallel systems use simultaneous processing, and distributed systems manage data across multiple nodes or sites.

Tier-based architectures separate application responsibilities differently: one-tier combines them locally, two-tier connects clients directly to a database server, and three-tier places an application layer between the client and database.

Database systems also depend on different user roles. Application programmers develop database-connected software, database designers structure data, DBAs administer the database environment, system analysts study requirements, and data scientists extract insights.
