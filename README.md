# Parallel_and_Distributed_Computing_with_Dask-Python

This repository contains my submission for exploring **parallel and distributed computing** using the **Dask** library in Python.  
The assignment emphasizes how to handle larger-than-memory datasets, perform parallel computations efficiently, and accelerate machine learning workflows on single and multiple cores.

---

### Business Problem

Modern data science workflows often encounter datasets too large to fit in memory or processes that are too slow for practical use on a single core.  
Traditional Python libraries like NumPy and Pandas struggle with such scaling.  
This project leverages **Dask**, a parallel computing framework that extends familiar APIs while enabling processing across multiple cores or even multiple machines.

The goal was to practice parallel computing fundamentals, task graph visualization, distributed computing setup, and parallelized machine learning using Dask and Scikit-Learn.

---

### Dataset Overview

The dataset used was **domestic flights from NYC airports (JFK, EWR, LGA)** from **1990 to 1999**, split across multiple `.csv` files.  
Key characteristics:

- Flight statistics across thousands of flights annually
- Date and time attributes
- Categorical attributes like origin, destination, and cancellation status

The dataset simulated the challenges of **larger-than-memory processing** by aggregating multiple years' worth of data.

---

### Project Objectives

The assignment was designed to:

- Understand concepts of **multithreading** vs **multiprocessing**
- Learn Dask’s architecture: Arrays, DataFrames, Bags, and Distributed Schedulers
- Set up **local Dask clusters** and visualize **task graphs**
- Perform **lazy evaluation** and **timing comparisons** between Pandas and Dask
- Process large datasets using **Dask DataFrames**
- Execute ML model training with **Scikit-Learn’s GridSearchCV** using:
  - Single-core
  - Multi-core (using joblib)
  - Dask distributed cluster
- Evaluate model performance and optimization techniques

---

### Solution Approach

**1. Environment Setup:**
- Installed Dask, graphviz, and associated libraries
- Created a Python virtual environment for clean project management

**2. Data Import and Preprocessing:**
- Used Dask's `read_csv()` with glob patterns to load multiple files in parallel
- Explicitly specified data types to avoid inference errors
- Created a combined `Date` column from Year, Month, Day
- Corrected missing values and set correct data types for all columns

**3. Exploratory Analysis and Lazy Computations:**
- Performed basic filtering, sampling, and aggregation
- Compared loading and processing speeds between Pandas and Dask
- Visualized Dask Task Graphs for selected operations

**4. Distributed Computing Setup:**
- Created a **Dask distributed client** with 4 workers and 2 threads each
- Explored live **dashboard diagnostics** (localhost:8787/status)
- Used Progress Bars for task progress monitoring

**5. Machine Learning:**
- Generated synthetic data using `make_classification()`
- Trained a **Support Vector Classifier (SVC)**:
  - Single-core (standard fitting)
  - Multi-core (using `n_jobs=-1` with joblib)
  - Parallelized with **Dask as backend** for joblib
- Compared grid search speeds and evaluated models
- Computed detailed classification reports (precision, recall, F1-scores)

**6. Finalization:**
- Shut down the Dask cluster after completion

---

### Business Value

This project demonstrates critical, real-world capabilities such as:

- **Efficient processing of large datasets** beyond RAM limitations
- **Accelerated ML model training** with multi-core and distributed backends
- **Cost-effective scaling** without the need for expensive hardware
- **Operational transparency** through dashboards and progress monitors
- Laying the groundwork for scaling to **enterprise-level big data** with minimal code changes

---

### Challenges Encountered

- Correctly setting data types during CSV imports (important to avoid type errors)
- Understanding lazy evaluation: remembering to use `.compute()` where necessary
- Navigating differences between Pandas and Dask API behaviors
- Handling task graph visualization dependencies (graphviz installations)
- Dealing with distributed memory warnings and performance tuning

---
