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
A high-level description of information needs that typically includes only the main concepts and the main relationships among them. Offers a clear and accessible representation using common and shared business terminology, enabling effective communication among stakeholders. Conceptual Model define what business information and process currently exist. 

<pre>
Concept Model example:

╔══════════╗                           ╔═══════╗
║ CUSTOMER ║ ──── Places an order ───> ║ ORDER ║
╚══════════╝                           ╚═══════╝
</pre>
- Conceptual model or _ontology_ defines the business objects and their relationship to each other.
- Focuses on capturing the high-level concepts, entities, relationships and processes as it relates to business.
- Represents the real-world entities, attributes, and relationships relevant to the business, independent of any specific implementation details.
- Uses concepts and notations that are closer to the business language and terminologies, such as Entity-Relationship (ER) diagrams or UML class diagrams.
- Provides a shared understanding of the domain among stakeholders, developers, and end-users.
- Serves as a foundation for the logical and physical design phases.

> Note: Conceptual Models are always business specific. There is nothing like a "reference Conceptual Model".

> Note: Application of conceptual modeling plus attribute binding to standard terminologies ensures that context and meaning are retained to guarantee a high degree of semantic interoperability within various business systems, significantly improving data quality. 

### Sample Conceptual Models

#### Sales Opportunity and Sales Order Conceptual Model

```
                                                         ┌─────┐     
                                                         │Quote│     
                                                         └──┬──┘     
                                                            │        
                                                        belongs to   
                                                            │        
                                                            ▼        
┌───────┐                      ┌───────┐               ┌───────────┐
│Contact├───associated─with───►│Account│◄──belongs─to──┤Opportunity│
└───┬───┘                      └───────┘               └────┬──────┘
    │                               ▲                       │        
    │                               │                       │        
potential to become              belongs to              turns to     
    │                               │                       │        
    ▼                               │                       ▼        
 ┌──────┐                       ┌───┴────┐               ┌─────┐     
 │ Lead ├─potential─to─become──►│Customer│               │Order│     
 └──────┘                       └────────┘               └─────┘     
```

#### Classic Library Borrowing Example

```
                      ┌─────requests────────┐        
                      │                     │        
                      │                     │        
                      │                     │        
                      ▼                     │        
┌─────────┐        ┌─────┐           ┌──────┴───────┐
│librarian├─lends─►│items│◄─borrows──┤library patron│
└─────────┘        └─────┘           └──────────────┘
                      ▲                              
                      │                              
               ┌──────┴───────┐                      
               │              │                      
           type of       type of                      
               │              │
          ┌────┴──────┐   ┌───┴────┐
          │ microfilm │   │ books  │                 
          └───────────┘   └────────┘

In this example microfil and books are
subtype (subclass) of items.       
                                                    
```


## Logical Modeling

A data model of a specific domain expressed in terms of data structures such as relational tables and columns geared towards a particular usecase or purpose (e.g. building a Customer Profile).

```
Logical Model example:
                         ╔═══════════════════╗
╔═══════════════════╗    ║ ORDER             ║
║ CUSTOMER          ║    ╠═══════════════════╣    ╔══════════════════╗
╠═══════════════════╣    ║ ORDER_KEY      PK ║    ║ PRODUCT          ║
║ CUSTOMER_KEY   PK ║1──M║ CUSTOMER_KEY   FK ║    ╠══════════════════╣
╚═══════════════════╝    ║ PRODUCT_KEY    FK ║1──1║ PRODUCT_KEY   PK ║               
                         ╚═══════════════════╝    ╚══════════════════╝

1. There is 1-to-Many relationship between CUSTOMER and ORDER
   i.e. a Customer can place several Orders, but an Order can
   only be tied to a single Customer
2. There is 1-to-1 relationship between ORDER and PRODUCT
   i.e. a Single order can only contain one Product

```
- Focuses on representing the structure and constraints of data required for a specific implementation, such as a database or software system.
- Defines the logical data structures, relationships, and integrity constraints based on the conceptual model. Relationships are elucidated in greater detail, incorporating specifics such as primary keys, foreign keys, and the hierarchical dependencies inherent in parent-child entity types. See afforementioned example model.
- Incorporates implementation-specific details and design decisions, such as data types, primary keys, foreign keys, grain, and normalization rules.
- Uses more technical terminology and concepts related to the target implementation platform or technology.
- Commonly uses techniques like relational data models, object-oriented models, or dimensional models (for data warehouses).
- Serves as a blueprint for the physical implementation of databases, software applications, or other systems.

## Physical Modeling

The model that details the database artefacts required to create relationships between tables, such as indexes, constraints, links and partitions.

```
Physical Model example (Data Vault):
                                                                                    
       hub_customer          hub_order           hub_product        
       ┌───────────────┐     ┌──────────────┐    ┌──────────────┐
       │hub_customer_hk│     │hub_order_hk  │    │hub_product_hk│
       │order_key      │     │order_key     │    │product_key   │
       │load_date      │     │load_date     │    │load_date     │
       │record_source  │     │record_source │    │record_source ├─────┐
       └───────┬───┬───┘     └───────────┬──┘    └───┬──────────┘     │
               │   │                     │           │                │
               │   │                     ▼           │                │
  sat_customer ▼   │    link_order_customer_product  ▼   sat_product  ▼ 
 ┌───────────────┐ │   ┌──────────────────────────────┐  ┌───────────────┐
 │hub_customer_hk│ └──►│link_order_customer_product_hk│  │hub_product_hk │
 │first_name     │     │hub_order_hk                  │  │product_name   │
 │last_name      │     │hub_customer_hk               │  │description    │
 │email          │     │hub_product_hk                │  │cost           │
 │address        │     │load_date                     │  │list_price     │
 │hashdiff       │     │record_source                 │  │hashdiff       │
 │load_date      │     └───────────────────────────┬──┘  │load_date      │
 │record_source  │                                 │     │record_source  │
 └───────────────┘                                 │     └───────────────┘
                                                   │
                       satl_order_customer_product ▼ 
                      ┌───────────────────────────────┐
                      │link_order_customer_product_hk │
                      │order_date                     │
                      │product_quantity               │
                      │{other descriptive attributes} │
                      │hashdiff                       │
                      │load_date                      │
                      │record_source                  │
                      └───────────────────────────────┘
```

- Focuses on the actual implementation details and technical specifications required to create the physical database or system. 
- Represents the physical storage structures, file organizations, indexing mechanisms, and access paths for data. For e.g. in case of a Data Vault, this will involve defining the HUB, LINKs, Satellites.
- Incorporates low-level details specific to the database management system (DBMS) or platform being used, such as table spaces, partitioning schemes, and storage parameters.
- Considers performance optimization techniques, such as indexing strategies, clustering, and denormalization.
- Serves as the final blueprint for creating and deploying the actual database or system implementation.

## Summary

In summary, [conceptual modeling](#conceptual-modeling) captures the high-level domain concepts, [logical modeling](#logical-modeling) defines the logical data structures and constraints based on the conceptual model, and [physical modeling](#physical-modeling) specifies the low-level implementation details and technical configurations for the actual deployment of the database or system.

| Model                              | Degree of Abstraction | Focus                                                | Independent of                |
|------------------------------------|-----------------------|------------------------------------------------------|-------------------------------|
| [Conceptual](#conceptual-modeling) | High                  | Global View of the Business, Business Entities and their relationship                          | Storage and Compute         |
| [Logical](#logical-modeling)       |                       | ER Model                                             |                               |
| [Physical](#physical-modeling)     | Low                   | Data storage and retrieval, and optimization thereof | Neither Storage nor Compute |


|                                 | [Conceptual Model](#conceptual-modeling) | [Logical Model](#logical-modeling) | [Physical Model](#physical-modeling) |
|---------------------------------|------------------|---------------|----------------|
| Entity Names                    | ✅               | ✅            |                |
| Entity Relationships            | ✅               | ✅            |                |
| Referential Integrity           |                  | ✅            |                |
| Business Keys                   |                  | ✅            |                |
| Primary Keys                    |                  | ✅            | ✅             |
| Foreign Keys                    |                  | ✅            | ✅             |
| Descriptive Attributes          |                  |               | ✅             |
| Table Names                     |                  |               | ✅             |
| Naming Convention               |                  |               | ✅             |
| Column Data Types               |                  |               | ✅             |
| Constraints                     |                  |               | ✅             |
| Normalization / Denormalization |                  |               | ✅             |
| Optimization / Query Assist     |                  |               | ✅             |


The progression from conceptual to logical to physical modeling ensures a systematic and structured approach to system design, facilitating communication, maintainability, and the ability to adapt to changing requirements or technologies.
