# Exercise 2: Analyze Copilot Adoption & User Engagement

### Estimated Duration: 15 Minutes

## Overview

In this exercise, you will load the Copilot organization usage data into Power BI and create essential measures to understand adoption patterns, user engagement levels, and team performance. You'll build visualizations that help managers identify top performers, engagement gaps, and areas for improvement across different teams and technologies.

## Objectives

You will be able to complete the following tasks:

- Task 1: Import Copilot usage data and understand the data structure
- Task 2: Create adoption and engagement measures for management insights
- Task 3: Build visualizations to identify usage patterns and team performance

## Prerequisites

- Successful completion of Exercise 1 with `copilot_org.csv` downloaded
- Power BI Desktop installed and signed in
- Basic familiarity with Power BI interface

## Task 1: Import and Configure Copilot Usage Data

In this task, you will load the GitHub Copilot organization usage data into Power BI Desktop to begin your analysis journey. This foundational step establishes the data connection that will power all your management insights, allowing you to understand adoption patterns, user engagement levels, and technology preferences across your development teams.

1. Launch **Power BI Desktop** from the desktop shortcut in your lab environment.

   ![](../media/mang-cor-c1.png)

   >**Getting Started:** Power BI Desktop allows you to connect to, transform, and visualize your data. It's the primary tool for creating interactive reports and dashboards.

1. Verify that you are signed in successfully your username will appear in the top-right corner.

   ![](../media/mang-cor-ex1-g7.png)

1. On the **Home** screen, select **Blank report**.

   ![](../media/git_co_man-e1-g2.png)

1. Go to the **Home (1)** tab and click **Get data (2)**.

   ![](../media/git_co_man-e1-g3.png)

1. In **Get Data**, choose **Text/CSV (1)** and select **Connect (2)**.

   ![](../media/git_co_man-e1-g16.png)

1. In the file picker, browse to **C:\Copilot_Datasets (1)**, select **copilot_org (2)**, and click **Open (3)**.

   ![](../media/mang-cor-ex1-g8.png)

1. In the preview dialog, confirm the delimiter is **Comma (1)** and click **Load (2)**.

   ![](../media/mang-cor-ex1-g9.png)

   >**Understanding Your Data**: The copilot_org dataset contains comprehensive daily usage metrics per user that provide crucial insights for management decision-making:
> - **Suggestions & Acceptances**: Measures both the volume of AI assistance offered and the quality/relevance as indicated by developer acceptance rates
> - **Teams & Roles**: Organizational context that allows you to compare adoption across different groups and experience levels
> - **Technology Preferences**: Editor (VS Code, JetBrains) and programming language data that helps identify which technology stacks benefit most from Copilot
> - **Chat Usage**: Both IDE-integrated and web-based AI chat interactions that indicate advanced feature adoption
> - **Activity Patterns**: Last activity dates and PR summary usage that help identify engagement trends and feature utilization

## Task 2: Create Strategic Management Measures

In this task, you'll create essential calculated measures that transform raw usage data into meaningful management insights. These measures will help you understand user engagement levels, team performance comparisons, and identify successful adoption patterns that can be replicated across your organization.

> **Manager's Perspective:** As a manager, you need metrics that answer critical questions: Who's actively using Copilot? How effectively are they using it? Which teams are seeing the best results? These measures provide those answers in quantifiable terms.

1. In the **Data (1)** pane on the right side of Power BI Desktop, right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

   >**Understanding Measures:** Measures are calculations that Power BI performs on your data in real-time. Unlike columns which store data, measures calculate values dynamically based on your current filters and selections.

1. Create a new measure named **Active Users (1)**: in the formula bar **(1)** paste the DAX below, then select **✔ (2)** to confirm

   ```
   Active Users = DISTINCTCOUNT('copilot_org'[user_login])
   ```

   ![](../media/mang-cor-ex1-g10.png)

1. Add another measure: right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

1. Create **Total Suggestions** : in the formula bar **(1)** paste the DAX below, then select **✔ (2)** to confirm

   ```
   Total Suggestions = SUM('copilot_org'[suggestions])
   ```

   ![](../media/mang-cor-ex1-g11.png)

1. Add another measure: right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

1. Create **Total Acceptances**: in the formula bar **(1)** paste the DAX below, then select **✔ (2)** to confirm

   ```
   Total Acceptances = SUM('copilot_org'[acceptances])
   ```

   ![](../media/mang-cor-ex1-g12.png)

1. Add another measure: right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

1. Create **Acceptance Rate %** to measure code suggestion quality:

   ```
   Acceptance Rate % = DIVIDE([Total Acceptances], [Total Suggestions], 0)
   ```

   ![](../media/mang-cor-ex1-g13.png)

   > **Manager Insight**: Acceptance rate indicates how relevant Copilot suggestions are. Higher rates (>50%) typically indicate better user adoption and tool effectiveness.

1. Add measure: right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

1. Create **Chat Users** to identify users leveraging AI chat:

   ```
   Chat Users = CALCULATE(
       DISTINCTCOUNT('copilot_org'[user_login]),
       'copilot_org'[ide_chat_interactions] > 0 || 'copilot_org'[dotcom_chat_interactions] > 0
   )
   ```

   ![](../media/mang-cor-ex1-g14.png)

1. Add measure: right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

1. Create **Total Chat Interactions**:

   ```
   Total Chat Interactions = 
   SUM('copilot_org'[ide_chat_interactions]) + 
   SUM('copilot_org'[dotcom_chat_interactions])
   ```

   ![](../media/mang-cor-ex1-g15.png)

1. Add measure: right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

1. Create **Highly Engaged Users** (users with significant activity):

   ```
   Highly Engaged Users = CALCULATE(
       DISTINCTCOUNT('copilot_org'[user_login]),
       'copilot_org'[acceptances] >= 10
   )
   ```

   ![](../media/mang-cor-ex1-g16.png)

   > **Manager Insight**: Highly engaged users are those accepting 10+ suggestions, indicating they're getting substantial value from Copilot.

1. Add measure: right-click your **copilot_org (2)** table and choose **New measure (3)** from the context menu.

   ![](../media/git_co_man-e1-g20.png)

1. Create **Team Adoption Rate**:

   ```
   Team Adoption Rate = DIVIDE([Highly Engaged Users], [Active Users], 0)
   ```

   ![](../media/mang-cor-ex1-g17.png)

## Task 3: Build Interactive Management Dashboards

In this task, you will create comprehensive visualizations that transform your data into actionable management insights. These dashboards will help you identify adoption patterns, recognize top-performing teams, and spot areas that may need additional support or training interventions.

### A. Create Team Performance Overview Dashboard

1. Rename your report page for better organization. Right-click on the page tab at the bottom and select **Rename**. Change it to **Copilot Adoption**.

   ![](../media/mang-cor-ex1-g32.png)

   >**Dashboard Organization:** Clear page names help stakeholders navigate your reports easily and understand the focus of each analysis section.

1. Insert a **Table** visual from the Visualizations pane.

   ![](../media/mang-cor-ex1-g18.png)

1. Add these fields to the table under the **Columns**.

   - **team (1)**
   - **Active Users (2)**
   - **Highly Engaged Users (3)**
   - **Team Adoption Rate (4)**
   - **Total Acceptances (5)**

      ![](../media/mang-cor-ex1-g19.png)

1. Once all columns are added, the table will display the metrics for each team. Review the created table — it should look like the example below.  

   ![](../media/mang-cor-ex1-g20.png)

   > **Manager Value**: This table shows which teams are adopting Copilot most effectively and where you might need additional training or support.

1. Format the **Table** visual for better presentation:

   - Select the **Table** visual **(1)**.
   - Open the **Visualizations** pane **(2)**.
   - Under the **Format visual** section, select **General (3)**.
   - In the **Effects** area, turn **On** the **Background**, **Visual border**, and **Shadow** options **(4)**.   

      ![](../media/mang-cor-ex1-g21.png)

### B. Create User Engagement Analysis

1. Insert a **Clustered bar chart**: in the **Visualizations** pane, select the **Bar chart** icon (1), then click **Clustered bar chart** (2). A blank visual will appear on the canvas (3). 

   ![](../media/mang-cor-ex1-g22.png)

1. Configure the chart:
   - **Y-axis**: user_login
   - **X-axis**: Total Acceptances
   - **Legend**: team

      ![](../media/mang-cor-ex1-g23.png)

1. Review the chart — it should resemble the example below.

   ![](../media/mang-cor-ex1-g24.png)

1. Notice that when you click a **team** in the bar chart (1), the corresponding data in the **table visual** (2) automatically updates — showing interactive filtering between visuals.

   ![](../media/mang-cor-ex1-g25.png)

   > **Manager Insight**: This identifies your top Copilot users and shows team distribution, helping you identify champions for peer training.

### C. Create Technology Adoption Matrix

1. Insert a **Matrix** visual: in the **Visualizations (1)** pane, select the **Matrix (2)** icon; a **blank matrix visual (3)** will appear on the canvas.

   ![](../media/mang-cor-ex1-g26.png)

1. Configure the **Matrix** visual as shown below:  
   - **Rows (1):** editor_primary  
   - **Columns (2):** language_primary  
   - **Values (3):** Active Users, Acceptance Rate %  

      ![](../media/mang-cor-ex1-g27.png)

      > **Manager Value**: This shows which technology combinations are most successful with Copilot, informing training and tooling decisions.

### D. Add Interactive Filters

1. Insert a **Slicer** for **team**: in the **Visualizations (1)** pane, select the **Slicer (2)** icon; a **blank slicer visual (3)** will appear on the canvas.

   ![](../media/mang-cor-ex1-g28.png)

1. Configure the **Slicer** visual: add **team (1)** and **role (2)** fields under **Field** to enable filtering by both attributes.

   ![](../media/mang-cor-ex1-g29.png)

1. Test the **Slicer** interactivity: select a **team (1)** and a specific **role (2)** — observe that all visuals dynamically update to reflect the selected filters.  

   ![](../media/mang-cor-ex1-g30.png)

1. Select another **team (growth)** from the **Slicer** to verify that all visuals update dynamically based on the selected filter. 

   ![](../media/mang-cor-ex1-g31.png)

   > **Manager Benefit**: These slicers allow you to drill down into specific teams or roles to understand adoption patterns and identify coaching opportunities.

## Notes

- Focus on trends rather than absolute numbers - adoption patterns are more important than raw usage counts
- Pay attention to acceptance rates by team/technology to identify where Copilot is working best
- Use this data to identify Copilot champions who can help train others
- Consider the experience level (role) when analyzing adoption - senior developers might use chat more while junior developers might rely more on code suggestions

## Summary

In this exercise, you successfully transformed raw Copilot usage data into meaningful management insights through comprehensive adoption and engagement analysis. You created strategic measures that help managers identify high-performing teams, understand technology preferences, and spot areas where additional support or training may be needed. The interactive dashboards you built provide the foundation for data-driven decisions about Copilot program optimization. These adoption metrics will now serve as the baseline for measuring productivity improvements in the next exercise, creating a complete picture of Copilot's organizational impact.

### You have successfully completed this exercise, please continue to next one >>
