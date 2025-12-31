# Databricks_documentation
# 1. Databricks
Databricks is a cloud-based unified data analytics platform designed for big data processing, analytics, data engineering, and machine learning. It provides a collaborative environment built on Apache Spark.

# 1.1 Workspace UI
The Databricks Workspace UI is the web interface where users interact with all Databricks features. It provides access to notebooks, jobs, data, clusters, ML components, and more.

# Key areas of the UI:

Sidebar – Navigation for workspace components (Workspace, Data, Compute, Jobs, etc.)

Main Canvas – Displays opened notebooks, files, and cluster dashboards.

Toolbar – Options like run commands, cell execution, settings, cluster selection.
# 1.2 Overview of UI Components
# Important UI components include:

| **Component**          | **Description**                                      |
| ---------------------- | ---------------------------------------------------- |
| **Workspace**          | Stores notebooks, folders, dashboards, and repos     |
| **Data**               | View, upload, and explore datasets and tables        |
| **Compute (Clusters)** | Manage Spark clusters used to run jobs and notebooks |
| **Repos**              | Connect workspaces with Git version control          |
| **Jobs**               | Schedule automated workflows and pipelines           |
| **Marketplace**        | Access various data and package providers            |
| **Settings**           | User profile, API tokens, and configuration          |

# 1.3 Workspaces
A Workspace organizes all user objects, including:
Notebooks

Libraries

Repos

ML models

Dashboards

Folder structures

Workspaces allow role-based access control for users and teams.

# 1.4 Notebooks
A Databricks Notebook is an interactive environment used to:

* Write and run code (Python, SQL, Scala, R)
  
* Visualize data
  
* Document workflows using Markdown
  
* Execute commands on a selected Spark cluster

* Notebooks support cell-based execution.

# 1.5 Libraries
Libraries are software packages installed to enhance your workspace or cluster.

# Common library types:

* Python packages (.whl or PyPI)
  
* JAR files (Scala/Java)
  
* CRAN R packages
  
# Libraries may be installed:
At the cluster level

Notebook/session level
# 1.6 Data
# The Data section lets users:

View datasets and schemas

Upload CSV, JSON, Parquet, and other files

Access tables and databases in the metastore

Ingest data into the Lakehouse
# Data may be stored in:

DBFS (Databricks File System)

External cloud storage (S3, ADLS, GCS)

Hive tables
# 1.7 Clusters
A Databricks cluster is a Spark-based compute engine where notebook code executes.
# Cluster features:
Distributed data processing

Support for auto-scaling

Managed Spark environment

Integration with Databricks runtime versions
# 2. Workspace Navigation
   # 2.1 Creating and Managing Notebooks
Click Workspace → Create → Notebook

Give the notebook a name

Choose default language (Python/SQL/Scala/R)

Attach a cluster to start running code

# Management actions:

Rename, delete, move, import/export

Run interactively or schedule in Jobs

# 2.2 Uploading and Managing Data
# Ways to upload data:
Drag & Drop via the Data UI

Using DBFS CLI

Using Databricks File browser

# Using Spark code:
df = spark.read.csv("/FileStore/tables/data.csv")

Data can then be transformed, queried, or registered as a table.

# 2.3 Managing Clusters
# Users can:

* Create new clusters
  
* Start/stop clusters
  
* Monitor usage and logs
  
* Apply policies and limits
  
Cluster actions available from the Compute section.

# 2.4 Accessing Libraries
# Installed libraries can be:
Viewed in the Libraries tab within a cluster UI

Installed via upload

Pulled from repositories (Maven, PyPI, CRAN)

# 2.5 Collaboration and Sharing
# Databricks provides real-time collaboration:

Multiple users can work in the same notebook

Role-based access control (view, edit, run)

Activity history and notebook permissions

# 2.6 Sharing Notebooks
# Steps:

1 Open a Notebook

2 Click Share

3 Add user emails or assign permissions:

* Can View
  
* Can Run
  
* Can Edit
 
* Can Manage
# 2.7 Collaborative Editing
# Multiple users can:

See real-time cursor movements

Chat through comments

Work simultaneously like Google Docs
# 2.8 Version History
# Databricks automatically stores versions of notebooks:

Undo changes using Revision History

Compare old and new versions

Restore previous versions anytime

# 3. Cluster Creation
# 3.1 Cluster Configuration
# Key configuration settings:
Databricks Runtime version
Python version

Auto-termination time

Worker node and driver specs

Cluster size (min/max nodes)

# 3.2 Cluster Type

| **Cluster Type**             | **Use Case**                                                                                                       |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Standard Cluster**         | Multi-purpose cluster used for general Spark computations such as ETL, data processing, and analytics              |
| **High Concurrency Cluster** | Shared cluster used by multiple users simultaneously, optimized for handling many concurrent queries and workloads |

# 3.3 Worker Node Types
Workers determine compute power. Options vary by cloud provider:

# Examples:
Memory Optimized

Compute Optimized

GPU Accelerated

# Node specs affect:
Speed of operations

Cost

Performance on large datasets
# 3.4 Auto Scaling Options
Auto scaling allows Databricks to adjust cluster size automatically based on workload.

# Benefits:
Reduced cost during low usage

Increased speed during load spikes

Fully managed scaling logic

# Configuration:

Set Min Workers

Set Max Workers

Databricks adds or removes nodes automatically

# 4. dbutils Command
dbutils is a Databricks utility command used to interact with files, notebooks, libraries, widgets, and secrets.

# 4.1 Overview of dbutils
# dbutils provides helper functions for:

File operations (copy, move, create, delete)

Notebook workflows (run notebooks, exit, pass values)

Library installation

Widgets (text, dropdown, multiselect)

Secrets handling
# 4.2 Accessing dbutils in Notebooks
# You can call dbutils directly:

dbutils.fs.ls("/databricks-datasets")

# In SQL notebooks:

-- Use Python command

%python

files = dbutils.fs.ls("/mnt/data")

# Why we use it?
To automate tasks and perform system-level operations inside notebooks.

# Where we use it?
Interaction with DBFS

Triggering other notebooks

Creating widgets

Installing libraries

Runtime utilities
# 4.3 Common dbutils Commands

| **Category** | **Command**                     | **Description**                     |
| ------------ | ------------------------------- | ----------------------------------- |
| FS           | `dbutils.fs.ls(path)`           | List files                          |
| FS           | `dbutils.fs.mkdirs(path)`       | Create directory                    |
| FS           | `dbutils.fs.rm(path, True)`     | Delete files or folders recursively |
| FS           | `dbutils.fs.cp(src, dst, True)` | Copy files or folders               |
| Notebook     | `dbutils.notebook.run()`        | Run another notebook                |
| Notebook     | `dbutils.notebook.exit()`       | Return value from notebook          |
| Widgets      | `dbutils.widgets.text()`        | Create text widget                  |
| Widgets      | `dbutils.widgets.get()`         | Read widget value                   |

# 1.4 dbutils.fs (File System Operations)
Definition Used to interact with files and directories in DBFS.

# Why use?
To read, write, delete, move files. Example:

# List files in a directory

dbutils.fs.ls("/")

# Create directory

dbutils.fs.mkdirs("/mnt/data")

# Remove directory/file

dbutils.fs.rm("/mnt/data", True)

# 1.5 dbutils.notebook (Notebook Operations)

Definition Used to call and manage other notebooks.

# Why use?
Creating pipelines

Notebook chaining

Reusing logic

# Example:

print(result)

# 1.6 dbutils.library (Library Operations)

Definition Used to install and manage external libraries at runtime. Why use?

To dynamically add libraries needed in a notebook.

# Example:
dbutils.library.installPyPI("pandas")

dbutils.library.restartPython()

# 1.7 dbutils.widgets (Widget Operations)

Definition Used to add input widgets in a notebook UI.

# Why use?

Parameterization

Interactive dashboards

# Example:
dbutils.widgets.text("input_val", "default_value", "Enter something")

dbutils.widgets.get("input_val")

# 5. Example Usages
5.1 Uploading and Downloading Files

Uploading via UI:

Data → Add Data → Upload

Programmatically:

# Upload from local not allowed via code directly, but once uploaded you can move

Download:

# Export file from DBFS to local (Databricks UI → DBFS File Browser)

# 5.2 Running External Notebooks
out = dbutils.notebook.run("/Shared/PrepData", 120, {"input": "/mnt/raw/data.csv"})

print(out)

# 5.3 Installing and Managing Libraries

Notebook-scoped installation:

%pip install numpy

Cluster-level installation:

Compute → Libraries → Install from PyPI/Maven/JAR/Wheel

# 5.4 Interacting with Widgets

Example of using widget value in query:

input_path = dbutils.widgets.get("input_path")

df = spark.read.csv(input_path)

df.show()

# 6. Read and Write in DBFS Path

# 6.1 Introduction to DBFS

DBFS = Databricks File System

A distributed file system

Mounted on cloud storage (S3/ADLS/GCS)

You can access paths such as:

/dbfs/...

/mnt/... (mounted external storage)

dbfs:/... (URI)

# 6.2 Overview of DBFS

Two access types:

DBFS root → /dbfs, ephemeral for some clusters

Mounted storage → persistent paths via /mnt/...

# 6.3 Mount Points

Mounting external storage:

dbutils.fs.mount(

    source="wasbs://container@storage.blob.core.windows.net/",
    
    mount_point="/mnt/data",
    
    extra_configs={"fs.azure.account.key.storage.blob.core.windows.net": key}
)
List mounts:

dbutils.fs.mounts()

# 6.4 Reading Data from DBFS

df = spark.read.csv("/mnt/raw/data.csv", header=True)

df.show()

# 6.5 Reading CSV/Parquet Files

CSV

df = spark.read.option("header", True).csv("dbfs:/mnt/raw/employees.csv")

Parquet

df = spark.read.parquet("dbfs:/mnt/processed/data.parquet")

# 6.6 Writing Data to DBFS

Use Spark DataFrame write operations:

df.write.mode("overwrite").csv("dbfs:/mnt/output/csv_folder")

df.write.mode("overwrite").parquet("dbfs:/mnt/output/parquet_folder")

# 6.7 Writing CSV/Parquet Files

Writing CSV

df.write.option("header", True).mode("overwrite").csv("dbfs:/mnt/data/employees_csv")

Writing Parquet

df.write.mode("overwrite").parquet("dbfs:/mnt/data/employees_parquet")

# 6.8 Commands for Writing CSV and Parquet Files

CSV Write Commands

df.write.option("header", True).csv("dbfs:/mnt/csv_output")

Parquet Write Commands

df.write.parquet("dbfs:/mnt/parquet_output")

# 6.9 Writing Other File Formats

JSON

df.write.json("dbfs:/mnt/json_output")

Delta

df.write.format("delta").save("dbfs:/mnt/delta_output")

Avro

df.write.format("avro").save("dbfs:/mnt/avro_output")

# 6.10 Commands for Writing Various File Formats

| **Format**  | **Command**                           |
| ----------- | ------------------------------------- |
| **CSV**     | `df.write.csv(path)`                  |
| **Parquet** | `df.write.parquet(path)`              |
| **JSON**    | `df.write.json(path)`                 |
| **Delta**   | `df.write.format("delta").save(path)` |
| **Avro**    | `df.write.format("avro").save(path)`  |

# 1. Medallion Architecture
1.1 Introduction to Medallion

Medallion Architecture is a data design pattern used in data lakes to organize data into multiple structured layers:

Bronze Layer – Raw data (unprocessed)

Silver Layer – Cleaned, validated, and enriched data

Gold Layer – Business-level aggregated data used for reporting

# Why Medallion Architecture?

Better data quality at every stage

Easier debugging and traceability

Clear separation between raw and business-ready data

# Flow
Source Systems → Bronze → Silver → Gold → BI/Analytics

# Example Scenario

Assume you are receiving daily sales CSV files:

Bronze: Load raw CSV files into Delta tables.

Silver: Remove duplicates, handle missing values, standardize formats.

Gold: Aggregate total sales per region/group for reporting or dashboards.

# 1.2 Use Cases and Applications

# Use Cases
Enterprise Data Lake modernization

ML feature data preparation

Incremental pipelines

Slowly Changing Dimensions

Stream + Batch processing

# Real Applications
Generating sales dashboards

Feeding ML models from enriched data

Customer analytics and segmentation

Finance misreporting audits

# 2. Delta Lake (Theory)
# 2.1 Introduction to Delta Lake
Delta Lake is a storage layer built on top of data lakes (like S3/ADLS/DBFS) that provides:
ACID transactions

Schema enforcement

Time Travel

Data reliability

It is widely used in Databricks for scalable data pipelines.

# 2.2 ACID Transactions
# ACID stands for:

Atomicity – All operations succeed or fail together

Consistency – Data always remains valid

Isolation – Concurrent writes never corrupt data

Durability – Once written, data is permanent

# Example
df.write.format("delta").mode("append").save("/mnt/sales")

Even if the job fails midway, your Delta table won't become corrupted due to ACID guarantees.

# 2.3 Time Travel

Time Travel allows querying older versions of a Delta table.

# Example
SELECT * FROM sales_table VERSION AS OF 4;


# or using timestamp:

SELECT * FROM sales_table TIMESTAMP AS OF '2024-11-21';

This is useful for:

Auditing

Comparing old data

Recovering deleted data

# 2.4 Delta Table
A Delta Table is stored like a normal directory but with a structured transaction log.

# Example
spark.sql("""

CREATE TABLE sales_delta

USING DELTA

AS SELECT * FROM sales_raw

""")

# 2.5 Delta Log

Every Delta table maintains a _delta_log directory that stores:

Metadata

Schema history

Commit logs

File actions and snapshots

This enables ACID and Time Travel features.

# 2.6 Usage and Benefits
# Benefits
Consistent and correct data

Scalable for large datasets

Supports both streaming and batch

Auto indexing for faster read

# Typical Use in ETL
bronze_df.write.format("delta").save("/mnt/bronze")

silver_df.write.format("delta").save("/mnt/silver")

gold_df.write.format("delta").save("/mnt/gold")

# 2.7 Schema Evolution
Delta supports evolving schema dynamically.

# Example
df.write.option("mergeSchema", "true").format("delta").save("/mnt/sales")

If new columns arrive, the table updates without failure.








