---

## 1. Creating an Azure DevOps Organization

The **Organization** serves as the container for your projects, users, and resources. It's usually named after your company or a major division.

1.  **Navigate to the Azure DevOps Portal:** Open your web browser and go to [https://dev.azure.com](https://dev.azure.com).
2.  **Sign In:** Sign in with the Microsoft account (MSA) or Azure Active Directory (Azure AD) credentials you want to use for administration.
3.  **Create Organization:**
    * If you don't have an organization, you'll be prompted to **Create an organization**.
    * If you have existing organizations, click the **New organization** button in the top right.
4.  **Name and Location:**
    * Choose a unique name for your organization (e.g., `YourCompanyDev`).
    * Select a hosting location/region closest to the majority of your users for better performance.
5.  **Validation:** Complete the security check if prompted.
6.  **Review:** Your new Azure DevOps organization URL will be `https://dev.azure.com/YourCompanyName`.

---

## 2. Creating a Project

A **Project** within the Organization is where your development work, source code, and boards reside.

1.  **Navigate to Your Organization:** Go to your new organization's home page (`https://dev.azure.com/YourCompanyName`).
2.  **Create Project:** Click on **+ New project**.
3.  **Project Details:**
    * **Project Name:** Choose a descriptive name (e.g., `ProductX Development`).
    * **Visibility:** Set to **Private** for internal projects (recommended) or **Public**.
4.  **Advanced Configuration:** Click **Advanced** (if necessary, though the defaults are often fine):
    * **Version control:** Select **Git** (industry standard) or Team Foundation Version Control (TFVC).
    * **Work item process:** **Crucially**, select the initial process. Choose **Agile** now, or **Basic** if you plan to change it later (see step 3).
5.  **Create:** Click **Create**.

---

## 3. Change the Process for the Board (Basic to Agile)

The **Process** defines the Work Item Types and workflow states used on your boards. We'll change the project from the simple **Basic** process to the more structured **Agile** process.

> **Note:** This requires **Project Collection Administrator** or **Organization Owner** permissions.

1.  **Go to Organization Settings:** Click the **Organization Settings** icon (⚙️) in the bottom-left corner of the Azure DevOps window.
2.  **Select Process:** Under the **Boards** section, select **Process**.
3.  **Select Project:** Click on the process your project is currently using (e.g., **Basic**).
4.  **Change Process:**
    * Select the **Projects** tab.
    * Hover over your target project and click the **...** (three dots/context menu).
    * Select **Change process**.
    * From the dropdown, select **Agile**.
5.  **Confirm:** Click **Save**. The work item types for your project are now aligned with the Agile framework (Epic, Feature, User Story, Task).

---

## 4. Creating the Epic

An **Epic** represents a large body of work that can span multiple sprints and features. It often aligns with a major business initiative.

1.  **Navigate to Boards > Boards:** From your project, go to the **Boards** section, and click on **Boards**.
2.  **Change Board Level:** Ensure the board level is set to the highest level, typically **Epics** (check the top-right corner filter).
3.  **Create New Work Item:** Click the **+ New Work Item** button and select **Epic**.
4.  **Title and Description:**
    * **Title:** Enter a brief, descriptive name (e.g., **Implement Customer Authentication Module**).
    * **Description:** Detail the high-level business value and scope.
5.  **Save:** Click **Save & Close**. 

---

## 5. Creating the Feature

A **Feature** is a smaller component of an Epic that delivers a tangible piece of value to the user. Features usually span multiple user stories.

1.  **Switch to Features Board:** In the **Boards** section, change the board level filter (top right) to **Features**.
2.  **Create Feature:** Click **+ New Work Item** and select **Feature**.
3.  **Title and Description:**
    * **Title:** Enter a name (e.g., **User Login via Social Media**).
    * **Description:** Describe what the feature does.
4.  **Link to Parent (Epic):**
    * In the Feature form, look for the **Related Work** section (or the **Links** tab).
    * Click **Add Link** > **Existing item**.
    * For **Link type**, select **Parent**.
    * Enter the **Epic ID** you created in Step 4, or click **Browse** to find it.
5.  **Save:** Click **Save & Close**.

---

## 6. Creating the User Story

A **User Story** describes a requirement from the perspective of an end-user. It's the primary unit of work for a development team in a sprint.

1.  **Switch to Stories Board:** In the **Boards** section, change the board level filter (top right) to **Stories** (or Backlog Items/Requirements, depending on your process).
2.  **Create User Story:** Click **+ New Work Item** and select **User Story**.
3.  **Title (As a..., I want..., So that...):** Use the standard User Story format (e.g., **As a returning user, I want to log in using Google, so that I can quickly access my account.**).
4.  **Link to Parent (Feature):**
    * In the User Story form, use the **Parent** link type to link it to the relevant **Feature** created in Step 5.
5.  **Define Acceptance Criteria:** Use the **Acceptance Criteria** field to list the conditions that must be met for the story to be considered "Done."
6.  **Save:** Click **Save & Close**.

---

## 7. Creating the Task

A **Task** is the smallest unit of work, often technical, required to complete a User Story. Tasks are typically assigned to individual team members and completed within a few hours to a day.

1.  **Open Parent User Story:** Open the User Story created in Step 6.
2.  **Add Task:**
    * In the User Story form, go to the **Related Work** section.
    * Click **Add Link** > **New item**.
    * For **Link type**, select **Child**.
    * For **Work item type**, select **Task**.
3.  **Task Details:**
    * **Title:** Enter a technical task (e.g., **Implement OAuth handshake with Google API**).
    * **Activity:** Set the type of work (e.g., Development, Testing, Documentation).
    * **Remaining Work:** Estimate the time required (in hours).
4.  **Save:** Click **OK** on the Task window, and then **Save & Close** on the User Story.

---

## 8. Creating the Parent and Child Relationship

This step summarizes and reinforces the hierarchy established in the previous steps. The standard hierarchy is: **Epic $\rightarrow$ Feature $\rightarrow$ User Story $\rightarrow$ Task**.

| Work Item Type | Relationship to Item Below | Relationship to Item Above | Purpose |
| :--- | :--- | :--- | :--- |
| **Epic** | **Parent** to Feature | - | Major Business Initiative |
| **Feature** | **Parent** to User Story | **Child** of Epic | Tangible User Value |
| **User Story** | **Parent** to Task | **Child** of Feature | Single User Requirement |
| **Task** | **Child** of User Story | - | Technical Work to Complete Story |

**How to link (In the Work Item Form):**

* To link a **child** item: Click **Add Link** > **New Item/Existing Item** > Select **Child** as the Link Type.
* To link a **parent** item: Click **Add Link** > **Existing Item** > Select **Parent** as the Link Type.

---

## 9. Changing the Type of the Work Items

Sometimes a User Story is too large and should be elevated to a Feature, or vice-versa.

1.  **Open the Work Item:** Find and open the work item you wish to change (e.g., a User Story).
2.  **Use the Context Menu:** Click the **...** (three dots/context menu) in the top right corner of the work item form.
3.  **Change Type:** Select **Change type**.
4.  **Select New Type:** Choose the new desired type from the dropdown (e.g., change **User Story** to **Feature**).
5.  **Confirm:** Click **OK**.
    > **Note:** This action moves the work item to the appropriate level on the board/backlog. Check and update its Parent/Child links if the hierarchy changes.

---

## 10. Inviting Members to the Project

Users need to be invited to the project to view the boards, contribute work, and participate in the development process.

1.  **Go to Project Settings:** Click the **Project Settings** icon (⚙️) in the bottom-left corner.
2.  **Select Teams or Permissions:** Under the **General** section, select **Permissions**.
3.  **Add User:**
    * Find the security group you want to add the user to (e.g., **Contributors** is the standard group for team members).
    * Click on the group, then click the **+ Add** button.
    * Enter the email addresses or display names of the users you want to invite.
4.  **Assign Access Level (If needed):** Ensure they have the correct **Access Level** (e.g., **Basic** for developers/testers, **Stakeholder** for users only needing to track progress). This is usually managed at the Organization Settings level under **Users**.
5.  **Confirm:** The invited members will now have access to the project's boards, repositories, and other resources based on their security group.

***