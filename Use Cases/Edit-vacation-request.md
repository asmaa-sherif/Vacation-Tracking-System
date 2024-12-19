## Edit a Pending Vacation Request

**Actors:** Employee

**Goal:** The employee wants to edit the description or title of a pending request.

**Preconditions:** 
- The employee is authenticated by the portal framework.
- Identified as an employee of the company with privileges to manage his or her own vacation time.
  
---

**Main Flow**:
 1. The employee logs into the VTS through the intranet portal.
 2. The VTS shows the employee's current vacation balance and any previous requests.
 3. The employee selects to edit a pending vacation request.
 4. The VTS displays an editable view of the selected request, allowing the employee to modify:
    - Request title
    - Request description
    - Start and end dates
    - Time off type
    - Submit Changes
 5. The employee submits the request.
     - If there are any errors, the system highlights them and asks the employee to fix them.
     - If the request is correct,the system validates the changes and updates the pending request.
 6. The employee is returned to the VTS home page.
 7. The displayed summaries are updated to reflect the changes in the employee's vacation time balance and request status.



**Alternative Flows:**

_Unauthorized Access:_

- If the employee is not authenticated or authorized, access to the VTS is denied.

_Request Not Found:_

- If the selected request is not found or invalid, an error message is displayed.

_Invalid Changes:_

- If the employee enters invalid information, the system displays error messages and highlights the invalid fields.

_System Error:_

- If a system error occurs during the editing process, an error message is displayed, and the user is notified.

**Postconditions:**

- The selected vacation time request is updated with the new information (if applicable).

- The request is either updated, withdrawn, or remains unchanged, depending on the employee's action.

- The employee's manager is notified of any changes to the request (if applicable).
---

### Flow Chart

  <img src="https://github.com/asmaa-sherif/Vacation-Tracking-System/blob/main/Flow%20chart/Edit%20request%20flow%20chart.png" width="75%" />

---

### State Diagram

---

### Sequence Diagram

---

### Pseudocode
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
    IF balance < CalculateDays(request.newStartDate, request.newEndDate) THEN
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
