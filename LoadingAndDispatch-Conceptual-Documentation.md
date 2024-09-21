### Loading and Dispatch - Conceptual Documentation

This document outlines the features and workflows of the **Loading and Dispatch**, focusing on the functionality of managing labor activities, product loading, and dispatch processes. The module is designed to efficiently assign staff, track product quantities, and ensure that the loading and dispatch of bricks are properly documented and approved.

---

### 1. Loading and Dispatch Screen

This screen allows users to view and manage all loading and dispatch records. It includes an overview of the pending, ongoing, and completed loading operations, with options to add new records.

**Key Features:**
- **View Loading And Dispatch List:** Displays a list of all past and current dispatch lists.
- **Add New Loading And Dispatch:** Allows users to create new loading and dispatch records by clicking the “Add” button, leading to a form where details can be entered.
- **Approve/Reject Records:** Allows for approval of dispatch operations pending manager validation.

---
### 2. Loading and Dispatch Details
   - Displays comprehensive details of each loading and dispatch activity, such as the staff involved, team name, product list, and timestamps.
   - Includes status information, such as approval or rejection reasons, and the total number of bricks involved.
   - Provides options for supervisors and admins to approve or reject loading and dispatch activities, along with modal prompts for confirmation.

---

### 3. Loading and Dispatch Form

The form allows users to create and submit a new loading and dispatch record, including all relevant details about the operation.

**Key Features:**
- **Team and Labor Assignment:**
  - **Select Staff:** Choose the number of laborers and assign specific staff members from the available list. The form ensures that the selected number of staff matches the number of laborers entered.
  - **Team Name:** Enter the name of the team handling the dispatch operation.
  
- **Product Information:**
  - **Add Products:** Allows users to add multiple products by specifying the type, quantity, dimensions, and the rack number from which they were taken.
  - **Total Quantity Calculation:** Automatically calculates the total number of bricks based on the dimensions and number of products entered.

- **Vehicle and Timing Details:**
  - **Vehicle Number:** Record the vehicle number responsible for the dispatch.
  - **Start and End Times:** Allows users to select the date and time the loading began and ended using date-time pickers.

- **Image Uploads:**
  - **Add Images:** Users can upload multiple images, such as photographs of the loaded vehicle or other relevant documentation, through the form.

- **Submission and Approval Workflow:**
  - **Submit Button:** Once all necessary fields are filled in, the user can submit the form. The record is then marked as pending approval until it is reviewed and approved by the management.
  
---


#### User Roles:
- **Supervisors/Admins**:
   - Can approve or reject loading and dispatch activities.
   - Can add or edit loading and dispatch .
- **General Users**:
   - Can view loading and dispatch details but have restricted access to modification or approval options.


#### Workflow:
1. **List View**: The list of loading and dispatch activities is presented, allowing users to search and select items.
2. **Details View**: When an activity is selected, users can view the details, approve or reject the task, or esdit the information (depending on their role).
3. **Approvals**: Admins or supervisors approve or reject tasks. Approval status is updated in real time and visible to all users.
4. **Adding Products:**
   - Users add product details, including dimensions and rack numbers, and the system ensures that the total number of bricks matches the specified details.
