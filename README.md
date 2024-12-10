# Vacation-Tracking-System

The Vacation System Idea is presented in <a href="https://www.oreilly.com/library/view/object-oriented-analysis-and/9780201895513/" style="text-decoration:none; font-weight:bold;">The Object Oriented Analysis And Design textbook, 3rd edition.</a> I worked on designing the system workflow and defining its use cases in detail including Flow diagrams, Sequence diagram, and ERD diagrams.

---

## Table of Contents
1. [Requirements](#requirements)
   - [Vision](#vision)
   - [Goals](#goals)
   - [Functional Requirements](#functional-requirements)
   - [Non-Functional Requirements](#non-functional-requirements)
   - [Constraints](#constraints)
   - [Assumptions](#assumptions)
2. [Use Cases](#use-cases)
   - [Manage Time Use Case](#manage-time-use-case)
     - [Main Flow](#main-flow)
     - [Alternative Flows](#alternative-flows)
     - [Flow Diagrams](#flow-diagrams)
     - [Sequence Diagram](#sequence-diagram)
     - [Database Design](#database-design)
     - [PseudoCode](#pseudocode)
3. [Tools Used](#tools-used)

---

## Requirements

### Vision
> Provide an intuitive platform for managing vacation, sick leave, and personal time off, minimizing HR involvement.

### Goals
> The system has the potential to save time and money mostly in the HR department
1. Empower employees to manage leave requests independently.
2. Reduce HR and managerial workloads.
3. Deliver a user-friendly, efficient system.

### Functional Requirements
1. **Request Management**: Validate, verify, and manage leave requests.
2. **Manager Approval**: Enable flexible approval settings.
3. **Historical Access**: Allow access to past and future requests.
4. **Notifications**: Notify employees and managers about request updates.
5. **Integration**: Interface with existing systems and support SSO.
6. **Activity Logs**: Maintain detailed audit logs.
7. **HR/Admin Control**: Enable override and personal leave management.

### Non-Functional Requirements
1. **Performance**: Handle high traffic efficiently.
2. **Scalability**: Support future growth.
3. **Security**: Ensure data privacy and secure authentication.
4. **Usability**: Provide an intuitive interface.
5. **Availability**: Offer 24/7 access with minimal downtime.
6. **Auditability**: Log all actions for tracking purposes.

### Constraints
1. Must integrate with current systems (intranet, HR legacy).
2. Comply with legal and privacy regulations.

### Assumptions
1. Accurate data from HR systems.
2. Employees have internet and SSO access.
3. Company policies are pre-defined and integrated.

---

## Use Cases
- [x] Manage Time [create new Request, Edit pending request, withdraw request, cancel Approved Request]
- [ ] Award Time
- [ ] Edit Employee Record
- [ ] Manage Locations
- [ ] Manage Leave categories
- [ ] Override Leave records
- [ ] Backup system Logs

### Actors
1. **Employee**: Manage vacation requests.
2. **Manager**: Approve/refuse requests, award time.
3. **HR Clerk**: Edit records, manage categories.
4. **System Admin**: Backup logs.

---

### Manage Time Use Case

#### Main Flow
 1. The employee login to the VTS through the company portal.
 2. The VTS shows the employee's current vacation balance and any pervious request.
 3. The employee chooses to create new vacation request.
 4. The employee selects the type of leave they want to use [Vacation, personal, sick] and selects date on a calender.
 5. The employee enters the required details, such as start date, end date, title, short description.
 6. The employee submits the request.
 7. If there are any errors, the system highlights them and asks the employee to fix them.
 8. If the request is correct, it is sent for manager approval.
 9. The employee is returned to the VTS home page.
 10. an email is immediately sent to authorized manager to approve the employee's request.
 11. The request status should be update to "Pending".
 12. The manager reponds to the email by clicking on a link 

#### Alternative Flows
1. **Withdraw Request**: Remove pending request, notify the manager.
2. **Cancel Approved Request**: Restore vacation balance, notify the manager.
3. **Edit Pending Request**: Update details, validate changes.

---

### Flow Diagrams

#### Main Flow
<img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Use%20case%20flow%20chart.png" width="75%" />

#### Alternative Flows
<p float="left">
  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Withdraw%20request%20flow%20chart.png" width="30%" />
  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Cancel%20request%20flow%20chart.png" width="30%" />
  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Edit%20request%20flow%20chart.png" width="30%" />
</p>

---

### Sequence Diagram
| <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Sequence%20diagram.png" width="100%" />
| --------------------------------------------------------------- |
|**Sequence Diagram**|

---

## Database Design

| <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Database%20Diagrams/ERD%20Diagram.png" width="75%" />|
| --------------------------------------------------------------- |
|**Entity-Relationship Diagram**|

| <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Database%20Diagrams/Entities.png" width="75%" />|
| --------------------------------------------------------------- |
|**Entities Diagram**|

---

## PseudoCode

### Vacation Request
1. Check employee balance and input validity.
2. Submit request for manager approval.

<p float="left">
  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/pseudocode/Vacation%20Request.png" width="75%" />
</p>

### Other Operations
1. **Withdraw Request**: Remove request, notify the manager.
2. **Cancel Request**: Restore balance, notify the manager.
3. **Edit Request**: Validate and update details.

<p float="left">
  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/pseudocode/Withdraw%20Request.png" width="30%" />
  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/pseudocode/Cancel%20Request%20.png" width="30%" />
  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/pseudocode/Edit%20Request.png" width="30%" />
</p>

---

## Tools Used
- [Visual Studio Code](https://code.visualstudio.com/)
- [Plant UML](https://plantuml.com/)
- [ExcaliDraw](https://excalidraw.com/)
- [DB Diagram](https://dbdiagram.io/home)
