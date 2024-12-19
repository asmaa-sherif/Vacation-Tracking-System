## Withdraw a Pending Vacation Request

**Actors:** Employee

**Goal:** The employee wants to withdraw an outstanding request for vacation time.

**Preconditions:** 
- The employee is authenticated by the portal framework.
- Identified as an employee of the company with privileges to manage his or her own vacation time.
  
---

**Main Flow**:
 1. The employee logs into the VTS through the intranet portal.
 2. The VTS shows the employee's current vacation balance and any previous requests.
 3. The employee selects a pending vacation time request.
 4. The system prompts the employee to confirm the withdrawal of the selected request.
 5.  The pending request is removed from the manager's approval queue.
 6.  An email notification is sent to the manager informing them of the withdrawal.
 7.  The request status is updated to "Withdrawn."
 8. The employee is returned to the VTS home page.
 7. The displayed summaries are updated to reflect the changes in the employee's vacation time balance and request status.

**Alternative Flows:**

- _Unauthorized Access:_ If the employee is not authenticated or authorized, access to the VTS is denied.

- _Request Not Found:_ If the selected request is not found or invalid, an error message is displayed.

- _System Error:_ If a system error occurs during the withdrawal process, an error message is displayed, and the user is notified.

**Postconditions:**

- The selected vacation time request is withdrawn.

- The employee's manager is notified of the withdrawal via email.

---

### Flow Chart

  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Withdraw%20request%20flow%20chart.png" width="75%" />

---

### State Diagram

---

### Sequence Diagram

---

### Pseudocode
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
