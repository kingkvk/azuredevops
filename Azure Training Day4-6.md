---

## Part II: Advanced Azure DevOps Board Configuration and Administration

### 1. How to Configure the Stages in the Board (Columns)

Customizing the board columns allows you to map the default workflow states (e.g., *New, Active, Closed*) to your team's specific process stages (e.g., *In Progress, In Test, In UAT*).

#### **Goal: Map States to Custom Columns**

1.  **Navigate to Boards:** Go to your Project, then select **Boards** (or **Sprints** for a Sprint Board).
2.  **Open Board Settings:** Click the **Settings** icon (⚙️) in the top-right corner of the board.
3.  **Columns Tab:** Select the **Columns** tab.
4.  **Add/Rename Columns:**
    * **To Rename:** Click on the column title (e.g., *Active*) and rename it (e.g., to **In Progress**).
    * **To Add:** Click the **+ Add Column** button to create a new stage (e.g., **In Test** or **In UAT**).
5.  **Map to State (Crucial Step):** For each column you create, you must define the **State mapping**:
    * **State:** Select the underlying work item state that the column represents.
        * **In Progress:** Map this column to the **Active** state.
        * **In Test / In UAT:** These are usually mapped to the **Resolved** state or kept under **Active** if testing is part of the "In Progress" work cycle. For complex flows, you may need a custom state (see admin note below).
        * **Closed:** Map this column to the **Closed** state.
    * **Limit:** (Optional) Set **Work in Progress (WIP) Limits** to enforce agile practices.
6.  **Save Changes:** Click **Save**.

> **Note on States vs. Columns:** The **State** is the value stored on the work item itself (*Active, Resolved, Closed*). The **Column** is the visual representation on the board. You map one or more columns to a single underlying state.

---

### 2. How to Assign Permissions to Users (Developer, Tester, Scrum Master)

Permissions are generally managed by placing users into predefined security groups.

#### **Goal: Define Roles and Permissions**

1.  **Go to Project Settings:** Click the **Project Settings** icon (⚙️) in the bottom-left corner.
2.  **Select Permissions:** Under the **General** section, select **Permissions**.
3.  **Review Default Groups:** Azure DevOps provides standard groups with predefined permissions:
    * **Readers:** Can view everything. Good for stakeholders or external auditors.
    * **Contributors:** The standard role for team members (Developers, Testers). They can create, edit, and move work items, and contribute code.
    * **Project Administrators:** Can manage teams, permissions, and project settings (Good for Scrum Masters or Delivery Managers).

4.  **Assign Users to Groups:**
    * Select the group (e.g., **Contributors**).
    * Go to the **Members** tab and click **+ Add**.
    * Search for and add the user(s) who will be developers or testers.

5.  **Scrum Master (Admin Role):**
    * If the Scrum Master needs to manage project settings (like configuring sprints, teams, and permissions), they should be added to the **Project Administrators** group.
    * Select **Project Administrators** group > **Members** > **+ Add** and include the Scrum Master.

6.  **Granular Permissions (If needed):**
    * You can set very specific permissions for a group (e.g., allowing a Tester group to **only** modify Bug work items).
    * Select a Group, then review the **Permissions** tab. You can set permissions like "Edit work items in this node" to **Allow** or **Deny**.

---

### 3. Key Administrative Concepts (Admin Must-Haves)

As an administrator training others, you should be familiar with these higher-level concepts:

#### **A. Team Configuration**

* **Teams vs. Project:** A single project can have multiple teams. Each team can have its own *backlog*, *sprint schedule*, and *board view* within the same project.
* **Configuration:** Go to **Project Settings** > **Teams**.
    * You can create a new team (e.g., `Team A - Frontend`) and assign specific team members and **Area Paths** to it.
    * *Why this matters:* It allows large projects to operate independently while sharing a common repository.

#### **B. Area and Iteration Paths**

These are the backbone of project structure and time management.

| Path Type | Purpose | Configuration Location | Admin Action |
| :--- | :--- | :--- | :--- |
| **Area Path** | Used for **categorizing** work items (e.g., by component, feature, or team). Also used to manage security/permissions. | **Project Settings** > **Project configuration** > **Area** | Define the logical structure (e.g., `ProjectX\Backend`, `ProjectX\UI`). |
| **Iteration Path** | Used for **time boxing** work items (i.e., Sprints and Releases). | **Project Settings** > **Project configuration** > **Iteration** | Define the sprints with start/end dates (e.g., `Sprint 1`, `Release 1`). |

#### **C. Process Customization (Advanced Board/State Changes)**

While you changed the process from Basic to Agile (Step 3), true customization allows you to modify the work item fields and workflow.

* **Custom States:** If your team needs a stage like "Waiting for Third Party" which doesn't fit the default **Active/Resolved** states, you must:
    1.  Go to **Organization Settings** > **Process**.
    2.  Create an **Inherited Process** from Agile.
    3.  Edit the work item type (e.g., User Story) and **add a new State** (e.g., "Blocked").
    4.  Change your project to use this new Inherited Process.
* **Custom Fields:** You can add new fields to work items (e.g., "Business Priority Score" or "Compliance Requirement"). This is also done via **Organization Settings** > **Process**.
