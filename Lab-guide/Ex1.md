# Exercise 1: Enable & Access Copilot Usage Reports (Read-only)

### Estimated Duration: 15 Minutes

## Overview

In this exercise, you will enable and access GitHub Copilot organization-level usage (activity) reports. These reports provide foundational visibility for managers and program owners to understand adoption, engagement, and value metrics before deeper analytics are built in later exercises.

## Objectives

You will be able to complete the following tasks:

- Task 1: Activate reporting features (initiate generation of the Activity report)
- Task 2: Download usage data (confirm report generation and retrieve CSV)

## Prerequisites

- You are an **Organization Owner** of the target GitHub organization (e.g., `contoso-impact`).
- GitHub Copilot Business or Enterprise is already licensed for the org.
- Email access to the owner mailbox (for the report-ready notification).

## Task 1: Activate Reporting Features

In this task you will navigate to the Copilot admin area and initiate the Activity report generation.

1. In the top-right of GitHub, click your **profile picture (1)** → select **Organizations (2)**.

   ![](../media/gt-co-ex1-g1.png)

1. On **Settings › Organizations**, click your org **contoso-impact** (role: **Owner**).  

   ![](../media/gt-co-ex1-g2.png)

1. On the org home, select **Settings** from the top navigation.  

   ![](../media/gt-co-ex1-g3.png)

1. In the left sidebar under **Code, planning, and automation (1)**, expand **Copilot (2)** → click **Access (3)**.  

   ![](../media/gt-co-ex1-g4.png)

1. On **Access management**, open **Get Usage report (1)** → choose **Activity report (new) (2)**.

   ![](../media/gt-co-ex1-g5.png)

## Task 2: Download Usage Data

In this task you will confirm the report request was accepted and obtain the CSV once the asynchronous generation completes.

1. Confirm the green banner **“Your activity report is being generated…”** appears.  

   ![](../media/gt-co-ex1-g6.png)

1. Watch for the email titled **“Your GitHub Copilot Activity report is ready”** and download the CSV if available.  

   ![](../media/gt-co-ex1-g7.png)

> **Tip:** Report generation can take several minutes depending on organization size. You can proceed to later exercises while waiting, then return to download.

## Notes

- If you do not see **Activity report (new)**, ensure your organization is on a supported Copilot plan and that you have Owner permissions.
- The downloaded CSV (often named like `copilot_org.csv`) will be used in Exercise 2 for building analytics measures.
- Regenerating a report overwrites the previous pending request but does not delete earlier downloaded files you saved locally.
- Keep the raw CSV unmodified; create a copy for transformation steps in later exercises.

<validation step="ex1-validate-usage-report" />

> **Validation Instructions**
> - Click the Validate button for this exercise in the lab environment UI.
> - If validation fails, re-check: (a) you initiated the Activity report, (b) banner appeared, (c) email received/download attempted.
> - For assistance email: cloudlabs-support@spektrasystems.com.

## Summary

In this exercise, you enabled GitHub Copilot usage reporting and requested the Activity report, then confirmed generation and (optionally) downloaded the resulting CSV. This dataset now serves as the authoritative source for adoption and engagement metrics you will model in subsequent exercises.

### You have successfully completed this exercise. Please continue to the next one >>
