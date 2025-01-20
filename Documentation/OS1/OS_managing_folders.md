# Detailed Documentation for Managing Branch Folders in Linux

This guide outlines the steps for creating branch folders, verifying folder structure, and setting folder ownership for specific organizational branches in Linux. These actions are typically performed by the root user for security and permissions management.

---

## 1. Create Branch Folders Using Root User

**Purpose:**  
Create dedicated folders for each branch of the organization (e.g., HR, Finance, Sales, Marketing, IT) as the root user.

**Command Syntax:**
```bash
sudo mkdir -p /company/HR /company/Finance /company/Sales /company/Marketing /company/IT
```
**Explanation:**

sudo: Allows execution of commands as the root user (if not already logged in as root).

mkdir: Creates directories.

-p: Ensures that all necessary parent directories are created, preventing errors if they already exist.

/company/HR, /company/Finance, etc.: Paths where each branch folder will be created.

Example Usage:

```bash
sudo mkdir -p /company/HR /company/Finance /company/Sales /company/Marketing /company/IT
```
**Expected Output:**

If successful, no output will appear, but the folders will be created under /company. You can verify them with ls (see next step).

## 2. Verify Folder Structure
**Purpose:**

Check if the branch folders have been created successfully.

**Command Syntax:**

```bash
ls -l /company
```
**Explanation:**

ls -l: Lists all files and directories in long format, showing detailed information like permissions, ownership, and date.

/company: The directory under which the branch folders should reside.

**Example Usage:**

```bash
ls -l /company
```
**Expected Output:**

Lists each branch folder with detailed information. Example:
yaml
```bash
drwxr-xr-x 2 root root 4096 Oct 31 10:15 HR
drwxr-xr-x 2 root root 4096 Oct 31 10:16 Finance
drwxr-xr-x 2 root root 4096 Oct 31 10:17 Sales
drwxr-xr-x 2 root root 4096 Oct 31 10:18 Marketing
drwxr-xr-x 2 root root 4096 Oct 31 10:19 IT
```
## 3. Set Ownership of Folders to Respective Branches
**Purpose:**

Assign ownership of each branch folder to the appropriate branch user group, allowing only authorized users access.

**Command Syntax:**

```bash
sudo chown :[group-name] /company/[branch-folder]

```
**Creating the group:**


Create a Group for Each Branch:

You can create a group for each branch using the groupadd command.

```bash
sudo groupadd hr
sudo groupadd finance
sudo groupadd sales
sudo groupadd marketing
sudo groupadd it
```
**Add Users to Their Respective Branch Group:**

Once the groups are created, add each user to their relevant branch group using the usermod command.

```bash
sudo usermod -aG hr prajwal
sudo usermod -aG hr samarth
sudo usermod -aG finance ashray
sudo usermod -aG finance pavani
```
# Repeat for other users and their respective groups
Assign Folder Ownership to the Group:

Set each branch’s folder to be owned by its respective group (e.g., hr for the HR folder), as shown in the previous steps.

With this setup, only members of each branch group can access the files within their branch’s folder, based on the permissions assigned. This is an effective way to organize and secure access within an organization.

**Explanation:**

sudo: Executes the command with root privileges.

chown: Changes the ownership of a file or directory.
:[group-name]: Sets the folder ownership to a specific user group (replace [group-name] with the branch group, e.g., hr).

/company/[branch-folder]: Path to the folder you are changing ownership for (replace [branch-folder] with the specific branch folder).

**Example Usage:**

```bash
sudo chown :hr /company/HR
sudo chown :finance /company/Finance
sudo chown :sales /company/Sales
sudo chown :marketing /company/Marketing
sudo chown :it /company/IT
```
**Expected Output:**

If successful, no output appears, but ownership will be updated. You can verify with ls -l /company.