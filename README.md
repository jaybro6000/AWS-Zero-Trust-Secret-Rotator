# 🔑 AWS Zero-Trust Secret Rotator

Serverless **Security Automation** project focused on eliminating hardcoded credentials in source code. By leveraging **AWS Secrets Manager** and **IAM Least Privilege** policies, this system retrieves sensitive data dynamically at runtime, significantly reducing the application's attack surface and adhering to Zero-Trust principles. ✨
---

## Full Implementation Gallery

### Phase 1: Security Assessment
1. **The Vulnerability:** Hardcoded credentials in a script.
<img width="1366" height="551" alt="The_Zero_Trust_Secret_Rotator_1" src="https://github.com/user-attachments/assets/146760ff-9971-4226-ac94-557e8bc85a4b" />

2. **Environment Analysis:** Identifying the target resource requiring access.
<img width="1366" height="585" alt="The_Zero_Trust_Secret_Rotator_2" src="https://github.com/user-attachments/assets/fa4aad10-a0a7-45ec-8204-f3914ec886ca" />


### Phase 2: Secure Configuration
3. **Secrets Vaulting:** Initializing the secret in AWS Secrets Manager.
<img width="1366" height="583" alt="The_Zero_Trust_Secret_Rotator_3" src="https://github.com/user-attachments/assets/1a8ae807-8f04-4386-b51a-0ecafeeb7d38" />

4. **Encryption Settings:** Configuring the KMS keys for the secret.
<img width="1366" height="581" alt="The_Zero_Trust_Secret_Rotator_4" src="https://github.com/user-attachments/assets/10238716-fa88-486f-8d0f-b9c66d63938d" />

5. **Secret Metadata:** Finalizing the secret naming and description.
<img width="1366" height="581" alt="The_Zero_Trust_Secret_Rotator_5" src="https://github.com/user-attachments/assets/f1992cc8-af51-4ed3-a6ae-9bad388899f2" />


### Phase 3: Identity & Access Management
6. **Policy Creation:** Writing the JSON policy for secret access.
<img width="1366" height="583" alt="The_Zero_Trust_Secret_Rotator_6" src="https://github.com/user-attachments/assets/ad521109-d8a5-4571-ba5f-558597928da3" />

7. **Role Assignment:** Attaching the policy to the Lambda execution role.
<img width="1366" height="586" alt="The_Zero_Trust_Secret_Rotator_7" src="https://github.com/user-attachments/assets/c2f54b99-6fa1-41c9-ae00-97064e5e40fd" />

8. **Trust Relationship:** Verifying the service can assume the role.
<img width="1366" height="639" alt="The_Zero_Trust_Secret_Rotator_8" src="https://github.com/user-attachments/assets/4af13b26-e41e-47e1-9f33-7a1f095fc811" />


### Phase 4: Automation & Verification
9. **Lambda Environment:** Setting up the Python 3.x environment.
<img width="1366" height="585" alt="The_Zero_Trust_Secret_Rotator_9" src="https://github.com/user-attachments/assets/8f226548-3188-4fe6-9ce9-e0cea702abd8" />

10. **The Logic:** Implementing the Boto3 `get_secret_value` call.
<img width="1366" height="586" alt="The_Zero_Trust_Secret_Rotator_10" src="https://github.com/user-attachments/assets/94435426-2641-407e-ae51-b867dd6cd04b" />

11. **Testing:** Triggering the test event for the rotator.
<img width="1366" height="539" alt="The_Zero_Trust_Secret_Rotator_11" src="https://github.com/user-attachments/assets/763fe44c-f5b1-40da-8bc0-f9aaf33eb8b7" />

12. **Final Audit:** Success logs in CloudWatch proving secure retrieval.
<img width="1366" height="583" alt="The_Zero_Trust_Secret_Rotator_12" src="https://github.com/user-attachments/assets/a331bbed-a56b-41df-a5b6-5aca18bad162" />
