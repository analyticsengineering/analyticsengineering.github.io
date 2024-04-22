# What is the difference between Logical Modeling and Conceptual Modeling and Physical Modeling?



<pre>
╔════════════════════════════════════════════════════════════════╗
║                 <a href="https://analyticsengineering.net/mailman/listinfo/wranglers"><b>Analytics Engineering</b></a> <b>Scope</b>                    ║
╠════════════════════════════════════════════════════════════════╣  
║ Understanding of                             Understanding of  ║
║ Business        <──────────────────────────> Data Modeling and ║
║ Processes                                    Databases         ║
╠════════════════════════════════════════════════════════════════╣
║ <a href="#conceptual-modeling"><b>Conceptual Modeling</b></a>  <b>▶</b>  <a href="#logical-modeling"><b>Logical Modeling</b></a>  <b>▶</b>  <a href="#physical-modeling"><b>Physical Modeling</b></a> ║
╚════════════════════════════════════════════════════════════════╝
</pre>

## Conceptual Modeling

```
Concept Modeling example:

╔══════════╗                           ╔═══════╗
║ CUSTOMER ║ ──── Places an order ───> ║ ORDER ║
╚══════════╝                           ╚═══════╝
```

- Focuses on capturing the high-level concepts, entities, relationships and processes as it relates to business.
- Represents the real-world entities, attributes, and relationships relevant to the business, independent of any specific implementation details.
- Uses concepts and notations that are closer to the business language and terminologies, such as Entity-Relationship (ER) diagrams or UML class diagrams.
- Provides a shared understanding of the domain among stakeholders, developers, and end-users.
- Serves as a foundation for the logical and physical design phases.

## Logical Modeling

```
Logical Modeling example:
                                  ╔════════════════════════════╗
╔════════════════════════════╗    ║ ORDER                      ║
║ CUSTOMER                   ║    ╠════════════════════════════╣    ╔═══════════════════════════╗
╠════════════════════════════╣    ║ ORDER_KEY      Primary Key ║    ║ PRODUCT                   ║
║ CUSTOMER_KEY   Primary Key ║1──M║ CUSTOMER_KEY   Foreign Key ║    ╠═══════════════════════════╣
╚════════════════════════════╝    ║ PRODUCT_KEY    Foreign Key ║1──1║ PRODUCT_KEY   Primary Key ║               
                                  ╚════════════════════════════╝    ╚═══════════════════════════╝

1. There is 1-to-Many relationship between CUSTOMER and ORDER i.e. a Customer can place several Orders, but an Order can only be tied to a single Customer
2. There is 1-to-1 relationship between ORDER and PRODUCT i.e. a Single order can only contain one Produce

```
- Focuses on representing the structure and constraints of data required for a specific implementation, such as a database or software system.
- Defines the logical data structures, relationships, and integrity constraints based on the conceptual model.
- Incorporates implementation-specific details and design decisions, such as data types, primary keys, foreign keys, grain, and normalization rules.
- Uses more technical terminology and concepts related to the target implementation platform or technology.
- Commonly uses techniques like relational data models, object-oriented models, or dimensional models (for data warehouses).
- Serves as a blueprint for the physical implementation of databases, software applications, or other systems.

## Physical Modeling
- Focuses on the actual implementation details and technical specifications required to create the physical database or system. 
- Represents the physical storage structures, file organizations, indexing mechanisms, and access paths for data. For e.g. in case of a Data Vault, this will involve defining the HUB, LINKs, Satellites.
- Incorporates low-level details specific to the database management system (DBMS) or platform being used, such as table spaces, partitioning schemes, and storage parameters.
- Considers performance optimization techniques, such as indexing strategies, clustering, and denormalization.
- Serves as the final blueprint for creating and deploying the actual database or system implementation.

In summary, conceptual modeling captures the high-level domain concepts, logical modeling defines the logical data structures and constraints based on the conceptual model, and physical modeling specifies the low-level implementation details and technical configurations for the actual deployment of the database or system.

The progression from conceptual to logical to physical modeling ensures a systematic and structured approach to system design, facilitating communication, maintainability, and the ability to adapt to changing requirements or technologies.
