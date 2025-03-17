# Keys in a Relational Database

In a **relational database**, a **key** is a column (or a set of columns) used to uniquely identify a row (record) in a table. Keys help maintain data integrity and establish relationships between tables.

## 🔹 Why Are Keys Important?

✅ Ensure data integrity  
✅ Prevent duplicate records  
✅ Establish relationships between tables  
✅ Improve query performance

---

## 🔑 Types of Keys in a Relational Database

### 1️⃣ Primary Key (PK)

- Uniquely identifies each record in a table.
- Cannot have `NULL` values.
- Each table can have **only one** primary key.

#### 📌 Example:

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT
);
```

### 2️⃣ Foreign Key (FK)

- Establishes a relationship between two tables.
- A column in one table that references the Primary Key in another table.
- Ensures referential integrity (prevents orphan records).

#### 📌 Example:

```sql
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID)
);
```

### 3️⃣ Candidate Key

- A set of columns that could be a Primary Key because they contain unique values.
- A table can have multiple candidate keys, but only one is chosen as the Primary Key.

#### 📌 Example:

In a Users table, both UserID and Email could be candidate keys.

```sql
CREATE TABLE Users (
    UserID INT,
    Email VARCHAR(255) UNIQUE,
    Name VARCHAR(100),
    PRIMARY KEY (UserID)
);
```

### 4️⃣ Super Key

- A super set of a Candidate Key that uniquely identifies a record.
- Example: (StudentID, Email) together is a Super Key if StudentID alone is unique.

#### 📌 Example:

```sql
CREATE TABLE Students (
    StudentID INT,
    Email VARCHAR(255),
    Name VARCHAR(100),
    PRIMARY KEY (StudentID, Email)
);
```

### 5️⃣ Composite Key

- A key made of two or more columns to uniquely identify a record.
- Used when a single column cannot uniquely identify rows.

#### 📌 Example:

```sql
CREATE TABLE OrderDetails (
    OrderID INT,
    ProductID INT,
    Quantity INT,
    PRIMARY KEY (OrderID, ProductID)
);
```

### 6️⃣ Unique Key

- Ensures values in a column are unique, but unlike Primary Keys, it can contain NULL values.

#### 📌 Example:

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Email VARCHAR(255) UNIQUE
);
```

## 🎯 Summary Table

| **Key Type**      | **Definition**                                   | **Allows NULL?** | **Unique?** | **Example**                        |
| ----------------- | ------------------------------------------------ | ---------------- | ----------- | ---------------------------------- |
| **Primary Key**   | Uniquely identifies each record.                 | ❌ No            | ✅ Yes      | `StudentID`                        |
| **Foreign Key**   | References a Primary Key in another table.       | ✅ Yes           | ❌ No       | `StudentID` in `Enrollments` table |
| **Candidate Key** | A column that could be a Primary Key.            | ❌ No            | ✅ Yes      | `Email`, `UserID`                  |
| **Super Key**     | A superset of a Candidate Key.                   | ❌ No            | ✅ Yes      | (`StudentID`, `Email`)             |
| **Composite Key** | A combination of columns that form a unique key. | ❌ No            | ✅ Yes      | (`OrderID`, `ProductID`)           |
| **Unique Key**    | Ensures uniqueness but allows NULLs.             | ✅ Yes           | ✅ Yes      | `Email`                            |

### 🏆 Conclusion

Keys are essential in relational databases for maintaining data integrity, ensuring uniqueness, and managing relationships between tables. Understanding the different types of keys helps in designing a well-structured, efficient database.
