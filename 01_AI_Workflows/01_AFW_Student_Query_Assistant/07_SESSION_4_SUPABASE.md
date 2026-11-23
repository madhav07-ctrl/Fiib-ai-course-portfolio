# Session 4 — Supabase Integration

## Objective
To create a student-record database and retrieve student information through a Supabase RPC function.

## Platform
Supabase

## Project Details
- Project Name: AFW Session 4
- Project Reference: wbrawoksvzcvfcasnslj
- [Supabase Dashboard](https://supabase.com/dashboard/project/wbrawoksvzcvfcasnslj)

## Database
Table Name: `public.afw_student_records`

The table stores fictional classroom student records with the following fields:
- Email
- Student Name
- Program
- AFW Sessions Attended
- AFW Sessions Missed
- Pending Assessments
- Evidence Folder Status
- Notes

## Database Function
Function Name: `get_afw_student_record(p_email text)`

This function retrieves a student record using the email address and returns the result in JSON format.

## API Details
- Project URL: `https://wbrawoksvzcvfcasnslj.supabase.co`
- REST API: `https://wbrawoksvzcvfcasnslj.supabase.co/rest/v1/`
- RPC Endpoint: `https://wbrawoksvzcvfcasnslj.supabase.co/rest/v1/rpc/get_afw_student_record`

## Testing Result
The Supabase lookup was tested through Google Apps Script.

- HTTP Response: 200
- Record Found: True
- Student Record: Returned successfully

## Integration
Google Apps Script connects to Supabase through the REST API. Supabase manages the database and lookup function, while Apps Script manages the workflow.

## Security
- Supabase Publishable key is stored in Apps Script Script Properties.
- No API keys or secret credentials are included in this repository.
- Only fictional classroom data is used.
# Session 4 — Google Apps Script Integration

## Objective
To automate student query processing by connecting Google Sheets, Supabase, and Gmail.

## Platform
Google Apps Script

## Project
AFW Session 4

## Apps Script Project Link
[Open AFW Session 4 Apps Script](https://script.google.com/u/0/home/projects/1MDoCEO4osiop6pZPQwcgT4D8LeeKccvWZ3N-JXvbXE-NBEjSJ6zouVVk/edit)

## Functions Implemented

1. `testReadPendingRows()` — Reads pending queries from Google Sheets.
2. `testSupabaseLookup()` — Tests the Supabase database connection.
3. `processLatestPendingRow()` — Processes the latest pending query, retrieves student information, and prepares a contextual email reply.

## Supabase Integration
Apps Script connects to the Supabase RPC function:

`get_afw_student_record(p_email text)`

## Automation Trigger
- Event source: Time-driven
- Function: `processLatestPendingRow`
- Frequency: Every minute

## Testing Results
- Google Sheets connection: Successful
- Supabase API response: HTTP 200
- Pending row reading: Successful
- Processing function: Executed; latest run reported no pending rows
- Trigger: Configured

## Workflow
Google Sheets → Apps Script → Supabase → Contextual Response → Gmail

## Security
Credentials are stored in Apps Script Script Properties and are not included in this repository.
