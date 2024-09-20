### **Production - Technical Documentation**

---

#### **Module: Production**

##### **1. Overview**
This module handles the process of creating, managing, and listing production-related data such as staff, materials, and production quantities. It includes multiple components such as the main production form, product details, and the addition of products to a production entry.

---

### **1. Production Form**

##### **Component Name**: `ProductionForm`

##### **Functionality**: 
- This form allows users to log production data, including staff, materials used, and product details. It also supports file uploads and images.

##### **Key Features**:
- **Multi-select employee**: Users can select multiple staff members from the list.
- **Product management**: Allows users to add and remove products.
- **Date & time picker**: Enables selection of start and end times for the production process.
- **File/image upload**: Users can upload images related to the production process.
- **Form validation**: Checks input fields such as number of labours and product quantities for completeness and validity.
- **Submission**: Sends the form data to the API endpoint for saving in the database.

##### **Key Functions and Components**:
- **State Management**:
  - `formData`: Stores form input fields such as start time, end time, number of labours, products, etc.
  - `selectedItems`: Stores the selected staff members.
  - `products`: Holds the list of products added to the production.
  - `imageUrls`: Manages the images uploaded by the user.

- **Event Handlers**:
  - `toggleModal(type)`: Toggles different modal views (multi-select, date picker).
  - `addProductList(savedProducts)`: Adds a product to the list of selected products.
  - `handleFieldChange(field, value)`: Updates form fields when user inputs or selects data.
  - `handleDelete(id)`: Removes a product from the list of selected products.
  - `hanldeProductionSubmit()`: Validates and submits the production data to the server.

- **APIs**:
  - `fetchEmployeeData()`: Fetches employee data from the API for multi-select.
  - `apiInstance.post('/createProductionList', productionData)`: Submits the production form data to create a new production record.

##### **Dependencies**:
- `react-native-modal-datetime-picker`: For date and time selection.
- `CustomMultiSelectDataModal`: For multi-select employee modal.
- `ImagePickerModal`: For image uploads.
- `apiInstance`: For API calls to save production data.

##### **Data Flow**:
1. The user inputs production-related information (start time, end time, number of labours, etc.).
2. Products are added through the `AddProductAndQty` component.
3. Images are uploaded through the `ImagePickerModal`.
4. On form submission, the data is validated and posted to the API.

---

### **2. Production Details**

##### **Component Name**: `ProductionDetails`

##### **Functionality**: 
- Displays detailed information about a specific production entry.
- Shows the list of products, staff involved, and total quantities.
- Provides an option to edit or update the production details.

##### **Key Features**:
- **Product list display**: Shows the details of each product involved in the production, including quantities and cement consumption ratios.
- **Image display**: Displays uploaded images related to the production process.
- **Staff details**: Lists staff members involved in the production.

##### **Key Functions and Components**:
- **State Management**:
  - `productionDetails`: Holds the fetched production details including products, staff, and other production metadata.

- **Event Handlers**:
  - `fetchProductionDetails(id)`: Fetches the production details by ID from the server.
  - `handleEdit()`: Allows the user to edit and update the production details.

- **APIs**:
  - `apiInstance.get('/getProductionDetails', { id })`: Fetches production details based on the production ID.

##### **Dependencies**:
- `react-native-modal`: For displaying additional information modals.
- `ProductList`: Component used to display the list of products with options to view/edit them.

##### **Data Flow**:
1. The production ID is passed to this component.
2. The production details are fetched using the production ID.
3. The user can view or modify the production details.

---

### **3. Production Screen**

##### **Component Name**: `ProductionScreen`

##### **Functionality**: 
- Displays a list of all production entries created.
- Allows navigation to view details or create a new production entry.

##### **Key Features**:
- **Listing**: Shows all production records in a scrollable list.
- **Navigation**: Provides buttons to view detailed production data or create a new production entry.

##### **Key Functions and Components**:
- **State Management**:
  - `productions`: Stores the list of all production records.

- **Event Handlers**:
  - `fetchProductions()`: Fetches the list of all production entries.
  - `navigateToProductionDetails(id)`: Navigates to the detailed view of a production entry.

- **APIs**:
  - `apiInstance.get('/getProductions')`: Fetches the list of production records from the server.

##### **Dependencies**:
- `FlatList`: For listing production entries.
- `react-navigation`: For navigating between production list and details screens.

##### **Data Flow**:
1. The list of productions is fetched using an API call.
2. The user can navigate to view production details or create a new production entry.

---

### **4. Add Product and Quantity**

##### **Component Name**: `AddProductAndQty`

##### **Functionality**: 
- Allows users to select products and enter corresponding quantities to be used in production.

##### **Key Features**:
- **Product selection**: Fetches and displays a list of products to select from.
- **Quantity input**: Takes input for the quantity of the selected product.

##### **Key Functions and Components**:
- **State Management**:
  - `formData`: Stores the selected product and its quantity.

- **Event Handlers**:
  - `handleFieldChange(field, value)`: Updates the selected product and its quantity.
  - `handleSavePress()`: Adds the selected product and quantity to the production form.

- **APIs**:
  - `fetchProductsDropDownDataCategoryId()`: Fetches the list of products for selection.

##### **Dependencies**:
- `CustomDataModal`: For product selection modal.
- `FormInput`: For input fields related to product and quantity.

##### **Data Flow**:
1. The user selects a product and enters a quantity.
2. On save, the product and quantity are passed back to the `ProductionForm` for further processing.

---

### **General Structure**

- **State Management**: Most components rely on local state (`useState`) for managing form inputs, selected data, and API responses.
- **API Calls**: Each component interacts with backend services through API calls using `apiInstance` to fetch and submit production data.
- **Navigation**: React Navigation (`navigation`) is used to switch between different screens such as production list, details, and form.

--- 
