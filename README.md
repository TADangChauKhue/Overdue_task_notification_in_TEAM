# Overdue_Task_Notifications_Teams

Automated weekly notification system that posts reminders in a Microsoft Teams channel for project tasks with passed target dates. This flow is built using Power Automate and runs under a service account to ensure reliability, scalability, and security.

## Introduction

In our IT department, project progress is tracked via a centralized reporting dashboard that includes key KPIs. One of the most important KPIs is the **number of tasks that have exceeded their target dates**. This Power Automate flow helps automate the follow-up process by sending a notification in Teams every Friday, ensuring that overdue tasks are addressed in a timely manner.

To improve maintainability and security, this flow is executed using a **dedicated service account**, ensuring continuity even if individual team members leave the company.

---

## 1. Business Problem

• How can we systematically remind project teams of overdue tasks each week?  
• How do we ensure the flow remains active regardless of personnel changes?  
• How do we filter, format, and send alerts without manual intervention?

---

## 2. Flow Logic (Power Automate)

### 🟦 Trigger:
- **Recurrence:** The flow runs automatically **every Friday**.

### 🟪 Steps:

1. **Get query results**  
   Connects to the source system (e.g., Azure DevOps or other reporting database) to retrieve all current task data.

2. **Initialize variable**  
   Sets up a working variable to process task information.

3. **Apply to each (loop)**  
   Iterates over the task list to check if the **target date has passed**.

4. **Initialize list variable (unique)**  
   Stores the unique list of persons assigned to tasks with overdue target dates. This ensures that each person's name appears only once in the final notification, even if they have multiple overdue tasks.

5. **Select**  
   Filters and formats the data to produce a **clean list of responsible persons** with at least one overdue task. This ensures clarity and focus in the message.

6. **Post message in a chat or channel**  
   Sends a **summary notification** directly into a Microsoft Teams channel to alert all stakeholders.

7. **Post card in a chat or channel (optional)**  
   Posts a visually rich adaptive card summarizing the overdue task information. The card includes a direct link to the reporting dashboard in Azure DevOps, allowing each person to quickly access and update their tasks. This ensures fast action and improves accountability.

## 3. Special Features

- 🛡️ **Service Account Execution:**  
  The flow runs under a **dedicated service account**, ensuring the automation:
  - Is not tied to a personal identity  
  - Remains operational even if team members change  
  - Complies with IT security best practices

- 🗓️ **Weekly Rhythm:**  
  Automatically alerts the team **every Friday** so actions can be taken before the next planning cycle.

- 🔄 **Scalable Setup:**  
  Easily adaptable to multiple project teams or departments.

## Overview and Example Output

Flow
![image](https://github.com/user-attachments/assets/4a76eea3-9327-4e84-b0c4-78a0158fe3d0)

Output
![image](https://github.com/user-attachments/assets/d1296dd0-8f00-4368-b264-f0556c85a22a)



