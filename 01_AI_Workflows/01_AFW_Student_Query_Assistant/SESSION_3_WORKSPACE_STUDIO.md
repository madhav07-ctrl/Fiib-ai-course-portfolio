# AFW Student Query Assistant

## 1. Project Overview

The AFW Student Query Assistant is an AI-powered email automation workflow developed as part of the **AI & the Future of Work** course at Fortune Institute of International Business (FIIB), New Delhi.

The objective is to process student emails, understand their queries, check approved course policies, identify cases requiring student-specific information or human review, and provide policy-grounded replies.

## 2. Working Project Link

**[Open AFW Student Query Assistant – Google Workspace Studio](https://studio.workspace.google.com/workflow/z24e7ca3c33eedd4c45377e652c1b7aa5)**

Note: Access to the workflow may require an authorized Google account.

## 3. Tools and Technologies

- Google Workspace Studio – Workflow automation
- Gemini – Student query understanding and classification
- NotebookLM – Approved course policy knowledge base
- Gmail – Email trigger and automated replies
- Google Sheets – Pending case review queue

## 4. Workflow Architecture

1. **Gmail Trigger:** Identifies emails related to AFW / AI & the Future of Work.
2. **Gemini:** Understands and classifies the student's query.
3. **NotebookLM:** Checks the query against approved course documents.
4. **Decision Step:** Determines whether student-specific data or human review is required.
5. **Google Sheets:** Adds cases requiring further review to a PENDING queue.
6. **Email Reply:** Sends a response based on the approved policy information.

## 5. Test Scenarios

| Test case | Expected workflow behavior |
|---|---|
| Attendance policy question | Policy-based reply; no review queue entry |
| Individual attendance status | PENDING review because student-specific data is required |
| Deadline exception request | PENDING review because faculty authority is required |

## 6. Responsible AI and Human Review

- Uses approved course documents as its knowledge source.
- Does not invent course policies or student records.
- Does not automatically approve deadline extensions, waivers or exceptions.
- Escalates cases requiring personal records or faculty decisions.
- Provides a policy-grounded reply even when a case requires further review.

## 7. Project Scope

This classroom version covers email-based query handling, policy grounding, decision-making and a Google Sheets review queue.

External student databases and human-alert integrations are planned for a subsequent stage and are not included in this build.

## 8. Project Evidence

The following supporting materials will be added:

- Workflow screenshots
- Gemini classifier prompt
- NotebookLM policy prompt
- Decision prompt
- Test results for the three scenarios

## 9. Academic Details

**Course:** AI & the Future of Work  
**Institute:** Fortune Institute of International Business (FIIB), New Delhi  
**Project:** AFW Student Query Assistant  
**Session:** 3
