# Vacation-Tracking-System

The Vacation System Idea is presented in [The Object Oriented Analysis And Design textbook, 3rd edition](https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Object_Oriented_Analysis_and_Design_with_Applications_3rd_Edition.pdf). I worked on designing the system workflow and defining its use cases in detail, including Flow Diagrams, Sequence Diagrams, and ERD diagrams.

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
> The system has the potential to save time and money mostly in the HR department.
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
 1. The employee logs into the VTS through the company portal.
 2. The VTS shows the employee's current vacation balance and any previous requests.
 3. The employee chooses to create a new vacation request.
 4. The employee selects the type of leave they want to use [Vacation, personal, sick] and selects dates on a calendar.
 5. The employee enters the required details, such as start date, end date, title, and a short description.
 6. The employee submits the request.
 7. If there are any errors, the system highlights them and asks the employee to fix them.
 8. If the request is correct, it is sent for manager approval.
 9. The employee is returned to the VTS home page.
 10. An email is immediately sent to the authorized manager to approve the employee's request.
 11. The request status is updated to "Pending."
 12. The manager responds to the email by clicking on a link to approve or reject the request.

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
| **Sequence Diagram** |

---

## Database Design

| <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Database%20Diagrams/ERD%20Diagram.png" width="75%" />|
| --------------------------------------------------------------- |
| **Entity-Relationship Diagram**|

| <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Database%20Diagrams/Entities.png" width="75%" />|
| --------------------------------------------------------------- |
| **Entities Diagram** |

---

## Pseudocode

### **Vacation Request**

#### **Create Vacation Request**
```plaintext
FUNCTION CreateVacationRequest(employeeID, startDate, endDate, title, description, categoryID):

    // Step 1: Authentication Check
    IF NOT IsAuthenticated(employeeID) THEN
        RETURN "Error: User not authenticated"
    END IF
    
    // Step 2: Check Employee's Available Vacation Balance
    balance = CheckVacationBalance(employeeID, categoryID)
    
    // Step 3: Validate if the employee has sufficient balance for the request
    IF balance < CalculateDays(startDate, endDate) THEN
        RETURN "Error: Insufficient balance"
    END IF

    // Step 4: Generate a unique Request ID for the new vacation request
    requestID = GenerateNewRequestID()

    // Step 5: Save the new vacation request to the database
    SaveToDatabase("VacationRequest", {
        "requestID": requestID,
        "employeeID": employeeID,
        "startDate": startDate,
        "endDate": endDate,
        "title": title,
        "description": description,
        "status": "Pending",  // Initially, status is "Pending"
        "categoryID": categoryID
    })

    // Step 6: Notify the manager about the new vacation request for approval
    NotifyManager(employeeID, requestID)

    // Step 7: Return a success message
    RETURN "Vacation request submitted successfully"
END FUNCTION

```
#### **Edit a Pending Vacation Request**
```plaintext
FUNCTION EditVacationRequest(requestID, newStartDate, newEndDate, newTitle, newDescription):

    // Step 1: Retrieve the current request details
    currentRequest = GetRequestFromDatabase(requestID)
    IF currentRequest.status != "Pending" THEN
        RETURN "Error: Only pending requests can be edited"
    END IF

    // Step 2: Check for sufficient vacation balance after the new dates
    balance = CheckVacationBalance(currentRequest.employeeID, currentRequest.categoryID)
    IF balance < CalculateDays(newStartDate, newEndDate) THEN
        RETURN "Error: Insufficient balance"
    END IF

    // Step 3: Update the request with new details
    currentRequest.startDate = newStartDate
    currentRequest.endDate = newEndDate
    currentRequest.title = newTitle
    currentRequest.description = newDescription

    // Step 4: Save the updated request to the database
    SaveToDatabase("VacationRequest", currentRequest)

    // Step 5: Notify the manager about the edit
    NotifyManager(currentRequest.employeeID, requestID)

    // Step 6: Return a success message
    RETURN "Vacation request updated successfully"
END FUNCTION
```

#### **Cancel an Approved Vacation Request**
```plaintext
FUNCTION CancelVacationRequest(requestID):

    // Step 1: Retrieve the current request details
    currentRequest = GetRequestFromDatabase(requestID)
    IF currentRequest.status != "Approved" THEN
        RETURN "Error: Only approved requests can be canceled"
    END IF

    // Step 2: Restore the employee's vacation balance
    balanceRestored = RestoreVacationBalance(currentRequest.employeeID, currentRequest.categoryID, CalculateDays(currentRequest.startDate, currentRequest.endDate))

    // Step 3: Update request status to "Canceled"
    currentRequest.status = "Canceled"
    
    // Step 4: Save the updated request to the database
    SaveToDatabase("VacationRequest", currentRequest)

    // Step 5: Notify the manager about the cancellation
    NotifyManager(currentRequest.employeeID, requestID)

    // Step 6: Return a success message
    RETURN "Vacation request canceled and balance restored"
END FUNCTION
```
#### **Withdraw Pending Vacation Request**
```plaintext
FUNCTION WithdrawVacationRequest(requestID):

    // Step 1: Retrieve the current request details
    currentRequest = GetRequestFromDatabase(requestID)
    IF currentRequest.status != "Pending" THEN
        RETURN "Error: Only pending requests can be withdrawn"
    END IF

    // Step 2: Update request status to "Withdrawn"
    currentRequest.status = "Withdrawn"
    
    // Step 3: Save the updated request to the database
    SaveToDatabase("VacationRequest", currentRequest)

    // Step 4: Notify the manager about the withdrawal
    NotifyManager(currentRequest.employeeID, requestID)

    // Step 5: Return a success message
    RETURN "Vacation request withdrawn successfully"
END FUNCTION

```

## Tools Used
- [Visual Studio Code](https://code.visualstudio.com/)
- [Plant UML](https://plantuml.com/)
- [ExcaliDraw](https://excalidraw.com/)
- [DB Diagram](https://dbdiagram.io/home).


