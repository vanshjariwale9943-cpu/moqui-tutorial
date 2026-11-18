# Moqui Training (Hotwax Module 0)

This repository contains a complete setup of the Moqui Framework connected to MySQL for backend application development. It is used as a foundation for learning and building enterprise applications like Order Management Systems (OMS) and ERP using Moqui at Hotwax.

## 📚 What is Moqui?

Moqui is an open source enterprise framework for building robust backend systems. It provides tools for entity modeling, service , UI screens, and integration, making it ideal for rapid enterprise application development.

## 🎯 Goals of This Module

- Understand how Moqui is installed
- Learn how a database is connected
- Explore runtime and component structure
- See how enterprise systems start from a backend engine

---

## 🛠 Prerequisites

Before starting, ensure you have the following installed:

- **Java 11 (JDK 11)**
- **Git**
- **MySQL 8**
- **MySQL Connector/J (JDBC Driver)**
- **IntelliJ IDEA** (optional but recommended)

---

## 🚀 Getting Started

### 1. Clone Moqui Framework

Moqui is cloned locally and run like a backend server:

```sh
git clone -b master https://github.com/moqui/moqui-framework.git
cd moqui-framework
```

### 2. Initialize Moqui Runtime

```sh
./gradlew getRuntime
```

This creates: `moqui-framework/runtime`

### 3. Create Custom Component

Create your custom component inside:

```
runtime/component/moqui-training
```

Follow the standard Moqui component structure (see below).

### 4. MySQL Database Setup

Run the following SQL in MySQL:

```sql
CREATE DATABASE moqui CHARACTER SET utf8;
CREATE USER 'moqui'@'localhost' IDENTIFIED BY '@12345abC';
GRANT ALL PRIVILEGES ON moqui.* TO 'moqui'@'localhost';
FLUSH PRIVILEGES;
```

### 5. Add JDBC Driver

Download MySQL Connector/J and place the JAR file in:

```
runtime/lib
```

This provides the driver class: `com.mysql.cj.jdbc.Driver`

### 6. Configure Moqui to Use MySQL

Edit `runtime/conf/MoquiDevConf.xml` and set:

```xml
<default-property name="entity_ds_db_conf" value="mysql8"/>
<default-property name="entity_ds_host" value="127.0.0.1"/>
<default-property name="entity_ds_database" value="moqui"/>
<default-property name="entity_ds_user" value="moqui"/>
<default-property name="entity_ds_password" value="@12345abC"/>
```

### 7. Load Data into MySQL

```sh
./gradlew load
```

### 8. Run Moqui Server

```sh
./gradlew run
```

### 9. Login

Open [http://localhost:8080](http://localhost:8080) in your browser.
Login with:

- **Username:** john.doe
- **Password:** moqui

---

## 🏗 Project Structure

- `component.xml` – Component descriptor
- `MoquiConf.xml` – Component configuration
- `entity/` – Entity definitions and data
  - `TutorialEntities.xml` – Entity definitions
  - `data/` – Sample/setup data
    - `TutorialDemoData.xml`, `TutorialSetupData.xml`
- `screen/` – UI screen definitions
  - `Tutorial.xml`, `tutorial/FindTutorial.xml`
- `service/` – Service logic
  - `tutorial/TutorialServices.xml`

---

## ℹ️ Additional Information

### CHARACTER SET utf8

- **Why use UTF-8?** Supports a wide range of characters for internationalization.
- **Impact:** Allows Unicode data storage and retrieval.
- **Other options:** `latin1`, `utf8mb4` (recommended for full Unicode support).

### JDBC Driver

- **Purpose:** Connects Java applications to databases.
- **Example:** `Class.forName("com.mysql.cj.jdbc.Driver");`

### IP Address and Hostname

- **Find your IP:**
  - Windows: `ipconfig`
  - Linux/Mac: `ifconfig` or `ip a`
- **entity_ds_host:** Specifies the database host (e.g., `127.0.0.1` for local).
- **127.0.0.1 vs localhost:** Both refer to the local machine; `localhost` resolves to `127.0.0.1` via DNS.

---

## ✅ Assignment Submission

- Push new data files and configuration changes to your repository.
- Ensure the repository includes:
  - Updated `MoquiDevConf.xml` with database configs
  - A README file explaining your setup process

---

## 👤 Author

Shivam Tripathi
