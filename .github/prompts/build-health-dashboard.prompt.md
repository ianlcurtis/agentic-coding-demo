# Build Health Metrics Dashboard

## Objective

Read the requirements in `Requirements.md` at the repository root, then plan and implement the Health Metrics Dashboard application end-to-end. Build, add tests, and run the application.

During planning, if you encounter unknowns that cannot be sensibly deduced from the requirements or the architectural decisions below, ask me for input before proceeding.

---

## Architectural Decisions

### Tier 1 — Frontend (React)

- Use React with Vite for project scaffolding.
- Use Tailwind CSS for styling.
- Use Recharts for charting / data visualization.
- Use React Router for page navigation (Dashboard, Log Entry, History).
- The frontend communicates with the middle tier via REST API calls (fetch or axios).

### Tier 2 — Middle Tier (.NET Aspire)

- Use .NET Aspire to orchestrate the application.
- Expose a RESTful Web API (ASP.NET Core) that the React frontend consumes.
- Use the **Repository Pattern** to abstract all database access behind interfaces (e.g., `IVitalRepository`, `IThresholdRepository`).
- The API project should depend only on repository interfaces; concrete implementations live in a separate data-access project.

### Tier 3 — Database (SQL Server)

- Design a SQL Server schema to store vitals, thresholds, and related data.
- Create SQL scripts for:
  - **Schema creation** (`create-schema.sql`) — tables, indexes, constraints.
  - **Seed data** (`seed-data.sql`) — sample vitals and default healthy-range thresholds.
- **For initial development and testing, implement an in-memory database** (e.g., EF Core `UseInMemoryDatabase`) behind the same repository interfaces so the app runs without a real SQL Server instance.
- The in-memory implementation should seed the same default data on startup.

### Project Structure (suggested)

```
/
├── Requirements.md
├── src/
│   ├── HealthDashboard.AppHost/          # .NET Aspire app host
│   ├── HealthDashboard.ServiceDefaults/  # Aspire service defaults
│   ├── HealthDashboard.Api/              # ASP.NET Core Web API
│   ├── HealthDashboard.Data/             # Repository interfaces + EF Core / in-memory implementations
│   ├── HealthDashboard.Models/           # Shared domain models / DTOs
│   └── frontend/                         # React + Vite app
├── tests/
│   ├── HealthDashboard.Api.Tests/        # API unit & integration tests
│   └── frontend/                         # React component / integration tests (Vitest)
├── sql/
│   ├── create-schema.sql
│   └── seed-data.sql
└── .github/
```

---

## Process

### Step 1 — Plan

1. Read `Requirements.md` fully.
2. Produce a detailed implementation plan covering:
   - Data model / entity design (tables, columns, relationships).
   - API endpoints (routes, methods, request/response shapes).
   - Frontend pages and components.
   - Test strategy (what to test, at which layer).
3. **Ask me** about anything that is ambiguous or has multiple reasonable approaches before writing code.

### Step 2 — Scaffold

4. Create the .NET Aspire solution with the projects listed above.
5. Scaffold the React + Vite frontend inside `src/frontend`.
6. Install all necessary packages.

### Step 3 — Implement Backend

7. Define domain models in `HealthDashboard.Models`.
8. Define repository interfaces in `HealthDashboard.Data`.
9. Implement the in-memory repository with default seed data.
10. Build API controllers that use the repository interfaces via dependency injection.
11. Wire up Aspire orchestration in the AppHost.

### Step 4 — Implement Frontend

12. Build the pages: Dashboard, Log Entry, History.
13. Build reusable components: VitalCard, VitalChart, VitalForm, HistoryTable, AlertBadge, DateRangeFilter.
14. Connect to the API with a service layer / custom hooks.
15. Implement form validation per the requirements.

### Step 5 — SQL Scripts

16. Write `sql/create-schema.sql` matching the data model.
17. Write `sql/seed-data.sql` with realistic sample data and default thresholds.

### Step 6 — Tests

18. Write API unit tests for repository logic and controller behavior.
19. Write frontend component tests with Vitest + React Testing Library.
20. Ensure all tests pass.

### Step 7 — Build & Run

21. Build the full solution.
22. Run the Aspire app host and confirm the dashboard loads with seed data, charts render, and CRUD operations work.
23. Report any issues and fix them.

---

## Constraints

- Do **not** require a running SQL Server instance to demo the app; the in-memory database must be the default.
- All API endpoints must return proper HTTP status codes and validation error messages.
- The frontend must be responsive down to 375px viewport width.
- Follow the acceptance criteria listed at the bottom of `Requirements.md`.
