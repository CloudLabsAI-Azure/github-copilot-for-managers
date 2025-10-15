## Exercise 2 — Analyze Manger Adoption Metrics

### Task 1: Load the Copilot org CSV into Power BI

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

### Task 2: Create Core Measures (KPI + Trend foundations)

In this task, you’ll add the DAX measures that power all “must-ship” visuals. Follow each step and confirm the green checkmark in the formula bar before moving on.

> **Why measures?**  
> Measures are reusable calculations evaluated in filter context (e.g., by date, editor, language, or user). This keeps your model lean and your visuals consistent.

---

1. In the **Data** pane, right-click your table **copilot_org (1)** → choose **New measure (3)**.

   ![](../media/git_co_man-e1-g20.png)

2. In the formula bar, create **Total Suggestions** (1) and click **✔ (2)**.

   Text to paste:  
   Total Suggestions = SUM('copilot_org'[suggestions])

   ![](../media/git_co_man-e1-g21.png)

3. Confirm **Total Suggestions** appears under your table.

   ![](../media/git_co_man-e1-g22.png)

> **Note:** If your table name is different, replace `'copilot_org'` in formulas accordingly.

---

4. Add another measure: right-click **copilot_org** → **New measure**.

   ![](../media/git_co_man-e1-g23.png)

5. Create **Total Acceptances** and click **✔**.

   Text to paste:  
   Total Acceptances = SUM('copilot_org'[acceptances])

   ![](../media/git_co_man-e1-g24.png)

---

6. Add another measure: **New measure**.

   ![](../media/git_co_man-e1-g25.png)

7. Create **Acceptance Rate %** and click **✔**.

   Text to paste:  
   Acceptance Rate % = DIVIDE([Total Acceptances], [Total Suggestions])

   ![](../media/git_co_man-e1-g26.png)

> **Note:** `DIVIDE` safely handles divide-by-zero compared to `/`.

---

8. Add another measure: **New measure**.

   ![](../media/git_co_man-e1-g27.png)

9. Create **Chat Interactions** and click **✔**.

   Text to paste:  
   Chat Interactions =  
   SUM('copilot_org'[ide_chat_interactions]) +  
   SUM('copilot_org'[dotcom_chat_interactions])

   ![](../media/git_co_man-e1-g28.png)

10. (If needed) Use **New measure** again from the table menu.

   ![](../media/git_co_man-e1-g29.png)

---

11. Create **Time Saved (hrs)** using the 10-seconds-per-acceptance heuristic, then click **✔**.

   Text to paste:  
   Time Saved (hrs) = DIVIDE( SUM('copilot_org'[acceptances]) * 10, 3600 )

   ![](../media/git_co_man-e1-g30.png)

12. Add another measure: **New measure** from **copilot_org**.

   ![](../media/git_co_man-e1-g31.png)

13. Create **Active Users** and click **✔**.  
    Counts distinct users with any activity (suggestions OR chat OR PR summaries) in current filter context.

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

   ![](../media/git_co_man-e1-g32.png)

> **Note:** This measure respects slicers/filters (Editor, Language, Date). If you filter to a team/week, *Active Users* reflects only that slice.

---

14. Add another measure: **New measure**.

   ![](../media/git_co_man-e1-g33.png)

15. (Alternate menu view) **New measure** also appears in the compact context menu.

   ![](../media/git_co_man-e1-g34.png)

16. (Reference) Ensure your **Active Users** formula matches before proceeding.

   ![](../media/git_co_man-e1-g35.png)

---

17. Create **Adoption Rate** and click **✔**.  
    Formula: Engaged Users ÷ Active Users. (You’ll add **Engaged Users** next task if not already present; for now wire the measure.)

   Text to paste:  
   Adoption Rate = DIVIDE([Engaged Users], [Active Users])

   ![](../media/git_co_man-e1-g36.png)

> **Note:** If **Engaged Users** isn’t created yet, you can paste this now; it will light up once that measure exists.

---

### Format the measures (make them exec-friendly)

18. Select **Acceptance Rate %** and set **Format = Percentage (1)** and **Decimal places = 2 (2)**.

   ![](../media/git_co_man-e1-g37.png)

19. Select **Time Saved (hrs)** and set **Format = Decimal number (1)** and **Decimal places = 2 (2)**.

   ![](../media/git_co_man-e1-g38.png)

20. Select **Adoption Rate** and set **Format = Percentage (1)** and **Decimal places = 2 (2)**.

   ![](../media/git_co_man-e1-g39.png)

