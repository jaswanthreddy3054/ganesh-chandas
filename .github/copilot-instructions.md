# Ganesh Chandas — GitHub Copilot Instructions

## Project
Application: Ganesh Chandas
Event: Chandas Management
Committee: Bala Ganesh Committee

This is a mobile-first donation/chanda management application.

## Technology
- Next.js
- TypeScript
- Tailwind CSS
- shadcn/ui
- Supabase PostgreSQL
- Supabase Auth
- Supabase Row Level Security (RLS)
- Gemini API
- Recharts
- SheetJS
- Vercel
- GitHub

Prefer free and open-source solutions wherever practical.

## Development Rules

1. Read this entire file before making changes.
2. Inspect the existing project before creating or modifying files.
3. Build incrementally in small phases.
4. Do not unnecessarily overwrite, delete, or restructure working code.
5. Keep the application mobile-first and responsive.
6. Keep the UI simple, clean, festive, and professional.
7. Use reusable components.
8. Keep business logic separate from UI where practical.
9. Never put API keys, passwords, service-role keys, or secrets in frontend code.
10. Use environment variables for secrets.
11. Never expose Supabase service-role credentials to the browser.
12. Use server-side permission checks for sensitive operations.
13. Use Supabase RLS for database security.
14. Validate user input on the server.
15. Do not invent data or fake successful operations.
16. Test each feature before moving to the next phase.
17. Do not add unnecessary dependencies.
18. Prefer the simplest reliable implementation when requirements are unclear.

## Roles

There are only two roles:

### Admin
Admin has complete access:
- Dashboard
- Donors
- Payments
- Sponsors
- Members
- Receipts
- Invitations
- AI Assistant
- Reports
- Exports
- Activity Logs
- Settings
- User management

### Member
Members can:
- Log in
- Add donors
- Search donors
- View permitted donor information
- Update permitted donor/payment information
- Mark payments paid/unpaid
- Record cash/UPI
- Set expected payment dates
- Generate receipts
- View their own activity
- Use AI only with data they are permitted to access

Members must NOT access:
- Overall committee financial totals
- Other members' performance
- Admin reports
- User management
- Invitation management
- Complete database exports
- Admin settings
- Unauthorized donor/payment information

## Donor Fields

Each donor should support:

- Unique donor code such as GC-00001
- Donor name
- Mobile number
- Sponsor yes/no
- Sponsor item
- Expected sponsor amount
- Donation/chanda amount
- Payment status: paid/unpaid
- Payment method: cash/UPI
- Expected payment date when unpaid
- Paid date when paid
- Free-text notes
- Created by/date
- Updated by/date

Prevent duplicate donor records by mobile number and donor code.
Show a clear warning before creating a possible duplicate.

## Payments

Support:
- Paid/unpaid status
- Cash/UPI
- Paid date
- Expected payment date
- Payment history where appropriate

## Receipt System

Receipt numbers should be generated automatically:

GC-R-000001

Receipts should look like a beautiful festive invitation/card rather than a boring financial invoice.

Include:
- Bala Ganesh Committee
- Ganesh Chandas
- Receipt number
- Donor name
- Donor code
- Amount
- Payment method
- Paid date
- Sponsor information when applicable
- Thank-you message
- Warm wishes

Support:
- Preview
- Print
- PDF/download
- Share
- Resend

Do not use copyrighted images unless supplied or properly licensed.

Suggested thank-you message:

"Thank you for your valuable contribution to the Bala Ganesh Committee. Your generous support helps us celebrate and organize this auspicious occasion with devotion and joy. We sincerely appreciate your support and extend our warmest wishes to you and your family."

## Invitations

Admin only.

Admin can:
- Upload invitation image
- Accept JPG/JPEG/PNG/WEBP
- Preview invitation
- Select recipients:
  - Selected People
  - Expected/Pending Donors
  - All Donors
- Preview recipient count
- Customize invitation message
- Share/download/copy invitation

Do not claim that an invitation was delivered unless a real messaging provider confirms delivery.

Design the architecture so WhatsApp/SMS providers can be added later.

## Admin Dashboard

Show:
- Total donors
- Total expected
- Total collected
- Total pending
- Paid count
- Unpaid count
- Cash collection
- UPI collection
- Sponsor count
- Expected sponsor amount
- Collection percentage

Charts:
- Paid vs unpaid
- Cash vs UPI
- Collection progress
- Collection over time
- Sponsorship

## Member Dashboard

Members should only see operational information relevant to themselves:
- Donors they added
- Their paid/unpaid records
- Follow-ups
- Recent activity

Do not expose committee-wide financial totals.

## Donor Management

Admin donor table:

- Code
- Name
- Mobile
- Sponsor
- Sponsor Item
- Amount
- Status
- Method
- Expected Date
- Paid Date
- Added By

Support:
- Search
- Filter
- Sort
- Add
- Edit
- Delete
- View
- Generate receipt
- Resend receipt

Filters:
- Paid/unpaid
- Cash/UPI
- Sponsor yes/no
- Date ranges
- Expected date
- Paid date
- Added by

## Exports

Admin only:
- CSV
- Excel
- Optional PDF

Allow exporting all or filtered data.

Members must not export the complete database.

## Gemini AI

Use Gemini API.

Admin AI can answer questions about:
- Overall collection
- Pending/overdue donors
- Top donors
- Sponsorship
- Member collection performance
- Target calculations

Member AI can only answer questions using records they are authorized to access.

AI must:
- Respect permissions
- Never receive unauthorized data
- Never invent values
- Clearly state when required data is unavailable

## Audit Logs

Admin only.

Record important actions such as:
- Donor changes
- Payment changes
- Receipt actions
- Member changes
- Invitation actions

Include:
- User
- Action
- Entity
- Date/time
- Old values where appropriate
- New values where appropriate

## Security

Use:
- Supabase Auth
- Supabase RLS
- Server-side authorization
- Secure environment variables
- Input validation
- Protected admin endpoints
- Secure upload handling

Never trust frontend role checks alone.

## Navigation

Admin:
Dashboard
Donors
Payments
Sponsors
Members
Receipts
Invitations
AI Assistant
Reports
Export
Activity Logs
Settings

Member:
Dashboard
My Donors
Add Donor
Payments
Receipts
AI Assistant
Profile

## Development Phases

Build in this order:

Phase 1:
Project setup and authentication

Phase 2:
Roles, database schema, RLS, donors and payments

Phase 3:
Dashboards, search, filters and exports

Phase 4:
Receipts

Phase 5:
Invitations

Phase 6:
Gemini AI

Phase 7:
Audit logs, security review, testing and deployment

Do not attempt to build every feature at once.

## Copilot Behavior

Before implementing a phase:
1. Explain briefly what will be changed.
2. Inspect existing files.
3. Implement only the requested phase.
4. Run appropriate checks/tests.
5. Report what was changed and any issues.

If a requirement is ambiguous, choose the simplest reasonable implementation and explain the assumption.