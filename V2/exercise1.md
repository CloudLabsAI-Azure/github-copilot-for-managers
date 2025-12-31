# Exercise 1: Understanding GitHub Copilot Features & Governance

### Estimated Duration: 45 Minutes

## Overview

In this exercise, you will explore GitHub Copilot's administrative capabilities from a manager's perspective. You'll learn how to configure organizational policies, manage feature access, understand the different Copilot capabilities, and implement governance best practices. This foundational knowledge is essential for effectively managing Copilot adoption across your development teams.

> **Why This Matters for Managers:** Before measuring Copilot's impact, you need to understand what you're managing. This exercise ensures you can confidently answer questions from leadership about security, compliance, and feature controls.

## Objectives

You will be able to complete the following tasks:

- Task 1: Understand GitHub Copilot capabilities and what developers experience
- Task 2: Navigate Copilot administrative settings and policy management
- Task 3: Configure feature controls and content exclusions
- Task 4: Implement governance best practices for your organization

## Prerequisites

- You are an **Organization Owner** of the target GitHub organization.
- GitHub Copilot Business or Enterprise is licensed for the organization.

---

## Task 1: Understanding GitHub Copilot Capabilities

In this task, you will learn about the different GitHub Copilot features and understand what developers experience when using Copilot. This knowledge helps you set realistic expectations and have informed conversations with your teams.

### A. Copilot Feature Overview

GitHub Copilot provides several AI-powered capabilities that help developers write code faster:

| Feature | Description | Manager Insight |
|---------|-------------|-----------------|
| **Code Completions** | AI suggests code as developers type in their IDE | Core feature - high volume of suggestions, key metric for adoption |
| **Copilot Chat (IDE)** | Conversational AI within VS Code, JetBrains, etc. | Deep integration - developers ask questions without leaving their editor |
| **Copilot Chat (GitHub.com)** | Chat interface on GitHub website | Accessible without IDE - good for code review, documentation |
| **PR Summaries** | AI-generated pull request descriptions | Saves time on documentation, improves PR quality |
| **CLI Suggestions** | Command-line assistance | Helps with DevOps tasks and terminal commands |
| **Copilot in GitHub Mobile** | AI assistance on mobile app | On-the-go code review and chat |

> **Manager Insight:** When reviewing adoption metrics, you'll see data for each of these features. Understanding what they do helps you interpret whether your teams are using Copilot effectively or only scratching the surface.

### B. Understanding the Developer Experience

1. In your browser, navigate to **GitHub.com** and sign in with your organization credentials.

   ![](../media/v2-ex1-github-signin.png)

1. Let's explore what Copilot Chat looks like on GitHub.com. Click the **Copilot icon** in the top navigation bar (if available for your organization).

   ![](../media/v2-ex1-copilot-chat-icon.png)

   > **What Developers See:** This chat interface allows developers to ask questions about code, get explanations, and receive coding assistance directly on GitHub.com - even when they're not in their IDE.

1. Explore the Copilot Chat interface:
   - Notice the **context awareness** - Copilot understands which repository you're viewing
   - See how developers can ask **natural language questions** about code
   - Observe the **code suggestion format** with syntax highlighting

   > **Manager Insight:** Developers who use Copilot Chat (both IDE and web) tend to show higher engagement levels. If your usage reports show low chat interactions, it may indicate a training opportunity.

### C. Copilot Business vs. Enterprise Features

Understanding the differences helps you make licensing decisions:

| Feature | Copilot Business | Copilot Enterprise |
|---------|------------------|-------------------|
| Code completions | ✅ | ✅ |
| Copilot Chat | ✅ | ✅ |
| PR Summaries | ✅ | ✅ |
| CLI suggestions | ✅ | ✅ |
| Organization policy controls | ✅ | ✅ |
| Usage metrics & reporting | ✅ | ✅ |
| **Knowledge Bases** | ❌ | ✅ |
| **Fine-tuned models** | ❌ | ✅ |
| **Audit logs (advanced)** | Basic | ✅ Advanced |

> **Decision Point:** If your organization has proprietary coding standards, internal libraries, or compliance requirements for detailed audit trails, Copilot Enterprise provides additional capabilities.

---

## Task 2: Navigate Copilot Administrative Settings

In this task, you will navigate the GitHub Copilot administrative area and understand the different configuration options available to organization owners.

1. In the top-right corner of GitHub, click your **profile picture (1)** and select **Your organizations (2)** from the dropdown menu.

   ![](../media/gt-co-ex1-g1.png)

1. On the Organizations page, locate and click your organization **contoso-impact** where you have Owner permissions.

   ![](../media/gt-co-ex1-g2.png)

1. Navigate to the **Settings** tab from the top navigation menu.

   ![](../media/gt-co-ex1-g3.png)

### A. Understanding the Copilot Settings Structure

1. In the left sidebar, locate the **Code, planning, and automation** section and expand **Copilot**.

   ![](../media/gt-co-ex1-g4.png)

   You'll see several sub-sections:

   | Section | Purpose | Manager Use Case |
   |---------|---------|------------------|
   | **Access** | Manage who can use Copilot | License allocation, team enablement |
   | **Policies** | Configure feature permissions | Security controls, feature rollout |
   | **Content exclusions** | Exclude files/repos from Copilot | IP protection, sensitive code |

   > **Manager Insight:** These three areas give you complete control over how Copilot is used in your organization. Understanding them is essential for governance discussions with security and compliance teams.

### B. Explore Access Management

1. Click on **Access** under the Copilot section.

   ![](../media/gt-co-ex1-g4.png)

1. On the Access management page, you can see:
   - **Total seats purchased** vs. **seats in use**
   - **List of users** with Copilot access
   - **Pending invitations**

   > **Manager Insight:** This is where you'll come to understand license utilization. If you have seats purchased but not assigned, that's wasted budget. If all seats are used but you have developers waiting, you may need to expand licensing.

1. Review the user list and note:
   - Which team members have access
   - Their last activity date
   - Whether they've accepted the invitation

   > **Best Practice:** Regularly review this list to identify:
   > - Users with access but no activity (potential training need)
   > - Active users who could be Copilot champions
   > - Pending invitations that need follow-up

---

## Task 3: Configure Policies and Feature Controls

In this task, you will explore and configure Copilot policies that control which features are enabled for your organization.

### A. Navigate to Policies

1. In the left sidebar under Copilot, click **Policies**.

   ![](../media/v2-ex1-policies-nav.png)

1. Review the available policy settings:

   | Policy | Options | Recommendation |
   |--------|---------|----------------|
   | **Suggestions matching public code** | Allow / Block | Consider blocking for IP-sensitive environments |
   | **Copilot Chat in IDE** | Enabled / Disabled | Enable - high value feature |
   | **Copilot Chat on GitHub.com** | Enabled / Disabled | Enable - accessible to all developers |
   | **Copilot in the CLI** | Enabled / Disabled | Enable for DevOps teams |
   | **Copilot pull request summaries** | Enabled / Disabled | Enable - saves documentation time |

   > **Security Insight:** The "Suggestions matching public code" policy is often a topic in security reviews. When set to "Block," Copilot will not show suggestions that match public code, reducing potential licensing concerns.

### B. Understanding Policy Inheritance

Policies can be set at different levels:

```
Enterprise (if applicable)
    └── Organization (your level)
            └── Repository (can override)
```

> **Manager Insight:** As an Organization Owner, your policy settings become the default for all repositories. Repository admins can be allowed to override these settings or be locked into your organizational policy.

### C. Feature Rollout Strategy

When rolling out Copilot features, consider a phased approach:

| Phase | Features Enabled | Target Users |
|-------|------------------|--------------|
| Pilot (Week 1-2) | Code completions only | 5-10 developers |
| Expand (Week 3-4) | Add Copilot Chat | Early adopters (20-30) |
| Full Rollout | All features | Organization-wide |

> **Manager Insight:** Starting with code completions allows developers to get comfortable with AI suggestions before introducing chat and other advanced features. This builds confidence and reduces resistance.

---

## Task 4: Configure Content Exclusions (Read Only)

Content exclusions allow you to prevent Copilot from accessing specific files or repositories. This is critical for protecting intellectual property and sensitive code.

### A. Understanding Content Exclusions

1. In the left sidebar under Copilot, click **Content exclusions**.

   ![](../media/v2-ex1-content-exclusions.png)

1. Review the content exclusion options:

   | Exclusion Type | Example | Use Case |
   |---------------|---------|----------|
   | **Repository exclusion** | `secret-sauce-repo` | Entire repo contains proprietary algorithms |
   | **Path exclusion** | `**/credentials/**` | Specific folders with sensitive data |
   | **File pattern** | `*.env, *.key` | Configuration files with secrets |

   > **Security Best Practice:** Work with your security team to identify:
   > - Repositories containing trade secrets or proprietary code
   > - Configuration files that might contain credentials
   > - Any code subject to export controls or regulatory requirements

### B. Common Exclusion Patterns

Here are recommended exclusion patterns for most organizations:

```
# Credentials and secrets
**/credentials/**
**/.env
**/*.key
**/*.pem
**/secrets/**

# Proprietary algorithms (customize for your org)
**/core-algorithm/**
**/trading-engine/**

# Compliance-sensitive areas
**/hipaa/**
**/pci/**
```

> **Manager Insight:** Content exclusions don't prevent developers from using Copilot - they just ensure Copilot doesn't train on or suggest code from these protected areas. This is a key talking point for security discussions.

---

## Task 5: Governance Best Practices for Managers

This task covers the non-technical aspects of Copilot governance that managers need to address.

### A. Creating an Organizational Copilot Policy

Work with your legal and compliance teams to establish:

1. **Acceptable Use Guidelines**
   - What types of code can be developed with Copilot assistance?
   - Are there restrictions for client-facing or regulated projects?
   - How should developers review AI-generated code?

2. **Code Review Requirements**
   - Should AI-generated code have additional review?
   - How do you ensure code quality and security?
   - What documentation is required?

3. **Training Requirements**
   - Do developers need training before using Copilot?
   - Are there resources for learning best practices?
   - How do you handle developers who are resistant?

> **Manager Insight:** Having a written policy helps answer questions from auditors, new employees, and leadership. It also sets clear expectations for developers.

### B. Addressing Common Developer Concerns

As a manager, you'll encounter these concerns:

| Concern | Response |
|---------|----------|
| "Will Copilot replace my job?" | Copilot is a tool that handles routine coding, letting you focus on creative problem-solving and architecture |
| "Is the code secure?" | All code should go through your normal review process; Copilot assists but doesn't replace developer judgment |
| "Does it learn from my code?" | Copilot Business/Enterprise does not train on your private code |
| "What about licensing?" | Configure the "block public code matches" policy to address concerns |

### C. Setting Team Adoption Goals

Establish realistic metrics for your teams:

| Metric | Target (Month 1) | Target (Month 3) | Target (Month 6) |
|--------|------------------|------------------|------------------|
| Users with Copilot access | 100% assigned | 100% assigned | 100% assigned |
| Users actively using | 50% | 75% | 85%+ |
| Acceptance rate | 20%+ | 30%+ | 40%+ |
| Chat feature usage | 25% | 50% | 60%+ |

> **Manager Insight:** These targets help you identify teams that need additional support or training. Don't expect immediate high adoption - it takes time for developers to integrate Copilot into their workflow.

---

## Summary

In this exercise, you gained comprehensive knowledge of GitHub Copilot from a management perspective:

- **Understood Copilot capabilities** - You now know what developers experience and can have informed conversations about features and adoption.

- **Navigated administrative settings** - You can access and manage Copilot configuration for your organization.

- **Learned policy management** - You understand how to control features and ensure security compliance.

- **Explored content exclusions** - You can protect sensitive code while enabling Copilot for appropriate use.

- **Established governance framework** - You have best practices for policies, addressing concerns, and setting adoption goals.

This foundation prepares you to effectively measure Copilot's impact in the following exercises, because you now understand exactly what you're measuring and why.

### You have successfully completed this exercise. Click Next >> to continue.
