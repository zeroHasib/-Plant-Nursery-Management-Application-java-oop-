# Plant Nursery Management Application 🌿

[![Java Version](https://shields.io)](https://oracle.com)
[![Database](https://shields.io)](https://mysql.com)
[![Design Pattern](https://shields.io)]()

A clean, modular Desktop Management Application built using **Java Swing** and **MySQL** to automate nursery business operations. The application provides an administrative dashboard to manage plant inventory, track stock levels, and perform live data updates securely.

---

## 📌 Project Features

- **Inventory Dashboard:** A visual interface to view the live status of all available plants.
- **Full CRUD Support:** Complete control to Add, View, Update, and Delete plant profiles seamlessly.
- **Enterprise Design Patterns:** Structured strictly using **MVC** (Model-View-Controller) separation and **DAO** (Data Access Object) data extraction abstraction layers.
- **Secure Persistence:** Connected to a relational MySQL backend using safe JDBC state execution.

---

##  System Architecture & File Structure

The project code is decouple-designed into logical layers to isolate visual elements from database query executions:

```text
PlantNurseryApp/
├── lib/
│   └── mysql-connector-j-26.7.0.jar      # JDBC communication driver
├── src/
│   ├── plantnurseryapp/
│   │   └── PlantNurseryApp.java          # Application main entry point
│   ├── database/
│   │   └── DatabaseConnection.java       # Handles session connections with MySQL
│   ├── model/
│   │   └── Plant.java                    # Encapsulated Data Model Class (POJO)
│   ├── dao/
│   │   └── PlantDAO.java                 # Centralized CRUD SQL execution handler
│   └── view/
│       └── DashboardFrame.java           # Graphical User Interface (Java Swing View)
```

---

## ⚙️ Component Breakdown

### 1. Database Connection (`DatabaseConnection.java`)
Manages the live session handshake protocols. It safely utilizes the JDBC `DriverManager` class to instantiate active pipelines to the target MySQL schema via structural connection pooling properties.

### 2. Plant Entity (`Plant.java`)
The structural business entity module encapsulating data variables. It maps database entity keys directly into object-oriented states (`plantId`, `name`, `price`, `quantity`) utilizing getter and setter wrappers.

### 3. Data Control Engine (`PlantDAO.java`)
Isolated script center processing parameterized transactions. It decouples UI frames by executing independent structural SQL queries (`INSERT`, `SELECT`, `UPDATE`, `DELETE`).

### 4. Visual Interface (`DashboardFrame.java`)
The window rendering the data landscape. Built explicitly via native Java AWT and Swing platforms to output scalable data tables alongside administrative action controls.

---

## System Execution Pipeline

```text
 [PlantNurseryApp (Main)] ──> Launches ──> [DashboardFrame (GUI Window)]
                                                    │
                                             Requests Rows
                                                    │
                                                    ▼
 [Database Server (MySQL)] <── SQL Exec <──  [PlantDAO (SQL Layer)]
            │
      Returns ResultSet
            │
            ▼
 [Mapped to Array of Plant Objects] ──> Populates ──> [UI Active Table Display]
```

1. **Bootstrapping:** The user fires the runtime architecture using `PlantNurseryApp.java`.
2. **Session Mapping:** The core system calls `DatabaseConnection.java` to secure a runtime environment communication bridge to the local MySQL server daemon.
3. **Execution Mapping:** When the UI requests historical or live parameters, `DashboardFrame` initializes a request callback targeting the encapsulated `PlantDAO` instance.
4. **Data Delivery:** `PlantDAO` queries the engine table, parses database entries into structured objects, and drops the generated list straight onto the user screen data table grid.

---

##  How to Setup and Run

### Prerequisites
- **Java Development Kit (JDK 8 or higher)** installed.
- **MySQL Server** installed and running on your system.

### Configuration Steps
1. **Database Setup:** Open your MySQL workbench/terminal and create a new schema:
   ```sql
   CREATE DATABASE plant_nursery;
   USE plant_nursery;

   CREATE TABLE plants (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(100) NOT NULL,
       price DOUBLE NOT NULL,
       quantity INT NOT NULL
   );
   ```
2. **Clone the Repository:**
   ```bash
   git clone https://github.com
   ```
3. **Environment Setup:** Ensure that `lib/mysql-connector-j-26.7.0.jar` is correctly added to your IDE project **Classpath / Build Path** dependencies.
4. **Run Application:** Execute the `PlantNurseryApp.java` class to initialize the system dashboard interface.

