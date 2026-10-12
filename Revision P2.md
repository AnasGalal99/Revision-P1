# **Vodafone Junior Software Tester Master Revision Guide (Part 2 of 2)**

Welcome to **Part 2** of your comprehensive revision guide. This section covers **Lessons 7 through 11**, followed by your **Master Revision Sheet**, **Key Comparisons Table**, **30 Likely Interview Q&As**, and **Self-Assessment Checklist**.

---

## **Part 2 Navigation**
* **Lesson 7:** Test Documentation, Test Case Anatomy, and RTM
* **Lesson 8:** Bug/Defect Life Cycle, Bug Reports, Severity vs. Priority, and Conflict Resolution
* **Lesson 9:** API Concepts, Layer Architecture, REST vs. SOAP, HTTP Methods & Status Codes
* **Lesson 10:** Practical Postman Testing, Variables, Auth, Mock Servers, Swagger, and Newman
* **Lesson 11:** Database & SQL for Testers (DDL vs. DML, Aggregates, Joins, Subqueries)
* **Master Revision Sheet**
* **Must-Memorize Comparisons Table**
* **30 Likely Technical Interview Q&As with Model Answers**
* **Final Self-Assessment Checklist**

---

# **Lesson 7: Test Documentation & Test Case Management**

### **1. Core Documentation Concepts**
* **Test Basis:** Any source document used to analyze requirements and extract test conditions (e.g., SRS, User Stories, UI Wireframes).
* **Testware:** The entire collection of artifacts produced by testers across the STLC (e.g., Test Plans, Test Cases, Bug Reports, Execution Logs, RTM).
* **Requirements Traceability Matrix (RTM):** A grid table mapping business requirements to corresponding test cases and defect IDs to guarantee **100% test coverage** and support **impact analysis** when requirements change.

---

### **2. Test Condition vs. Test Scenario vs. Test Case**

| Concept | Definition & Scope | Practical Example (Ana Vodafone Login) |
| :--- | :--- | :--- |
| **Test Condition** | Smallest individual feature element that can be verified. | Password Text Box. |
| **Test Scenario** | High-level description of an end-to-end user workflow. | Verify that a registered customer can log in. |
| **Test Case** | Detailed set of step-by-step instructions, inputs, preconditions, and expected outcomes. | **TC_LOG_01:** Enter `01012345678`, enter PIN `1234`, click Submit \\(\rightarrow\\) Expected Result: Redirect to Dashboard. |

---

### **3. Mandatory Fields of a Professional Test Case Template**
1. **Test Case ID (TC_ID):** Unique alphanumeric code (e.g., `TC_VF_CASH_01`).
2. **Title / Summary:** Clear description of what is being tested.
3. **Pre-Conditions:** Prerequisites required before running test steps.
4. **Test Data:** Specific input values used during execution.
5. **Test Steps:** Sequential instructions for the tester.
6. **Expected Result:** Correct system behavior defined by requirements.
7. **Actual Result:** Observed system behavior (Left blank until execution).
8. **Status:** Execution outcome (**Pass**, **Fail**, **Blocked**, **Not Executed**).

> **Crucial Interview Distinction:** Unexecuted Test Cases contain only *Expected Results*. Bug Reports contain *Actual Results*, build numbers, screenshots, and assigned developers.

---

# **Lesson 8: Bug Life Cycle, Bug Reports, Severity vs. Priority, and Conflict Resolution**

### **1. The Bug / Defect Life Cycle**

```
 [ NEW ] ──> [ ASSIGNED ] ──> [ OPEN ] ──> [ FIXED ] ──> [ PENDING RETEST ] ──> [ RETESTING ]
                                                                                   │
                 ┌─────────────────────────────────────────────────────────────────┴─────────────────────────────────┐
                 ▼                                                                                                   ▼
           (Fix Fails)                                                                                         (Fix Passes)
          [ REOPENED ] ──> (Back to Dev)                                                                      [ VERIFIED ] ──> [ CLOSED ]
```

* **Other Developer Decision States:**
  * **Rejected:** Developer considers the behavior valid or non-bug.
  * **Duplicate:** The defect is already logged in another ticket.
  * **Deferred:** Valid bug postponed to a future sprint.
  * **Not a Bug:** Software behaves strictly according to specifications.

---

### **2. Severity vs. Priority Matrix**

* **Severity:** Technical damage depth on system functionality (Assigned by Tester).
* **Priority:** Business urgency and speed required to fix the defect (Assigned by PO / QA Lead).

```
                     HIGH SEVERITY                  LOW SEVERITY
             ┌──────────────────────────────┬──────────────────────────────┐
HIGH         │ High Severity / High Priority│ Low Severity / High Priority │
PRIORITY     │ • Main function broken       │ • Company logo wrong color   │
             │ • App crashes on launch      │ • Brand typo on home page    │
             ├──────────────────────────────┼──────────────────────────────┤
LOW          │ High Severity / Low Priority │ Low Severity / Low Priority  │
PRIORITY     │ • App crashes on legacy OS   │ • Typo on rarely visited     │
             │ • Error in rare corner case  │   terms & conditions page    │
             └──────────────────────────────┴──────────────────────────────┘
```

---

### **3. Handling Developer Conflicts (When a Dev Rejects Your Bug)**
1. **Re-check Specifications:** Review SRS / Acceptance Criteria to verify requirement violation.
2. **Provide Clear Evidence:** Attach reproduction steps, screenshots, videos, and network logs.
3. **Escalate Constructively:** Discuss the issue during Daily Standup or consult the **Product Owner (PO)** for business clarification.

---

# **Lesson 9: API Concepts, Layer Architecture, REST vs. SOAP, HTTP Methods & Status Codes**

### **1. What is an API & Where Does It Sit?**
* **API (Application Programming Interface):** A set of rules allowing different software applications or layers to communicate and exchange data.
* **3-Tier Architecture:** Presentation Layer (GUI) \\(\rightarrow\\) **Application Layer (APIs & Business Logic)** \\(\rightarrow\\) Database Layer.

---

### **2. REST vs. SOAP**

| Comparison Aspect | REST | SOAP |
| :--- | :--- | :--- |
| **Type** | **Architectural Style** (flexible guidelines). | **Strict Protocol** (rigid standards). |
| **Data Format** | Primary format is **JSON** (also XML, text). | Uses **XML exclusively**. |
| **State & Weight** | **Stateless, lightweight, fast, scalable**. | Heavyweight, slower XML parsing, **WS-Security**. |

---

### **3. Core HTTP Methods, Safety, and Idempotency**

| HTTP Method | Purpose | Sends Body? | Is Safe? | Is Idempotent? |
| :--- | :--- | :---: | :---: | :---: |
| **GET** | Fetch / Read data. | No | **YES** | **YES** |
| **POST** | Create new resource. | Yes | No | No |
| **PUT** | Full Replace / Overwrite object. | Yes | No | **YES** |
| **PATCH** | Partial Update (specific fields). | Yes | No | No |
| **DELETE** | Remove resource. | No | No | **YES** |

---

### **4. Must-Know HTTP Status Codes**
* **2xx (Success):** `200 OK`, `201 Created` (POST success), `204 No Content` (DELETE success).
* **4xx (Client Error):** `400 Bad Request` (Invalid syntax), `401 Unauthorized` (Missing token / Who are you?), `403 Forbidden` (Authenticated but lacking permissions), `404 Not Found` (Endpoint doesn't exist).
* **5xx (Server Error):** `500 Internal Server Error` (Backend code crash), `502 Bad Gateway`, `503 Service Unavailable`, `504 Gateway Timeout`.

---

### **5. Isolating Frontend vs. Backend Bugs**
1. Open Browser **Inspect \\(\rightarrow\\) Network Tab** and execute failing action.
2. If API returns `200 OK` with correct JSON data but UI renders wrong \\(\rightarrow\\) **Frontend Bug**.
3. If API returns `500 Server Error` or malformed data \\(\rightarrow\\) Test in **Postman**:
   * Fails in Postman \\(\rightarrow\\) **Backend / Database Bug**.
   * Passes in Postman \\(\rightarrow\\) **Frontend Bug** (UI sends malformed payload).

---

# **Lesson 10: Practical Postman Testing, Variables, Auth, Mock Servers, Swagger, and Newman**

### **1. Postman Variable Scopes**

```
Global Scope ──> Environment Scope ──> Collection Scope ──> Session Scope
```

* **Global:** Visible across all collections in the workspace.
* **Environment:** Tied exclusively to active environment (`staging` vs. `prod`).
* **Collection:** Stored inside a specific collection folder.
* **Session:** Temporary local memory, never saved to cloud or shared.

---

### **2. Postman Scripting & CLI Tools**
* **Pre-request Script:** Runs **before** request execution (e.g., generating dynamic test numbers).
* **Tests Tab (Assertions):** Runs **after** receiving response (e.g., verifying `pm.response.to.have.status(200)`).
* **Swagger (OpenAPI):** Interactive developer API documentation acting as the **Test Basis**.
* **Mock Server:** Fake server simulating API responses for parallel frontend/test development.
* **Newman:** Command-line runner for Postman collections, essential for **CI/CD automated testing**.

---

# **Lesson 11: Database & SQL for Software Testers**

### **1. DDL vs. DML Commands**

```
                                  SQL COMMANDS
                                       │
            ┌──────────────────────────┴──────────────────────────┐
            ▼                                                     ▼
    1. DDL (Data Definition)                              2. DML (Data Manipulation)
 (Defines Table Structure/Schema)                        (Manipulates Row Data)
  • CREATE                                                • SELECT
  • ALTER                                                 • INSERT
  • DROP                                                  • UPDATE
  • TRUNCATE                                              • DELETE
```

---

### **2. Crucial Database Comparisons**

#### **A. UPDATE (DML) vs. ALTER (DDL)**
* **`ALTER`:** Modifies **table structure** (e.g., `ALTER TABLE Users ADD email VARCHAR(100);`).
* **`UPDATE`:** Modifies **row field data** (e.g., `UPDATE Users SET status = 'ACTIVE' WHERE user_id = 5;`).

#### **B. DELETE vs. TRUNCATE vs. DROP**

| Feature | DELETE | TRUNCATE | DROP |
| :--- | :--- | :--- | :--- |
| **Command Type** | **DML** | **DDL** | **DDL** |
| **What It Removes** | Specific matching rows. | **ALL rows** instantly. | **Entire table structure AND data**. |
| **Schema Remains?** | **YES** | **YES** | **NO** |
| **WHERE Clause?** | **YES** | **NO** | **NO** |
| **Rollback / Speed** | Slower (Rollback possible). | Fast (No rollback). | Instant (No rollback). |

#### **C. WHERE vs. HAVING Clause**
* **`WHERE`:** Filters individual raw rows **before** `GROUP BY` aggregation (Cannot use aggregate functions).
* **`HAVING`:** Filters aggregated summary groups **after** `GROUP BY` runs (Evaluates aggregate functions like `COUNT()`, `SUM()`).

---

### **3. SQL Joins Summary**
* **INNER JOIN:** Matching keys in **both tables**.
* **LEFT JOIN:** All records from left table + matching records from right table.
* **RIGHT JOIN:** All records from right table + matching records from left table.

---

### **4. Classic Interview Query: Find 2nd Highest Salary**
```sql
SELECT MAX(salary) AS SecondHighestSalary
FROM Employees
WHERE salary < (SELECT MAX(salary) FROM Employees);
```

---

# **Master Revision Sheet**

```
1. QA vs. QC              : QA = Process & Prevention | QC = Product & Detection
2. Error / Bug / Failure  : Human Mistake -> Code Bug -> System Failure
3. SDLC Models            : Waterfall (Linear/Late test) | V-Model (Parallel static review) | Agile (Iterative/Sprints)
4. Scrum Ceremonies       : Planning, Refinement, Standup (15m), Review (Demo), Retrospective
5. Verification / Valid.  : Verification = Static (No code run) | Validation = Dynamic (Run build)
6. STLC Phases            : Requirements -> Planning -> Case Dev -> Env Setup -> Execution -> Closure
7. Test Plan vs Strategy  : Plan = Project-level, dynamic | Strategy = Company-level, static
8. Testing Levels         : Unit (Dev) -> Integration (Interfaces) -> System (E2E) -> Acceptance (UAT)
9. Scaffolding            : Stub = Dummy called sub-function | Driver = Dummy calling main function
10. Smoke vs. Sanity      : Smoke = Wide/shallow health check | Sanity = Focused check on bug fix
11. Retest vs. Regression : Retest = Verify bug fix | Regression = Verify unchanged code didn't break
12. Black-Box Design      : EP (Partitions), BVA (Edges), Decision Table (2^n rules), State Transition
13. BVA Formula           : [Min-1, Min, Min+1] and [Max-1, Max, Max+1]
14. Coverage Rule         : 100% Decision Coverage GUARANTEES 100% Statement Coverage
15. Severity vs Priority  : Severity = Technical damage | Priority = Business urgency
16. REST vs SOAP          : REST = JSON, Stateless, Fast | SOAP = XML, Protocol, WS-Security
17. HTTP Methods          : GET (Read/Safe), POST (Create), PUT (Full replace), PATCH (Partial), DELETE
18. HTTP Status Codes     : 200 (OK), 201 (Created), 400 (Bad Data), 401 (Unauth), 403 (Forbidden), 404 (Missing), 500 (Crash)
19. Bug Isolation         : Inspect Network Tab -> 200 OK with UI glitch = Frontend | 500 = Backend/Postman
20. SQL DDL vs DML        : DDL = CREATE, ALTER, DROP, TRUNCATE | DML = SELECT, INSERT, UPDATE, DELETE
21. DELETE / TRUNCATE     : DELETE = Filtered rows (DML) | TRUNCATE = All rows fast (DDL)
22. WHERE vs HAVING       : WHERE = Raw rows before grouping | HAVING = Aggregated groups after GROUP BY
```

---

# **Must-Memorize Technical Comparisons**

| # | Topic 1 | Topic 2 | Core Key Difference |
| :---: | :--- | :--- | :--- |
| **1** | **QA** | **QC** | QA is process-oriented (prevention); QC is product-oriented (detection). |
| **2** | **Verification** | **Validation** | Verification evaluates specs without executing code; Validation executes code build. |
| **3** | **Test Plan** | **Test Strategy** | Test Plan is project-specific and dynamic; Test Strategy is organization-wide and static. |
| **4** | **Stub** | **Driver** | Stub simulates a missing called sub-function; Driver simulates a missing calling controller. |
| **5** | **Smoke Testing** | **Sanity Testing** | Smoke tests broad health on new builds; Sanity tests focused module fixes on updated builds. |
| **6** | **Retesting** | **Regression** | Retesting verifies a specific bug fix; Regression verifies unchanged features didn't break. |
| **7** | **Equivalence Partitioning** | **Boundary Value Analysis** | EP tests representative partition values; BVA tests edge boundary limits where bugs concentrate. |
| **8** | **Statement Coverage** | **Decision Coverage** | Decision coverage tests TRUE/FALSE branches; 100% decision coverage guarantees 100% statement coverage. |
| **9** | **Severity** | **Priority** | Severity measures technical damage depth; Priority measures business fix urgency. |
| **10** | **401 Unauthorized** | **403 Forbidden** | 401 means credentials missing (Unidentified user); 403 means user identified but lacks permissions. |
| **11** | **REST** | **SOAP** | REST is an architectural style using JSON; SOAP is a strict XML protocol. |
| **12** | **PUT** | **PATCH** | PUT replaces the entire resource; PATCH updates only specific specified fields. |
| **13** | **ALTER** | **UPDATE** | ALTER modifies database table schema (DDL); UPDATE modifies row field data (DML). |
| **14** | **DELETE** | **TRUNCATE** | DELETE removes specific rows with WHERE clause; TRUNCATE removes all rows instantly. |
| **15** | **WHERE** | **HAVING** | WHERE filters raw rows before grouping; HAVING filters summary groups after GROUP BY. |

---

# **30 Likely Technical Interview Questions & Model Answers**

#### **1. Why is software testing necessary?**
> Software is built by humans who can make errors due to tight deadlines or complex logic. Testing identifies defects before release, prevents financial loss, ensures requirement compliance, and builds customer trust.

#### **2. What is the difference between QA and QC?**
> QA is process-oriented and focuses on defining standards to prevent defects. QC is product-oriented and focuses on executing tests to identify defects in the software build.

#### **3. Explain Error, Bug, and Failure.**
> An Error is a human mistake made in code or specs. A Bug is the resulting flaw in the software code. A Failure is the visible abnormal behavior or crash observed when executing the software.

#### **4. How does the V-Model improve upon the Waterfall model?**
> Waterfall delays testing until coding completes, making fixes expensive. The V-Model runs static verification activities (reviewing specs/designs) in parallel with development phases, catching bugs early.

#### **5. Explain the main Scrum ceremonies.**
> Sprint Planning (select stories & set goal), Backlog Refinement (clarify & estimate stories), Daily Standup (15-min progress/blocker check), Sprint Review (demo increment to stakeholders), and Sprint Retrospective (internal process review).

#### **6. What is the difference between Verification and Validation?**
> Verification is static testing reviewing specs, designs, and code without executing software ("Are we building the system right?"). Validation is dynamic testing executing the built application ("Are we building the right system?").

#### **7. What are the 6 phases of the STLC?**
> Requirements Analysis, Test Planning, Test Case Development, Test Environment Setup, Test Execution & Defect Reporting, and Test Cycle Closure.

#### **8. What is the difference between a Test Plan and a Test Strategy?**
> A Test Strategy is a high-level, organization-wide static document defining quality standards. A Test Plan is a low-level, project-specific dynamic document detailing schedules, resources, scope, and risks.

#### **9. What is the Requirements Traceability Matrix (RTM)?**
> The RTM is a grid mapping business requirements to test cases and bug IDs to guarantee 100% test coverage and enable impact analysis during requirement changes.

#### **10. Explain the 4 levels of software testing.**
> Unit Testing (isolated code functions by devs), Integration Testing (interface data flows), System Testing (E2E requirements on production-like build), and Acceptance Testing (UAT/release readiness).

#### **11. What is the difference between a Stub and a Driver?**
> A Stub acts as a dummy called sub-function when the top module is ready but lower logic is missing. A Driver acts as a dummy calling module when the lower sub-module is ready but top controllers are missing.

#### **12. What is the difference between Load Testing and Stress Testing?**
> Load Testing evaluates performance under expected normal and peak traffic. Stress Testing pushes the system beyond normal operational limits to find breaking points and observe recovery.

#### **13. Differentiate between Smoke Testing and Sanity Testing.**
> Smoke Testing is a broad, shallow health check on initial builds to verify stability before accepting full testing. Sanity Testing is a focused, deep check on updated builds to verify specific bug fixes.

#### **14. Explain Retesting versus Regression Testing.**
> Retesting re-executes failed test cases to verify that a specific bug was fixed. Regression Testing re-runs existing test suites across unchanged modules to ensure recent code fixes didn't break existing functionality.

#### **15. What is Equivalence Partitioning (EP)?**
> EP is a black-box design technique that divides input data into logical valid/invalid partitions and tests one representative value from each group, assuming all group values behave identically.

#### **16. How do you perform Boundary Value Analysis (BVA)?**
> BVA tests boundary edge limits where bugs concentrate. For a range \\([A, B]\\), test values are \\(A-1, A, A+1\\) and \\(B-1, B, B+1\\).

#### **17. Why does 100% Decision Coverage guarantee 100% Statement Coverage?**
> Decision coverage forces execution of both TRUE and FALSE decision outcomes. By executing all decision branches, every code statement within those branches is guaranteed to run at least once.

#### **18. What field is in a Bug Report but missing from an unexecuted Test Case?**
> The Actual Result (the observed failure), along with screenshots, build number, and assigned developer. An unexecuted test case contains only the Expected Result.

#### **19. What is the difference between Severity and Priority?**
> Severity measures technical damage depth on system function (assigned by tester). Priority measures business urgency and required fix speed (assigned by PO/Lead).

#### **20. Give an example of a Low Severity / High Priority bug.**
> A misspelled brand logo ("VodaFonee") or wrong color scheme on the main landing page. Technical function is unaffected, but brand reputation impact requires an immediate fix.

#### **21. What do you do if a developer rejects your bug as "Not a Bug"?**
> Re-check requirement specs, provide reproduction steps/screenshots/logs, and if specs are ambiguous, escalate to the Product Owner for business clarification.

#### **22. What is an API and where does it sit in software architecture?**
> An API is an interface allowing software components to communicate. It operates in the Application Layer (Business Logic) connecting the Presentation Layer (UI) with the Database Layer.

#### **23. Compare REST and SOAP APIs.**
> REST is a lightweight, stateless architectural style using JSON and HTTP methods. SOAP is a strict, heavyweight XML protocol offering advanced WS-Security for financial transactions.

#### **24. Explain the difference between HTTP PUT and PATCH.**
> PUT performs a full replace/overwrite of a resource (requires sending all fields). PATCH performs a partial update modifying only specified fields.

#### **25. What is the difference between HTTP 401 and 403 status codes?**
> 401 Unauthorized means authentication credentials are missing or invalid (Unidentified user). 403 Forbidden means the user is authenticated but lacks permission to access the resource.

#### **26. How do you isolate whether a defect is Frontend or Backend?**
> Inspect the browser Network Tab. If the API returns `200 OK` with correct JSON data but UI renders wrong, it is a Frontend bug. If the API returns `500 Server Error`, test in Postman; if it fails in Postman, it is a Backend bug.

#### **27. What is Newman and why is it used?**
> Newman is a command-line runner for Postman collections that executes API test suites headlessly in terminal environments, enabling integration into CI/CD pipelines (e.g., Jenkins).

#### **28. Differentiate between DDL and DML commands in SQL.**
> DDL (Data Definition Language) manages database schemas/structures (`CREATE`, `ALTER`, `DROP`, `TRUNCATE`). DML (Data Manipulation Language) manages individual row data (`SELECT`, `INSERT`, `UPDATE`, `DELETE`).

#### **29. What is the difference between DELETE and TRUNCATE in SQL?**
> DELETE is a DML command that removes specific rows using a `WHERE` clause and can be rolled back. TRUNCATE is a DDL command that instantly removes all rows from a table without deleting table schema.

#### **30. What is the difference between WHERE and HAVING in SQL?**
> WHERE filters raw rows before `GROUP BY` runs and cannot evaluate aggregate functions. HAVING filters aggregated summary groups after `GROUP BY` runs and evaluates aggregate functions (`SUM()`, `COUNT()`).

---

# **Final Self-Assessment Checklist**

Check off each item once you can comfortably explain it out loud in clear English without looking at your notes:

- [ ] **Lesson 1:** Explain QA vs. QC, Error vs. Bug vs. Failure, and why testing is necessary.
- [ ] **Lesson 2:** Explain Waterfall vs. V-Model, Verification vs. Validation, and the 5 Scrum ceremonies.
- [ ] **Lesson 3:** List the 6 STLC phases, Test Plan vs. Test Strategy, and RTM purpose.
- [ ] **Lesson 4:** Describe the 4 testing levels and explain Stubs vs. Drivers with examples.
- [ ] **Lesson 5:** Distinguish Load vs. Stress, Smoke vs. Sanity, and Retesting vs. Regression.
- [ ] **Lesson 6:** Apply EP and BVA formulas, and explain why Decision Coverage \\(\ge\\) Statement Coverage.
- [ ] **Lesson 7:** List mandatory fields of a Test Case and explain Test Condition vs. Scenario vs. Case.
- [ ] **Lesson 8:** Walk through the Bug Life Cycle, Severity vs. Priority matrix, and developer conflict resolution.
- [ ] **Lesson 9:** Explain REST vs. SOAP, HTTP methods (PUT vs PATCH), status codes (401 vs 403), and bug isolation.
- [ ] **Lesson 10:** Explain Postman variable scopes, Pre-request vs. Tests scripts, Swagger, and Newman.
- [ ] **Lesson 11:** Categorize DDL vs. DML, compare DELETE vs TRUNCATE vs DROP, WHERE vs HAVING, and write the 2nd highest salary query.

---

### **Congratulations!**
You have successfully completed your **Vodafone Junior Software Tester Interview Preparation Program**. You now possess a deep, structured understanding of manual testing, STLC, Agile, API testing, SQL, and technical interview strategies. Good luck with your Vodafone interview!
