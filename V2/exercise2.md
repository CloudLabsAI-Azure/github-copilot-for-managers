# Exercise 2: Experience GitHub Copilot Yourself

### Estimated Duration: 12 Minutes

## Overview

In this exercise, you will use GitHub Copilot hands-on to understand what your developers (or customers' developers) experience daily. This personal experience is invaluable - whether you're a manager evaluating Copilot for your team or a sales professional demonstrating it to prospects. You'll build real scripts, generate code with AI assistance, and discover the "aha moments" that make Copilot compelling.

> **Why This Matters:** People who have used Copilot speak authentically about its value. This 12-minute investment transforms you from someone who "knows about Copilot" to someone who can say "When I used Copilot, I experienced..." - a powerful shift in credibility.

## Objectives

You will be able to complete the following tasks:

- Task 1: Verify GitHub Copilot is active and understand the interface
- Task 2: Build business automation scripts with Copilot assistance
- Task 3: Use Copilot Chat for explanations and demo scenarios

## Prerequisites

- VS Code installed with GitHub Copilot extension enabled
- GitHub Copilot license assigned to your account
- Basic familiarity with VS Code interface
- Completion of Exercise 1 (understanding Copilot features)

---

## Task 1: Setup and Verify Your Copilot Experience

In this task, you'll verify that GitHub Copilot is active and understand the two main ways to interact with it: inline suggestions and Copilot Chat.

### A. Verify Copilot is Active

1. Open **Visual Studio Code** from your desktop or taskbar.

   ![](../media/v2-ex2-open-vscode.png)

1. Look at the bottom-right corner of VS Code for the **GitHub Copilot icon** (1). It should show a checkmark indicating Copilot is active.

   ![](../media/v2-ex2-copilot-active.png)

   > **Troubleshooting:** If you see a warning icon or "Copilot: Inactive", click the icon and sign in with your GitHub account. Contact your lab instructor if issues persist.

1. Create a new file by pressing **Ctrl+N** (Windows) or **Cmd+N** (Mac).

1. Save the file as `test_copilot.py` by pressing **Ctrl+S** (Windows) or **Cmd+S** (Mac). Choose a location like your Desktop.

   > **Why .py extension?** Python is widely understood and great for quick demos. Copilot works with 40+ languages, but Python is perfect for business automation examples.

### B. Understand the Two Copilot Interfaces

GitHub Copilot provides two ways to assist you:

| Interface | How It Works | Best For |
|-----------|--------------|----------|
| **Inline Suggestions** | AI suggests code as you type (gray text) | Writing code quickly, autocomplete on steroids |
| **Copilot Chat** | Conversational AI in a sidebar panel | Asking questions, explaining code, generating templates |

You'll use both in this exercise!

---

## Task 2: Build Business Automation with Copilot

In this task, you'll create practical business scripts that demonstrate Copilot's capabilities. These are the same types of tasks your developers (or customer developers) handle daily.

### A. Scenario 1: Sales Data Analysis Script

Let's build a Python script that analyzes sales data from a CSV file - a common business need.

1. In your `test_copilot.py` file, type the following comment and press **Enter**:

   ```python
   # Function to read a CSV file and calculate total sales by region
   ```

1. **Watch the magic!** Copilot will suggest code in gray text. Press **Tab** to accept the suggestion.

   ![](../media/v2-ex2-inline-suggestion.png)

   > **Manager/Sales Insight:** This is the moment customers get excited. In seconds, Copilot generated a complete function with error handling, comments, and proper structure. This isn't just autocomplete - it understood business intent from a simple comment.

1. Continue by typing another comment and letting Copilot suggest:

   ```python
   # Function to generate a sales report with charts
   ```

1. Again, press **Tab** to accept Copilot's suggestion.

   > **Key Talking Point:** "I described what I wanted in plain English, and Copilot wrote the code. Imagine this across thousands of developers for months - the time savings compound dramatically."

**What Just Happened?**
- You wrote ~2 lines of comments
- Copilot generated ~20-40 lines of working code
- The code includes imports, error handling, and best practices
- **Time saved**: ~10-15 minutes of manual coding

### B. Scenario 2: Email Template Generator

Now let's create something that resonates with business users - automated email generation.

1. Create a new file: Press **Ctrl+N** and save as `email_automation.py`

1. Type this comment:

   ```python
   # Function to generate professional follow-up email template for a sales meeting
   # Include: greeting, meeting recap, next steps, call to action
   ```

1. Press **Enter** and let Copilot generate the function. Accept with **Tab**.

   ![](../media/v2-ex2-email-template.png)

1. Below that, type:

   ```python
   # Function to personalize the email with customer name and company
   ```

1. Accept Copilot's suggestion.

   > **Sales/Manager Talking Point:** "This shows Copilot isn't just for 'coding' - it understands business processes. It helped me build a tool that my sales team could actually use."

### C. Scenario 3: ROI Calculator (Perfect for Demos!)

This one is gold for customer conversations or executive presentations.

1. Create a new file: `roi_calculator.py`

1. Type:

   ```python
   # Function to calculate GitHub Copilot ROI based on:
   # - Number of developers
   # - Average hourly rate
   # - Time saved per developer per day (hours)
   # - Copilot cost per user per month
   # Return: Annual ROI percentage, payback period in months
   ```

1. Let Copilot generate the complete function. You'll see it creates a sophisticated calculation.

1. Now type:

   ```python
   # Example usage with sample data
   ```

1. Copilot will even generate test code showing how to use the function!

   ![](../media/v2-ex2-roi-calculator.png)

   > **Pro Tip for Sales/Managers:** This ROI calculator you just built? Use it in actual customer meetings! You created a real tool in under 2 minutes.

**Reflection Moment:**
- You created 3 working scripts in ~5 minutes
- No deep Python knowledge required
- Each script solves a real business problem
- This is what developers experience all day, every day with Copilot

---

## Task 3: Use Copilot Chat for Explanations and Demos

In this task, you'll use the conversational Copilot Chat feature to ask questions, get explanations, and prepare demo scenarios.

### A. Open Copilot Chat

1. In VS Code, click the **Chat icon** in the left sidebar (it looks like a conversation bubble) or press **Ctrl+Alt+I** (Windows) or **Cmd+Alt+I** (Mac).

   ![](../media/v2-ex2-open-chat.png)

1. The Copilot Chat panel will open on the left side of your screen.

### B. Ask Copilot to Explain Code

Let's use a real-world scenario: explaining complex Power BI DAX formulas (which you'll encounter in Exercise 5).

1. In the Copilot Chat, type:

   ```
   Explain this Power BI DAX formula in simple terms: 
   Hours Saved per Dev = DIVIDE([Total Acceptances], [Active Users], 0) * 0.5
   ```

1. Press **Enter** and watch Copilot provide a clear explanation.

   ![](../media/v2-ex2-chat-explain.png)

   > **Manager Insight:** When reviewing analytics with your team, you can quickly get explanations of complex formulas without hunting through documentation.
   
   > **Sales Insight:** Customers often ask "How does this work?" - Copilot helps you provide instant, accurate answers during demos.

### C. Generate Documentation

1. Go back to your `roi_calculator.py` file and highlight the ROI function code.

1. Right-click and select **Copilot** → **Generate Docs** (or type `/doc` in Chat).

   ![](../media/v2-ex2-generate-docs.png)

1. Copilot will generate professional documentation with parameter descriptions and examples.

   > **Key Talking Point:** "Developer documentation is often an afterthought because it's tedious. Copilot makes it effortless, improving code quality across the organization."

### D. Practice Demo Scenarios

These are three powerful demos you can show to anyone:

**Demo 1: The "Autocomplete Magic" (30 seconds)**
1. Create a new Python file
2. Type: `# Function to send a Slack notification when a PR is approved`
3. Press Enter and watch Copilot generate the entire function
4. **Talking point:** "This used to take 10 minutes. Now it's 10 seconds."

**Demo 2: The "Complex Logic Generator" (2 minutes)**
1. In Chat, ask: "Write a Python function to detect anomalies in daily sales data using statistical methods"
2. Watch Copilot generate sophisticated statistical code
3. **Talking point:** "Even experienced developers would spend 20-30 minutes researching this. Copilot provides it instantly."

**Demo 3: The "Learning Assistant" (1 minute)**
1. Copy any complex code (use your ROI calculator)
2. In Chat, ask: "Explain this code to a non-technical manager"
3. Watch Copilot provide a clear business-friendly explanation
4. **Talking point:** "Copilot doesn't just write code - it democratizes understanding. Anyone can learn what code does."

### E. (Optional) Record Your Demo

If you have screen recording software:

1. Record yourself doing one of the demos above
2. Save the video for customer meetings or internal presentations
3. Having your own "live" footage is more authentic than generic marketing videos

---

## Notes

### What You Just Experienced

- **Speed**: Tasks that take 10-30 minutes were reduced to seconds  
- **Quality**: Generated code includes error handling, comments, best practices  
- **Accessibility**: You didn't need deep programming expertise to be productive  
- **Versatility**: Works for data analysis, automation, documentation, learning  
- **Business Value**: Every script you created solves real business problems  

### Key Talking Points for Your Next Conversation

**For Managers:**
- "I used Copilot myself to build data analysis scripts in minutes"
- "Now I understand why my developers are so enthusiastic about it"
- "The ROI isn't just about speed - it's about empowering everyone"

**For Sales Professionals:**
- "When I first tried Copilot, I was skeptical. But then I built a sales data analyzer in 2 minutes..."
- "I'm not a developer, but Copilot made me productive with Python immediately"
- "Let me show you something I built with Copilot just this morning..."
- "The moment that convinced me was when it predicted my entire function from a comment"

### Objections You Can Now Handle Authentically

| Objection | Your Response (Based on Experience) |
|-----------|-------------------------------------|
| "Is it really that helpful?" | "Yes - I built 3 working scripts in 5 minutes. Let me show you my ROI calculator..." |
| "Will developers trust AI-generated code?" | "The code includes error handling and best practices. I reviewed it and it's production-ready." |
| "Isn't it just autocomplete?" | "No - I described a complex ROI calculator in English and it wrote sophisticated logic." |
| "What if it's wrong?" | "Developers still review and test. But I found Copilot gives me a great starting point every time." |
| "Do you need to be an expert coder?" | "I'm not! I used simple comments and Copilot did the heavy lifting." |

### Files You Created (Keep These!)

- `test_copilot.py` - Sales data analysis functions
- `email_automation.py` - Professional email templates
- `roi_calculator.py` - **Use this in actual ROI discussions!**

These are now **your demo assets** - real code you created with Copilot.

---

## Summary

In just 12 minutes, you experienced what makes GitHub Copilot transformative. You built practical business tools, learned how AI assistance works in real-time, and discovered compelling demo scenarios. More importantly, you can now speak from experience - whether you're a manager evaluating Copilot's value or a sales professional building customer trust.

This hands-on experience transforms your credibility. You're no longer repeating marketing claims - you're sharing personal discoveries. In the next exercises, you'll analyze data that measures these productivity improvements at scale across entire development teams.

**Pro Tip:** Keep these Python files! When someone asks "Have you actually used Copilot?", open these files and say "Yes - here's what I built..."

---

### You have successfully completed this exercise. Click **Next >>** to continue to Exercise 3.
