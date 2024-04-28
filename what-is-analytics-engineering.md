# What is Analytics Engineering

Analytics engineering is an emerging discipline that combines principles and practices from software engineering, data engineering, and data analytics. The goal of analytics engineering is to increase the reliability, efficiency, and scalability of data analytics by applying software engineering best practices to the data analytics process.

Some key aspects of analytics engineering include:


## Data Modeling
Analytics Engineering is responsible for [Conceptual Modeling](what-is-the-difference-between-logical-modelling-and-conceptual-modelling-and-physical-modelling.md#conceptual-modeling) to [Logical Modeling](what-is-the-difference-between-logical-modelling-and-conceptual-modelling-and-physical-modelling.md#logical-modeling) to [Physical Modeling](what-is-the-difference-between-logical-modelling-and-conceptual-modelling-and-physical-modelling.md#physical-modeling). Designing and implementing data models that support efficient data storage, retrieval, and analysis.

<pre>
╔════════════════════════════════════════════════════════════════╗
║                 <a href="https://analyticsengineering.net/mailman/listinfo/wranglers"><b>Analytics Engineering</b></a> <b>Scope</b>                    ║
╠════════════════════════════════════════════════════════════════╣  
║ Understanding of                             Understanding of  ║
║ Business        <──────────────────────────> Data Modeling and ║
║ Processes                                    Databases         ║
╠════════════════════════════════════════════════════════════════╣
║ <a href="what-is-the-difference-between-logical-modelling-and-conceptual-modelling-and-physical-modelling.md#conceptual-modeling"><b>Conceptual Modeling</b></a>  <b>▶</b>  <a href="what-is-the-difference-between-logical-modelling-and-conceptual-modelling-and-physical-modelling.md#logical-modeling"><b>Logical Modeling</b></a>  <b>▶</b>  <a href="what-is-the-difference-between-logical-modelling-and-conceptual-modelling-and-physical-modelling.md#physical-modeling"><b>Physical Modeling</b></a> ║
╚════════════════════════════════════════════════════════════════╝
</pre>

## Data Pipelines
Developing robust and scalable data pipelines to transform Raw Data from various sources into Modeled Data to create a unified data platform for analysis.

## Data Contracts
While Analytics Engineering is not responsible for defining the Data Contracts, it is responsible for enforcing the Data Contracts on the Transformed and Modeled data.

<pre>
                    ┌──Data─Contract─────┐                        
                    │                    │                        
                    │ Data Constraints   │                        
                    │ Data Quality       │                        
┌──────────┐        │ Data Definitions   │          ┌─────────────────────┐
│          │Define  │ Data Encoding      │ Implement│                     │
│ Business ├───────►│ Data Structure     │◄─────────┤<a href="https://analyticsengineering.net/mailman/listinfo/wranglers"><b>Analytics Engineering</b></a>│
│          │Verify  │ Data Types         │ Enforce  │                     │
│          ├───────►│ Data Format        │◄─────────┤                     │
└──────────┘        └────────────────────┘          └─────────────────────┘
</pre>

### Data Quality 
Implementing processes and tools to monitor and ensure the quality, consistency, and integrity of data throughout its lifecycle. Applying software testing methodologies and monitoring tools to data pipelines and analytics processes to ensure reliability and catch issues early.

## Productionization
Packaging and deploying data analytics solutions as reusable, scalable, and maintainable products or services.
   
## Collaboration
Facilitating collaboration between data engineers, data scientists, and other stakeholders to streamline the data analytics workflow.

The goal of analytics engineering is to bridge the gap between ad-hoc data analysis and production-ready data analytics systems, enabling organizations to make data-driven decisions more efficiently and at scale.
