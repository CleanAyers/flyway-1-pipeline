# flyway-1-pipeline

# 🏗️ Cluster 1 – Flyway Pipeline

## Overview
This repository manages all **schema-level DDL migrations** for Cluster 1.  
It is part of the distributed Flyway structure defined in the [shared-flyway-ddl](https://github.com/CleanAyers/shared-flyway-ddl) parent repository.

**Purpose:**  
- Versioned SQL migrations `V__` prefix  
- Structural changes to tables, views, functions, and indexes  
- Separate lifecycle from `ecs-1-grants` (access control repository)  

---

## 📂 Structure
```
├── flyway-1-pipeline/                    # 🏗️ Cluster 1 schema migrations
│   ├── ro-shared-ddl/                    # Synced from parent
│   │   ├── sql/
│   │   │   └── V1__test.sql
│   │   └── sh/
│   │       └── child_pull_shared.sh
│   └── README.md
```


---

## 🚀 Usage
Run migrations locally or through CI/CD:

```bash
flyway -configFiles=conf/flyway.conf migrate
```

## 🧩 Notes

- All DDL scripts must be idempotent where feasible.

- Do not include grants or permissions here — those belong to flyway-1-grants.

- Sync schema baselines periodically with shared-flyway-ddl/global/baseline/.