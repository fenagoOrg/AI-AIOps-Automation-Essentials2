# HR Policies Q&A - Step-by-Step Guide

## Table of Contents

**1. Introduction**

**2. Prerequisites**

**3. Workflow Steps**

**Step 1: Access Langflow Online**

**Step 2: Add Components to Your Workflow**

**Step 3: Running the Workflow**

**4. Benefits of This System**

**5. Conclusion**

**Introduction**

This guide will walk you through creating an HR Policies Q&A system using Langflow. This system allows users to ask questions about HR policies and receive AI-generated responses. Follow the steps below to build your own interactive HR assistant.

**Prerequisites**

- Before you begin, ensure you have the following:

- Access to Langflow Web Interface (No local installation required)

- OpenAI API Key (for accessing the language model)

**Workflow Steps**

**Step 1:** Access Langflow Online

1. Open your web browser.

2. Navigate to Langflow’s hosted platform.

3. Log in or sign up if required.

4. Start a new project.

**Step 2: Add Components to Your Workflow**

**1. File Component**

- Drag a File component onto the canvas.

- Set the Path to an HR policy document (e.g., HR_Policies.txt).

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang1.1.png?raw=true)

**2. Parse Data**

- Add a Parse Data component to extract text from the file.

- Set the Template to {text}.

- Connect the File Component to the Parse Data Component.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang1.2.png?raw=true)

**3. Prompt Component**

- Add a Prompt component to structure user questions.

- Use the template:

```html
Answer user's questions based on the document below:

---

{Document}

---

Question:
```
- Connect Parse Data to Prompt.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang1.4.png?raw=true)

**4. Chat Input Component**

- Add a Chat Input component for users to type their questions.

`Example: "What is the Maternity Leave policy?"`

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang1.3.png?raw=true)

**5. LLM Model (OpenAI)**

- Drag an OpenAI Component onto the canvas.

- Connect it to the Prompt Component.

- Input your OpenAI API Key.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang.15.png?raw=true)


**6. Chat Output Component**

- Add a Chat Output component.

- Connect it to the OpenAI Component to display responses.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang1.6.png?raw=true)


**Step 3: Running the Workflow**

- Upload an HR policy document.

- Enter a question in the Chat Input field.

- Run the flow and review the AI-generated response in the Chat Output field.

Benefits of This System

✔️ Quick access to HR policy details✔️ Reduces workload on HR teams✔️ Provides accurate and structured responses

**Adjust the connections as shown in the below image.**

**Final flow:**
![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/LANG!.png?raw=true)
