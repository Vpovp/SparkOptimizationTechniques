```mermaid
flowchart TD

    A[Driver<br>(Spark Application)] --> B[Cluster Manager<br>(YARN / Kubernetes)]

    B --> C1[Worker Node 1]
    B --> C2[Worker Node 2]
    B --> C3[Worker Node 3]

    C1 --> D1[Executor]
    C2 --> D2[Executor]
    C3 --> D3[Executor]

    D1 --> E1[Core 1]
    D1 --> E2[Core 2]

    D2 --> E3[Core 1]
    D2 --> E4[Core 2]

    D3 --> E5[Core 1]
    D3 --> E6[Core 2]

    E1 --> F1[Task]
    E2 --> F2[Task]
    E3 --> F3[Task]
    E4 --> F4[Task]
    E5 --> F5[Task]
    E6 --> F6[Task]

    F1 --> G[Partitions]
    F2 --> G
    F3 --> G
    F4 --> G
    F5 --> G
    F6 --> G
```


# Lazy Operations in Spark

## 📌 What is Lazy Evaluation?

In Apache Spark, **lazy evaluation** means that transformations on data are **not executed immediately**.  
Instead, Spark **builds a logical plan (DAG)** and only executes it when an **action** is triggered.

---

## 🧠 Simple Definition

> Lazy operations are transformations that **do not execute immediately**, but instead **record the steps** to be executed later.

---

## 🔄 Types of Operations in Spark

### 1. Transformations (Lazy)
- Do not trigger execution
- Return a new DataFrame / RDD
- Build execution plan

**Examples:**
```python
df.filter("age > 25")
df.select("name")
df.groupBy("city")
```

## 🔹 Actions (Trigger Execution)
- Execute the plan
- Return result

**Examples:**
```
df.show()
df.count()
df.collect()
```

---

