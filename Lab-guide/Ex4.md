## Exercise 4 — Report and Drive Adoption
*Duration: 15 Minutes*

### Task 1: Build an Executive Dashboard

1. **Create a new page for executives**  
   - At the bottom, click **+** to add a page → rename to **Executive Dashboard**.  
   - In **View ▸ Canvas settings**, set **Type = 16:9** for widescreen layout.  

    ![](../media/git_co_man-e1-g1.png)

2. **Bring over your core visuals**  
   - From your adoption page, copy/paste these onto **Executive Dashboard**:  
     - **Cards**: *Active Users*, *Engaged Users*, *Adoption Rate*, *Time Saved (hrs)*, *Chat Interactions*.  
     - **Line chart**: *Total Acceptances vs Date* (keep dual-axis with *Total Suggestions* if used).  
     - **Clustered bar**: *Top users by Total Acceptances*.  
     - **Donut**: *Acceptances by language_primary*.  
     - **Table**: detail table.  
   - Arrange in a clean 2-row layout: **KPI strip at top**, **charts middle**, **table bottom**.  

   ![](../media/git_co_man-e1-g2.png)

3. **Add slicers for executive filtering**  
   - Add **Slicer** for **date** (use *Between* type) and place top-left.  
   - Add **Slicer** for **editor_primary** and **language_primary** (Tile style) next to date.  
   ![](../media/git_co_man-e1-g3.png)

4. **Create ROI callout measures (simple, no parameters)**  
   - In **copilot_org**, create:  
     ```DAX
     -- Adjust the 75 to your org’s fully-loaded hourly rate (currency-agnostic).
     Estimated Cost Savings =
       [Time Saved (hrs)] * 75
     ```
   - Format **Estimated Cost Savings** as **Currency** (0–0 dp).  
   ![](../media/git_co_man-e1-g4.png)

5. **Add ROI cards**  
   - Insert **Card** → bind to **Time Saved (hrs)**. Title: **Hours Saved**.  
   - Insert **Card** → bind to **Estimated Cost Savings**. Title: **Est. Cost Savings**.  
   - Place these on the right side of the KPI strip.  
   ![](../media/git_co_man-e1-g5.png)

6. **Add an “Assumptions” text box**  
   - Insert **Text box** (top-right, under ROI cards) → paste:  
     ```
     Assumptions:
     • 10 seconds saved per acceptance
     • Hourly rate = 75 (adjust per org)
     • Filters on this page recalculate savings
     ```
   - Reduce opacity slightly so it reads as a note.  
   ![](../media/git_co_man-e1-g6.png)

7. **Polish titles & formatting**  
   - For each visual, set **Title** to a business-friendly name (e.g., “Adoption Rate”, “Top Acceptors”, “Acceptances Over Time”).  
   - Cards: **Display units = None**, **Decimal places = 2** for percentages.  
   - Align visuals (multi-select → **Format ▸ Align / Distribute**).  
   ![](../media/git_co_man-e1-g7.png)

8. **(Optional) Add Smart narrative summary**  
   - Insert **Smart narrative** visual → Power BI autogenerates key takeaways.  
   - Edit the text to include: adoption highlights, spikes, and cohort insights.  
   ![](../media/git_co_man-e1-g8.png)

9. **Bookmark a “Default Executive View”**  
   - Clear slicers to your standard timeframe (e.g., **Last 30 days**).  
   - **View ▸ Bookmarks ▸ Add** → name **Executive Default** → enable **Data** + **Display**.  
   ![](../media/git_co_man-e1-g9.png)

---

### Task 2: Present Findings & Next Steps

1. **Create a one-page summary (optional separate page)**  
   - Add a new page **Executive Summary**.  
   - Insert **Text box** with these sections and fill from your visuals:  
     - **Top Performers** (developers/teams with highest *Total Acceptances*).  
     - **Overall Gains** (Adoption Rate, Hours Saved, Est. Cost Savings).  
     - **Cohorts for Coaching** (Bottom 10 acceptors / low adoption segments).  
     - **Next Steps** (training plan, editor rollouts, language-specific tips).  
   ![](../media/git_co_man-e1-g10.png)

2. **Export or publish for leadership**  
   - **Export ▸ PDF** for a static deck handout; or **Export ▸ PowerPoint** to present live.  
   - **Home ▸ Publish** to Power BI Service → choose workspace.  
   ![](../media/git_co_man-e1-g11.png)

3. **Share with stakeholders**  
   - In Power BI Service, open the report → **Share** → enter leadership emails, add a short note, and include the **Executive Default** bookmark in your message.  
   ![](../media/git_co_man-e1-g12.png)

4. **Recommend actions (paste into your mail/Teams post)**  
   - **Train low-adoption cohort**: schedule a 60-min Copilot workshop for Bottom 10 users.  
   - **IDE focus**: prioritize the editor with highest **Acceptance Rate %** for rollout.  
   - **Language playbook**: replicate prompts/libraries seen in top-performing languages.  
   - **Quarterly goal**: +10% **Adoption Rate** and +5% **PR Throughput** vs baseline.

> You now have a polished **Executive Dashboard** with clear **ROI callouts**, plus a **shareable summary** to drive the Copilot rollout strategy.
