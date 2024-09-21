## Loading And Dispatch - Technical Documentation

## **1. Loading and Dispatch Screen**

### **Purpose**:
The **Loading and Dispatch Screen** is designed to display a list of ongoing, pending, and completed loading and dispatch activities. It enables users to search, filter, and initiate new loading and dispatch tasks while tracking the status of existing ones.

### **Key Functions**:

- **fetchLoadingAndDispatch()**  
  Retrieves the list of loading and dispatch activities from the backend, supporting infinite scrolling for large datasets.

  **Processes**:
  - Fetches data in batches to improve performance and reduce load times.
  - Handles search and filtering criteria to display relevant records.

- **handleSearchTextChange(text)**  
  Filters the list of dispatch activities based on user input.

  **Parameters**:  
  - `text` (String): The search query entered by the user to filter dispatch records (e.g., staff name, vehicle number, date).

  **Processes**:  
  - Triggers a debounced search to minimize performance impact.
  - Calls the fetch function to refresh the list based on the search text.

- **navigateToDetails(itemId)**  
  Navigates the user to the **Loading and Dispatch Details Screen** of a selected record.

  **Parameters**:  
  - `itemId` (String): The unique identifier of the dispatch activity to display detailed information.

---

## **2. Loading and Dispatch Details Screen**

### **Purpose**:
The **Loading and Dispatch Details Screen** provides comprehensive information about a specific dispatch operation, including assigned staff, product quantities, vehicle information, and approval status.

### **Key Functions**:

- **fetchLoadinAndDispatchDetails(id)**  
  Retrieves detailed information for the selected dispatch activity from the backend.

  **Parameters**:  
  - `id` (String): The unique identifier of the dispatch activity.

  **Processes**:  
  - Fetches all relevant details, including staff assignment, product list, vehicle data, and approval status.
  - Updates the screen with fetched data for review and action.

- **handleApprove(status, reason)**  
  Allows supervisors or admins to approve or reject a dispatch task.

  **Parameters**:  
  - `status` (String): The approval status, either "Approved" or "Rejected".
  - `reason` (String): If rejected, provides the reason for rejection (mandatory when rejecting).

  **Processes**:  
  - Validates user roles (only supervisors or admins can perform this action).
  - Updates the dispatch status in the system and logs the decision, including any rejection reason.

- **displayProductImages(imageList)**  
  Displays a gallery of images related to the dispatch task (e.g., photos of loaded vehicles).

  **Parameters**:  
  - `imageList` (Array): A list of image URLs related to the dispatch activity.

---

## **3. Loading and Dispatch Form**

### **Purpose**:
The **Loading and Dispatch Form** is used to create or update dispatch records, capturing details about the assigned staff, product quantities, vehicle information, and supporting media (e.g., photos).

### **Key Functions**:

- **handleFormChange(field, value)**  
  Updates the form's state whenever a user modifies an input field.

  **Parameters**:  
  - `field` (String): The name of the field being updated (e.g., "teamName", "vehicleNumber").
  - `value` (Any): The new value provided by the user.

  **Processes**:  
  - Validates the form input and updates the local state.
  - Ensures correct data types for each field (e.g., text, numbers).

- **handleAddProduct(productDetails)**  
  Adds product information to the list of items being loaded for dispatch.

  **Parameters**:  
  - `productDetails` (Object): Contains details such as the product type, dimensions, and quantity.

  **Processes**:  
  - Validates the product details.
  - Updates the total quantity of bricks being dispatched based on the entered product dimensions and count.

- **handleFormSubmit()**  
  Validates all form inputs and submits the dispatch record to the backend for processing.

  **Processes**:  
  - Ensures all mandatory fields (e.g., staff, products, vehicle) are filled in.
  - Constructs the final data payload and sends it to the API.
  - Triggers the submission workflow, marking the task as "Pending" until reviewed by an admin.

- **handleImageUpload(images)**  
  Handles the upload of images related to the dispatch task.

  **Parameters**:  
  - `images` (Array): A collection of image files to be uploaded.

  **Processes**:  
  - Allows multiple images to be uploaded.
  - Stores the images on the server and links them to the dispatch record.

