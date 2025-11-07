# More Database Concepts

For a business analyst, the world revolves around data. But data doesn't simply exist in a void; it must be stored, organized, protected, and made accessible. Databases are the engines that perform these critical tasks.

To use a common analogy, if data is the new oil, databases are the storage tanks, pipelines, and refineries. They are the essential infrastructure that allows us to turn raw data into the refined fuel - reports, dashboards, and predictive models - that powers modern business decisions.

The specific type of database used by a company fundamentally impacts an analyst's work: it dictates the structure of the data, the speed of our queries, and even the types of questions we can feasibly ask. This chapter explores the different types of databases and the core concepts that every analyst must understand.

---

## 🧭 The Two Primary Roles of a Database: OLTP vs. OLAP

Databases are highly specialized tools. In a business context, they are typically optimized for one of two very different jobs: **running the business** or **analyzing the business**.

### 🔁 Online Transaction Processing (OLTP)

An **Online Transaction Processing (OLTP)** database is designed to run the daily operations of a business. Its primary job is to process a high volume of small, concurrent transactions very quickly.

- **Primary Function:** Fast **writes** and **updates** of single records.
- **Analogy:** A digital filing cabinet. When a customer makes a purchase, the database needs to quickly find their record (`CustomerID = 503`), update their order status, and log the transaction.
- **Examples:** E-commerce checkout systems, bank ATMs, CRMs, and flight reservation systems.
- **Analyst's View:** This is often the "live" or "production" database. Querying it directly for large-scale analysis can be slow and may even interfere with business operations.

### 📊 Online Analytical Processing (OLAP)

An **Online Analytical Processing (OLAP)** database is designed specifically for business intelligence and analysis. Its purpose is to answer complex questions using vast amounts of historical data.

- **Primary Function:** Fast **reads** and **aggregations** (e.g., `SUM`, `AVG`, `COUNT`) across millions or billions of records.
- **Analogy:** A massive pivot table. An analyst doesn't care about a single transaction; they want to know, "What was the total `SUM(Sales)` by `Region` for the last `Quarter`?"
- **Examples:** A **Data Warehouse**, a data mart, or a Business Intelligence (BI) dashboard.
- **Analyst's View:** This is the analyst's playground. These systems are built for the exact type of complex, read-heavy queries we run.

The critical takeaway is that a single database cannot excel at both jobs. This is why companies build **data warehouses**

Data Storage Architecture: Row-Oriented vs. Columnar
The performance difference between OLTP and OLAP systems stems from how they physically store data on a disk.

Imagine a simple Sales table:

| **TransactionID** | **Product** | **Region** | **SaleAmount** |
| ----------------- | ----------- | ---------- | -------------- |
| 1                 | Apple       | North      | 1.00           |
| 2                 | Berry       | South      | 0.50           |
| 3                 | Apple       | West       | 1.25           |

:::{important} The need for data warehouses
The takeaway is that a single database cannot excel at both jobs. This is why companies build **data warehouses** - specialized OLAP systems fed by **ETL (Extract, Transform, Load)** pipelines that move data from OLTP sources to analytical storage.
:::

### 📦 Row-Oriented Storage (Optimized for OLTP)

Traditional databases store this data one row at a time.

```
(1, 'Apple', 'North', 1.00)
(2, 'Berry', 'South', 0.50)
(3, 'Apple', 'West', 1.25)
```

This structure is perfect for OLTP tasks. To retrieve a single order (`SELECT * FROM Sales WHERE TransactionID = 2;`), the database finds the start of that row and reads all its data in one efficient operation.

However, it is very inefficient for an analytical query like `SELECT SUM(SaleAmount) FROM Sales;`. To get the `SaleAmount` for every row, the database is forced to read all the other data (TransactionID, Product, Region) along with it, which wastes time and resources.

### 📑 Columnar Storage (Optimized for OLAP)

Modern analytical databases (like those in a data warehouse) store data one column at a time.

```
(1, 2, 3)
('Apple', 'Berry', 'Apple')
('North', 'South', 'West')
(1.00, 0.50, 1.25)
```

This structure is terrible for OLTP. To retrieve `TransactionID = 2`, the database must jump to four different places on the disk and "stitch" the row back together.

But for our analytical query (`SELECT SUM(SaleAmount) FROM Sales;`), this design is revolutionary. The database **only reads the `SaleAmount` column**, dramatically reducing disk I/O and accelerating analytical queries.

Modern data warehouses like **Snowflake**, **Amazon Redshift**, and **Google BigQuery** all use columnar storage under the hood.

---

## 🗄️ The Relational Model: SQL Databases

For decades, the dominant database model has been the **Relational Database Management System (RDBMS)**. The language used to communicate with these databases is **SQL (Structured Query Language)**. This is still the most common type of database an analyst will encounter. Unless you have a specific reason to use something else, SQL databases are the default choice.

### Model

Data is stored in highly structured tables (rows and columns) with predefined relationships between them (e.g., a `CustomerID` in the `Customers` table links to the `Orders` table).

- **Schema:** The most important concept in an RDBMS is its **schema**. The schema is a strict blueprint that defines all tables, columns, and data types (e.g., `SaleAmount` must be a `DECIMAL(10,2)`) **before** any data is written. This is known as **schema-on-write**.
- **Key Feature (ACID):** Relational databases are built for reliability and consistency, guaranteed by **ACID compliance**:
  - **A**tomicity: An entire transaction (like a bank transfer) either succeeds completely or fails entirely.
  - **C**onsistency: The data is always in a valid, logical state.
  - **I**solation: Concurrent transactions do not interfere with each other.
  - **D**urability: Once data is saved, it is saved permanently.
- **Examples:** Microsoft SQL Server, Oracle, MySQL, PostgreSQL.

### 🔗 Relationships and Joins

Relational databases are "relational" because they connect entities via **keys**:

- **Primary Key:** A unique identifier for each record in a table (e.g., `CustomerID` in `Customers`).
- **Foreign Key:** A field in another table that references that primary key (e.g., `CustomerID` in `Orders`).

This structure enables **JOINs**, where data from multiple tables can be combined:

```sql
SELECT c.Name, SUM(o.Total)
FROM Customers c
JOIN Orders o ON c.CustomerID = o.CustomerID
GROUP BY c.Name;
```

### ⚙️ Indexing and Performance

Indexes work like a book's table of contents: they let the database find rows faster. Analysts should understand that indexing speeds up queries but slows down inserts/updates - a tradeoff especially relevant in OLTP systems.

### 🧩 Normalization vs. Denormalization

- **Normalization** minimizes redundancy by splitting data into multiple related tables (e.g., 3rd Normal Form).
- **Denormalization** combines data for performance (common in OLAP star or snowflake schemas).

---

## 🌐 The Rise of NoSQL: Handling the 3 Vs

In the 2000s, the web exploded. Companies like Google, Amazon, and Facebook faced data challenges that the traditional relational model couldn't handle, often defined by the "3 Vs":

- **Volume:** Unprecedented amounts of data.
- **Velocity:** Data arriving at incredible speed (clicks, sensor data, social media posts).
- **Variety:** Data was no longer neat and structured. It was messy, semi-structured, or unstructured (JSON files, logs, user comments, images).

This led to the creation of **NoSQL ("Not Only SQL")** databases, a family of non-relational databases built for flexibility and massive scale.

- **Model:** Varies, but the key is a **flexible schema**. There is no predefined blueprint. You can store data as you receive it. This is called **schema-on-read** (you impose structure when you query the data, not when you store it).
- **Key Feature (BASE):** To achieve speed and scale, NoSQL databases often trade strong ACID compliance for a model called **BASE** (Basically Available, Soft state, **Eventual consistency**).
  - **Eventual Consistency:** This is a key concept. It means that if you update a record (like your social media profile), the change will propagate, but it may take a few seconds for all users globally to see it. This is unacceptable for a bank but perfectly fine for most web applications.

:::{seealso} Liking a social media post

Imagine you click the ❤️ "Like" button on a friend's photo on Instagram, Facebook, or LinkedIn.

When you tap "Like," your app immediately updates the heart icon to red and shows "1 Like" → "2 Likes."

But under the hood, this action is being sent to a distributed database - one that stores copies of data across multiple servers (or nodes) around the world.

Let's say the platform has three database replicas:

| Node | Location  | Function                 |
| ---- | --------- | ------------------------ |
| A    | New York  | Primary (handles writes) |
| B    | London    | Replica                  |
| C    | Singapore | Replica                  |

Here's the flow:

1.  **You tap ❤️ in New York.**

    - The Like is immediately written to **Node A** (the nearest one).
    - Node A confirms: "OK, this user liked the post."

2.  **Replication in progress.**

    - Node A begins sending updates to Nodes B and C in the background.
    - This takes a little time --- maybe a few milliseconds or seconds --- depending on network latency.

3.  **Meanwhile... your friend in Singapore refreshes the post.**

    - Her phone connects to **Node C**.
    - But Node C hasn't received your "Like" yet.
    - She still sees **"1 Like"**, even though you've already liked it.

4.  **A few moments later...**
    - Node C receives the update.
    - Now all three replicas agree: **"2 Likes."**

:::

### 🧩 Common NoSQL Types

- **Document Databases (e.g., MongoDB):** Stores data in flexible, JSON-like "documents." Ideal for user profiles, product catalogs, and content management.
- **Key-Value Stores (e.g., Redis):** A massive, simple dictionary. You have a `Key` (like `'UserID_123'`) and a `Value` (like `'{ "name": "Bob", "cart": [...] }'`). It is blazing fast for caching data.
- **Graph Databases (e.g., Neo4j):** Focus on relationships rather than tables - ideal for social networks, recommendation systems, and fraud detection.

### 🧮 SQL vs. NoSQL: A Comparison

NoSQL is not a replacement for SQL. They are different tools for different jobs. An analyst in a large company will almost certainly interact with both. Many modern systems are polyglot - organizations use SQL for transactions, NoSQL for scale, and even stream databases for real-time data (Kafka, Materialize, etc.).

| **Feature**        | **SQL (Relational)**               | **NoSQL (Non-Relational)**             |
| ------------------ | ---------------------------------- | -------------------------------------- |
| **Data Model**     | Structured (Tables, Rows, Columns) | Flexible (Documents, Key-Value, Graph) |
| **Schema**         | **Fixed** (Schema-on-Write)        | **Dynamic** (Schema-on-Read)           |
| **Primary Use**    | OLTP, Data Warehousing (ACID)      | Big Data, Web Apps, Unstructured Data  |
| **Consistency**    | **Strong** (ACID)                  | **Eventual** (BASE)                    |
| **Query Language** | SQL                                | Varies (e.g., MQL for Mongo)           |
| **Scaling**        | **Vertical** (Scale-Up)            | **Horizontal** (Scale-Out)             |

---

## 📈 Database Scaling Strategies

As data volume grows, a database must be able to scale to handle the load. There are two fundamental strategies for this.

### ⬆️ Vertical Scaling (Scale-Up)

- **Analogy:** "Get a bigger box."
- **How it works:** You increase the resources of a single server - more CPU, more RAM, and faster hard drives.
- **Common with:** Traditional SQL databases.
- **Limitation:** This becomes exponentially expensive, and you eventually hit a physical limit. You can't buy a server with 10,000 CPUs.

### ➡️ Horizontal Scaling (Scale-Out)

- **Analogy:** "Get more boxes."
- **How it works:** You distribute the data and the workload across a cluster of many smaller, cheaper, commodity servers.
- **Common with:** NoSQL databases (which are designed for this) and modern OLAP systems.
- **Benefit:**

---

## ⚙️ Distributed Processing: How Horizontal Scaling Works

Horizontal scaling requires a new way of processing data called **distributed processing**. The old model was to "move all the data to the code" (i.e., pull 10TB of data from the database onto your single analysis server). This is no longer possible.

If your data cannot fit into the memory of a single machine, you need to rethink your approach.

The new model is to "move the code to the data." This is best explained by the **Split-Apply-Combine** (or **MapReduce**) paradigm.

Imagine you need to count all mentions of the word "apple" in a 10TB dataset, and you have a 10-server cluster.

1.  **SPLIT:** The system automatically splits the 10TB file into 10 1TB chunks and sends one chunk to each of the 10 servers.
2.  **APPLY (Map):** The system sends your "count apples" code to _all 10 servers_. Each server then counts the apples _only in its own 1TB chunk_ simultaneously (in parallel).
3.  **COMBINE (Reduce):** A central "master" server doesn't do the hard work. It just asks each server for its final, small answer (Server 1: "I found 500," Server 2: "I found 300," etc.) and adds them up.

This ability to split a massive job into small parallel tasks is the foundation of modern big data analytics frameworks like **Apache Spark**. Popular frameworks that use this model include:

- **Hadoop MapReduce** (the pioneer)
- **Apache Spark** (in-memory distributed computing)
- **Dask** (Python-native parallel computing)
- **Google BigQuery / AWS Athena** (serverless distributed query engines)

:::{hint} Split-Apply-Combine Pattern

Do you recall where you saw the Split-Apply-Combine pattern before? It was in the chapter on **Pandas** when we used the `.groupby()` method to aggregate data. The same fundamental concept applies here, but at a much larger scale across multiple servers!

In fact, Split-Apply-Combine is a universal pattern in data analysis, whether you're working on your local machine with Pandas or on a massive distributed system like Spark.
:::

---

## 🧠 Emerging Trends: Serverless, Real-Time, and Vector Databases

Modern analytics pushes beyond batch processing:

- **Serverless Databases:** Auto-scale with usage (e.g., BigQuery, Aurora Serverless).
- **Streaming Databases:** Process events in real-time (e.g., Kafka, Materialize).
- **Vector Databases (e.g., Pinecone, Milvus):** Store machine-learning embeddings for semantic search and generative AI.
- **Hybrid Transaction/Analytical Processing (HTAP):** Systems like SingleStore and AlloyDB that aim to combine OLTP and OLAP in one engine.

---

## ✅ Summary: The Right Tool for the Job

There is no "best" database. The right choice always depends on the problem you are trying to solve. As a business analyst, your environment will dictate the tools you use:

- If you are querying the live **CRM or ERP system**, you are likely hitting an **OLTP (Row-Oriented SQL)** database. Be mindful that your queries are competing with live business operations.
- If you are using the company's **Data Warehouse or a BI tool**, you are in an **OLAP (Columnar)** environment. These databases are built for you - query away!
- If you are working with **web logs, IoT, or unstructured feeds**, you are in the **NoSQL, Data Lake, or Streaming** world.
- The best analysts are fluent in **multiple database paradigms** - understanding not just how to query data, but how and where it's stored.
