# Agentic Coding Demo

A collection of real-world application requirements and prompt files designed to showcase **GitHub Copilot's agentic coding capabilities** — autonomously planning, scaffolding, implementing, testing, and running complete applications from a set of requirements.

## What This Repo Is

This repository contains **requirements documents** and **Copilot prompt files** that you can point GitHub Copilot at to have it build entire applications end-to-end with minimal human intervention. The goal is to demonstrate how agentic AI can go from a specification to a working, tested application.

Each example includes:

- A **requirements document** describing the application to be built (user stories, acceptance criteria, data models, etc.).
- A **prompt file** (`.github/prompts/`) that instructs Copilot on architecture, project structure, technology choices, and the step-by-step process to follow.

## Examples

| Example | Requirements | Prompt | Description |
|---------|-------------|--------|-------------|
| Health Metrics Dashboard | [requirements/health-metrics-dashboard.md](requirements/health-metrics-dashboard.md) | [.github/prompts/build-health-dashboard.prompt.md](.github/prompts/build-health-dashboard.prompt.md) | A full-stack health vitals tracker with React + .NET Aspire + SQL Server |

*More examples coming soon.*

## How to Use

1. **Open this repo in VS Code** with the [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) extension installed.
2. **Open the prompt file** for the example you want to build (e.g., `.github/prompts/build-health-dashboard.prompt.md`).
3. **Run the prompt** using Copilot's agentic mode and watch it plan, scaffold, implement, test, and run the application.

## Repo Structure

```
├── .github/
│   └── prompts/              # Copilot prompt files for each example
├── requirements/             # Application requirements documents
└── README.md
```

## Contributing

Have an interesting set of requirements that would make a good agentic coding demo? Contributions are welcome — add a requirements doc and a matching prompt file.

## License

This project is provided for demonstration purposes.
