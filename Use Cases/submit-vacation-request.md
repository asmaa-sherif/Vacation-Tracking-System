## Manage Time Use Case

**Actors:** Employee

**Goal:** The employee wishes to submit a new request for vacation time.

**Preconditions:** 
- The employee is authenticated by the portal framework.
-  Identified as an employee of the company with privileges to manage his or her own vacation time.
  
---

**Main Flow**:
 1. The employee logs into the VTS through the intranet portal.
 2. The VTS shows the employee's current vacation balance and any previous requests.
 3. The employee selects to create a new vacation request.
 4. The employee selects the type of leave they want to use [vacation, personal, sick] and selects dates on a calendar with a posistive balance.
 5. The employee enters the required details, such as start date, end date, title, and a short description.
 6. The employee submits the request.
     - If there are any errors, the system highlights them and asks the employee to fix them.
     - If the request is correct, it is sent for manager approval.
 7. The employee is returned to the VTS home page.
 10. An email is immediately sent to the authorized manager to approve the employee's request.
 11. The request status is updated to "Pending."

---

### Flow Chart

<img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Use%20case%20flow%20chart.png" width="75%" />

---

**Alternative Flows**
- **Withdraw Request**:
   - The employee wants to withdraw an outstanding request for vacation time.
- **Cancel Approved Request**:
   - The employee wants to cancel an approved vacation time request.
- **Edit Pending Request**:
   - The employee wants to edit the description or title of a pending request.

---

### State Diagram

---

### Sequence Diagram

---

### Pseudocode
```plaintext
FUNCTION CreateVacationRequest(employeeID, startDate, endDate, title, description, categoryID):

    // Step 1: Authentication Check
    IF NOT IsAuthenticated(employeeID) THEN
        RETURN "Error: User not authenticated"
    END IF
    
    // Step 2: Check Employee's Available Vacation Balance
    balance = CheckVacationBalance(request.employeeID, request.categoryID)
    
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
        "status": "Pending",  
        "categoryID": categoryID
    })

    // Step 6: Notify the manager about the new vacation request for approval
    NotifyManager(employeeID, requestID)

    // Step 7: Return a success message
    RETURN "Vacation request submitted successfully"
END FUNCTION

```
