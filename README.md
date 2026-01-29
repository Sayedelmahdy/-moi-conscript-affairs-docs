# Conscript Affairs Management System (Egyptian Ministry of Interior)
Public, redacted documentation for the MVC software system used to manage conscript affairs.  
Source code and sensitive configuration are intentionally excluded from any public release.

## 1) Project Purpose
This system digitizes and centralizes conscript administration workflows, enabling:
- Accurate tracking of conscripts, officers, and departments.
- Daily completion (التمام اليومي) and attendance/leave oversight.
- Structured reporting and exports for operational and leadership review.
- Secure, role-based access and audit-friendly logging.

## 2) Core Modules (منظومة الوحدات)
Below are the functional modules defined by the permission system, mapped to the MVC areas:
- الحضوروالاجازات (Attendance & Leaves): calendar views, leave tracking, holiday alerts.
- النسخ_الاحتياطى (Backups): on-demand and scheduled backups.
- الاحصائيات (Dashboard/Analytics): KPIs and breakdowns by department, officer, state, etc.
- الادارات (Departments): department CRUD and structure management.
- الضباط (Officers): officer registry and assignment controls.
- المبيتات (Overnight): overnight/shift placement and removal.
- المجندين (Soldiers): core conscript registry and lifecycle.
- ملاحظات_المجندين (Soldier Notes): notebooks, files, and history export.
- حالات_المجندين (Soldier States): state changes (leave, mission, absence, etc.).
- العمل_المسند (Assigned Work): task/role assignment to conscripts.
- الادوار (Roles): role management.
- الصلاحيات (Permissions): fine-grained permissions per module.
- المستخدمين (Users): user management.
- المجندين_المحذوفين (Deleted Soldiers): archive and restore.
- تنبيهات_الاجازات (Holiday Alerts): leave expiry and return alerts.
- التمام_اليومي (Daily Completion): daily presence reporting.
- التنبيهات (Notifications): in-app notification system.

## 3) Major Features (Summary of What’s Built)
### Conscript Management
- Full registry CRUD for soldiers (create, edit, delete, restore).
- State lifecycle management (e.g., present, leave, mission, absence, training).
- Bulk operations: bulk state updates, bulk delete/restore.
- Excel import/export for large datasets.

### Officer & Department Management
- Officer and department CRUD.
- Assignment of conscripts to officers and departments.
- Department-level and officer-level count analytics.

### Attendance, Leaves, and Daily Completion
- Attendance calendar with time-based filters.
- Holiday alerts and return tracking.
- Daily completion reporting with export to Excel.

### Soldier Notebooks & History
- Notes per soldier with categories and attachments.
- File preview/download and notebook history export.

### Alarms, Notifications, and Chat
- Alarm creation/editing with recurrence, snooze, dismiss, and completion.
- Alarm history and real-time alarm updates via SignalR hubs.
- Notifications module and internal chat UI.

### Dashboards & Analytics
- Department/officer counts and KPI panels.
- Statistics by soldier state, qualification, governorate, religion, and radif dates.
- Advanced filtering and exclusion logic for analytics.

### Backup & Data Protection
- Manual and scheduled backups (Hangfire job scheduling).
- Automatic Excel snapshot backup of conscript data.

## 4) Data Model (Core Entities)
Key domain entities defined in the system:
- Soldier, SoldierHistory, SoldierStatus, SoldierNotebook, SoldierNotebookFile
- Officer, Department, WorkAssignedTo
- Alarm, AlarmHistory, Notification, ChatMessage

## 5) System Architecture (MVC + Services + Repositories)
- Presentation: ASP.NET Core MVC with Razor Views.
- Business Layer: Services and DTOs for validation and workflows.
- Data Layer: Repositories with Entity Framework Core (SQL Server).
- Authentication & Authorization: ASP.NET Identity + per-module permissions.
- Real-time: SignalR hubs (notifications, chat, alarms).
- Background Jobs: Hangfire (scheduled backups, alarm processing).

## 6) Technology Stack
- .NET 8 / ASP.NET Core MVC
- Entity Framework Core (SQL Server)
- ASP.NET Identity (roles, permissions)
- Hangfire (background jobs)
- SignalR (real-time notifications/chat)
- Serilog (structured JSON logs)
- Excel/PDF/Doc generation libraries: EPPlus, ClosedXML, NPOI, DocX, PdfSharp, iTextSharp
- Utility: FuzzyStrings + Levenshtein for search/matching

## 7) Security & Access Control
- Role-based access control with module-level permissions.
- Custom permission policies and authorization handlers.
- Secure cookies and session handling.
- Logging middleware for request tracking and auditability.

## 8) Localization & UI
- Arabic UI with Egyptian locale (`ar-EG`).
- Date format standardized to `dd/MM/yyyy`.
- Excel-like grid views with filtering, sorting, and bulk actions.

## 9) Operational Notes (Redacted for Public Version)
- Secrets (connection strings, credentials, keys) are not shared.
- Backups are configured through secured paths and scheduled jobs.
- Production deployment uses HTTPS and restricted access.

## 10) Folder Map (High-Level)
- `Controllers/` MVC controllers for modules.
- `Views/` Razor UI for each module.
- `Models/` Core entity models.
- `DTO/` Data transfer objects.
- `Services/` Business logic.
- `Repositories/` Data access.
- `Data/` EF Core context.
- `Migrations/` EF Core migrations.
- `Filters/`, `Middlewares/`, `Helpers/` cross-cutting utilities.

## 11) Public-Repo Policy (for Certificates/Showcase)
This public documentation is designed to support certifications and approvals while keeping
operational code and sensitive data private. If a public GitHub repo is required, publish:
- This README and related documentation only.
- Redacted diagrams/screenshots (no PII).
- Optional: API flowcharts, architecture diagrams, and sample reports with masked data.

---
If you need a printable certificate summary or a Ministry-ready brief, request a formal
one-page report based on this document.
