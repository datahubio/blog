---
title: "How Queryless Turns Raw Data Files Into Insights with DuckDB"
description: "Queryless lets anyone explore raw data using natural language—like asking \"What were our sales last month?\" in chat. Behind the scenes, it generates analytical SQL queries and runs them on DuckDB to turn files into fast, interactive insights."
date: 2026-03-09
authors: [João Demenech]
---

![[hero.png]]

In a previous article, we explored the idea of **chat‑first access to data** and how Queryless makes it possible to interact with datasets through conversation (see: [https://datahub.io/blog/data-portals-to-chat-first-access](https://datahub.io/blog/data-portals-to-chat-first-access)).

In this article, we focus on a specific part of that system: **how [Queryless](https://datahub.io/queryless) analyzes raw data files**. 

Queryless lets anyone explore data using natural language—like asking "What were our sales last month?" in chat. Behind the scenes, it generates analytical SQL queries and runs them on DuckDB to turn files into fast, interactive insights. But before looking at how Queryless analyzes raw files, it helps to understand the challenge teams face when working with them.

> 👉 **Learn more and try Queryless:** visit [https://querylessai.com](https://datahub.io/queryless).

https://youtu.be/KM5RhPq9jn0

## The Problem

Organizations accumulate data in many everyday formats that often become the starting point for analysis, for example:

- CSV exports from tools like Stripe, HubSpot, or Shopify
- Excel or spreadsheet files shared between teams
- analytics exports from internal tools
- log or event data

These files often end up stored in cloud drives, data folders, or shared storage. **Extracting insights from them usually requires loading the data into a database, writing SQL queries, or building dashboards.** 

Queryless approaches this differently by allowing teams to query those files directly.

## Talking to Your Data Files

To solve this problem, instead of manually loading files into databases or building dashboards first, with **Queryless** anyone can ask questions about their data directly through chat interfaces such as Telegram.

When the data source is a **raw file**, Queryless turns a question into an answer through a simple pipeline:

- A user asks a question about the data
- Queryless determines which dataset is relevant
- The file is retrieved from its storage location (for example S3, Google Drive, or another file system)
- The file is downloaded and cached locally
- Queryless reads the file metadata (such as schema, column names, and types)
- A SQL query is generated from the user's question
- The query is executed using **DuckDB**
- Results are returned as tables, summaries, or charts

Raw datasets can live in many storage systems—such as **Amazon S3**, **Google Drive**, other cloud storage services, or internal file servers—and Queryless can work with common file formats like **CSV, Excel (XLSX), Parquet, and JSON**.

This allows Queryless to run analytical queries directly on the retrieved files without loading them into a separate data warehouse or pipeline. But how does Queryless actually turn a question into a SQL query?

![[diagram.png]]

## Query Generation and Execution

Once the dataset is available, Queryless converts user questions into SQL queries and executes them using DuckDB.

For example, a user might ask:

```
What were the total sales in March?
```

Queryless first identifies the relevant dataset, then inspects its metadata (such as column names and schema) to generate the query needed to answer the question.

Example:

```sql
SELECT
  SUM(sales) AS total_sales
FROM transactions
WHERE date >= '2024-03-01'
AND date < '2024-04-01';
```

This query is then executed by **DuckDB**, the analytical engine used by Queryless.

DuckDB is well suited for this workload because it uses fast columnar and vectorized execution:

- executes analytical SQL very quickly
- can query data files directly
- requires minimal infrastructure

This allows Queryless to analyze raw datasets efficiently while keeping the architecture lightweight.

## Debugging Queryless Answers and Charts

Once answers are generated, it is often useful to understand how they were produced.

If a result or chart looks unexpected, you can ask Queryless to show the SQL used to generate it. This makes it easier to debug how an answer was produced.

Example prompt:

```
Show the SQL used for this result.
```

Queryless might return:

```sql
SELECT
  DATE_TRUNC('month', order_date) AS month,
  SUM(revenue) AS total_revenue
FROM orders
GROUP BY 1
ORDER BY 1;
```

This transparency allows users to verify results or reuse the query elsewhere.

![[explain.png]]

## Queryless Can Learn Facts About Your Data

While inspecting queries helps understand results, Queryless can also learn from user feedback.

Datasets often contain ambiguous column names. Clarifying them helps improve future query generation accuracy. For example:

- `value`
- `amount`
- `score`

If a result looks incorrect, users can ask Queryless how it produced the answer.

```
Explain how you calculated this result.
```

Queryless can describe which columns, aggregations, and filters were used.

If the user notices a mistake, they can correct the definition. For example:

```
When I say revenue, I mean the column "total_amount".
Please remember that definition.
```

Queryless can store this information and apply it to future queries, gradually learning how the dataset should be interpreted.

## Conclusion

Queryless combines several technologies to make raw data easier to explore:

- natural language interfaces
- automated SQL generation
- DuckDB for fast analytical queries
- flexible access to raw data files

Together these components allow teams to move from **raw files to insights** through a chat‑first approach to data access—echoing the broader idea explored in our earlier article. Instead of building pipelines and dashboards first, teams can start by simply asking questions and iterating from there.

> 👉 To learn more or try it yourself, visit [**https://querylessai.com**](https://datahub.io/queryless).

