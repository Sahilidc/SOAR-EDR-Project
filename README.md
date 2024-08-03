# **Title:** SOAR EDR Project - Automated Detection and Response for Credential Access Attacks

![image](https://github.com/user-attachments/assets/9be0f952-48aa-434f-90b7-b85bf316e52b)

## **Description:** This project demonstrates an automated Security Orchestration, Automation, and Response (SOAR) system integrated with Endpoint Detection and Response (EDR) to detect and respond to credential access attacks using the Lazagne hack tool.
![Screenshot 2024-08-03 233316](https://github.com/user-attachments/assets/9b0ce437-d28f-4770-9f05-6d68e95cd751)


----------

### **Story:**


![Screenshot 2024-08-03 222323](https://github.com/user-attachments/assets/8ade0ed6-284f-44d9-84c6-19b8148c256d)


1.  **Create Detection in LimaCharlie:**
    
    -   LimaCharlie is configured to detect the use of the Lazagne hack tool on endpoint devices.
    -   When the Lazagne tool is detected, an alert is generated within LimaCharlie.
2.  **Alert Forwarded to Tines:**
    
    -   The alert from LimaCharlie is forwarded to Tines, a security orchestration platform, for further processing.
    -   Tines receives the alert with the following details:
        -   Time of detection
        -   Computer Name
        -   Source IP
        -   Process Name
        -   Command Line used
        -   File Path
        -   Sensor ID
        -   Link to the detection (if applicable)
3.  **Notifications via Slack and Email:**
    
    -   Tines sends the alert details to both Slack and Email.
    -   The message contains:
        -   Time of detection
        -   Computer Name
        -   Source IP
        -   Process Name
        -   Command Line used
        -   File Path
        -   Sensor ID
        -   Link to the detection (if applicable)
4.  **User Prompt for Isolation Decision:**
    
    -   Tines prompts the user to decide whether to isolate the compromised machine.
    -   The prompt is sent to both Slack and Email with options: "Yes" or "No".
5.  **User Decision - Yes (Isolate the Machine):**
    
    -   If the user chooses "Yes", Tines triggers LimaCharlie to isolate the compromised machine automatically.
    -   A message is sent to Slack with the isolation status:
        -   Message: "The computer <computer> has been isolated."
6.  **User Decision - No (Do Not Isolate the Machine):**
    
    -   If the user chooses "No", LimaCharlie does not isolate the machine.
    -   A message is sent to Slack requesting further investigation:
        -   Message: "The computer <computer> was not isolated, please investigate."

----------
### **EVENT**

![Opera Snapshot_2024-08-03_233124_app limacharlie io](https://github.com/user-attachments/assets/d7a96611-bc43-490c-95ae-3b0f75030e7e)

### **Detection Of LaZagne**

![Opera Snapshot_2024-08-03_233354_app limacharlie io](https://github.com/user-attachments/assets/96325267-48c0-4132-8851-d3d60ef8250e)

### **Result of Detect Rule**

![Opera Snapshot_2024-08-03_233558_app limacharlie io](https://github.com/user-attachments/assets/69a4caf8-7919-4c34-8bce-13f3860ce4cc)


**Workflow Overview:**

1.  **Detection:**
    -   LimaCharlie detects the usage of the Lazagne hack tool on a compromised machine.
    -   ![Opera Snapshot_2024-08-03_233010_app limacharlie io](https://github.com/user-attachments/assets/74034d99-b51a-4f4d-a2bc-e4a24945ff0d)

2.  **Alert Generation:**
    -   An alert is generated in Tines with detailed information about the detection.
    -   ![Opera Snapshot_2024-08-03_233022_github com](https://github.com/user-attachments/assets/a75a3233-9f20-4b1d-a314-3ae2eed018d1)

    -   
3.  **User Notification:**
    -   The alert details are sent via Slack and Email to notify the user.
    -   ![Opera Snapshot_2024-08-04_000247_app slack com](https://github.com/user-attachments/assets/09c3ee40-ff3e-4a99-af8f-94c777f5870b)

4.  **User Decision:**
    -   The user is prompted to decide whether to isolate the machine.
    -   ![image](https://github.com/user-attachments/assets/799051ee-15a2-4f10-93f6-f77d2c295b22)

5.  **Automated Response:**
    -   If the user chooses to isolate the machine, LimaCharlie performs the isolation, and Slack is updated with the isolation status.
    -   If the user decides not to isolate the machine, a notification is sent to Slack requesting further investigation.

**Note:** This project is a proof-of-concept (PoC) designed to enhance cybersecurity defenses by integrating SOAR capabilities with EDR for efficient and automated incident response. The detection rule specifically targets the Lazagne tool to demonstrate the system's effectiveness in handling credential access threats.
