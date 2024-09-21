### Shifting and Stacking

#### Overview:
The **Shifting and Stacking** module manages labor activities and product movement within a warehouse or storage environment. This module enables the assignment of staff to specific tasks, tracking of brick products, and overseeing workflow processes for shifting and stacking operations. Supervisors and administrators can monitor, approve, or reject the execution of tasks, ensuring an organized approach to labor and product handling.

#### Key Features:
1. **Task Assignment and Staff Management**: 
   - The module allows administrators and supervisors to assign staff to shifting and stacking tasks. 
   - It provides a detailed view of the staff involved, including the number of laborers and their roles.

2. **Product Tracking**: 
   - Users can track the products (specifically bricks) being handled during the shifting and stacking process, including the number of bricks moved and the start and end times of the activity.
   - Product details such as the team name and labor count are displayed for better transparency.

3. **Approval Workflow**: 
   - Supervisors and administrators can approve or reject the completion of tasks. 
   - The status of each task (Pending, Approved, or Rejected) is clearly displayed along with any reasons for rejection.
   - Only users with specific roles (supervisors and administrators) can approve or reject tasks.

5. **Role-Based Access**:
   - The module restricts certain actions like task approval or modification to users with the appropriate role (e.g., supervisors, administrators), ensuring accountability.

#### Display Fields:
The **Shifting and Stacking Module** displays the following key fields:
- **Created By**: Name of the user who initiated the task.
- **Approval Status**: Status of the task (Pending, Approved, Rejected).
- **Start Time**: The time when the task began.
- **End Time**: The time when the task was completed.
- **Team Name**: The name of the team assigned to the task.
- **Number of Labors**: Total number of laborers involved.
- **Staff**: A list of staff members involved in the task.
- **Product Details**: Information about the brick products being shifted, including product count.
- **Total Bricks**: Total number of bricks shifted during the task.
- **Approved & Verified By**: Name of the supervisor or administrator who approved the task.
- **Rejected Reason**: If applicable, the reason for rejecting the task.
- **Rejected By**: Name of the user who rejected the task.
- **Images**: Uploaded images related to the task.

#### User Roles and Permissions:
- **Supervisors**: Can assign tasks, approve or reject tasks, and view detailed reports.
- **Administrators**: Have full access, including task creation, approval, and rejection.
- **Laborers**: Can view assigned tasks and provide feedback on task completion but do not have approval rights.


### Add Shifting And Stacking

The **Shifting and Stacking Form** is designed to manage the logistical processes involved in shifting and stacking products (e.g., bricks) through a structured workflow. This form captures key details such as staff involved, number of laborers, products being handled

#### Key Functionalities:

1. **Form Input Management:**
   - Captures information including start time, end time, team name, number of laborers, and selected staff members.
   - Provides fields to add details of products, including product names, quantities, and rack numbers for storage.

2. **Product Addition:**
   - The user can add products involved in the shifting and stacking process. Each product has fields for quantity, size (length, width, height), and additional details like rack number and extra bricks.
   - The total quantity of bricks is automatically calculated based on product dimensions and extra bricks.

3. **Employee Selection:**
   - Allows users to select staff members (laborers) involved in the task via a multi-select dropdown.
   - Ensures the selected number of staff matches the number of laborers specified.

4. **Image Upload:**
   - Provides functionality for users to upload and delete images related to the task, such as product photos or receipts.
   
5. **Validation and Submission:**
   - Ensures necessary fields are filled, such as number of laborers, selected staff, and product information before allowing submission.
   - Data such as total number of bricks and associated images are submitted for approval and further action.

6. **Modal Support:**
   - Various modal popups support the selection of staff, date and time (start and end), and products.

---

### Add Product and Details Screen Overview

This screen is responsible for adding detailed product information to the shifting and stacking task.

#### Key Functionalities:

1. **Product Selection:**
   - Allows users to select a product from a dropdown list, categorized by product types.
   
2. **Rack Selection:**
   - Users can select the rack number where products are stored, ensuring the system tracks the quantity of available products in that rack.
   - The form validates the quantity of bricks being added against the available inventory in the selected rack.

3. **Product Dimensions and Quantity Calculation:**
   - Users can enter product dimensions (length, width, height) and any extra bricks. Based on these inputs, the total quantity of bricks is calculated automatically.
   
4. **Validation and Saving:**
   - Mandatory fields are validated before saving, ensuring all required data, such as product and rack number, are entered.
   - The selected products and details are added to the shifting and stacking form for tracking.
