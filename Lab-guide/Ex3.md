## Exercise 3: Calculate Productivity Improvements

### Estimated Duration: 20 Minutes

## Overview

In this exercise, you will translate raw adoption measures into manager-ready productivity indicators. You’ll surface baseline KPI cards (Active Users, Engaged Users, Adoption Rate, Time Saved, Chat Interactions) and introduce slicers that allow stakeholders to segment performance by editor and language. These assets help quantify early value and identify optimization focus areas.

## Objectives

You will be able to complete the following tasks:

- Task 1: Establish baseline KPI metrics (create core cards for visibility)
- Task 2: Compute improvement ratios (add contextual slicers for comparative analysis)

## Prerequisites

- Completion of Exercise 2 with core measures already created (Active Users, Engaged Users, Adoption Rate, Time Saved (hrs), Chat Interactions).
- Power BI report file open with the `copilot_org` dataset loaded.

## Task 1: Establish Baseline Metrics

In this task, you will build a concise KPI deck using Card visuals to surface the most critical adoption and productivity signals for leadership dashboards.

1. On the **Visualizations** pane, switch to **Build visual** and insert a **Card** visual. 

   ![](../media/git_co_man-e1-g40.png)

1. With the new card selected **(1)**, in **Data** expand your dataset and check **Active Users (2)**. It will land in **Fields (3)** for the card.  

   ![](../media/git_co_man-e1-g41.png)

1. Confirm the card displays the KPI value for **Active Users**.  

   ![](../media/git_co_man-e1-g42.png)

1. Resize the card as needed using the bottom-right drag handle so it reads cleanly on the canvas.  

   ![](../media/git_co_man-e1-g43.png)

1. Add a second **Card** visual for **Engaged Users** (repeat the insert step).

   ![](../media/git_co_man-e1-g44.png)

1. With the second card selected **(1)**, select **Engaged Users (3)** from **copilot_org (2)** to populate the KPI.  
   ![](../media/git_co_man-e1-g45.png)

1. Insert a third **Card** visual for **Adoption Rate**. 

   ![](../media/git_co_man-e1-g46.png)

1. Populate the third card with the **Adoption Rate** measure **(3)**. Verify it appears in **Fields (4)** and renders on the canvas **(1)**.  

   ![](../media/git_co_man-e1-g47.png)

1. With the **Adoption Rate** card selected **(1)**, open **Format visual (paint roller) (2)** → **Visual (3)** and set:  
   - **Display units:** **None (4)**  
   - **Value decimal places:** **2 (5)**  
   > **Tip:** Turning off display units avoids “K/M” abbreviations that can hide important precision for percentage KPIs.  
   
   ![](../media/git_co_man-e1-g48.png)

1. Still on the **Adoption Rate** card, go to **Format visual** → **General (3)**. Under **Apply settings to (4)** make sure **Adoption Rate** is selected, then set:  
    - **Format:** **Percentage (5)**  
    - **Decimal places:** **2 (6)**  
    > **Note:** If your measure already returns a fraction (e.g., 0.42), formatting as **Percentage** renders **42.00%** without changing the underlying calculation.
    
    ![](../media/git_co_man-e1-g49.png)

1. **Add “Time Saved (hrs)” KPI card**  
    In **Visualizations**, keep **Build visual** selected and click the **Card** visual.  
    
    ![](../media/git_co_man-e1-g50.png)

1. **Bind the Time Saved (hrs) measure**  
    Select the new card, then in **Data** check **Time Saved (hrs)** so it appears in **Fields** and renders on the canvas.  
    
    ![](../media/git_co_man-e1-g51.png)

1. **Add a “Chat Interactions” KPI card**  
    With **Build visual** selected, click **Card** again to insert another card.  
    
    ![](../media/git_co_man-e1-g52.png)

## Task 2: Compute Improvement Ratios

In this task, you will add interactive slicers enabling comparative analysis (e.g., how adoption differs by editor or language) to contextualize the baseline KPIs and guide targeted enablement strategies.

1. In **Visualizations (1)**, click the **Slicer** visual (2) to insert a slicer onto the page.

   ![](../media/git_co_man-e1-g60.png)

1. With the slicer selected (1), set **Field (2)** to **editor_primary** to filter by IDE/editor.

   ![](../media/git_co_man-e1-g61.png)

1. Format the slicer: select the slicer (1) → go to **Format visual (2)** → **Visual (3)** → expand **Slicer settings (4)** → set **Style (5)** to **Tile**.

   ![](../media/git_co_man-e1-g62.png)

1. Insert another **Slicer**: in **Visualizations (1)** choose **Slicer (2)** to add a second slicer.

   ![](../media/git_co_man-e1-g63.png)

1. With the new slicer selected (1), set **Field (2)** to **language_primary** to filter by primary language.

   ![](../media/git_co_man-e1-g64.png)

1. Format the language slicer to tiles: select the slicer (1) → **Format visual (2)** → **Visual (3)** → set **Style (4)** to **Tile**.

   ![](../media/git_co_man-e1-g65.png)

## Notes

- Ensure all measures come from the same semantic model to avoid duplicated logic.
- Arrange KPI cards in a consistent left-to-right reading order: Adoption Rate, Active Users, Engaged Users, Time Saved (hrs), Chat Interactions (or adapt to your executive priorities).
- Consider conditional formatting (color rules) once thresholds for “healthy adoption” are defined.
- Slicers can be synchronized across pages later if you build a multi-page report.

<validation step="ex3-validate-productivity" />

> **Validation Instructions**
> - Click the Validate button for this exercise in the lab environment UI.
> - Confirm all KPI cards render expected values and slicers filter them dynamically.
> - If validation fails, verify that prerequisite measures were created in Exercise 2.
> - For assistance email: cloudlabs-support@spektrasystems.com.

## Summary

In this exercise, you elevated core adoption metrics into a productivity-focused KPI layout and added segmentation controls (editor and language) to support comparative insights. This prepares the ground for advanced efficiency modeling and trend storytelling in subsequent exercises.

### You have successfully completed this exercise. Please continue to the next one >>