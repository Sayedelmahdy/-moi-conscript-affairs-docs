# Architecture Overview

## High-Level Layers
- Presentation: ASP.NET Core MVC + Razor Views
- Business Logic: Services + DTOs
- Data Access: Repositories + EF Core (SQL Server)
- Security: ASP.NET Identity + custom permission policies
- Background: Hangfire jobs
- Real-time: SignalR hubs (notifications, chat, alarms)

## Key Components
- Controllers: module endpoints (Soldiers, Officers, Departments, States, Alarms, etc.)
- Services: domain workflows (state transitions, imports/exports, backups)
- Repositories: data persistence and queries
- Filters/Middleware: logging, timing, authorization

## Data Flow (Typical)
User -> MVC Controller -> Service -> Repository -> EF Core -> SQL Server

## Integration Points
- Excel import/export for bulk operations
- PDF/Doc generation for reports
- SignalR for real-time events

## Suggested Diagram (Add to assets/)
1) User/UI
2) MVC Controllers
3) Services
4) Repositories
5) Database
6) Hangfire/SignalR

## Advanced Architecture Diagram (Mermaid)
Copy this into GitHub (it renders automatically):

```mermaid
flowchart TB
  subgraph Client["Client / Browser"]
    UI["Razor Views + JS UI"]
  end

  subgraph App["ASP.NET Core MVC App"]
    Ctl["Controllers"]
    Svc["Services (Business Logic)"]
    Repo["Repositories (Data Access)"]
    Auth["AuthN/AuthZ\nIdentity + Permissions"]
    Filters["Filters/Middleware\nLogging + Timing"]
    Hubs["SignalR Hubs\nNotifications / Chat / Alarms"]
    Jobs["Background Jobs\nHangfire"]
  end

  subgraph Data["Data Layer"]
    Db["SQL Server\nEF Core"]
    Files["Files/Exports\nExcel/PDF/Doc"]
  end

  subgraph Ext["External/Supporting"]
    Scheduler["Hangfire Scheduler"]
    Excel["EPPlus / ClosedXML / NPOI"]
    Pdf["iTextSharp / PdfSharp"]
    Docx["DocX / OpenXML"]
    Log["Serilog (JSON Logs)"]
  end

  UI -->|HTTP| Ctl
  Ctl --> Svc
  Svc --> Repo
  Repo --> Db

  Ctl --> Auth
  Ctl --> Filters
  Filters --> Log

  Svc --> Excel
  Svc --> Pdf
  Svc --> Docx
  Excel --> Files
  Pdf --> Files
  Docx --> Files

  Hubs <--> UI
  Ctl --> Hubs

  Jobs --> Svc
  Scheduler --> Jobs
  Jobs --> Db
  Jobs --> Files
```
