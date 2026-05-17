# Milestone 2 — ERD Design & Normalization Report  
## AI Dataset Management & Innovation System

---

# 1. Introduction

This document explains the normalization process applied to the database schema of the AI Dataset Management & Innovation System. The schema was analyzed using First Normal Form (1NF), Second Normal Form (2NF), and Third Normal Form (3NF) to ensure proper structure, eliminate redundancy, and maintain data integrity.

---

# 2. Normalization Process Overview

Each table in the database has been reviewed step-by-step to ensure compliance with normalization rules. If no changes were required, justification is provided.

---

# 3. USERS TABLE

## 1NF (First Normal Form)
All attributes are atomic and contain single values:
- name, email, password, role, created_at

No repeating groups exist.

## 2NF (Second Normal Form)
- Primary key: user_id
- All attributes depend fully on the primary key.

No partial dependency exists.

## 3NF (Third Normal Form)
- All attributes depend only on user_id.
- No transitive dependencies exist.

✔ Result: The table is in 3NF because all non-key attributes depend only on the primary key.

---

# 4. CATEGORIES TABLE

## 1NF
All attributes are atomic:
- category_name, description

## 2NF
- Primary key: category_id
- No partial dependency exists.

## 3NF
- No attribute depends on another non-key attribute.

✔ Result: The table is in 3NF because all attributes depend only on category_id.

---

# 5. DATASETS TABLE

## 1NF
All attributes are atomic:
- title, description, size_mb, file_type, file_path, upload_date

## 2NF
- Primary key: dataset_id
- No partial dependency exists.

## 3NF
- user_id and category_id are foreign keys.
- All attributes depend only on dataset_id.

✔ Result: The table is in 3NF because all non-key attributes depend only on the primary key.

---

# 6. TAGS TABLE

## 1NF
- tag_name is atomic and unique.

## 2NF
- Primary key: tag_id
- Full dependency exists.

## 3NF
- No transitive dependency exists.

✔ Result: The table is in 3NF because no dependency exists beyond the primary key.

---

# 7. DATASET_TAGS TABLE (JUNCTION TABLE)

## 1NF
Each record contains atomic values:
- dataset_id, tag_id

## 2NF
- Composite primary key (dataset_id, tag_id)
- No partial dependency exists.

## 3NF
- No transitive dependency exists.

✔ Result: The table is in 3NF because all attributes depend fully on the composite key.

---

# 8. RATINGS TABLE

## 1NF
All attributes are atomic:
- rating, user_id, dataset_id

## 2NF
- Primary key: rating_id
- No partial dependency exists.

## 3NF
- All attributes depend only on rating_id.

✔ Result: The table is in 3NF because no transitive dependency exists.

---

# 9. INNOVATIONS TABLE

## 1NF
All attributes are atomic:
- title, description, created_at

## 2NF
- Primary key: innovation_id
- No partial dependency exists.

## 3NF
- dataset_id is a foreign key.
- All attributes depend only on the primary key.

✔ Result: The table is in 3NF because all attributes depend only on the primary key.

---

# 10. Redundancy Check

The database schema was analyzed for redundancy and duplicate data.

- No repeating groups were found.
- No redundant attributes exist across tables.
- Data duplication is avoided using proper foreign keys.
- The many-to-many relationship between datasets and tags is implemented using the dataset_tags junction table.

✔ Result: The schema is fully normalized with no redundancy.

---

# 11. ERD Update Summary

The final ER Diagram reflects the following relationships:

- Users → Datasets (1:M)
- Categories → Datasets (1:M)
- Datasets ↔ Tags (M:N via dataset_tags)
- Users → Ratings (1:M)
- Datasets → Ratings (1:M)
- Datasets → Innovations (1:M)

All relationships are properly implemented using primary and foreign keys, ensuring referential integrity.

---

# 12. Conclusion

The AI Dataset Management & Innovation System database is fully normalized up to Third Normal Form (3NF). The design eliminates redundancy, ensures data integrity, and supports efficient relational structure. The final ERD accurately reflects all normalization rules and relationships.
