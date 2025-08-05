# Task 2: Phishing Email Analysis Report

This report documents the end-to-end process of analyzing a suspicious email header to identify a phishing attempt. The analysis uses the free online tool `MXToolbox`.

---

### **Objective**

To demonstrate the process of extracting an email's technical header, using an external tool for analysis, and interpreting the results to definitively identify a phishing email.

---

## **Part 1: The Analysis Process**

The core of the analysis involves three practical steps: extracting the evidence, submitting it to a tool, and interpreting the output.

### **Step 1: Extracting the Email Header**

The first step is to get the full "header" source code of the suspicious email. The header contains technical details about the email's origin and path, which are hidden in a normal inbox view.

*   **How to find it:** In most email clients (like Gmail or Outlook), you can find this by clicking on the options for a specific email (usually three dots `...`) and selecting a menu item like:
    *   `Show original`
    *   `View message source`
    *   `View raw message`
*   **Action:** You would then copy the entire block of text that appears, starting from `Return-Path:` or `Received:`. For this report, the header text below was used.

### **Step 2: Submitting the Header to MXToolbox**

With the header copied, the next step is to use an online tool to parse this technical data into a human-readable format.

*   **Tool Used:** `MXToolbox Email Header Analyzer`
*   **Website:** `https://mxtoolbox.com/EmailHeaders.aspx`
*   **Action:** As shown in the screenshot below, the full email header was pasted into the text box on the website, and the "Analyze Header" button was clicked.

<img width="1354" height="675" alt="header prompt" src="https://github.com/user-attachments/assets/a8f4731a-05c4-4649-88ab-74f7bc3c0c25" />


---

## **Part 2: MXToolbox Analysis Results**

After clicking "Analyze Header," MXToolbox processed the data and provided a detailed report.The output clearly shows that the email is fraudulent.


### **Summary of Key Findings from MXToolbox**

The analysis provided conclusive proof of phishing through multiple technical failures.

| Header Field | Value / Finding | Analysis & Conclusion |
| :--- | :--- | :--- |
| **`Authentication-Results`** | `spf=fail`, `dkim=fail`, `dmarc=fail` | **This is definitive proof of a phish.** The email failed all three major authentication checks, proving it was not sent from an authorized server and its contents are not trustworthy. |
| **`From`** | `service@paypai.com` | This is a **look-alike domain**, deliberately misspelled to impersonate the real `paypal.com`. |
| **`Received`** | From `smtp.fakehost.com` | The email originated from a server named `fakehost.com`, which is clearly not an official PayPal server. |
| **`Reply-To`** | `no-reply@secure-paypal-review.com` | The reply address is another unofficial, suspicious domain, confirming the attacker's intent to deceive. |
| **`X-Mailer`** | `Microsoft Outlook Express 6.0` | The email was sent with obsolete software, not a professional corporate email system. |

<img width="1344" height="612" alt="mxtoolbox1" src="https://github.com/user-attachments/assets/a13fadbb-ac7b-49e2-a668-c0b451e3f299" />
<img width="1346" height="663" alt="mxtoolbox2" src="https://github.com/user-attachments/assets/d3a1cfa5-e5a8-4f90-a306-d54a45f1b3e6" />
<img width="1357" height="682" alt="mxtoolbox3" src="https://github.com/user-attachments/assets/b807866a-54a0-4645-b6d0-c40d44566287" />


---

### **Conclusion**

The process of analyzing the email header is a critical skill in threat detection. By taking the raw header data and processing it with a tool like MXToolbox, we were able to instantly uncover multiple, undeniable indicators of a phishing attack.

The **failed SPF, DKIM, and DMARC authentication results** provide the technical "smoking gun," while the deceptive domain names and server information confirm the social engineering intent. The email is **100% fraudulent**.


