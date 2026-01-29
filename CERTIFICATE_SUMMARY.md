# Project Certificate Summary

Last updated: January 29, 2026

## Project Name
Conscript Affairs Management System (Egyptian Ministry of Interior)

## Project Type
ASP.NET Core MVC web application (enterprise/government administrative system)

## Purpose
Digitize and centralize conscript administration workflows, improve accuracy of daily completion, attendance and leave oversight, and enable secure reporting for leadership review.

## Organization
Egyptian Ministry of Interior

## Scope of Work (Delivered Capabilities)
- Full conscript registry with lifecycle management (create, edit, delete, restore).
- Officer and department management, including assignment and analytics.
- Attendance and leave calendar with holiday alerts and return tracking.
- Daily completion reporting with Excel export.
- Soldier notes (notebooks) with file attachments and history export.
- Alarms with recurrence, snooze, dismiss, and history tracking.
- Notifications and internal chat with real-time updates.
- Dashboards and analytics (state, qualification, governorate, religion, radif dates).
- Scheduled backups and data export snapshots.
- Role-based access control with module-level permissions.

## Architecture and Technology
- .NET 8 / ASP.NET Core MVC
- Entity Framework Core (SQL Server)
- ASP.NET Identity (roles and permissions)
- Hangfire (background jobs)
- SignalR (real-time notifications and chat)
- Serilog (structured logging)
- Excel and PDF generation tools (EPPlus, ClosedXML, NPOI, PdfSharp, iTextSharp)

## Security and Privacy
- Role-based access control and permission policies.
- Audit-friendly logging.
- Public repository intentionally excludes source code, secrets, and sensitive data.

## Status
Implemented and operational (internal use).

## Evidence
Place the official certificate PDF in:
- `assets/certificates/MOI-Certificate.pdf`

## Notes
This summary is provided for certificate and documentation purposes.
Operational code and sensitive configuration remain private by policy.
