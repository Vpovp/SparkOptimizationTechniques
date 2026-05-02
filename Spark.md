```mermaid
flowchart TD

    A[Driver (Spark Application)]
    A --> B[Cluster Manager (YARN / Kubernetes)]

    B --> C1[Worker Node 1]
    B --> C2[Worker Node 2]

    C1 --> D1[Executor 1]
    C1 --> D2[Executor 2]

    C2 --> D3[Executor 3]
    C2 --> D4[Executor 4]

    D1 --> E1[Core 1]
    D1 --> E2[Core 2]

    D2 --> E3[Core 1]
    D2 --> E4[Core 2]

    D3 --> E5[Core 1]
    D3 --> E6[Core 2]

    D4 --> E7[Core 1]
    D4 --> E8[Core 2]

    %% Tasks run on cores
    E1 --> F1[Task]
    E2 --> F2[Task]
    E3 --> F3[Task]
    E4 --> F4[Task]
    E5 --> F5[Task]
    E6 --> F6[Task]
    E7 --> F7[Task]
    E8 --> F8[Task]

    %% Each task processes one partition
    F1 --> G1[Partition 1]
    F2 --> G2[Partition 2]
    F3 --> G3[Partition 3]
    F4 --> G4[Partition 4]
    F5 --> G5[Partition 5]
    F6 --> G6[Partition 6]
    F7 --> G7[Partition 7]
    F8 --> G8[Partition 8]


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

