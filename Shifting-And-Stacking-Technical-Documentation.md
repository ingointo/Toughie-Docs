### Shifting And Stacking - Technical Documentation
#### Overview

The **Shifting and Stacking Module** is designed to facilitate the management of logistics involving staff assignments and product handling, particularly in the context of shifting and stacking operations. The module includes a form for data entry and product management, as well as listing and details screens for better tracking and management.

---

### Components

#### 1. Shifting and Stacking Form

**Purpose:** 
To collect detailed information related to the shifting and stacking process, including staff selection, product details, and timeframes.

**Key Functions:**

- **`toggleModal(type)`**  
  Toggles the visibility of modals for selecting employees, start time, and end time.  
  - **Parameters:**  
    - `type` (String): The type of modal to display (e.g., "multiSelectEmployee", "startTime", "endTime").

- **`handleFieldChange(field, value)`**  
  Updates the form data state when any input field is changed.  
  - **Parameters:**  
    - `field` (String): The name of the field being updated.  
    - `value` (Any): The new value for the specified field.

- **`handleShiftingAndStackingSubmit()`**  
  Validates the form inputs and submits the collected data to the backend for processing.  
  - **Processes:**  
    - Ensures that the number of laborers matches the number of selected staff members.
    - Validates that products are added before submission.
    - Constructs the payload and sends it to the API.

- **`addProductList(savedProducts)`**  
  Adds selected products to the product list for the shifting and stacking operation.  
  - **Parameters:**  
    - `savedProducts` (Object): The product details to be added.

- **`getTotalQuantity()`**  
  Calculates the total number of bricks based on the entered product details.  
  - **Returns:**  
    - (Number): The total quantity of bricks.

- **`handleDelete(id)`**  
  Removes a product from the product list based on its unique identifier.  
  - **Parameters:**  
    - `id` (String): The identifier of the product to be removed.

---

#### 2. Shifting and Stacking Listing Screen

**Purpose:** 
To display a list of all shifting and stacking operations, allowing users to view and navigate to specific entries.

**Key Functions:**

- **`fetchData()`**  
  Retrieves the list of existing shifting and stacking operations from the backend.  
  - **Processes:**  
    - Updates the state with the retrieved data for rendering the list.

#### 3. Shifting and Stacking Details Screen

The **Shifting and Stacking Details Screen** provides a comprehensive view of a specific shifting and stacking operation, enabling users to see key details, approval statuses, and associated products. It allows authorized users to approve or reject the operation based on predefined criteria.

---

### Key Components

#### 1. State Management

- **`shiftingAndStackingDetails`**: An object that holds the detailed information of the selected shifting and stacking operation.
- **`isVisible`**: A boolean state to control the visibility of the approval confirmation modal.
- **`rejectModalVisible`**: A boolean state to manage the visibility of the rejection modal.
- **`showApproveButton`**: A boolean state to determine if the approve/reject buttons should be displayed based on user permissions.

---

### Key Functions

- **`fetchProductionDetails()`**  
  Fetches the details of the shifting and stacking operation from the backend API.  
  - **Process:**  
    - Sends a GET request to `/viewShiftingAndStacking/{id}`.
    - Updates the `shiftingAndStackingDetails` state with the fetched data.
    - Sets visibility for the approval button based on user group and current approval status.

- **`handleApprove()`**  
  Handles the approval process for the shifting and stacking operation.  
  - **Process:**  
    - Constructs an update payload containing approval details.
    - Sends a PUT request to `/updateShiftingAndStacking` to update the approval status.
    - Calls `fetchProductionDetails()` upon successful approval to refresh the details.

- **`handleRejectionSubmit(text)`**  
  Submits rejection details for the shifting and stacking operation.  
  - **Parameters:**  
    - `text` (String): The reason for rejection.  
  - **Process:**  
    - Constructs an update payload with rejection details.
    - Sends a PUT request to update the rejection status.
    - Refreshes the details by calling `fetchProductionDetails()`.

- **`renderItem({ index, item })`**  
  Renders an individual image item in the FlatList for product images.  
  - **Parameters:**  
    - `index` (Number): The index of the item in the list.
    - `item` (Object): The image URI for rendering.  
  - **Returns:**  
    - A component that displays the image and navigates to a fullscreen view on press.

---

### User Interface Elements

- **Header**: Includes a back button and an optional edit icon based on user permissions.
- **Form Inputs**: Displays various details such as created by, approval status, team name, number of labors, etc. Each field is non-editable.
- **Product List**: Uses a FlatList to display all associated products with the shifting and stacking operation.
- **Action Buttons**: Displays approval and rejection buttons based on the user's permissions and the current approval status.

---

### State Management

All components leverage React's state management to track user inputs and manage modal visibility, using hooks such as `useState` and `useEffect` for data fetching and dynamic updates.

### User Experience Considerations

- **Validation:** The forms include validation checks to ensure that all required fields are filled out before submission.
- **User Feedback:** Toast notifications are used to inform users of success or error states during interactions, enhancing the overall user experience.
- **Dynamic Inputs:** As the user interacts with the forms, relevant inputs are dynamically updated based on previous selections (e.g., recalculating total bricks).
- **Conditional Rendering**: The approval and rejection buttons are only shown to users with appropriate permissions.
- **Feedback Modals**: Utilizes confirmation and rejection modals to gather user confirmation before proceeding with actions.
- **Dynamic Data Fetching**: Automatically fetches details when the screen gains focus to ensure up-to-date information.
