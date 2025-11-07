# Exercise 1: Enable & Access Copilot Usage Reports (Read Only)

### Estimated Duration: 15 Minutes

## Overview

In this exercise (Read Only), you will enable and access GitHub Copilot organization-level usage reports to establish foundational visibility for managers and program owners. You will learn how to request activity reports that provide crucial data about adoption patterns, user engagement, and usage metrics across your organization. 

This exercise demonstrates the complete workflow from report generation to data acquisition, introducing you to the rich analytics possibilities available when Copilot usage data is combined with organizational context. The comprehensive datasets you'll work with showcase advanced analytics scenarios that help managers understand not just who is using Copilot, but how effectively different teams, roles, and technology stacks are leveraging AI assistance.

These reports form the basis for the comprehensive analytics dashboard you'll build in subsequent exercises, enabling data-driven decisions about Copilot deployment and optimization strategies across your development organization.

## Objectives

You will be able to complete the following tasks:

- Task 1: Product Overview for Managers and Pre-Sales
- Task 2: Navigate to GitHub Copilot administrative settings and activate reporting features
- Task 3: Request and download organization-level usage data for analysis

## Task 1: Product Overview for Managers and Pre-Sales

In this task, you will understand the GitHub Copilot and its usecases.

#### What is GitHub Copilot?

**GitHub Copilot** is an AI-powered coding assistant developed by GitHub and OpenAI that helps developers write code faster, smarter, and with fewer errors.  
It works directly inside popular development environments like Visual Studio Code, Visual Studio, Neovim, and JetBrains IDEs, offering context-aware code suggestions, explanations, and completions in real time as developers type.

Copilot has evolved from being a simple autocomplete tool into an AI pair programmer that assists across the entire software lifecycle from writing code to fixing bugs, writing tests, and even explaining complex code logic.  
It leverages large language models (LLMs) trained on billions of lines of code, enabling it to understand natural language prompts and generate corresponding code suggestions instantly.

#### Why It Matters for Managers and Sales Teams

GitHub Copilot is not just a developer productivity tool, it’s a strategic enabler that transforms how teams deliver software and how organizations measure engineering efficiency, speed, and innovation.

##### For Managers
Copilot provides visibility into how AI can drive measurable performance gains across teams, reduced development time, faster onboarding, and improved code quality.  
With Copilot usage reports and Power BI analytics, managers can make data-driven decisions to scale AI-assisted development effectively across their organization.

##### For Pre-Sales & Sales Teams
Copilot becomes a business differentiator.  
It allows pre-sales engineers to demonstrate tangible customer outcomes such as faster feature delivery, reduced backlog, and improved developer satisfaction.  
The metrics derived from usage and productivity analysis can be turned into compelling ROI stories and customer success cases that strengthen business conversations.

#### How GitHub Copilot Helps Organizations

| **Benefit Area** | **Description** | **Why It Matters for Business** |
|-------------------|------------------|---------------------------------|
| **Developer Productivity** | Suggests entire lines or functions, helping developers complete work faster. | Reduces coding time, enabling faster release cycles and innovation. |
| **Quality and Consistency** | Generates consistent, standards-aligned code patterns. | Improves maintainability and reduces rework costs. |
| **Onboarding Efficiency** | Helps new developers understand unfamiliar codebases with inline explanations. | Speeds up onboarding and reduces time-to-productivity. |
| **Cross-Technology Enablement** | Supports dozens of languages and frameworks, helping teams explore new stacks. | Expands organizational technical agility. |
| **Innovation Enablement** | Frees developers from repetitive work, letting them focus on solving business problems. | Drives innovation and higher business impact per developer. |
| **Data-Driven Insights** | Usage reports show real adoption, engagement, and productivity trends. | Enables clear ROI justification for management and customers. |

#### The Business Value of GitHub Copilot

GitHub Copilot bridges the gap between engineering output and business outcomes. By combining usage analytics with productivity metrics, organizations can quantify how AI assistance directly translates into faster delivery, higher quality, and lower cost.

- **Accelerated Delivery:** Teams ship features faster by reducing coding and debugging time.  
- **Reduced Costs:** Fewer reworks, less time spent on boilerplate code, and improved focus mean lower operational overhead.  
- **Higher Developer Satisfaction:** Developers report feeling more focused, creative, and less fatigued, leading to lower attrition and higher retention.  
- **Competitive Advantage:** Organizations adopting Copilot early can demonstrate measurable improvements in velocity and innovation to clients and stakeholders.  

## Task 2: Navigate to GitHub Copilot Administrative Settings

In this task, you will navigate to the GitHub Copilot administrative area within your organization settings and initiate the Activity report generation. This report provides comprehensive usage data that managers need to understand Copilot adoption across their development teams.

1. In the top-right corner of GitHub, click your **profile picture (1)** and select **Organizations (2)** from the dropdown menu.

   ![](../media/gt-co-ex1-g1.png)

   >**Note:** You must have Organization Owner permissions to access Copilot usage reports. If you don't see your organization listed, contact your GitHub administrator.

1. On the **Settings › Organizations** page, locate and click your organization **contoso-impact** where you have **Owner** role permissions.  

   ![](../media/gt-co-ex1-g2.png)

1. Once you're in the organization dashboard, navigate to the **Settings** tab from the top navigation menu.  

   ![](../media/gt-co-ex1-g3.png)

   >**Manager Insight:** The organization settings area is where you control all aspects of Copilot deployment, including user access, policy settings, and usage reporting.

1. In the left sidebar navigation, locate the **Code, planning, and automation (1)** section, expand **Copilot (2)**, and click on **Access (3)**.  

   ![](../media/gt-co-ex1-g4.png)

1. On the **Access management** page, locate the **Get Usage report (1)** section and select **Activity report (new) (2)** from the available options.

   ![](../media/gt-co-ex1-g5.png)

   >**Understanding Activity Reports:** The Activity report provides per-user metrics including code suggestions, acceptances, chat usage, and technology preferences. This data is essential for measuring adoption success and identifying areas for improvement.

## Task 3: Request and Download Organization Usage Data

In this task, you will initiate the report generation process and obtain the CSV file containing your organization's Copilot usage data. This data will serve as the foundation for all subsequent analysis and dashboard creation.

1. After selecting the Activity report option, confirm that the green notification banner **"Your activity report is being generated…"** appears at the top of the page.  

   ![](../media/gt-co-ex1-g6.png)

   >**Important:** Report generation is an asynchronous process that runs in the background. The time required depends on your organization size and usage history.

1. Monitor your email for the notification titled **"Your GitHub Copilot Activity report is ready"** and download the attached CSV file when it becomes available.  

   ![](../media/gt-co-ex1-g7.png)

   >**Manager Value:** This CSV contains per-user data including suggestions offered, acceptances, team assignments, editor preferences, and chat usage patterns - all critical metrics for understanding Copilot ROI and adoption success.

1. Once downloaded, save the CSV file to a known location on your computer for use in the upcoming exercises.

   >**Best Practice:** Keep the original CSV file unmodified as your source of truth. You'll create working copies for analysis in Power BI to preserve data integrity.

   >**Note:** The datasets used in this lab have been enhanced with additional organizational context (teams, roles, technology stacks) to provide comprehensive analytics scenarios. In production environments, enriching GitHub Copilot usage data with organizational metadata may require integration with HR systems, development tool APIs, or manual data collection processes.

## Notes

- If you do not see **Activity report (new)**, ensure your organization is on a supported Copilot plan and that you have Owner permissions.
- The downloaded CSV (often named like `copilot_org.csv`) will be used in Exercise 2 for building analytics measures.
- Regenerating a report overwrites the previous pending request but does not delete earlier downloaded files you saved locally.
- Keep the raw CSV unmodified; create a copy for transformation steps in later exercises

## Summary

In this exercise, you successfully enabled GitHub Copilot usage reporting and initiated the Activity report generation process. You learned how to navigate the administrative settings, request comprehensive usage data, and understand the value of this information for management decision-making. The CSV dataset you obtained now serves as the authoritative foundation for all subsequent adoption analysis, engagement metrics, and ROI calculations you'll perform in the following exercises. This data-driven approach ensures your Copilot program decisions are based on concrete evidence rather than assumptions.

### You have successfully completed this exercise, please continue to next one >>
