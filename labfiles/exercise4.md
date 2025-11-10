# Exercise 4: Build Executive Dashboard & Calculate ROI

### Estimated Duration: 30 Minutes

## Overview

In this exercise, you will create an executive-ready dashboard that combines adoption metrics from Exercise 2 and productivity improvements from Exercise 3 to calculate and present the return on investment (ROI) of GitHub Copilot. You'll build a comprehensive view that executives can use to make data-driven decisions about Copilot expansion and optimization.

## Objectives

You will be able to complete the following tasks:

- Task 1: Create ROI calculation measures using productivity improvements
- Task 2: Build an executive summary dashboard with key insights
- Task 3: Publish the dashboard to Power BI Service for sharing

## Task 1: Create ROI Calculation Measures

In this task, you'll create measures that translate productivity improvements into financial value and calculate the ROI of Copilot investment.

### A. Time Savings Calculations

1. Click on (+) at the bottom tab area and select **New page**.

1. Rename the page to **Executive Dashboard**.

   ![](../media/mang-cor-ex4-g1.png)

1. In the **Data** pane, right-click the **pr_baseline** table (1) and select **New measure** (2) to create a new DAX measure.

   ![](../media/mang-cor-ex1-g39.png)

1. In the formula bar, paste the DAX for **Hours Saved per Dev per Month** (1) given below and click **✔** (2) to save and apply the measure.

   ```
   Hours Saved per Dev per Month = 
   VAR LeadTimeReduction = [Lead Time Improvement]
   VAR AvgPRsPerMonth = [Post-Copilot PRs Merged] 
   VAR HoursSaved = LeadTimeReduction * AvgPRsPerMonth
   RETURN HoursSaved
   ```

   ![](../media/mang-cor-ex4-g2.png)

1. In the **Data** pane, right-click the **pr_baseline** table (1) and select **New measure** (2) to create a new DAX measure.

   ![](../media/mang-cor-ex1-g39.png)

1. In the formula bar, paste the DAX for **Total Hours Saved Organization** (1) given below and click **✔** (2) to save and apply the measure.

   ```
   Total Hours Saved Organization = 
   [Hours Saved per Dev per Month] * [Active Users]
   ```

   ![](../media/mang-cor-ex4-g3.png)

### B. Financial Value Calculations

1. Create **Developer Hourly Rate** parameter for ROI sensitivity analysis:
   
1. Go to **Modeling** (1) → **New parameter** → **Numeric range** (2).

   ![](../media/co-po-ex4-g3.png)

1. Configure the parameter settings as shown:  
   - **Type:** Numeric range (1)  
   - **Name:** Developer Hourly Rate (2)  
   - **Data type:** Whole number (3)  
   - **Minimum:** 50 (4)  
   - **Maximum:** 200 (5)  
   - **Increment:** 10 (6)  
   - **Default:** 75 (7)  
   - **Add slicer to this page:** Checked (8)  
   - Click **Create** (9) to generate the parameter.

      ![](../media/mang-cor-ex4-g4.png)

1. Right-click the **pr_baseline** table and select **New measure**. In the formula bar, paste the DAX for **Monthly Time Savings Value** (1) given below and click **✔** (2) to save and apply the measure.

   ```
   Monthly Time Savings Value = 
   [Total Hours Saved Organization] * 'Developer Hourly Rate'[Developer Hourly Rate Value]
   ```

   ![](../media/mang-cor-ex4-g11.png)

   Format as **Currency** with **0 decimal places**.

   > **Note**: Use the full table reference 'Developer Hourly Rate'[Developer Hourly Rate Value] to ensure proper parameter reference.

1. Right-click **pr_baseline** table → **New measure** and in the formula bar, paste the DAX for **Annual Time Savings Value** (1) given below and click **✔** (2) to save and apply the measure.

   ```
   Annual Time Savings Value = [Monthly Time Savings Value] * 12
   ```

   ![](../media/mang-cor-ex4-g6.png)

### C. ROI Calculations

1. Create **Annual Copilot Cost** parameter:
   
1. Go to **Modeling** (1) → select **New parameter** (2) → choose **Numeric range** (3) to create the **Annual Copilot Cost** parameter.

   ![](../media/mang-cor-ex4-g7.png)

1. Configure the parameter for **Annual Copilot Cost per User** as shown below:  
   - **Type:** Numeric range (1)  
   - **Name:** Annual Copilot Cost per User (2)  
   - **Data type:** Whole number (3)  
   - **Minimum:** 100 (4)  
   - **Maximum:** 500 (5)  
   - **Increment:** 20 (6)  
   - **Default:** 228 (7)  
   - **Add slicer to this page:** Checked (8)  
   - Click **Create** (9) to finalize the parameter.

      ![](../media/mang-cor-ex4-g12.png)

   > **Important**: After creating the parameter, you should see "Annual Copilot Cost per User Value" appear in your Data pane under the parameter section.

1. Right-click **pr_baseline** table → **New measure**. Create **Total Annual Copilot Investment**:

   ```
   Total Annual Copilot Investment = 
   [Active Users] * 'Annual Copilot Cost per User'[Annual Copilot Cost per User Value]
   ```

   ![](../media/mang-cor-ex4-g10.png)

   > **Note**: Use the full table reference 'Annual Copilot Cost per User'[Annual Copilot Cost per User Value] to ensure proper parameter reference.

1. Right-click **pr_baseline** table → **New measure**. Create **Copilot ROI %**:

   ```
   Copilot ROI % = DIVIDE(
       [Annual Time Savings Value] - [Total Annual Copilot Investment],
       [Total Annual Copilot Investment],
       0
   )
   ```

   ![](../media/mang-cor-ex4-g14.png)

   Format as **Percentage** with **0 decimal places**.

1. Right-click **pr_baseline** table → **New measure**. Create **ROI Payback Period (months)**:

   ```
   ROI Payback Period (months) = DIVIDE(
       [Total Annual Copilot Investment],
       [Monthly Time Savings Value],
       0
   )
   ```

   ![](../media/mang-cor-ex4-g15.png)

   Format as **Decimal number** with **1 decimal place**.

1. **Verify Parameter Creation**: In the **Data** pane, you should see both parameters:
   - **Developer Hourly Rate** with "Developer Hourly Rate Value" underneath
   - **Annual Copilot Cost per User** with "Annual Copilot Cost per User Value" underneath

      ![](../media/mang-cor-ex4-g16.png)

      ![](../media/mang-cor-ex4-g17.png)

## Task 2: Build Executive Dashboard

In this task, you'll create a comprehensive executive dashboard that tells the complete Copilot story from adoption to ROI.

1. Insert **Card** visuals for the most important executive metrics:

   ![](../media/mang-cor-ex4-g19.png)

   - **Copilot ROI %** (make this prominent with large font)

      ![](../media/mang-cor-ex4-g20.png)

   - **ROI Payback Period (months)**
   - **Annual Time Savings Value**
   - **Active Users**

      ![](../media/mang-cor-ex4-g21.png)

   > **Executive Value**: These 5 cards immediately communicate the business case for Copilot in terms executives understand.

### C. Create Adoption vs Impact Matrix

1. Insert a **Scatter chart** to show the relationship between adoption and productivity:

   ![](../media/mang-cor-ex4-g22.png)

   - **X-axis**: Active Users (from copilot_org, by team)
   - **Y-axis**: Lead Time Improvement % (from Exercise 3)
   - **Size**: Annual Time Savings Value (by team)
   - **Legend**: team

      ![](../media/mang-cor-ex4-g23.png)

   > **Executive Insight**: This shows which teams are both adopting Copilot well AND seeing productivity benefits, identifying success stories to replicate.

### D. Add Productivity Improvement Summary

1. Insert a **Clustered column chart** showing key improvements:

   - **X-axis**: Custom values ("Lead Time", "Cycle Time", "Throughput")
   - **Y-axis**: Improvement percentages

   ![](../media/mang-cor-ex4-g24.png)

1. Interact and review the dashabord.

   ![](../media/mang-cor-ex4-g25.png)

## Task 3: Publish to Power BI Service

In this task, you'll publish the dashboard to Power BI Service so it can be shared with executives and stakeholders.

1. In **Power BI Desktop**, select **File** → **Publish** → **Publish to Power BI**.

   ![](../media/gt-co-ex1-g8.png)

1. Choose **My workspace** and click **Select**.

   ![](../media/gt-co-ex1-g12.png)

1. When prompted to save changes, click **Save** and provide a meaningful filename like:
   `Copilot_PowerBI`

   ![](../media/gt-co-ex1-g11.png)

1. After successful publish, click **Got it** to complete the process.

   ![](../media/gt-co-ex1-g13.png)


## Notes

- **ROI focuses on time savings** - the primary quantifiable benefit of Copilot for development teams
- **Use parameters** to make the dashboard adaptable to different organizations and scenarios
- **Separate technical details** from executive summary - executives need the "so what" not the "how"
- **Include payback period** - executives want to know when they'll see returns
- **Show team-level results** - helps identify where additional training or support might be needed
- **Consider additional benefits** like improved code quality, reduced bugs, and developer satisfaction in narrative

## Summary

In this exercise, you created a comprehensive executive dashboard that transforms Copilot usage data into clear business value metrics. You calculated ROI based on productivity improvements, created scenario analysis capabilities, and published the results to Power BI Service. This dashboard provides executives with the data-driven insights needed to make informed decisions about Copilot expansion and optimization across the organization.


### Congratulations! You have successfully completed the Measuring GitHub Copilot Impact for Managers lab series. You now have the skills to measure, analyze, and communicate the business value of GitHub Copilot in your organization.


