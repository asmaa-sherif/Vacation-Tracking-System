## Cancel Vacation Request

**Actors:** Employee

**Goal:** The employee wants to cancel an approved vacation time request.

**Preconditions:** 
- The employee is authenticated by the portal framework.
- Identified as an employee of the company with privileges to manage his or her own vacation time.
  
---

**Main Flow**:
 1. The employee logs into the VTS through the intranet portal.
 2. The VTS shows the employee's current vacation balance and any previous requests.
 3. The employee selects an approved request that is either future-dated or within the past 5 business days for cancellation.
 4. The system prompts the employee to confirm the cancellation.
 5. An email notification is sent to the employee's manager.
 6. The request status is updated to "Canceled."
 9. The employee is returned to the VTS home page.
 7. The displayed summaries are updated to reflect the changes in the employee's vacation time balance and request status.

---

**Alternative Flows:**

- _Unauthorized Access:_ If the employee is not authenticated or authorized, access to the VTS is denied.

- _Request Not Found:_ If the selected request is not found or invalid, an error message is displayed.

- _System Error:_ If a system error occurs during the cancellation process, an error message is displayed, and the user is notified.

**Postconditions:**

- The selected vacation time request is canceled.

- The employee's vacation time balance is updated to reflect the cancellation.

- The employee's manager is notified of the cancellation via email.


### Flow Chart

  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Cancel%20request%20flow%20chart.png" width="75%" />

---

### State Diagram

---

### Sequence Diagram

---

### Pseudocode
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
