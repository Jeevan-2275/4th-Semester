# Unit 1: Introduction to Enterprise Java & JDBC - Deep Notes

> **Target:** 7-Mark Questions
> **Key Concepts:** JDBC Architecture, Drivers, ACID Properties, MVC.

---

## Q1: Explain JDBC Architecture and Types of Drivers. (7 Marks - *Crucial*)

**JDBC (Java Database Connectivity)** is an API that enables Java applications to interact with databases.

### The 4 Types of JDBC Drivers
1.  **Type 1: JDBC-ODBC Bridge Driver**
    *   Uses ODBC software installed on the client machine.
    *   *Cons:* Platform dependent (needs Windows), Slow. (Obsolete).
2.  **Type 2: Native API Driver**
    *   Uses native C/C++ libraries of the database.
    *   *Cons:* Needs client-side installation.
3.  **Type 3: Network Protocol Driver**
    *   Uses middleware application server. Very flexible but needs middleware.
4.  **Type 4: Thin Driver (Pure Java)**
    *   Directly converts JDBC calls into database-specific vendor protocol.
    *   *Pros:* No client installation needed. Fastest. **Most used today.**

> **Mnemonic:** **"B-N-N-T"** (Bridge, Native, Network, Thin).

---

## Q2: Difference between Statement, PreparedStatement, and CallableStatement. (7 Marks)

| Feature | Statement | PreparedStatement | CallableStatement |
| :--- | :--- | :--- | :--- |
| **Usage** | General purpose SQL queries. | Parameterized queries (Dynamic). | Stored Procedures. |
| **Performance** | Slow (Compiles SQL every time). | **Fast** (Pre-compiled query). | Fast (Database logic). |
| **Security** | Vulnerable to **SQL Injection**. | **Secure** (Prevents SQL Injection). | Secure. |
| **Syntax** | `executeQuery("SELECT * FROM...")` | `setInt(1, 101); executeQuery()` | `prepareCall("{call myProc(?)}")` |

---

## Q3: Transaction Management (ACID Properties). (5 Marks)

A **Transaction** is a unit of work that is either completed fully or not at all.
**ACID Properties:**
1.  **Atomicity:** All or Nothing. (Commit or Rollback).
2.  **Consistency:** Database remains valid before and after transaction.
3.  **Isolation:** Multiple transactions don't interfere with each other.
4.  **Durability:** Once committed, data is saved permanently even if power fails.

### JDBC Methods for Transactions
*   `con.setAutoCommit(false);` // Start Transaction
*   `con.commit();` // Save Changes
*   `con.rollback();` // Undo Changes if error occurs

---

## Q4: Explain MVC Architecture. (7 Marks)

**MVC (Model-View-Controller)** is a design pattern separating concerns in an application.

1.  **Model:** Represents Data & Logic (JavaBeans / Database).
    *   *Job:* Handles data rules.
2.  **View:** Represents the User Interface (JSP / HTML).
    *   *Job:* Displays data to user.
3.  **Controller:** Represents the Request Handler (Servlet).
    *   *Job:* Takes user request, calls Model, tells View what to show.

```mermaid
graph LR
    User((User)) -->|Request| Controller[Controller (Servlet)]
    Controller -->|Update| Model[Model (JavaBean/DB)]
    Model -->|Data| Controller
    Controller -->|Select| View[View (JSP)]
    View -->|Response| User
```
