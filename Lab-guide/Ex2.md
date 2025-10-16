## Exercise 2: Analyze Manager Adoption Metrics

### Estimated Duration: 30 Minutes

## Overview

In this exercise, you will load the raw Copilot organization usage export, define core analytic measures in Power BI (or a similar BI tool), and build initial visuals to understand suggestion activity, acceptance quality, user engagement, and early adoption patterns. These measures become the building blocks for executive dashboards in later exercises.

## Objectives

You will be able to complete the following tasks:

- Task 1: Import usage data into the analytics tool
- Task 2: Create core DAX measures (suggestions, acceptances, acceptance rate, interactions, time saved, active users, adoption rate)
- Task 3: Visualize adoption trends (line and bar charts)

## Prerequisites

- Successful completion of Exercise 1 with `copilot_org.csv` (or similarly named) downloaded.
- Power BI Desktop installed (or equivalent analytical environment supporting DAX-style measures).
- Basic familiarity with navigating the Power BI interface.

## Task 1: Import Data into Analytics Tool

In this task, you will load the exported Copilot usage CSV into Power BI so that the data model is available for creating reusable analytical measures. This establishes the semantic foundation for all subsequent adoption and performance insights.

1. Launch **Power BI Desktop** from the desktop.

   ![](../media/git_co_man-e1-g1.png)

1. On the **Home** screen, select **Blank report**.

   ![](../media/git_co_man-e1-g2.png)

1. Go to the **Home (1)** tab and click **Get data (2)**.

   ![](../media/git_co_man-e1-g3.png)

1. In **Get Data**, choose **Text/CSV (1)** and select **Connect (2)**.

   ![](../media/git_co_man-e1-g16.png)

1. In the file picker, browse to **C:\\LabFiles (1)**, select **copilot_org (2)**, and click **Open (3)**.

   ![](../media/git_co_man-e1-g17.png)

1. In the preview dialog, confirm the delimiter is **Comma** and click **Load**.

   ![](../media/git_co_man-e1-g19.png)

## Task 2: Create Core Measures

In this task, you’ll add the DAX measures that power all “must-ship” visuals. Follow each step and confirm the green checkmark in the formula bar before moving on.

> **Why measures?**  
> Measures are reusable calculations evaluated in filter context (e.g., by date, editor, language, or user). This keeps your model lean and your visuals consistent.

1. In the **Data** pane, right-click your table **copilot_org (1)** → choose **New measure (3)**.

   ![](../media/git_co_man-e1-g20.png)

1. In the formula bar, create **Total Suggestions** (1) and click **✔ (2)**.

   ```
   Total Suggestions = SUM('copilot_org'[suggestions])
   ```

   ![](../media/git_co_man-e1-g21.png)

1. Confirm **Total Suggestions** appears under your table.

   ![](../media/git_co_man-e1-g22.png)

   > **Note:** If your table name is different, replace `'copilot_org'` in formulas accordingly.

1. Add another measure: right-click **copilot_org** → **New measure**.

   ![](../media/git_co_man-e1-g23.png)

1. Create **Total Acceptances** and click **✔**.

   ```
   Total Acceptances = SUM('copilot_org'[acceptances])
   ```

   ![](../media/git_co_man-e1-g24.png)

1. Add another measure: **New measure**.

   ![](../media/git_co_man-e1-g25.png)

1. Create **Acceptance Rate %** and click **✔**.

   ```
   Acceptance Rate % = DIVIDE([Total Acceptances], [Total Suggestions])
   ```

   ![](../media/git_co_man-e1-g26.png)

   > **Note:** `DIVIDE` safely handles divide-by-zero compared to `/`.

1. Add another measure: **New measure**.

   ![](../media/git_co_man-e1-g27.png)

1. Create **Chat Interactions** and click **✔**.

   ```
   Text to paste:  
   Chat Interactions =  
   SUM('copilot_org'[ide_chat_interactions]) +  
   SUM('copilot_org'[dotcom_chat_interactions])
   ```

   ![](../media/git_co_man-e1-g28.png)

1. (If needed) Use **New measure** again from the table menu.

   ![](../media/git_co_man-e1-g29.png)

1. Create **Time Saved (hrs)** using the 10-seconds-per-acceptance heuristic, then click **✔**.

   ```
   Time Saved (hrs) = DIVIDE( SUM('copilot_org'[acceptances]) * 10, 3600 )
   ```

   ![](../media/git_co_man-e1-g30.png)

1. Add another measure: **New measure** from **copilot_org**.

   ![](../media/git_co_man-e1-g31.png)

1. Create **Active Users** and click **✔**.  
    Counts distinct users with any activity (suggestions OR chat OR PR summaries) in current filter context.

   ```
   Text to paste:  
   Active Users =  
   VAR Users = VALUES('copilot_org'[user_login])  
   RETURN  
   COUNTROWS(  
       FILTER(  
           Users,  
           CALCULATE(  
               SUM('copilot_org'[suggestions]) +  
               SUM('copilot_org'[ide_chat_interactions]) +  
               SUM('copilot_org'[dotcom_chat_interactions]) +  
               SUM('copilot_org'[pr_summaries_created])  
           ) > 0  
       )  
   )
   ```
   
   ![](../media/git_co_man-e1-g32.png)

> **Note:** This measure respects slicers/filters (Editor, Language, Date). If you filter to a team/week, *Active Users* reflects only that slice.

1. Add another measure: **New measure**.

   ![](../media/git_co_man-e1-g33.png)

1. (Alternate menu view) **New measure** also appears in the compact context menu.

   ![](../media/git_co_man-e1-g34.png)

1. (Reference) Ensure your **Active Users** formula matches before proceeding.

   ![](../media/git_co_man-e1-g35.png)

1. Create **Adoption Rate** and click **✔**.  
    Formula: Engaged Users ÷ Active Users. (You’ll add **Engaged Users** next task if not already present; for now wire the measure.)

   Text to paste:  
   Adoption Rate = DIVIDE([Engaged Users], [Active Users])

   ![](../media/git_co_man-e1-g36.png)

> **Note:** If **Engaged Users** isn’t created yet, you can paste this now; it will light up once that measure exists.

### Format the measures (make them exec-friendly)

1. Select **Acceptance Rate %** and set **Format = Percentage (1)** and **Decimal places = 2 (2)**.

   ![](../media/git_co_man-e1-g37.png)

1. Select **Time Saved (hrs)** and set **Format = Decimal number (1)** and **Decimal places = 2 (2)**.

   ![](../media/git_co_man-e1-g38.png)

1. Select **Adoption Rate** and set **Format = Percentage (1)** and **Decimal places = 2 (2)**.

   ![](../media/git_co_man-e1-g39.png)

## Task 3: Visualize Adoption Trends

In this task, you will build core visuals (line and bar charts) that surface temporal adoption patterns and relative developer contribution. These visuals help stakeholders quickly spot growth, plateaus, and outliers for targeted enablement actions.

A. Line chart — “Suggestions Accepted” by Developer (weekly view)

1. On the **Report** canvas, insert a **Line chart**.  

   ![](../media/git_co_man-e1-g54.png)

1. With the line chart selected, set the **X-axis** to your **date** field. In **Data**, expand **date ▸ Date Hierarchy** and keep **Month**/**Day** active (this approximates weekly trends if you don’t have a Week field).

   > If you already created a week field (e.g., `Week Start`), use that instead for true weekly buckets.  

   ![](../media/git_co_man-e1-g55.png)

1. Add **Total Acceptances** to the **Y-axis**.  

   ![](../media/git_co_man-e1-g56.png)

1. Add **user_login** to **Legend** to split the series by developer.  

   > Each line now represents a developer’s accepted suggestions over time.

B. Bar chart — “Top/Bottom” developers by accepted suggestions

1. Insert a **Clustered bar chart**.  

   ![](../media/git_co_man-e1-g57.png)

1. Bind fields:  
   - **Y-axis:** **user_login**  
   - **X-axis:** **Total Acceptances**  

   ![](../media/git_co_man-e1-g58.png)

1. (Alt. binding view) On the canvas, select the horizontal **Clustered bar chart (1)**. In **Visualizations**, drag **user_login** to **Y-axis (2)**, and add **Total Suggestions (3)** plus **Total Acceptances (4)** to **X-axis** for side-by-side comparison.  

   ![](../media/git_co_man-e1-g59.png)

## Notes

- If a field name differs (e.g., table not named `copilot_org`), adjust measure references accordingly.
- Consider hiding raw numeric columns after creating measures to reduce accidental drag-and-drop usage.
- The heuristic for **Time Saved (hrs)** (10 seconds per acceptance) can be tuned later—keep logic centralized in a single measure for easy adjustment.
- Adoption vs. Engagement: Define **Engaged Users** explicitly (e.g., threshold of N acceptances or chat interactions) before showcasing Adoption Rate to leadership.

<validation step="ex2-validate-analytics" />

> **Validation Instructions**
> - Click the Validate button for this exercise in the lab environment UI.
> - Ensure all listed measures compile without errors and visuals render data.
> - If validation fails, re-check table/field names and measure syntax.
> - For assistance email: cloudlabs-support@spektrasystems.com.

## Summary

In this exercise, you ingested raw Copilot usage data, authored core analytical measures, and produced foundational visuals to surface acceptance performance and user activity. These assets establish a reusable semantic layer for later dashboards and deeper adoption analytics.

### You have successfully completed this exercise. Please continue to the next one >>
