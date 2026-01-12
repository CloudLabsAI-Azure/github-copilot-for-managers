# Day1: Beginner Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 1 | Microsoft Purview DLP | Easy | What is the primary purpose of creating a Data Loss Prevention (DLP) policy in Microsoft Purview? | To encrypt all Microsoft 365 data by default | To identify, monitor, and prevent sensitive data from being shared inappropriately | To back up user emails automatically for compliance | To restrict user sign-ins based on device location | Choice 2 |
| 2 | Microsoft Purview DLP | Easy | In the lab, which Microsoft 365 workload was selected as the scope for the Credit Card DLP policy? | Microsoft Teams | SharePoint Online | Exchange email | OneDrive for Business | Choice 3 |
| 3 | Microsoft Purview DLP | Easy | What happens when a user attempts to send an email containing a credit card number that matches the DLP rule? | The email is delivered but logged for review | The email is encrypted and sent | The email is blocked and the user is notified | The user account is suspended | Choice 3 |
| 4 | Device Onboarding | Easy | Why is device onboarding required in Microsoft Purview? | To enable device encryption | To monitor and protect sensitive data on endpoints | To deploy Windows updates | To manage device hardware inventory | Choice 2 |

# Day1: Intermediate Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 5 | Device Onboarding | Intermediate | When onboarding a Windows device using the local script method, what must be done before running the script? | Rename the script file | Disable Windows Defender | Unblock the script in file properties | Move the script to the system folder | Choice 3 |
| 6 | Sensitivity Labels | Intermediate | What is the purpose of enabling Auto-labeling when creating a sensitivity label? | Apply labels only when users select them manually | Automatically apply labels when sensitive content is detected | Encrypt all documents regardless of content | Archive labeled files automatically | Choice 2 |
| 7 | Microsoft Purview Roles | Intermediate | Which role group assignment is required for a user to manage DLP policies and sensitivity labels? | Global Reader | Security Administrator | Exchange Administrator | Teams Administrator | Choice 2 |
| 8 | DSPM for AI | Intermediate | What is the purpose of enabling Microsoft Purview Audit in DSPM for AI? | Block AI prompts automatically | Record AI-related user and admin activities | Train Copilot responses | Encrypt AI prompts and responses | Choice 2 |

# Day1: Advanced Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 9 | DSPM for AI | Advanced | After completing DSPM for AI recommendations, where can you review detailed AI prompts and responses? | Microsoft Defender for Endpoint | Microsoft Purview Activity Explorer | Azure Monitor Logs | Compliance Manager | Choice 2 |
| 10 | AI Security Governance | Advanced | Why is Microsoft Purview integrated with Microsoft Defender for Cloud and Defender for AI? | To replace Azure Security Center | To centralize monitoring and governance of data and AI security | To deploy AI models automatically | To reduce licensing requirements | Choice 2 |

# Day2: Beginner Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 1 | Entra ID App Consent | Easy | What is the main goal of restricting user consent to Microsoft-verified publishers in Microsoft Entra ID? | Prevent users from signing in to any third-party apps | Allow access only to Microsoft-owned SaaS products | Reduce the risk of users granting high-impact permissions to untrusted apps | Force all requests through Conditional Access | Choice 3 |
| 2 | Entra ID Permissions | Easy | In Entra ID permission classifications, why are certain permissions marked as low risk? | They cannot access user data | They are frequently used and have minimal security impact | They bypass admin consent | They expire automatically | Choice 2 |
| 3 | Admin Consent | Easy | What is the purpose of enabling Admin consent requests? | Automatically approve permissions | Allow users to request permissions requiring admin approval | Disable user consent | Assign app ownership automatically | Choice 2 |
| 4 | Conditional Access | Easy | Why did you create a Named Location using your external IP address? | Whitelist all internet traffic | Define a trusted corporate network | Improve authentication performance | Bypass MFA | Choice 2 |

# Day2: Intermediate Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 5 | Authentication Strength | Intermediate | What security risk is mitigated by disabling SMS-based authentication? | Password spraying | Token replay | SMS interception and SIM-swap attacks | Browser hijacking | Choice 3 |
| 6 | Conditional Access | Intermediate | Why was the Conditional Access policy initially scoped to one test user? | Single-user limitation | Prevent tenant-wide lockouts | Trusted locations limitation | Reduce licensing | Choice 2 |
| 7 | Conditional Access | Intermediate | What does the Exclude trusted locations setting accomplish? | Blocks known networks | Allows access only from trusted locations | Forces MFA on trusted networks | Disables enforcement | Choice 2 |
| 8 | Security Defaults | Intermediate | Why is Security Defaults disabled before creating custom Conditional Access policies? | Conflicts with custom rules | Reduces authentication strength | CA cannot be enabled otherwise | No MFA support | Choice 1 |

# Day2: Advanced Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 9 | Conditional Access Logs | Advanced | If sign-in logs show the Location condition was not matched, what does it indicate? | Policy failed | Sign-in from trusted location | MFA bypassed | User excluded | Choice 2 |
| 10 | Authentication Strength | Advanced | Why is Authentication Strength enforced specifically for Salesforce? | Cannot be tenant-wide | Contains sensitive business data | Replaces CA | No MFA support | Choice 2 |

# Day3: Beginner Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 1 | Compliance Manager | Easy | What is the primary purpose of creating an Assessment in Compliance Manager? | Enforce configs | Track compliance against a regulation | Generate playbooks | Replace DLP | Choice 2 |
| 2 | Compliance Scope | Easy | Why select specific services when creating an assessment? | Reduce cost | Scope controls to relevant workloads | Enable remediation | Reduce time | Choice 2 |
| 3 | Compliance Controls | Easy | What does a Failed control status indicate? | Out of scope | Not evaluated | At least one failed improvement action | Microsoft incomplete | Choice 3 |
| 4 | Microsoft Actions | Easy | What is the purpose of the Microsoft actions tab? | Third-party actions | Microsoft-managed compliance actions | Failed customer actions | License tracking | Choice 2 |

# Day3: Intermediate Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 5 | Assessment Groups | Intermediate | Why group assessments in Compliance Manager? | Improve performance | Organize related assessments | Enforce inheritance | ISO requirement | Choice 2 |
| 6 | Progress Tracking | Intermediate | What does the Progress tab primarily show? | Microsoft actions only | Completion percentage and points | Security alerts | User logs | Choice 2 |
| 7 | Improvement Actions | Intermediate | What is an Improvement Action? | Incident response | Required step to meet a control | Security baseline | Training task | Choice 2 |
| 8 | Adaptive Protection | Intermediate | Why prefer Custom setup over Quick setup? | Quick setup disables alerts | Granular control | Deprecated | Faster | Choice 2 |

# Day3: Advanced Level

| Sr No | Topic | Difficulty Level | Question Text | Answer Choice 1 | Answer Choice 2 | Answer Choice 3 | Answer Choice 4 | Correct Answer |
|------|------|------------------|---------------|-----------------|-----------------|-----------------|-----------------|----------------|
| 9 | AI Red Teaming | Advanced | What is the main security benefit of the AI Red Teaming Agent? | Blocks prompts | Simulates adversarial behavior | Replaces filters | Generates reports | Choice 2 |
| 10 | Red Teaming Auth | Advanced | Why is Azure CLI authentication used for the Red Teaming Agent? | Permanent access | Secure identity-based access | Bypass CA | Offline execution | Choice 2 |