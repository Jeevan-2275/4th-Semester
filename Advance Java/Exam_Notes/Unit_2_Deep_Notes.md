# Unit 2: Servlets & Session Management - Deep Notes

> **Target:** 7-Mark Questions
> **Key Concepts:** Lifecycle, Session Tracking, Init vs Context.

---

## Q1: Explain the Servlet Lifecycle (Steps & Methods). (7 Marks)

A Servlet goes through 3 main phases managed by the Web Container (Tomcat).

### The Phases
1.  **Loading & Instantiation:** The container loads the class and creates an object.
2.  **Initialization:** `init()` method is called **once**.
    *   Used to open database connections or read config.
3.  **Request Handling:** `service()` method is called for **each request** (Get/Post).
    *   Spawns a new thread for every user request.
4.  **Destruction:** `destroy()` method is called **once** when stopping the server.
    *   Used to close connections.

```mermaid
graph TD
    A[Start] --> B[Load Class & Create Instance]
    B --> C[Call init()]
    C --> D{Ready for Service}
    D -->|Client Request| E[Call service()]
    E -->|Generate Response| D
    D -->|Server Shutdown| F[Call destroy()]
    F --> G[End]
```

---

## Q2: What is Session Management? Explain 4 Techniques. (7 Marks - *Sureshot*)

**Session Management** is a way to maintain the state of a user (remember who they are) across multiple requests since HTTP is a **stateless** protocol.

### 1. Cookies
*   Small piece of text stored on the **Client's Browser**.
*   *Pros:* Simple.
*   *Cons:* Limited size (4KB), User can disable it.

### 2. Hidden Form Fields
*   Adding `<input type="hidden" value="...">` in HTML forms.
*   *Pros:* Works without cookies.
*   *Cons:* Only works when submitting a form.

### 3. URL Rewriting
*   Appending the session ID to the URL (e.g., `url?jsessionid=123`).
*   *Pros:* Works everywhere.
*   *Cons:* URLs look ugly; Security risk if URL is shared.

### 4. HttpSession API (Server Side)
*   Creating a Session object on the **Server**.
*   `HttpSession session = request.getSession();`
*   *Pros:* Most secure, can store Objects (not just text).
*   *Cons:* Consumes server memory.

---

## Q3: Difference between ServletConfig and ServletContext. (5 Marks)

| Feature | ServletConfig | ServletContext |
| :--- | :--- | :--- |
| **Scope** | One per **Servlet** (Local Global). | One per **Web Application** (Global). |
| **Usage** | Params specific to one servlet (e.g., specific Page Limit). | Params for whole app (e.g., Database URL). |
| **Object** | Distinct config object for each servlet. | Singleton object shared by all servlets. |
| **web.xml tag** | `<init-param>` inside `<servlet>` | `<context-param>` outside `<servlet>` |

---

## Q4: What is a Filter in Servlet? (5 Marks)

A **Filter** is an object that intercepts the request related to a resource (Servlet/JSP) before/after it runs.

### Use Cases
1.  **Authentication/Authorization:** Check if user is logged in before letting them see the page.
2.  **Logging:** Record request times for analytics.
3.  **Data Compression:** Zip response data before sending.

### Methods
*   `init()`
*   `doFilter()` -> Contains the logic.
*   `destroy()`
