## Lab: Health Care Staffing Invoice Generator

### **Part 1: Account Setup and Getting Started**

### **Step 1: Access LangFlow**
1. Open your web browser and navigate to [LangFlow](https://www.langflow.org/).
2. Click on the **Sign Up** button in the top-right corner of the homepage.

# **Use Case 1: Customer Complaint Resolver**

### **Step 2:Create a New Langflow Project**
1. Open Langflow and click Blank Flow to start from scratch.
2. Name your flow: Customer Complaint Resolver.
3. Save to store your project.(Just click Crtl + S)

![](./images/1.png)

![](./images/2.png)


### **Step 3: Add an Input Node (User Complaint Submission)

1. Drag and drop the Input node onto the canvas.
2. Select Chat Input to allow users to submit their complaints.
3. Configure Input Node:
- Prompt: "Describe your issue in detail, including order ID (if applicable)."
- Enable history tracking to retrieve previous complaints from a customer.
4.Save.


### Step 4: Add a Data Storage Node (Retrieve Past Complaints)]

1. Drag and drop the Vector Store node to store and retrieve past complaint records.
2. Choose Datastax Astra DB (or another vector database like Pinecone).
3. Connect the Chat Input node to the Vector Store node.

---



### **Objective**:
Create a flow to:
- Generate invoices for clients.
- Calculate recruiter commissions.
- Summarize placement data.

