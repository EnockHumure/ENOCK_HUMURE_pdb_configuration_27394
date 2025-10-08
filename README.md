# ENOCK_HUMURE_pdb_configuration_27394
assignment 2 about the pdb configuration 

# Oracle Database Assignment: PDB Management & OEM Configuration

## Table of Contents
- [Student Information](#student-information)
- [Assignment Overview](#assignment-overview)
- [Task 1: Primary PDB Creation](#task-1-primary-pdb-creation)
- [Task 2: PDB Lifecycle Management](#task-2-pdb-lifecycle-management)
- [Task 3: Oracle Enterprise Manager](#task-3-oracle-enterprise-manager)
- [Technical Implementation](#technical-implementation)
- [Challenge Resolution](#challenge-resolution)
- [References Learnings](#References)

## Student Information

| Detail | Information |
|--------|-------------|
| **Full Name** | Enock Humure|
| **Student ID** | 27394 |
| **GROUP** | C |
| **Course** | Database Development with PL/SQL |
| **Instructor** | Eric Maniraguha |
| **Submission Date** | [08/october/2025] |

## Assignment Overview

This assignment demonstrates practical database administration skills through:

- **PDB Creation** - Establishing dedicated database environment for coursework
- **Database Lifecycle Management** - Demonstrating creation and deletion operations  
- **OEM Configuration** - Setting up enterprise management tools
- **Troubleshooting** - Resolving common database administration challenges

## Task 1: Primary PDB Creation

### Objective
Create a permanent pluggable database to host all coursework materials and assignments.

**Database Configuration:**
- **PDB Name:** `en_pdb_27394`
- **Administrative User:** `enock_plsqlauca_27394`
- **Access Level:** READ WRITE with auto-start enabled
- **Purpose:** Primary database for PL/SQL coursework

### Implementation Evidence
#### Primary PDB Setup

**SYSDBA Connection Establishment**  
Database Connection]<img width="771" height="415" alt="PICTURE ONE" src="https://github.com/user-attachments/assets/a55782ba-0e9e-4c4f-8c67-fd6e12c31d59" />
*Initial connection with SYSDBA privileges*

```sql
    CREATE PLUGGABLE DATABASE en_pdb_27394
  2  ADMIN USER enock_plsqlauca_27394 IDENTIFIED BY enock
  3  FILE_NAME_CONVERT =('C:\dbms_oracle\oradata\XE\pdbseed\', 'C:\dbms_oracle\oradata\XE\XEPDB1');

```sql
```
**PDB Creation Execution**  
PDB Creation<img width="1138" height="112" alt="create pluggable database" src="https://github.com/user-attachments/assets/3e4fc7d1-7988-4e59-9ef3-924b64dbe60e" />
*Successful creation of en_pdb_27394 with admin user*
```sql
 SHOW PDBS;
```sql
```
**User Account Setup**  
User Creation 
<img width="1086" height="192" alt="SHOW DELETED TABLE" src="https://github.com/user-attachments/assets/7c100761-825e-4602-921c-2c2f4b1e6e6f" />
  
*Administrative user enock_plsqlauca_27394 configured*
*Confirmation of PDB in READ WRITE mode*


## Task 2: PDB Lifecycle Management

### Objective
Showcase complete database lifecycle management through creation and controlled deletion of a temporary PDB.

**Temporary Database Details:**
- **PDB Name:** `en_to_delete_pdb_27394`
- **Lifecycle Phases:** Creation → Activation → Deactivation → Permanent Removal
- **Data Management:** Complete datafile cleanup included

### Process Documentation

**Temporary PDB Creation**  
*Creation of temporary database en_to_delete_pdb_27394*
```sql
CREATE PLUGGABLE DATABASE en_to_delete_pdb_27394
  2  ADMIN USER temp IDENTIFIED BY enock1
  3  FILE_NAME_CONVERT = ('C:\dbms_oracle\oradata\XE\pdbseed\','C:\dbms_oracle\oradata\XE\en_to_delete_pdb_27394\');
```sql
```

Temp PDB-delete-table Creation
<img width="1261" height="147" alt="CREATING THE DELETED TABLE" src="https://github.com/user-attachments/assets/0da8d691-09cc-40e9-8c6d-b03ca09171a9" />

**Database Deletion Confirmation**  

PDB Deletion
<img width="897" height="290" alt="DROPIG DELETE TABLE" src="https://github.com/user-attachments/assets/20e0d425-9df2-4f23-945b-f9ca2bd02cb0" />

*Successful deletion with datafile removal*

```sql
SHOW PDBS;
DROP PLUGGABLE DATABASE en_to_delete_pdb_27394 INCLUDING DATAFILES;
```sql
```


## Task 3: Oracle Enterprise Manager

### Objective
Configure and validate Oracle Enterprise Manager for comprehensive database monitoring and administration.

**OEM Configuration:**
- **HTTP Access Port:** 8080
- **Secure HTTPS Port:** 8443  
- **Management Console:** https://localhost:8443/em
- **User Session:** enock_plsqlauca_27394

### Configuration Evidence
```sql
 BEGIN
  2       DBMS_XDB_CONFIG.SETHTTPPORT(8080);
  3       DBMS_XDB_CONFIG.SETHTTPSPORT(8443);
  4  END;
  5  /
```sql
```

**Port Configuration**  
Port Setup
HTTP Port: 8080
HTTPS Port: 8443
HERE YOU CAN ACCESS URL:https://localhost:8443/em
<img width="927" height="443" alt="OEM CONFIFURATION" src="https://github.com/user-attachments/assets/0d76ed8c-7bbf-4028-9297-01948a8b0973" />

*HTTP and HTTPS port configuration*

**OEM Login Interface**  
*Enterprise Manager login screen*

OEM Login
<img width="1296" height="612" alt="login in oracle database" src="https://github.com/user-attachments/assets/957cad6c-1d5c-47cb-b774-e45c2dad78c5" />
 
**Management Dashboard**  
*OEM dashboard showing user session and database status*

Dashboard Overview
<img width="1303" height="645" alt="OEM dashboard" src="https://github.com/user-attachments/assets/209ffd0f-b5f3-4478-85c8-544025304829" />


### technical-implementation

- **Database Version:** Oracle 21c Express Edition
- **Container Database:** ORACLE21CDB
- **Platform:** Windows
- **Administrative Access:** SYSDBA privileges
- **Management Tools:** SQL*Plus, Oracle Enterprise Manager

###  challenge-resolution

- **Always check PDB status before opening to avoid errors
- **FILE_NAME_CONVERT parameter is required when creating from pdbseed
- **Using SAVE STATE ensures PDB opens automatically after database restarts
- **OEM setup was straightforward once ports were properly configured
  
 ### References
 
- ** Oracle Database 21c Documentation
- ** Course Lecture: "Introduction to PL/SQL"
- ** Course Lecture: "Oracle Database Environment (CDBs & PDBs) & OEM"
