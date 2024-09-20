### Production - Conceptual Documentation

#### Overview:
The **Labour Submodule** in the **Production** module is responsible for managing production-related tasks. It allows users to view and track production entries, manage labour activities, and monitor associated production details. The functionality varies based on user roles, such as **supervisors** and **admins**, who have additional privileges like approving or rejecting production entries.

---

### 1. Production Listing

This component displays a list of production records, providing a searchable and paginated view. Users can filter through the production entries and select individual records for further details.

**Key Features:**
- **Fetch and display production data** from the backend, including shift details, production output, and assigned labour.
- **Search functionality** to filter production records based on text input.
- **Role-based access** determines whether certain buttons, like the "Add Production" button, are visible.

**Key Functions:**

- **fetchProduction():**
    - **Description:** Fetches production data from the backend, with pagination and search functionality.
    - **Usage:** Called during component initialization and triggered by search or pagination actions.
    - **Parameters:**
        - `offset`: The number of records to skip.
        - `limit`: The number of records to fetch.
        - `searchText`: The search query for filtering results.
    - **API Call:** GET request to `/viewProductionList`.
    - **Error Handling:** Displays an error message if the data cannot be fetched.
  
- **handleEndReached():**
    - **Description:** Fetches additional production data when the user scrolls to the end of the list.
    - **Usage:** Triggered automatically when the list reaches the bottom.
  
- **debouncedSearch():**
    - **Description:** Debounces the search input to avoid multiple API calls for rapid typing.
    - **Usage:** Activated when the user types in the search bar, delaying the API call for 1 second after typing stops.

- **showFabButton (Conditional rendering):**
    - **Description:** Determines whether the floating action button (FAB) for creating new production entries is visible.
    - **Usage:** Shown only to users with the role of **supervisor** or **admin**.

---

### 2. Production Details

The **Production Details** screen provides comprehensive information about a specific production entry, including labour details, production output, materials used, and time logs. It also offers the ability for supervisors and admins to approve or reject production records.

**Key Features:**
- **Detailed production data**: Shift number, start/end time, number of bricks produced, cements used, and associated labour names.
- **Approval functionality**: Supervisors and admins can approve or reject production entries.
- **View associated products**: Display of products manufactured during the production shift.
  
**Key Functions:**

- **fetchProductionDetails():**
    - **Description:** Fetches detailed information for a selected production entry.
    - **Usage:** Called when the production details screen is loaded.
    - **API Call:** GET request to `/viewProductionList/{id}`.
    - **Error Handling:** Logs errors if the data cannot be fetched.

- **handleApprove():**
    - **Description:** Allows a supervisor or admin to approve the production entry.
    - **Usage:** Triggered when the "Approve" button is pressed.
    - **API Call:** PUT request to `/updateProductionList` with approval data.

- **handleRejectionSubmit():**
    - **Description:** Allows a supervisor or admin to reject the production entry, with an option to provide a reason.
    - **Usage:** Triggered when the "Reject" button is pressed, followed by the submission of a rejection reason.
    - **API Call:** PUT request to `/updateProductionList` with rejection data.

---

### 3. Production Creation


The **Production Creation** screen The Balance of Production module facilitates the management of daily production activities. It allows users to track production details, including employee assignments, products produced, and materials used. This module integrates features such as adding products, calculating totals, and uploading supporting images.


#### **Key Screens & Features:**

1. **Production Form Screen**
   - **Purpose:** This screen captures all relevant details of a production shift, including start/end times, staff involved, products produced, and material usage.
   
   - **Displayed Fields & Functions:**
     - **Start Time & End Time:** 
       - Allows users to select the start and end times of the production shift using a datetime picker.
     - **Shift No & Team Name:** 
       - Input fields for specifying the shift number and team name.
     - **Number of Labours:** 
       - Input field for specifying the number of laborers working in the shift. 
       - **Note:** Validates that the number of selected employees matches the number of laborers entered.
     - **Select Staff:** 
       - Modal for selecting staff from a list of employees.
     - **Add Products:** 
       - Allows users to add products by navigating to the product selection screen.
       - Each product entry includes the product name, quantity, cement consumption ratio, and category details.
     - **Cements Used (Bags) & Materials Used:** 
       - Input fields for specifying the amount of cement and other materials used.
     - **Uploads:** 
       - Users can upload supporting images, with the ability to delete individual images.

   - **Additional Functionalities:**
     - **Image Upload:** Users can upload and manage multiple images related to the production using the `ImagePickerModal`.
     - **Validation:** 
       - Ensures that the required number of staff matches the entered number of laborers.
       - Validates that at least one product is added before submitting the form.
     - **Toast Notifications:** Provides feedback on submission success or errors.

---

2. **Add Product and Quantity Screen**
   - **Purpose:** This screen allows users to add products to the production record and specify the quantity produced.
   
   - **Displayed Fields & Functions:**
     - **Select Products:** 
       - Dropdown for selecting products from a predefined list. Each product includes attributes such as name, cement consumption ratio, and category.
     - **Quantity:** 
       - Input field for specifying the quantity of the selected product.
   
   - **Additional Functionalities:**
     - **Validation:** 
       - Ensures that both product and quantity fields are filled before proceeding.
     - **Save Button:** 
       - Adds the product to the production list and navigates back to the main form.

---

#### **Main Actions:**
- **Submit Production:** Submits the production data, including product details, labor information, and materials used.
- **Error Handling:** Displays errors for incomplete fields or validation issues via toast notifications.

### Role-Based Access Control
- **Supervisors and Admins**: Can view, approve, reject, and create production entries.
- **Other Roles**: Limited to viewing production records without the ability to approve, reject, or create entries.


