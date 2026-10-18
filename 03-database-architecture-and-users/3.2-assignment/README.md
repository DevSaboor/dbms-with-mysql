# 📝 Assignment — Database Architecture, Tiers & User Management

## 📌 Instructions

- Attempt each question before revealing its answer.
- Use your own wording when writing answers for submission.
- Include examples where requested.
- Focus on accurate concepts and clear explanations.
- No SQL queries or SQL-writing exercises are required for this assignment.

---

## Part A — Database Architecture

### Q1. Define database architecture and explain four factors it influences.

<details>
<summary>🔎 Click to reveal the answer</summary>

Database architecture is the overall organization of a database system, including its components, processing arrangements, communication, and data storage.

It influences performance, scalability, reliability, and security. It also affects how easily the system can be maintained and expanded.

</details>

### Q2. Explain centralized database architecture. State two advantages and two disadvantages.

<details>
<summary>🔎 Click to reveal the answer</summary>

Centralized architecture manages a database through one central system or server.

**Advantages:**
- Centralized management and maintenance.
- Easier enforcement of consistent data rules.

**Disadvantages:**
- The central system may become a performance bottleneck.
- A failure may interrupt database services if suitable redundancy is absent.

</details>

### Q3. What is client-server database architecture? Explain how it works with an example.

<details>
<summary>🔎 Click to reveal the answer</summary>

Client-server architecture separates client applications from a database server. The client sends requests to the server, the server processes them, and the results are returned to the client.

For example, library staff may use desktop software that connects to a shared database server containing book and member records.

</details>

### Q4. Define parallel database architecture and explain its advantages and limitations.

<details>
<summary>🔎 Click to reveal the answer</summary>

Parallel database architecture uses multiple processors or nodes to perform suitable database operations simultaneously.

It can improve performance and support large workloads. However, coordinating processors, distributing work, and combining results introduces complexity. Performance gains also depend on the workload and implementation.

</details>

### Q5. Define distributed database architecture. Explain partitioning, fragmentation, replication, and location transparency.

<details>
<summary>🔎 Click to reveal the answer</summary>

Distributed database architecture manages data across multiple interconnected nodes or sites.

- **Partitioning:** Divides a dataset into portions that can be distributed across nodes.
- **Fragmentation:** Divides a database relation or dataset into smaller logical pieces.
- **Replication:** Maintains copies of data on multiple nodes.
- **Location transparency:** Allows users or applications to access data without needing to manage its physical location directly, to the extent supported by the system.

These techniques help systems distribute storage and processing, but they require careful coordination.

</details>

### Q6. Differentiate between homogeneous and heterogeneous distributed database systems.

<details>
<summary>🔎 Click to reveal the answer</summary>

A homogeneous distributed database system uses the same DBMS software or a compatible common database environment across its participating sites.

A heterogeneous distributed database system may combine different DBMS products, data models, or technologies. Such systems require mechanisms to handle differences in data formats, interfaces, and behavior.

</details>

### Q7. Compare centralized, client-server, parallel, and distributed database architectures.

<details>
<summary>🔎 Click to reveal the answer</summary>

| Architecture | Main Characteristic | Main Challenge |
|---|---|---|
| Centralized | Management concentrated around a central system | Bottlenecks and central failure risk |
| Client-server | Clients communicate with a database server | Network dependency and server workload |
| Parallel | Multiple processors work simultaneously | Coordination and workload distribution |
| Distributed | Data or services spread across multiple sites | Network coordination and data consistency |

Each model serves different requirements, and actual performance and reliability depend on implementation.

</details>

---

## Part B — Tier-Based Architectures

### Q8. What is a tier in application architecture? Name the three common tiers.

<details>
<summary>🔎 Click to reveal the answer</summary>

A tier is a logical or physical division of an application's responsibilities.

The three common tiers are:

1. **Presentation tier:** Displays information and accepts user input.
2. **Application tier:** Processes requests and applies business rules.
3. **Database tier:** Stores and manages data.

</details>

### Q9. Explain one-tier architecture with its advantages, disadvantages, and a suitable example.

<details>
<summary>🔎 Click to reveal the answer</summary>

One-tier architecture combines the user interface, application logic, and database functionality within one local environment.

**Advantages:** Simple setup, easy local access, and minimal network dependency.

**Disadvantages:** Sharing data across many users and centrally managing separate installations can be difficult.

**Example:** A standalone personal database application used on one computer.

</details>

### Q10. Explain two-tier architecture and describe its request flow.

<details>
<summary>🔎 Click to reveal the answer</summary>

Two-tier architecture consists of a client application and a database server.

The user interacts with the client, the client sends a request directly to the database server, the server processes it, and the result returns to the client.

For example, a school's desktop administration software may connect directly to its shared database server.

</details>

### Q11. Describe the three tiers of a three-tier database application and explain the role of each.

<details>
<summary>🔎 Click to reveal the answer</summary>

1. **Presentation tier:** Provides the interface through which users interact with the application.
2. **Application tier:** Processes requests, validates inputs, applies business rules, and coordinates database access.
3. **Database tier:** Stores and manages data, enforces database constraints, and processes database operations.

Separating these responsibilities can improve maintainability and support security controls.

</details>

### Q12. Compare one-tier, two-tier, and three-tier architectures.

<details>
<summary>🔎 Click to reveal the answer</summary>

| Feature | One-Tier | Two-Tier | Three-Tier |
|---|---|---|---|
| Organization | Combined local environment | Client and database server | Client, application server, database server |
| Database access | Local or embedded | Direct from client | Through application tier |
| Complexity | Usually lowest | Moderate | Usually highest |
| Typical use | Standalone tools | Internal desktop systems | Web and enterprise applications |

The appropriate design depends on the application's requirements rather than the number of tiers alone.

</details>

### Q13. A university creates a web portal where students view grades and register for courses. Which tier architecture is suitable, and why?

<details>
<summary>🔎 Click to reveal the answer</summary>

A three-tier architecture is a suitable choice. The presentation tier provides the student portal, the application tier handles authentication and registration rules, and the database tier stores academic records.

This arrangement separates responsibilities and allows database access to be mediated by the application tier.

</details>

---

## Part C — Database Users and Responsibilities

### Q14. Who are naive or parametric end users? Give three examples.

<details>
<summary>🔎 Click to reveal the answer</summary>

Naive or parametric end users perform routine database operations through predefined application interfaces and generally do not need detailed knowledge of the DBMS.

Examples include bank tellers processing routine transactions, railway reservation clerks, and office staff entering records.

</details>

### Q15. Explain the role of application programmers in a database system.

<details>
<summary>🔎 Click to reveal the answer</summary>

Application programmers develop software that interacts with databases. They implement application features, user interfaces, database connectivity, input validation, and the logic needed to retrieve or update information.

For example, a developer may create a student registration application connected to a database backend.

</details>

### Q16. Differentiate between sophisticated users, specialized users, and casual users.

<details>
<summary>🔎 Click to reveal the answer</summary>

- **Sophisticated users:** Use database or analytical tools directly to retrieve and analyze information.
- **Specialized users:** Develop or use domain-specific database applications, such as CAD or scientific modeling systems.
- **Casual users:** Access database information occasionally, often through reports, forms, or query tools.

The categories differ mainly in how users interact with the system and the nature of their tasks.

</details>

### Q17. Explain the responsibilities of a Database Administrator (DBA).

<details>
<summary>🔎 Click to reveal the answer</summary>

A DBA administers and maintains the database environment.

Responsibilities include managing user permissions, monitoring performance and resources, maintaining database software, planning backups, supporting recovery, and helping ensure operational security and availability.

</details>

### Q18. Differentiate between a system analyst and a database designer.

<details>
<summary>🔎 Click to reveal the answer</summary>

A **system analyst** studies user requirements, analyzes workflows, and evaluates the feasibility of a proposed system.

A **database designer** determines how data should be organized, including data structures, relationships, keys, and integrity constraints.

The analyst focuses on understanding system requirements, while the designer focuses on translating data requirements into a suitable database structure.

</details>

### Q19. Explain the role of a data scientist and identify two tasks they may perform.

<details>
<summary>🔎 Click to reveal the answer</summary>

A data scientist uses statistical, computational, and analytical techniques to extract insights from data.

Two possible tasks are analyzing enrollment trends and developing predictive models to estimate future course demand.

</details>

### Q20. Match each responsibility to the most appropriate database role.

<details>
<summary>🔎 Click to reveal the answer</summary>

| Responsibility | Appropriate Role |
|---|---|
| Managing database permissions and recovery | Database Administrator |
| Designing data structures and relationships | Database Designer |
| Developing database-connected applications | Application Programmer |
| Gathering and evaluating system requirements | System Analyst |
| Performing routine data entry through forms | Naive / Parametric User |
| Analyzing data using statistical models | Data Scientist |
| Retrieving information directly using query tools | Sophisticated User |
| Developing domain-specific database applications | Specialized User |

In practice, one person may perform multiple roles, especially in smaller organizations.

</details>

---

## Part D — Application and Analysis

### Q21. A small company stores its departmental data in one centrally managed database. Identify the architecture and explain why it may be suitable.

<details>
<summary>🔎 Click to reveal the answer</summary>

This is a centralized database architecture.

It may be suitable because the company can manage data, access permissions, and maintenance from one central location. However, it should consider server capacity, backup procedures, and the risk of service interruption if the central system fails.

</details>

### Q22. A company uses several processors to analyze a large dataset simultaneously. Identify the architecture and explain its main benefit.

<details>
<summary>🔎 Click to reveal the answer</summary>

This describes parallel database processing. Multiple processors work on suitable parts of the workload at the same time, potentially reducing processing time and increasing analytical capacity.

The benefit depends on how effectively the workload can be divided and coordinated.

</details>

### Q23. An international organization maintains data across several regional sites. What architecture may be appropriate, and what challenges must be considered?

<details>
<summary>🔎 Click to reveal the answer</summary>

A distributed database architecture may be appropriate because it supports data management across multiple sites.

Challenges include network latency, coordination between nodes, data consistency, security, backup, and recovery.

</details>

### Q24. Evaluate the statement: “Three-tier architecture automatically guarantees complete database security.”

<details>
<summary>🔎 Click to reveal the answer</summary>

The statement is incorrect. Three-tier architecture separates the user interface, application logic, and database, helping control how users access data.

However, security still depends on correct authentication, authorization, input validation, secure communication, configuration, and other protective measures.

</details>

### Q25. A manager occasionally opens a report, while an office clerk performs the same predefined data-entry task throughout the day. Identify each user's likely category.

<details>
<summary>🔎 Click to reveal the answer</summary>

The manager is likely a **casual user** because they access the database occasionally to retrieve information.

The office clerk is likely a **naive or parametric end user** because they repeatedly perform predefined operations through an application interface.

</details>

### Q26. Explain why parallel and distributed database architectures should not be treated as identical.

<details>
<summary>🔎 Click to reveal the answer</summary>

Parallel architecture focuses on executing work simultaneously across multiple processors or nodes. Distributed architecture focuses on managing data or database services across multiple interconnected sites or nodes.

A distributed system may use parallel processing, so the two approaches can overlap, but they describe different architectural concerns.

</details>

---

## ✅ Final Checklist

Before considering the assignment complete, confirm that you can:

- [ ] Explain all four database architecture models.
- [ ] Compare one-tier, two-tier, and three-tier applications.
- [ ] Describe the request flow in each tier architecture.
- [ ] Identify the major database user roles.
- [ ] Distinguish a DBA from a database designer and system analyst.
- [ ] Explain the difference between parallel and distributed architectures.
- [ ] Apply architecture concepts to practical scenarios.
- [ ] Explain why architecture alone does not guarantee security or reliability.

**End of assignment.**
