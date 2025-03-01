# **Product Quality Analysis - Step-by-Step Guide**

## **Table of Contents**
1. [Introduction](#introduction)
2. [Workflow Overview](#workflow-overview)
3. [Step-by-Step Implementation](#step-by-step-implementation)
   - [Step 1: Add Chat Input Component](#step-1-add-chat-input-component)
   - [Step 2: Configure the Prompt Component](#step-2-configure-the-prompt-component)
   - [Step 3: Connect the OpenAI Component](#step-3-connect-the-openai-component)
   - [Step 4: Add Structured Output Component](#step-4-add-structured-output-component)
   - [Step 5: Parse Data for Analysis](#step-5-parse-data-for-analysis)
   - [Step 6: Display Results with Chat Output](#step-6-display-results-with-chat-output)
4. [Final Testing and Execution](#final-testing-and-execution)
5. [Conclusion](#conclusion)

---

## **Introduction**
This guide walks you through creating a **Product Quality Analysis** system in **Langflow**. This system allows users to input product details and receive AI-powered feedback on whether a product is damaged and eligible for a refund. ( Image Recognition)

---

## **Workflow Overview**
The system consists of the following components:
1. **Chat Input** – Users enter product details.
2. **Prompt** – Defines how the AI should analyze product condition.
3. **OpenAI Component** – Uses GPT-4-turbo to process inputs.
4. **Structured Output** – Extracts AI-generated insights in a structured format.
5. **Parse Data** – Converts structured data into readable output.
6. **Chat Output** – Displays the final response to the user.

---

## **Step-by-Step Implementation**

### **Step 1: Add Chat Input Component**
- Drag and drop a **Chat Input** component onto the Langflow canvas.
- This component allows users to input product details.
- No extra configuration is required.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lag21.png?raw=true)
---

### **Step 2: Configure the Prompt Component**
- Add a **Prompt** component and connect it to the **Chat Input**.
- In the **Template** section, enter the following prompt:

`Identify if the product is damaged.`

- This instructs the AI to assess the product condition.


![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang22.png?raw=true)

---

### **Step 3: Connect the OpenAI Component**
- Drag an **OpenAI** component onto the canvas.
- Connect it to the **Prompt** component.
- Configure the following settings:
- **Model Name:** `gpt-4-turbo`
- **Temperature:** `0.10` (ensures precise outputs)
- **OpenAI API Key:** Enter your API key.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang23.png?raw=true)

---

### **Step 4: Add Structured Output Component**
- Drag a **Structured Output** component onto the canvas.
- Connect it to the **OpenAI Component**.
- Set **Schema Name** as `image_classification`.
- Define the **Output Schema** for structured AI responses.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang24.png?raw=true)

---

### **Step 5: Parse Data for Analysis**
- Drag a **Parse Data** component and link it to the **Structured Output**.
- Set the **Template** as:

`Damaged: {Damaged} Refund : {refund}Description: {description} `

- This extracts relevant insights from AI-generated responses.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang25.png?raw=true)

---

### **Step 6: Display Results with Chat Output**
- Add a **Chat Output** component.
- Connect it to the **Parse Data** component.
- This ensures the final decision (damaged or not) is displayed to the user.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/lang26.png?raw=true)

---

## **Final Testing and Execution**
1. **Upload product image** in the **Chat Input** field.
2. **Run the workflow** and observe how the AI processes the information.
3. The **Chat Output** displays whether the product is damaged and eligible for a refund.

---

## **Conclusion**
You have successfully built a **Product Quality Analysis** system using Langflow. This workflow helps automate product condition evaluation, reducing manual efforts. You can further enhance it by integrating an image-processing model for visual inspection. 🚀

