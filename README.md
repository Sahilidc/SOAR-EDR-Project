

## **Title:** SOAR EDR Project - Automated Detection and Response for Credential Access Attacks

**Description:** This project demonstrates an automated Security Orchestration, Automation, and Response (SOAR) system integrated with Endpoint Detection and Response (EDR) to detect and respond to credential access attacks using the Lazagne hack tool.

----------

**Story:**

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

**Workflow Overview:**

1.  **Detection:**
    -   LimaCharlie detects the usage of the Lazagne hack tool on a compromised machine.
2.  **Alert Generation:**
    -   An alert is generated in Tines with detailed information about the detection.
3.  **User Notification:**
    -   The alert details are sent via Slack and Email to notify the user.
4.  **User Decision:**
    -   The user is prompted to decide whether to isolate the machine.
5.  **Automated Response:**
    -   If the user chooses to isolate the machine, LimaCharlie performs the isolation, and Slack is updated with the isolation status.
    -   If the user decides not to isolate the machine, a notification is sent to Slack requesting further investigation.

**Note:** This project is a proof-of-concept (PoC) designed to enhance cybersecurity defenses by integrating SOAR capabilities with EDR for efficient and automated incident response. The detection rule specifically targets the Lazagne tool to demonstrate the system's effectiveness in handling credential access threats.
