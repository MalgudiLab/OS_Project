# **Project Documentation: Branch File Access Management on Linux**

## **Project Overview**
The purpose of this project is to set up a file structure for an organization with multiple branches (HR, Finance, Sales, Marketing, and IT). Each branch will have its own directory, and users from each branch will be granted read, write, and delete permissions for files in their respective directories. The project also ensures that individual users within a branch have access to their personal folders where only they and their branch's group members can access the files.

## **Branches and Users**

The following users will be created, each belonging to their respective group (representing the branch):

1. **HR Group:**
   - Prajwal
   - Samarth
2. **Finance Group:**
   - Ashray
   - Pavani
3. **Sales Group:**
   - Mahith
   - Raghu
   - Pratham
4. **Marketing Group:**
   - Atrinandan
   - Rushil
5. **IT Group:**
   - Pavan
   - Abhinandan

Each user will have the ability to read, write, and delete files within their own branch folder.

## **Step-by-Step Setup**

### **Step 1: Directory Structure Creation**
We will create the following directories to store the files for each branch:

```bash
sudo mkdir -p /org/{HR,Finance,Sales,Marketing,IT}

sudo groupadd hr
sudo groupadd finance
sudo groupadd sales
sudo groupadd marketing
sudo groupadd it


# Create HR users and assign them to the HR group
sudo useradd -m -G hr prajwal
sudo useradd -m -G hr samarth

# Create Finance users and assign them to the Finance group
sudo useradd -m -G finance ashray
sudo useradd -m -G finance pavani

# Create Sales users and assign them to the Sales group
sudo useradd -m -G sales mahith
sudo useradd -m -G sales raghu
sudo useradd -m -G sales pratham

# Create Marketing users and assign them to the Marketing group
sudo useradd -m -G marketing atrinandan
sudo useradd -m -G marketing rushil

# Create IT users and assign them to the IT group
sudo useradd -m -G it pavan
sudo useradd -m -G it abhinandan

# Set ownership to root and group to HR for HR directory
sudo chown root:hr /org/HR
sudo chmod 770 /org/HR

# Set ownership to root and group to Finance for Finance directory
sudo chown root:finance /org/Finance
sudo chmod 770 /org/Finance

# Set ownership to root and group to Sales for Sales directory
sudo chown root:sales /org/Sales
sudo chmod 770 /org/Sales

# Set ownership to root and group to Marketing for Marketing directory
sudo chown root:marketing /org/Marketing
sudo chmod 770 /org/Marketing

# Set ownership to root and group to IT for IT directory
sudo chown root:it /org/IT
sudo chmod 770 /org/IT

# For HR Users
sudo mkdir /org/HR/prajwal /org/HR/samarth
sudo chown prajwal:hr /org/HR/prajwal
sudo chown samarth:hr /org/HR/samarth
sudo chmod 770 /org/HR/prajwal /org/HR/samarth

# Access files 
su - prajwal
cd /org/HR
ls -l

