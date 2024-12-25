# Vacation-Tracking-System

The Vacation System Idea is presented in [The Object Oriented Analysis And Design textbook, 3rd edition](https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Object_Oriented_Analysis_and_Design_with_Applications_3rd_Edition.pdf). I worked on designing the system workflow and defining its use cases in detail, including Flow Diagrams, Sequence Diagrams, and ERD diagrams.

---

## Table of Contents
- [Overview](#overview)
   - [Domain](#domain)
   - [Vision](#vision)
   - [Goals](#goals)
   - [Functional Requirements](#functional-requirements)
   - [Non-Functional Requirements](#non-functional-requirements)
   - [Constraints](#constraints)
   - [Assumptions](#assumptions)
   - [Use Cases](#use-cases)
   - [Actors](#actors)
   - [Flow Diagram](#flow-diagram)
   - [Alternative Use Cases](#alternative-use-cases)
- [Sequence Diagram](#sequence-diagram)
- [Data Model](#data-model)
- [UI](#ui)
- [Tools Used](#tools-used)

---

## Overview

### Domain
Managers struggle to effectively manage and stay aware of their employees' vacation schedules.

---


### Vision
A Vacation Tracking System (VTS) will provide individual employees with the capability to manage their own vacation time, sick leave, and personal time off,
without having to be an expert in company policy or the local facility’s leave policies.

---

### Goals
Give individual employees the capability and responsibility to manage this particular aspect of their employment agreements with the company.
1. Empower employees to manage leave requests independently.
2. Reduce HR and managerial workloads.
3. Deliver an easy to use, intuitive, and intelligent system.

---

### Functional Requirements
**Employee**:
   - Can validate, verify, and manage leave requests.
   - Can edit or withdraw pending requests and cancel approved request.
   - Can access to requests for the previous calendar year,and allows requests to be made up to a year and a half in the future.
     
**Manager Approval**:
   - Enable flexible approval settings.
   - Award personal leave time.
     
**HR Clerk**:
   - Enable override all actions restricted by rules, with logging of those overrides.
     
**System Administrators**:
   - Maintain system logs and ensure smooth technical operations.
     
**Notifications**:
   - Notify managers about request updates.
   - Notify employees of request status changes.
     
**Integration**:
   - Using the portal’s single-sign-on mechanisms for all authentication.
   - Intergrate HR department legacy systems to retrieve required employee information and changes.
   
**Activity Logs**:
   - Maintain detailed audit logs.

---

### Non-Functional Requirements
**Scalability**: Support future growth.
     
**Security**: Ensure data privacy and secure authentication.
     
**Usability**: Provide an intuitive and easy to use interface.
     
**Auditability**: Log all actions for tracking purposes.

---

### Constraints
- Must integrate with current systems (intranet portal, HR legacy).
- Comply with legal and privacy regulations.
- The system uses existing intranet hardware and middleware.

---

### Assumptions
- Accurate data from HR systems.
- Employees have internet and single-sign-on access.
- Company policies are pre-defined and integrated.

---

## Use Cases
- [x] Manage Time [create new Request, Edit pending request, withdraw request, cancel Approved Request]
- [ ] Approve Request [Managers review and respond to leave requests]
- [ ] Award Time [Managers grant additional leave time within limits]
- [ ] Edit Employee Record [HR clerks modify employee details, allowances, or leave rules]
- [ ] Manage Locations [HR clerks handle location-specific policies and restrictions]
- [ ] Manage Leave categories [HR clerks manage leave types and associated rules]
- [ ] Override Leave records [HR clerks override automated decisions while maintaining logs]
- [ ] Backup system Logs [Administrators archive system transaction logs]

---

<img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Use%20Case%20Model.png" width="85%" />

---

### Actors
**_Employee_**
   - Manage vacation requests.
   - Submits, withdraws, or edits vacation requests.
     
**_Manager_**
   - Approve/refuse requests.
   - Award additional leave.

**_HR Clerk_**
   - Manages employee records, rules, and overrides.
   - Ensures the system reflects updated policies.
     
**_System Admin_**
   - Manages technical resources, backups, and logs.
---

### Flow Diagram

<img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Screenshot%202024-12-18%20at%2018.46.12.png" width="85%"/>

 ---
 
### Alternative Use Cases
- [Manage vacation time](https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Use%20Cases/submit-vacation-request.md)
- [Edit Pending Vacation time request](https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Use%20Cases/Edit-vacation-request.md)
- [Cancel vacation request](https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Use%20Cases/cancel-vacation-request.md)
- [Withdraw pending vacation time request](https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Use%20Cases/withdraw-vacation-request.md)

---

### Sequence Diagram
| <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Sequence%20diagram.png" width="85%" />
| --------------------------------------------------------------- |
| **Sequence Diagram** |

---

## Data Model

| <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/ERD.png"  width="85%" />|
| --------------------------------------------------------------- |
| **Entity-Relationship Diagram**|



---

## UI

---


## Tools Used
- [Visual Studio Code](https://code.visualstudio.com/)
- [Plant UML](https://plantuml.com/)
- [ExcaliDraw](https://excalidraw.com/)
- [DB Diagram](https://dbdiagram.io/home).


