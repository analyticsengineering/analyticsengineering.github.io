# [Analytics Engineering Mailing List](https://analyticsengineering.net/mailman/listinfo/wranglers) Archive

|Archive| 	View by| Subscription |
|-------|----------|------|
|2024:| 	[Thread](/2024/thread.html), [Subject](/2024/subject.html), [Author](/2024/author.html), or [Date](/2024/date.html)| [Subscribe to Analytics Engineering Mailing List](https://analyticsengineering.net/mailman/listinfo/wranglers)|


# What is Analytics Engineering?
Analytics Engineering sits at the intersection of Business, Data Analysis and Data Engineering. It is responsible for bringing modeled, robust, efficient, and integrated data products to life. A practitioner of Analytics Engineering interfaces with the Business and collects Business Requirements and then models the data in the Data Warehouse to reflect the Business. Once the data is modeled in the Data Warehouse they are responsible for bringing the data to Information Mart, which then is consumed by Data Analysts and Business Intelligence team to produce Charts and Dashboard as per business requirements.

## Data Engineers vs. Analytics Engineers

Data Engineers aim to understand how the data is stored in the source systems, and how and what to extract. They build data pipelines to make that happend. Analytics engineers, on the other hand, aim to understand how the data is going to be used (they use it themselves or are able to serve the business directly) and they make sure the data meets a certain standard of quality and regularly revise it. In addition to building well modelled and analyst-friendly Information Mart tables, Analytics Engineers implement a comprehensive set of data quality checks to ensure the accuracy, business relevancy and timeliness of the data.

# Tools
An Analytics Engineer is not responsible for extraction of the data from the source systems. That is usually handled by Data Engineering team. As such, tools that are used by Analytics Engineers are more geared towards Business Requirement collection, Data Modelling and Data Warehousing 

## Modelling

### Conceptual Modelling
This is typically the starting point and requires understanding of Business from the Subject Matter expert in each area. Typically mind mapping tool and other business requirement gathering tools are used for Conceptual Modelling.

### Logical Modelling
Logical Modelling as it relates to Analytics Engineering involves modelling of business processes and entities.

### Physical Modelling
This requires modelling of actual storage structures depending on the Warehousing Modelling methodology being implemented. For e.g. Data vault modeling will require defining the HUB, LINKS and Satellite to reflect the Business.

## Storage
Data is stored in a variety of ways, one of the key deciding factors is in how the data will be used. Data engineers optimize data storage and processing systems to reduce costs. They use data compression, partitioning, and archiving.

### Data warehouses

If the data is structured and online analytical processing is required (but not online transaction processing), then Data warehouse are a main choice. They enable data analysis, mining, and artificial intelligence on a much larger scale than databases can allow, and indeed data often flow from databases into data warehouses. Business analyst, data engineers, and data scientists can access data warehouses using tools such as SQL or business intelligence software.

### Data lakes 
A data lake is a centralized repository for storing, processing, and securing large volumes of data. A data lake can contain structured data from Relational database, semi-structured data, unstructured data, and binary data. A data lake can be created on premises or in a cloud-based environment using the services from Cloud computing public cloud vendors such as Amazon, Microsoft, or Google.

# See also
1. [What is Analytics Engineering?](what-is-analytics-engineering.md)
2. [What does an Analytics Engineer do?](what-does-an-analytics-engineering-do.md)
3. [Are Analytics Engineers in Demand?](are-analytics-engineers-in-demand.md)
4. [What is the difference between logical modeling and conceptual modeling and physical modeling?](what-is-the-difference-between-logical-modelling-and-conceptual-modelling-and-physical-modelling.md)

