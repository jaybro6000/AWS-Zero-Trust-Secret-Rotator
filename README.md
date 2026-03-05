# The Zero Trust Secret Rotator

## **Project Overview**

This project demonstrates a **Zero Trust** approach to credential management by automating the rotation of sensitive database passwords. Using **AWS Secrets Manager** and **AWS Lambda**, the system ensures that long-lived credentials are eliminated, significantly reducing the impact of potential credential leakage.

## **Features**

* **Automated Lifecycle:** Moves away from static, hardcoded passwords to dynamically generated credentials.
* **Least Privilege IAM:** Uses a custom execution role with scoped permissions to interact only with required secrets.
* **Audit Logging:** Integrated with **Amazon CloudWatch** to provide a full audit trail of rotation events.
* **Serverless Architecture:** Utilizes Python 3.12 on AWS Lambda for a cost-effective, scalable security solution.

## **Tech Stack**

* **Cloud Provider:** AWS
* **Services:** Secrets Manager, Lambda, IAM, CloudWatch
* **Language:** Python (Boto3 SDK)

---

## **Deployment Steps**

### **1. Store the Initial Secret**

* Create a new secret in **AWS Secrets Manager**.
* Select **"Other type of secret"** and define a key-value pair (e.g., `db_password`).
***Shows the naming convention `Production/Database/Password`.*
* **<img width="1366" height="585" alt="The_Zero_Trust_Secret_Rotator_2" src="https://github.com/user-attachments/assets/2ee3738d-7150-4471-9919-e705503486b1" />

### **2. Create the Rotation Lambda**

* Author a Lambda function from scratch using the **Python 3.12** runtime.
***<img width="1366" height="581" alt="The_Zero_Trust_Secret_Rotator_5" src="https://github.com/user-attachments/assets/ce93ef30-820f-4359-b499-c07e01392a5f" />

### **3. Configure Least Privilege Permissions**

* Attach a policy to the Lambda's execution role allowing `secretsmanager:UpdateSecret`.
*Shows the IAM policy attachment.*
* **<img width="1366" height="586" alt="The_Zero_Trust_Secret_Rotator_7" src="https://github.com/user-attachments/assets/1977d533-1352-4875-8283-a547cee48f5c" />

### **4. Implement the Rotation Logic**

* The script generates a new 16-character alphanumeric string and updates the `SecretString` in the vault.
* **<img width="1366" height="639" alt="The_Zero_Trust_Secret_Rotator_8" src="https://github.com/user-attachments/assets/fc4a0f08-04c7-4159-93a7-539ea7665136" />
** - *Shows the Python code implementation.*

---

## **Validation & Monitoring**

### **Execution Logs**

When the function is triggered, **CloudWatch** captures the success message and identifies the tail end of the new password for verification.

* **<img width="1366" height="539" alt="The_Zero_Trust_Secret_Rotator_11" src="https://github.com/user-attachments/assets/d6f6b951-1a1a-4b20-94f2-8d5b50457a92" />
** - *Shows the successful log events in CloudWatch.*

### **Vault Confirmation**

The final verification confirms that the secret value in the vault matches the rotation log, proving the automation worked as intended.

* **<img width="1366" height="583" alt="The_Zero_Trust_Secret_Rotator_12" src="https://github.com/user-attachments/assets/4ce6f15c-40c4-4b9f-8318-851d6df3a605" />
** - *Shows the updated secret value ending in the correct characters.*

---

## **Key Security Takeaways**
- **Reduced Attack Surface:** Zero sensitive data exists in the source code.
- **Auditability:** Every secret access is now logged and traceable via CloudWatch.
- **Scalability:** New services can adopt this secure pattern without changing the underlying architecture.
