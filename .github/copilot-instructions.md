# Copilot Coding Standards

## General

- Prefer clarity over cleverness; write readable, self-documenting code.
- Keep functions and methods short and single-purpose.
- Use meaningful names for variables, functions, types, and files.
- Avoid magic numbers and strings — use named constants or enums.
- Handle errors explicitly; never silently swallow exceptions.
- Write comments only when the "why" isn't obvious from the code itself.

## C# / .NET

- Target .NET 9 and use top-level statements for program entry points.
- Use file-scoped namespaces.
- Prefer `record` types for DTOs and immutable data; use `class` for entities with identity.
- Use `async`/`await` throughout — never block on async code with `.Result` or `.Wait()`.
- Register dependencies with the narrowest lifetime possible (`Scoped` for request-scoped services, `Singleton` for stateless services).
- Follow the Repository Pattern: controllers depend on interfaces, not concrete data-access classes.
- Use data annotations for model validation on DTOs.
- Return appropriate HTTP status codes from controllers (201 for created, 204 for no content, 400 for validation errors, 404 for not found).
- Serialize enums as strings using `JsonStringEnumConverter`.
- Prefix interface names with `I` (e.g., `IVitalRepository`).
- Use nullable reference types and avoid suppressing nullability warnings without justification.

## ASP.NET Core Web API

- Use attribute routing with `[ApiController]` and `[Route("api/[controller]")]`.
- Keep controllers thin — delegate business logic to services or repositories.
- Use `ActionResult<T>` return types for endpoints that return data.
- Enable CORS policies explicitly rather than using blanket allow-all in production.

## Entity Framework Core

- Configure model constraints (precision, indexes, unique constraints) in `OnModelCreating` or with data annotations.
- Use `AsNoTracking()` for read-only queries.
- Seed default data through a dedicated static initializer, not EF migrations.

## SQL Server

- Use `IF NOT EXISTS` guards in schema creation scripts for idempotency.
- Add `CHECK` constraints for data integrity (e.g., positive values).
- Create indexes on frequently filtered columns.
- Use `MERGE` for idempotent seed data inserts.

## TypeScript / React

- Use TypeScript strict mode; avoid `any`.
- Prefer `enum` for fixed sets of values shared with the backend.
- Use functional components with hooks — no class components.
- Keep components small and composable; extract reusable UI into its own file.
- Co-locate component files with their tests when practical.
- Use `useState` for local state and lift state up only when siblings need it.
- Use `useCallback` and `useMemo` for functions and values passed as props to prevent unnecessary re-renders.

## React Router

- Use `BrowserRouter` with `Routes` and `Route` for page navigation.
- Use `NavLink` for navigation elements that need active-state styling.

## Tailwind CSS

- Use utility classes directly in JSX — avoid custom CSS unless Tailwind utilities are insufficient.
- Use responsive prefixes (`sm:`, `md:`, `lg:`) for mobile-first responsive design.
- Maintain consistent spacing and color usage across components.

## Recharts

- Wrap charts in `ResponsiveContainer` for fluid sizing.
- Provide accessible alternatives (e.g., data tables in `<details>` elements) for screen reader users.
- Use `ReferenceArea` to visualize threshold/healthy-range bands.

## Testing

- Name tests descriptively: `MethodOrComponent_Scenario_ExpectedResult`.
- Test behavior, not implementation details.
- Use xUnit for .NET tests; use Vitest with React Testing Library for frontend tests.
- Prefer integration tests with `WebApplicationFactory` for API endpoint testing.
- Query DOM elements by role or label (accessible queries) rather than by class name or test ID.
- Mock external dependencies (API calls, timers) — never hit real services in unit tests.

## Accessibility

- Use semantic HTML elements (`nav`, `main`, `table`, `button`, `label`).
- Associate form inputs with `<label>` elements via `htmlFor`/`id`.
- Use ARIA attributes (`role`, `aria-label`, `aria-invalid`, `aria-describedby`) where semantic HTML alone is insufficient.
- Ensure all interactive elements are keyboard-navigable.
- Provide `role="alert"` for error messages and `role="status"` for success messages.
