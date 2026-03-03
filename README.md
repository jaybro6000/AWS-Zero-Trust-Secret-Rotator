# 🔑 AWS Zero-Trust Secret Rotator: Eliminating Hardcoded Credentials

A security-engineered automation project designed to remediate one of the most common cloud vulnerabilities: **hardcoded secrets**. This project implements **AWS Secrets Manager** to move from static, plain-text passwords to a dynamic, encrypted retrieval system using **Python (Boto3)** and **Least-Privilege IAM roles**.

---

## Architecture Overview
- **Storage:** AWS Secrets Manager (AES-256 Encryption)
- **Compute:** AWS Lambda (Event-driven execution)
- **Permissions:** IAM Service Roles (Granular resource-level access)
- **Observability:** Amazon CloudWatch Logs

---

## 📸 Step-by-Step Implementation

### Phase 1: Identifying the Security Gap
**1. The "Before" State:** A Python script containing hardcoded, plain-text credentials—a high-risk vulnerability that could lead to credential exposure in version control.
<img width="1366" height="551" alt="The_Zero_Trust_Secret_Rotator_1" src="https://github.com/user-attachments/assets/14d35d47-e1a6-4804-a288-8f4a04c8591b" />


### Phase 2: Building the Secure Vault
**2. Initializing Secrets Manager:** Creating a managed secret to move sensitive data out of the application code and into a secure, encrypted vault.
<img width="1366" height="585" alt="The_Zero_Trust_Secret_Rotator_2" src="https://github.com/user-attachments/assets/d1bca47c-8904-45f3-8a31-2ed83c0f6a0b" />

**3. Configuration & Metadata:** Defining the secret key-value pairs and setting up the administrative tags for tracking.
<img width="1366" height="583" alt="The_Zero_Trust_Secret_Rotator_3" src="https://github.com/user-attachments/assets/634775b7-3f4a-4a25-b1ee-118c545e3cf4" />

**4. Review & Finalization:** Final verification of the secret's encryption settings before deployment.
<img width="1366" height="581" alt="The_Zero_Trust_Secret_Rotator_4" src="https://github.com/user-attachments/assets/82ec4ebe-1b3b-4852-8fee-36e82337e0ea" />


### Phase 3: Identity & Governance (IAM)
**5. Crafting the Security Policy:** Writing a JSON-based IAM policy to strictly limit access to the `GetSecretValue` action.
<img width="1366" height="581" alt="The_Zero_Trust_Secret_Rotator_5" src="https://github.com/user-attachments/assets/accc7df4-60fc-4a7d-98d4-928360c0d068" />

**6. Enforcing Least Privilege:** Attaching the policy to the Lambda execution role, ensuring the "Zero-Trust" principle is met.
<img width="1366" height="583" alt="The_Zero_Trust_Secret_Rotator_6" src="https://github.com/user-attachments/assets/c3e2a9e6-6f97-4f67-83b3-60c1a9e0a5d2" />

**7. Trust Relationships:** Verifying the execution role's ability to interact with the Secrets Manager service securely.
<img width="1366" height="586" alt="The_Zero_Trust_Secret_Rotator_7" src="https://github.com/user-attachments/assets/d8df4a27-8e13-4de9-a511-b08dd6fea11c" />


### Phase 4: Automation & Execution
**8. Provisioning the Function:** Setting up the AWS Lambda environment to handle the secret rotation and retrieval logic.
<img width="1366" height="639" alt="The_Zero_Trust_Secret_Rotator_8" src="https://github.com/user-attachments/assets/ae546a08-fa2f-4d49-8fc9-e1d4014c0c0f" />

**9. Implementing the Boto3 Logic:** The "After" state. Rewriting the application logic to fetch secrets dynamically via the AWS SDK.
<img width="1366" height="585" alt="The_Zero_Trust_Secret_Rotator_9" src="https://github.com/user-attachments/assets/f61b759c-2acf-4102-8e9f-485805e35f32" />

**10. Configuring Environment Variables:** Ensuring the function knows which Secret ID to call without hardcoding the ID itself.
<img width="1366" height="586" alt="The_Zero_Trust_Secret_Rotator_10" src="https://github.com/user-attachments/assets/9663bebc-fcfd-432b-80da-3564594afcaa" />


### Phase 5: Verification & Audit
**11. Execution Testing:** Triggering a manual test to verify the end-to-end handshake between Lambda and Secrets Manager.
<img width="1366" height="539" alt="The_Zero_Trust_Secret_Rotator_11" src="https://github.com/user-attachments/assets/a93c1cf9-564f-431f-808a-ed6fa71ab5ed" />

**12. Final Proof of Success:** Detailed CloudWatch Logs showing a 200 OK response and successful secret retrieval without exposing the value.
<img width="1366" height="583" alt="The_Zero_Trust_Secret_Rotator_12" src="https://github.com/user-attachments/assets/a9c300c5-90f5-4899-b95c-8b1c9f67dac4" />


---

## 💡 Key Takeaways
- **Reduced Attack Surface:** Zero sensitive data exists in the source code.
- **Auditability:** Every secret access is now logged and traceable via CloudWatch.
- **Scalability:** New services can adopt this secure pattern without changing the underlying architecture.
