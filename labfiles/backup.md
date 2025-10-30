## Exercise 2 — Analyze Manger Adoption Metrics

### Task 1: Import Data into Analytics Tool

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

### Task 2: Create Core Measures

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

## Task 3: Create and Format KPI Cards

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

1. **Bind the Chat Interactions measure**  
    Select the new card and, in **Data**, check **Chat Interactions** so the value shows in **Fields**.  
    
    ![](../media/git_co_man-e1-g53.png)

1. **Insert a Line chart for trends**  
    With **Build visual** active, choose the **Line chart** icon.  
    
    ![](../media/git_co_man-e1-g54.png)

1. **Configure the X-axis with Date hierarchy**  
    Select the line chart, expand **date ▸ Date Hierarchy** in **Data**, and ensure **Year**, **Quarter**, **Month**, and **Day** are active on the **X-axis**.  
    
    ![](../media/git_co_man-e1-g55.png)

1. **Add measures to the line chart**  
    - **Y-axis:** add **Total Acceptances**  
    - **Secondary y-axis:** add **Total Suggestions** (for dual-axis comparison)  
    ![](../media/git_co_man-e1-g56.png)  
    > **Tip:** Dual axes help when the series have different scales.

1. **Add a Clustered bar chart**  
    With **Build visual** selected, click **Clustered bar chart**. 
    
    ![](../media/git_co_man-e1-g57.png)

1. **Show top acceptors by user**  
    - **Y-axis:** **user_login**  
    - **X-axis:** **Total Acceptances**  
    
    ![](../media/git_co_man-e1-g58.png)

1. On the **Report** canvas, select the horizontal **Clustered bar chart (1)**. In **Visualizations** → **Y-axis (2)** drag **user_login**. In **X-axis**, add **Total Suggestions (3)** and **Total Acceptances (4)**.

   ![](../media/git_co_man-e1-g59.png)

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

1. Insert a **Table** visual: in **Visualizations (1)** click **Table (2)** to add a summary table (we’ll bind fields in a later step).

   ![](../media/git_co_man-e1-g66.png)

1. Insert a **Donut chart**: in **Visualizations (1)** click **Donut chart (2)** to add a distribution visual.

   ![](../media/git_co_man-e1-g67.png)

1. With the **Donut chart (1)** selected, set **Legend (2)** to **language_primary** and **Values (3)** to **Total Acceptances** to show acceptances by language.

   ![](../media/git_co_man-e1-g68.png)