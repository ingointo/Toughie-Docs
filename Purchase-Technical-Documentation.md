## **Purchase - Technical Documentation**

### **1. Add Purchase**

The **Add Purchase** functionality allows users to create a new purchase by adding product details and submitting the form.

#### Key Functions:

1. **`addProductList(savedProducts)`**
   - **Description**: Adds the selected products to the current purchase order.
   - **Usage**: 
     - This function is invoked when a user selects products from the "Add Products" screen.
     - It takes an array of product objects and appends them to the `products` state, which holds the list of products in the current purchase order.
   - **Parameters**: 
     - `savedProducts`: Object containing product information like product ID, quantity, unit cost, etc.
   - **Purpose**: To dynamically update the list of products before purchase submission.

2. **`toggleModal(type)`**
   - **Description**: Handles the opening and closing of modals such as the date picker and employee selection.
   - **Usage**: 
     - Invoked when a user interacts with fields requiring modals (e.g., date/time picker, multi-select employee).
     - The function toggles visibility of these modal components based on the `modalType`.
   - **Parameters**: 
     - `type`: Defines the type of modal to open (e.g., 'multiSelectEmployee', 'dateTime').

3. **`handleFieldChange(field, value)`**
   - **Description**: Updates the form state dynamically when the user interacts with input fields.
   - **Usage**: 
     - This function is used across various fields (e.g., dateTime, employee selection).
     - It ensures the form data is kept up to date as the user interacts with it.
   - **Parameters**: 
     - `field`: The field being updated (e.g., 'dateTime', 'employee').
     - `value`: The new value for the field.

4. **`calculateTotals()`**
   - **Description**: Calculates the total quantity and amount for the products added to the purchase order.
   - **Usage**: 
     - This function iterates through the list of products and sums up their quantities and total costs.
     - The results are displayed before the user submits the form.
   - **Returns**: 
     - An object containing `quantity` and `amount` totals.

5. **`handlePurchaseSubmit()`**
   - **Description**: Submits the purchase order to the backend API.
   - **Usage**: 
     - This function is triggered when the user clicks the "Save" button to submit the purchase.
     - It validates the form (e.g., checks if products have been added), compiles the form data, and sends it to the API.
   - **API Call**: 
     - `apiInstance.post('/createToughieVendorBill', purchaseData)`
     - Sends the compiled `purchaseData` object to the backend for storage and processing.
   - **Error Handling**: 
     - Displays error messages using Toast if the submission fails or if required fields are missing.

---

### 2. Purchase Details
The **Purchase Details** component allows users to view and manage detailed information about a particular purchase, such as products, payment status, and approval status. Different functionalities are available based on the user's role (e.g., supervisor).

#### Key Features:
- View basic details: Sequence number, Date, Supplier name, Approval status, Payment status, etc.
- Handle Approval and Rejection of purchases.
- Update the payment status (e.g., Partially Paid, Fully Paid).

#### Key Functions:

- **fetchPurchaseDetails():**
    - **Description:** Fetches detailed information of a selected purchase.
    - **Usage:** Called during initialization and anytime the user revisits the page.
    - **API Call:** Makes a GET request to `/viewToughieVendorBill/{id}`.
    - **Error Handling:** Logs errors in case of a failed API request.

- **handleApprove():**
    - **Description:** Updates the approval status of the purchase to "Approved".
    - **Usage:** Called when the supervisor clicks the "Approve" button.
    - **API Call:** Makes a PUT request to `/updateToughieVendorBill` to update the status.
    - **Error Handling:** Logs errors if the API request fails.

- **handleUpdatePayment(amount):**
    - **Description:** Updates the payment status and amount paid for the purchase.
    - **Usage:** Called when the user updates the payment amount.
    - **Parameters:**
        - `amount`: The new payment amount to be added.
    - **API Call:** Makes a PUT request to `/updateToughieVendorBill` with payment details.
    - **Error Handling:** Logs errors if the API request fails.

- **handleRejectionSubmit(text):**
    - **Description:** Updates the approval status of the purchase to "Rejected" and stores the rejection reason.
    - **Usage:** Called when the supervisor clicks the "Reject" button and submits a rejection reason.
    - **Parameters:**
        - `text`: The reason for rejecting the purchase.
    - **API Call:** Makes a PUT request to `/updateToughieVendorBill` to update the status and reason.
    - **Error Handling:** Logs errors if the API request fails.

---

### **3. Listing (Purchase Listing Screen)**

The **Purchase Listing** screen displays all the submitted purchase orders. Each order is shown in a list, providing an overview of purchases made by the user.

#### Key Functions:

1. **`FlatList` (Rendering Purchase List)**
   - **Description**: Renders the list of purchases using the `FlatList` component.
   - **Usage**: 
     - Used within the UI to display purchase details in a scrollable format.
   - **Data Source**: 
     - Binds to the `purchases` state, which contains an array of purchase orders.
   - **Item Renderer**: 
     - The `renderItem` prop is used to define how each purchase order is displayed, including purchase ID, supplier, and date.

2. **`fetchPurchaseData()`**
   - **Description**: Fetches a list of submitted purchases from the backend.
   - **Usage**: 
     - This function is called when the listing screen is initialized (`useEffect`).
     - It populates the list of purchase orders to be displayed on the listing screen.
   - **API Call**: 
     - A GET request is made to retrieve purchase orders.
   - **Error Handling**: 
     - Displays error messages if data retrieval fails.

3. **`onPurchaseSelect(purchaseId)`**
   - **Description**: Handles user interaction when a purchase is selected from the list.
   - **Usage**: 
     - When a user taps on a purchase item in the list, this function is invoked.
     - It navigates to the purchase details screen, passing the `purchaseId` as a parameter.
   - **Navigation**: 
     - `navigation.navigate('PurchaseDetails', { purchaseId })`
     - Navigates to the purchase details screen.

---

