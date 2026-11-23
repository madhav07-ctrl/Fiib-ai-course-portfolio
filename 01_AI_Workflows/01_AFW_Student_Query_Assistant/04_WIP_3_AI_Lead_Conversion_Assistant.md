# WIP 3 – Windigitaly AI Lead Conversion Assistant

**Project:** Windigitaly AI Lead Conversion Assistant  
**Project Type:** PGDM – AI Application Development  
**Organization:** Windigitaly  
**Development Stage:** Working Classroom Application  
**Submission:** WIP 3

---

## 1. Project Overview

WIP 3 focuses on the development of the Windigitaly AI Lead Conversion Assistant, an AI-powered application designed to support the lead management and client acquisition process of Windigitaly, a digital marketing agency.

Digital marketing agencies receive enquiries from different channels. Managing these enquiries, understanding customer requirements, qualifying prospects, preparing follow-up messages, and tracking conversion outcomes can involve considerable manual effort.

The proposed application brings these activities into one workspace. It combines lead management features with AI-assisted enquiry analysis, qualification suggestions, follow-up drafting, and reporting.

The main objective is to improve the consistency of enquiry management, reduce repetitive work, and provide better visibility into the client acquisition pipeline.

The application is designed as a decision-support system. AI-generated suggestions are reviewed by team members before decisions are saved or messages are sent.

## 2. Working Application

The project has progressed from an initial prototype to a working classroom application.

The application is accessible through Google AI Studio.

**Working AI Application:**

[Open Windigitaly AI Lead Conversion Assistant – Google AI Studio](https://aistudio.google.com/apps/3a6717da-edb7-40f3-b23c-2f1f1f6e14dc?showAssistant=true&showPreview=true&fullscreenApplet=true&pli=1)

The application link provides access to the AI Studio app and its preview.

**Purpose of the application:**

- Organize incoming prospect enquiries.
- Maintain lead information.
- Analyse customer requirements.
- Identify missing information.
- Support lead qualification.
- Prepare follow-up message drafts.
- Track lead status and pipeline activity.
- Provide summaries of stored lead and follow-up records.

## 3. Business Problem

Windigitaly receives enquiries from prospective customers who are interested in services such as digital marketing, social media management, SEO, website development, and performance marketing.

Managing the enquiry-to-client journey consistently can be challenging when information, communication, and follow-up activities are handled across different platforms and manual records.

The project addresses five major business challenges.

### 3.1 Scattered Enquiry Information

Enquiry details may be available across different messages, forms, and manual records. This can make it difficult to maintain a consistent view of prospect information.

### 3.2 Uneven Lead Qualification

The team needs a consistent way to understand a prospect's requirements, service needs, budget, timeline, and suitability.

### 3.3 Follow-up Gaps

Without clear next actions and follow-up dates, important prospects may not receive timely communication.

### 3.4 Limited Pipeline Visibility

Managers need a reliable view of the lead pipeline, including the current stage of each prospect and the outcome of enquiries.

### 3.5 Repetitive Manual Work

Initial enquiry analysis, checking missing information, and preparing responses can require repeated manual effort.

The application is intended to support these areas through a structured digital workflow.

## 4. Proposed Solution

The Windigitaly AI Lead Conversion Assistant provides a centralized workspace for managing prospect enquiries and supporting the conversion process.

The solution combines lead records, AI-assisted analysis, follow-up drafting, and reporting.

The application follows five stages:

### Step 1 – Capture

A team member enters a new enquiry or adds a lead record.

The purpose is to maintain prospect information in a structured format.

### Step 2 – Analyse

The AI assistant analyses the enquiry and helps identify:

- Customer requirements.
- Services of interest.
- Available budget information.
- Expected timeline.
- Missing information.
- Suggested qualification details.

The AI should leave information unspecified when the customer has not provided it rather than inventing details.

### Step 3 – Review

A team member reviews the AI-generated analysis and edits the lead information where required.

This is the human-control checkpoint in the workflow.

### Step 4 – Follow-up

The application can generate a response or follow-up message draft based on the enquiry.

The team member reviews and approves the draft before contacting the prospect.

### Step 5 – Track

The lead status is updated, and the team can review pipeline information and reporting data.

**Overall workflow:**

Enquiry Capture → AI Analysis → Human Review → Follow-up Draft → Lead Tracking

## 5. Application Modules

The application is organized into six main modules.

### 5.1 Overview Dashboard

The dashboard provides an overall view of the lead pipeline.

It includes:

- Pipeline summary.
- Lead temperatures.
- Pending follow-ups.
- Lead-stage breakdown.

The purpose is to help the team understand the current position of incoming enquiries.

### 5.2 Lead Management

The Lead Management module handles prospect records.

Its functions include:

- Creating new lead records.
- Searching existing prospects.
- Reviewing lead information.
- Updating prospect details.
- Changing lead statuses.

This module provides a structured location for maintaining enquiry information.

### 5.3 AI Lead Assistant

The AI Lead Assistant supports the analysis of customer enquiries.

Its functions include:

- Understanding customer requirements.
- Summarizing enquiries.
- Identifying missing information.
- Suggesting qualification details.
- Supporting AI chat.
- Preparing follow-up message drafts.

The AI output is treated as a suggestion and requires human review.

### 5.4 Follow-up Manager

The Follow-up Manager helps organize follow-up activities.

It is intended to make next actions more visible and support timely communication with prospects.

### 5.5 Reports and Analytics

The Reports and Analytics module provides summaries calculated from stored lead and follow-up records.

It supports better visibility into pipeline activity and lead outcomes.

### 5.6 Data Handling

Lead records are stored in Firestore.

CSV/Excel import is being tested as part of the application's data-handling development.

## 6. Technology Stack

The application uses the following technologies and services.

| Technology | Purpose |
|---|---|
| Google AI Studio | AI application access and preview |
| Firestore | Storage of lead records |
| OpenRouter API | AI model connectivity |
| Baidu ERNIE 5.5 Flash Preview | Currently tested free model endpoint |
| TypeScript | Application development |

### 6.1 Firestore

Firestore is used to store lead records.

The application uses this database layer to maintain prospect information for lead management and reporting.

### 6.2 OpenRouter API

The AI features connect through the OpenRouter API.

The currently tested model endpoint is Baidu ERNIE 5.5 Flash Preview.

The endpoint is being used through a free model offering. Its availability, response speed, and usage limits depend on the provider.

### 6.3 TypeScript

TypeScript is used in application development. Build and TypeScript checks were reported as successfully completed in the project presentation.

## 7. Workflow Demonstration

The project presentation includes an illustrative example showing how the application handles a customer enquiry.

**Illustrative customer enquiry:**

"Hi, we run a small café chain and want help growing our Instagram and running Google Ads."

This example demonstrates the following process.

### 7.1 Enquiry Capture

The customer enquiry is entered into the application.

The system receives information about the prospect's interest in social media and paid advertising.

### 7.2 AI Analysis

The AI assistant identifies:

| Field | AI Analysis |
|---|---|
| Interest | Social media and paid ads |
| Budget | Not specified |
| Timeline | Not specified |
| Next Step | Ask for budget and timeline |

The assistant does not assume a budget or timeline when the customer has not provided those details.

### 7.3 Follow-up Draft

The application prepares a suggested response:

"Thanks for reaching out! To suggest the right plan, could you share your budget range and ideal start date?"

The team member reviews and approves the message before sending it.

**Note:** This is an illustrative example, not real customer data.

## 8. Testing and Validation

The project presentation reports the following technical checks.

| Test Area | Reported Result |
|---|---|
| API status and provider connectivity | HTTP 200 OK |
| Enquiry analysis | Structured qualification fields returned |
| Missing information handling | Budget and timeline left unspecified |
| Follow-up draft endpoint | HTTP 200 OK |
| AI chat endpoint | HTTP 200 OK |
| Build checks | Passed |
| TypeScript checks | Passed |

These results indicate that the tested API endpoints and application checks were functioning during the reported tests.

However, endpoint-level testing does not establish that every application workflow is fully verified or that the application is production-ready.

## 9. Safeguards and Limitations

The application follows important safeguards to ensure that AI suggestions are reviewed appropriately.

### 9.1 Human Review

AI-generated lead classifications and follow-up messages are suggestions.

A team member reviews the output before saving decisions or contacting a prospect.

### 9.2 Avoiding Incorrect Information

The AI must not invent:

- Customer budgets.
- Project timelines.
- Customer requirements.
- Other facts that have not been provided.

Missing information should be identified rather than guessed.

### 9.3 Model Availability

The currently tested AI model uses a free endpoint.

Availability, response speed, and usage quotas may change depending on the provider.

### 9.4 Data Privacy

Real client data requires appropriate permission, privacy controls, and secure access.

### 9.5 Application Readiness

Successful API responses and build checks are useful technical indicators, but they do not independently prove production readiness.

### 9.6 Messaging Control

The application prepares follow-up drafts for human approval.

Automatic customer messaging is not claimed in this version.

## 10. Current Development Status

The application is currently a working classroom application and remains under end-to-end verification.

| Development Stage | Status |
|---|---|
| Working application build | Completed |
| API connectivity checks | Tested |
| Enquiry analysis | Tested |
| AI chat and follow-up draft endpoints | Tested |
| Build and TypeScript checks | Passed |
| End-to-end verification | In progress |
| Controlled pilot | Planned |
| Live client deployment | Not yet approved |

The project is not yet approved for live client deployment.

## 11. Implementation Roadmap

The next stage focuses on validating the application before moving toward a controlled pilot.

### 11.1 Validate Lead Records

Test the following activities:

- Adding lead records.
- Editing existing records.
- Refreshing and checking stored information.
- Deleting records.

### 11.2 Validate CSV/Excel Imports

Test data imports using a clean sample file and review the handling of errors.

### 11.3 Validate AI Outputs

Test different types of customer enquiries.

Check:

- Accuracy of enquiry analysis.
- Identification of missing information.
- Consistency of qualification suggestions.
- Quality of follow-up message drafts.
- Whether the AI avoids inventing customer details.

### 11.4 Controlled Pilot

After validation, the next proposed stage is a controlled pilot.

The pilot should use anonymized or authorized data, with human review and monitoring of application outcomes.

Wider implementation should be considered only after the pilot results have been evaluated.

## 12. Expected Business Value

The application is intended to support Windigitaly's operations in the following areas:

| Business Area | Intended Contribution |
|---|---|
| Enquiry management | Centralized lead information |
| Lead qualification | More consistent analysis |
| Follow-up management | Better visibility of next actions |
| Customer communication | Structured follow-up drafts |
| Reporting | Improved pipeline visibility |
| Operational efficiency | Reduced repetitive manual work |

These are intended benefits. Actual business impact must be measured during a controlled pilot against an established baseline.

## 13. Conclusion

WIP 3 demonstrates the development of a working AI Lead Conversion Assistant for Windigitaly.

The application brings together lead management, AI-assisted enquiry analysis, qualification suggestions, follow-up drafting, and reporting within one workspace.

The project has progressed beyond the initial concept into a working classroom application, with API connectivity and application checks reported as successful.

The next priority is end-to-end verification of lead records, data imports, and AI outputs, followed by a controlled pilot.

The application is intended to support the team's decision-making and improve enquiry management. It does not replace human judgment or claim to be ready for unrestricted live client deployment.

## 14. Supporting Resources and Evidence

### A. Working AI Application

[Open Windigitaly AI Lead Conversion Assistant – Google AI Studio](https://aistudio.google.com/apps/3a6717da-edb7-40f3-b23c-2f1f1f6e14dc?showAssistant=true&showPreview=true&fullscreenApplet=true&pli=1)

### B. Project Presentation

[View / Download WIP 3 – AI Lead Conversion Assistant](./WIP_3_AI_Lead_Conversion_Assistant.pptx)

### C. Presentation Contents

The supporting PowerPoint covers:

1. Project introduction.
2. Business context and problem.
3. Five-step solution workflow.
4. Illustrative enquiry demonstration.
5. Six application modules.
6. Technology architecture.
7. Testing and safeguards.
8. Current development stage.
9. Implementation roadmap.
10. Conclusion and questions.

### D. Source and Evidence Note

This documentation is based on the uploaded Windigitaly AI Lead Conversion Assistant presentation and the Google AI Studio application link.

Testing results and development status are reported as presented in the project material. Proposed pilot activities and expected business benefits are identified as future plans rather than completed outcomes.
