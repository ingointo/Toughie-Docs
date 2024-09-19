# **Purchase Module**

## **Purpose**
- Simplify the vendor billing process.
- Enhance communication between suppliers and supervisors.
- Provide real-time updates on payment statuses and approvals.

## **Key Features**
1. **Approval Workflow**: Supervisors can approve or reject purchase requests based on predefined conditions.
2. **Payment Tracking**: Track payment statuses, including partial and full payments, along with payment due amounts.
3. **Search Functionality**: Users can quickly search and filter purchase orders.
4. **Dynamic UI Elements**: Buttons for approval, rejection, and payment updates are dynamically displayed based on the user’s role.
5. **Detailed Product Tracking**: Vendor bills include detailed product information with quantity and status tracking.
6. **Role-Based Access**: Features are shown or hidden based on the user’s role (e.g., supplier, administrator, supervisor).
7. **Real-Time Updates**: Automatically fetches and displays the latest data when a user revisits a page.

## **Workflow**

### **Purchase Listing Screen**
- **Role-Based Access**: Based on the user’s role (supplier, admin, or supervisor), relevant vendor bills are displayed after login.
- **Data Fetching**: Vendor bills are fetched from the API and displayed in a scrollable list, with new data fetched automatically as the user scrolls.
- **Search Functionality**: A search bar allows users to find specific vendor bills.
- **Navigation**: Selecting a vendor bill navigates the user to the **Purchase Details Screen**.

### **Purchase Details Screen**
- **Bill Details**: Shows information such as sequence number, date, supplier name, approval status, payment status, total amount, amount paid, and amount due.
- **Product Details**: Displays a list of products related to the vendor bill, including received quantity and other details.
- **Approval & Rejection**: Supervisors can approve or reject the vendor bill. Rejections include a reason for rejection.
- **Payment Updates**: Supervisors can update payment statuses, tracking partial and full payments once the bill is approved.

### **Add Purchase Screen**

#### **Purpose**
This module allows users to submit and manage purchase orders by creating and updating product entries with details like product name, quantity, unit cost, and total amounts. It supports managing purchase details for suppliers, calculating totals, and handling purchase approval workflows.

#### **Key Functionalities**
1. **Purchase Form**: 
   - This form allows users to input essential purchase details such as:
     - **Date and Time**: Users can select the purchase date and time.
     - **Supplier Selection**: Automatically fetches the logged-in user’s supplier profile.
     - **Product List**: Users can add multiple products to the purchase. Each product entry includes details such as product name, quantity, unit cost, and unit of measure.
   - A running total is displayed, showing the total quantity and amount of products added.
   
2. **Product Management**:
   - **Add Products**: The module provides a way to search and select raw materials or products to add to the purchase list. Users specify quantity and unit cost for each product.
   - **Unit of Measure (UOM)**: For each product, users can select the unit of measure, which is retrieved dynamically based on the product selected.
   - **Delete Product**: Users can remove a product from the list before submitting the purchase.

3. **Totals Calculation**: 
   - The module automatically calculates the total quantity and amount based on the products added. This total is displayed to the user before submission.

4. **Purchase Submission**:
   - When the purchase is submitted, the following details are included:
     - **Supplier Details**: Pulled from the user’s profile.
     - **Product Line Items**: Each product’s ID, name, quantity, unit cost, unit of measure, and category.
     - **Total Amount**: The total amount due for the purchase.
     - **Approval and Payment Status**: Purchases are marked as 'pending' approval and 'unpaid' by default.
   - Upon submission, the data is sent to the backend API, where it undergoes validation and storage.

5. **Feedback and Validation**:
   - The module ensures that required fields (such as adding products) are validated before submission.
   - After submission, success or error messages are displayed based on the outcome of the API response, providing feedback to the user.

### **Buttons Visibility Conditions**
- **Approve Button**: Visible to supervisors when the approval status is pending.
- **Reject Button**: Visible to supervisors when approval is pending but not rejected.
- **Update Payment Button**: Visible to supervisors when the bill is approved but not fully paid.

## **Data Flow**
- **Initial Data Load**: Upon page load, vendor bills are fetched from the API based on the user’s role.
- **Pagination**: Data is loaded in chunks, with additional bills loaded as the user scrolls.
- **Form Submissions**: Approvals, rejections, or payment updates are sent to the server via API calls, and the interface is updated accordingly.

