# 🧠 System Architecture

## Overview

The system is designed as a **modular automation**, where each block has a clearly defined responsibility within the overall workflow.

The main scenario processes incoming emails and their attachments, while the output is optimized for non-technical users who interact only with Airtable.

---

## Global Workflow

1. Monitor unread emails in Gmail
2. Classify emails using a Router
3. Move emails to the appropriate label
4. Process attachments individually
5. Upload files to Google Drive
6. Aggregate relevant information
7. Store structured data in Airtable

---

## Email Classification

A **Router** is used to split the flow into three main paths:

- Control Notes
- Pre-valuation
- Non-banking Assigned

Each route applies filters based on:
- Email subject
- Email body content
- Specific keywords

This design allows easy extension and maintenance without duplicating scenarios.

---

## Attachment Processing

The **List email attachments and media** module emits one bundle per attachment, which enables:

- Independent processing of each file
- Filtering out signatures, banners, or small images
- Uploading only relevant documents to Google Drive

No additional Iterator is required, as the module already processes attachments individually.

---

## Information Aggregation

After uploading files to Google Drive, an **Aggregator** is used to:

- Consolidate attachment information
- Group files by email using the `Message ID`
- Prepare a clean, structured output for Airtable

The aggregated information includes:
- File name
- Google Drive link
- Logical location derived from the email label

---

## Airtable Output

Each processed email generates a record in Airtable containing:
- File name
- Folder / category
- Direct link to the file in Google Drive

The output is designed to be **human-readable**, avoiding technical arrays or internal system structures.
