# GitHub Copilot Prompts Collection

> Task-specific prompts for code generation, documentation, testing, and workflow automation with GitHub Copilot

This collection contains over 100 specialized prompts designed to enhance your GitHub Copilot experience across various domains, languages, and use cases. Each prompt is optimized for specific development tasks and can be triggered using `/` commands in GitHub Copilot Chat.

## Quick Start

1. Browse the prompts in this directory
2. Use a prompt by typing `#file:prompt-name.prompt.md` in GitHub Copilot Chat
3. Follow the prompt-specific workflow and instructions

## Cheatsheet

### Essential Workflow Prompts

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [conventional-commit](conventional-commit.prompt.md) | Generate standardized commit messages following Conventional Commits spec | Terminal |
| [git-flow-branch-creator](git-flow-branch-creator.prompt.md) | Analyze changes and create semantic Git Flow branches | Terminal |
| [create-readme](create-readme.prompt.md) | Generate comprehensive README files for projects | Agent |
| [review-and-refactor](review-and-refactor.prompt.md) | Code review and refactoring assistance | Codebase, Problems |

### Python Development

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [pytest-coverage](pytest-coverage.prompt.md) | Run pytest with coverage analysis and achieve 100% coverage | Agent |
| [python-mcp-server-generator](python-mcp-server-generator.prompt.md) | Generate Model Context Protocol servers in Python | Agent |
| [dataverse-python-quickstart](dataverse-python-quickstart.prompt.md) | Quick start guide for Dataverse with Python | - |
| [dataverse-python-production-code](dataverse-python-production-code.prompt.md) | Production-grade Dataverse Python patterns | - |
| [dataverse-python-advanced-patterns](dataverse-python-advanced-patterns.prompt.md) | Advanced Dataverse integration patterns | - |

### Database & SQL

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [sql-optimization](sql-optimization.prompt.md) | Universal SQL performance optimization and query tuning | Codebase, Problems |
| [sql-code-review](sql-code-review.prompt.md) | SQL code review and best practices | - |
| [postgresql-optimization](postgresql-optimization.prompt.md) | PostgreSQL-specific performance tuning | - |
| [postgresql-code-review](postgresql-code-review.prompt.md) | PostgreSQL code review | - |
| [cosmosdb-datamodeling](cosmosdb-datamodeling.prompt.md) | Azure Cosmos DB data modeling guidance | - |

### Documentation & Planning

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [documentation-writer](documentation-writer.prompt.md) | Generate comprehensive documentation | Agent |
| [create-architectural-decision-record](create-architectural-decision-record.prompt.md) | Create ADRs for architecture decisions | - |
| [create-specification](create-specification.prompt.md) | Generate detailed technical specifications | Agent |
| [create-implementation-plan](create-implementation-plan.prompt.md) | Create structured implementation plans | Agent |
| [create-technical-spike](create-technical-spike.prompt.md) | Plan and document technical spikes | - |
| [create-tldr-page](create-tldr-page.prompt.md) | Create concise TL;DR documentation pages | - |

### GitHub Workflows

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [create-github-action-workflow-specification](create-github-action-workflow-specification.prompt.md) | Design GitHub Actions workflows | - |
| [create-github-issue-feature-from-specification](create-github-issue-feature-from-specification.prompt.md) | Generate GitHub issues from specs | - |
| [create-github-pull-request-from-specification](create-github-pull-request-from-specification.prompt.md) | Create PRs from specifications | - |
| [my-issues](my-issues.prompt.md) | View and manage your GitHub issues | - |
| [my-pull-requests](my-pull-requests.prompt.md) | View and manage your pull requests | - |

### Testing

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [breakdown-test](breakdown-test.prompt.md) | Break down features into test cases | - |
| [csharp-mstest](csharp-mstest.prompt.md) | Generate MSTest unit tests for C# | - |
| [csharp-nunit](csharp-nunit.prompt.md) | Generate NUnit tests for C# | - |
| [csharp-xunit](csharp-xunit.prompt.md) | Generate xUnit tests for C# | - |
| [java-junit](java-junit.prompt.md) | Generate JUnit tests for Java | - |
| [javascript-typescript-jest](javascript-typescript-jest.prompt.md) | Generate Jest tests for JS/TS | - |
| [playwright-generate-test](playwright-generate-test.prompt.md) | Generate Playwright end-to-end tests | - |

### MCP Server Generators

Generate Model Context Protocol servers in various languages:

| Language | Prompt |
|----------|--------|
| Python | [python-mcp-server-generator](python-mcp-server-generator.prompt.md) |
| C# | [csharp-mcp-server-generator](csharp-mcp-server-generator.prompt.md) |
| TypeScript | [typescript-mcp-server-generator](typescript-mcp-server-generator.prompt.md) |
| Java | [java-mcp-server-generator](java-mcp-server-generator.prompt.md) |
| Go | [go-mcp-server-generator](go-mcp-server-generator.prompt.md) |
| Kotlin | [kotlin-mcp-server-generator](kotlin-mcp-server-generator.prompt.md) |
| Rust | [rust-mcp-server-generator](rust-mcp-server-generator.prompt.md) |
| Ruby | [ruby-mcp-server-generator](ruby-mcp-server-generator.prompt.md) |
| Swift | [swift-mcp-server-generator](swift-mcp-server-generator.prompt.md) |
| PHP | [php-mcp-server-generator](php-mcp-server-generator.prompt.md) |

### Cloud & Infrastructure

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [az-cost-optimize](az-cost-optimize.prompt.md) | Azure cost optimization recommendations | - |
| [azure-resource-health-diagnose](azure-resource-health-diagnose.prompt.md) | Diagnose Azure resource health issues | - |
| [containerize-aspnetcore](containerize-aspnetcore.prompt.md) | Containerize ASP.NET Core applications | - |
| [multi-stage-dockerfile](multi-stage-dockerfile.prompt.md) | Create optimized multi-stage Dockerfiles | - |
| [update-avm-modules-in-bicep](update-avm-modules-in-bicep.prompt.md) | Update Azure Verified Modules in Bicep | - |

### .NET Development

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [dotnet-best-practices](dotnet-best-practices.prompt.md) | Apply .NET best practices | - |
| [dotnet-design-pattern-review](dotnet-design-pattern-review.prompt.md) | Review and suggest design patterns | - |
| [dotnet-upgrade](dotnet-upgrade.prompt.md) | Upgrade .NET projects to newer versions | - |
| [csharp-async](csharp-async.prompt.md) | Async/await patterns in C# | - |
| [csharp-docs](csharp-docs.prompt.md) | Generate C# XML documentation | - |
| [ef-core](ef-core.prompt.md) | Entity Framework Core guidance | - |
| [aspnet-minimal-api-openapi](aspnet-minimal-api-openapi.prompt.md) | Create ASP.NET Minimal APIs with OpenAPI | - |

### Java & Spring Boot

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [create-spring-boot-java-project](create-spring-boot-java-project.prompt.md) | Scaffold Spring Boot Java projects | - |
| [create-spring-boot-kotlin-project](create-spring-boot-kotlin-project.prompt.md) | Scaffold Spring Boot Kotlin projects | - |
| [java-springboot](java-springboot.prompt.md) | Spring Boot development guidance | - |
| [java-docs](java-docs.prompt.md) | Generate Javadoc documentation | - |
| [java-refactoring-extract-method](java-refactoring-extract-method.prompt.md) | Extract method refactoring in Java | - |
| [java-add-graalvm-native-image-support](java-add-graalvm-native-image-support.prompt.md) | Add GraalVM native image support | - |

### Power Platform

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [power-apps-code-app-scaffold](power-apps-code-app-scaffold.prompt.md) | Scaffold Power Apps code applications | - |
| [power-bi-dax-optimization](power-bi-dax-optimization.prompt.md) | Optimize DAX queries in Power BI | - |
| [power-bi-model-design-review](power-bi-model-design-review.prompt.md) | Review Power BI data model design | - |
| [power-bi-performance-troubleshooting](power-bi-performance-troubleshooting.prompt.md) | Troubleshoot Power BI performance | - |
| [power-bi-report-design-consultation](power-bi-report-design-consultation.prompt.md) | Power BI report design consultation | - |
| [power-platform-mcp-connector-suite](power-platform-mcp-connector-suite.prompt.md) | Power Platform MCP connector suite | - |

### AI & Automation

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [declarative-agents](declarative-agents.prompt.md) | Create declarative AI agents | - |
| [mcp-copilot-studio-server-generator](mcp-copilot-studio-server-generator.prompt.md) | Generate Copilot Studio MCP servers | - |
| [ai-prompt-engineering-safety-review](ai-prompt-engineering-safety-review.prompt.md) | Review prompts for safety and bias | - |
| [prompt-builder](prompt-builder.prompt.md) | Build structured prompts | - |

### Productivity & Utilities

| Prompt | Use Case | Tools |
|--------|----------|-------|
| [tldr-prompt](tldr-prompt.prompt.md) | Create concise TL;DR summaries | - |
| [convert-plaintext-to-md](convert-plaintext-to-md.prompt.md) | Convert plain text to Markdown | - |
| [shuffle-json-data](shuffle-json-data.prompt.md) | Shuffle JSON data for testing | - |
| [editorconfig](editorconfig.prompt.md) | Generate .editorconfig files | - |
| [remember](remember.prompt.md) | Remember context across conversations | - |
| [memory-merger](memory-merger.prompt.md) | Merge and consolidate memory contexts | - |

### Blueprint Generators

Generate comprehensive blueprints for various aspects of your project:

| Prompt | Use Case |
|--------|----------|
| [architecture-blueprint-generator](architecture-blueprint-generator.prompt.md) | System architecture blueprints |
| [code-exemplars-blueprint-generator](code-exemplars-blueprint-generator.prompt.md) | Code example blueprints |
| [copilot-instructions-blueprint-generator](copilot-instructions-blueprint-generator.prompt.md) | GitHub Copilot instruction blueprints |
| [folder-structure-blueprint-generator](folder-structure-blueprint-generator.prompt.md) | Project folder structure blueprints |
| [readme-blueprint-generator](readme-blueprint-generator.prompt.md) | README file blueprints |
| [technology-stack-blueprint-generator](technology-stack-blueprint-generator.prompt.md) | Technology stack blueprints |
| [project-workflow-analysis-blueprint-generator](project-workflow-analysis-blueprint-generator.prompt.md) | Workflow analysis blueprints |

### Feature Breakdown

| Prompt | Use Case |
|--------|----------|
| [breakdown-epic-arch](breakdown-epic-arch.prompt.md) | Break down epics into architecture tasks |
| [breakdown-epic-pm](breakdown-epic-pm.prompt.md) | Break down epics from PM perspective |
| [breakdown-feature-implementation](breakdown-feature-implementation.prompt.md) | Break down features into implementation tasks |
| [breakdown-feature-prd](breakdown-feature-prd.prompt.md) | Break down features into PRD format |
| [breakdown-plan](breakdown-plan.prompt.md) | General feature breakdown planning |

### Playwright & Testing Automation

| Prompt | Use Case |
|--------|----------|
| [playwright-automation-fill-in-form](playwright-automation-fill-in-form.prompt.md) | Automate form filling with Playwright |
| [playwright-explore-website](playwright-explore-website.prompt.md) | Explore websites with Playwright |
| [playwright-generate-test](playwright-generate-test.prompt.md) | Generate Playwright tests |

### Additional Tools

| Prompt | Use Case |
|--------|----------|
| [add-educational-comments](add-educational-comments.prompt.md) | Add educational comments to code |
| [comment-code-generate-a-tutorial](comment-code-generate-a-tutorial.prompt.md) | Generate tutorials from code |
| [boost-prompt](boost-prompt.prompt.md) | Enhance and improve prompts |
| [finalize-agent-prompt](finalize-agent-prompt.prompt.md) | Finalize agent prompts |
| [first-ask](first-ask.prompt.md) | Initial project analysis |
| [repo-story-time](repo-story-time.prompt.md) | Generate repository narratives |
| [model-recommendation](model-recommendation.prompt.md) | Recommend appropriate AI models |
| [mkdocs-translations](mkdocs-translations.prompt.md) | Manage MkDocs translations |
| [next-intl-add-language](next-intl-add-language.prompt.md) | Add languages to Next.js intl |
| [update-markdown-file-index](update-markdown-file-index.prompt.md) | Update Markdown file indexes |
| [write-coding-standards-from-file](write-coding-standards-from-file.prompt.md) | Extract coding standards from files |

## Prompt Structure

All prompts follow a consistent structure with YAML frontmatter:

```yaml
---
agent: 'agent'  # or 'ask' for simpler prompts
description: 'Brief description of what the prompt does'
tools: ['tool1', 'tool2']  # Optional: Required Copilot tools
tested_with: 'Model information'  # Optional: Testing details
---
```

## Usage Tips

### Preferred Languages
According to workflow preferences, prioritize these languages:
1. Python
2. Bash
3. YAML
4. JSON
5. XML

PowerShell is not preferred unless explicitly requested.

### Security & Best Practices
- All prompts emphasize secure, idempotent infrastructure-as-code
- Environment variables for sensitive data
- Careful avoidance of matching public code too closely

### Response Format
- Prompts typically output complete files unless "snippet" is mentioned
- Comments placed on separate lines above referenced code
- New comments distinguished with an extra `#` or `/`

## Contributing

When adding new prompts:

1. Follow the naming convention: `lowercase-with-hyphens.prompt.md`
2. Include proper YAML frontmatter with `description` field
3. Specify `agent` field (`'agent'` or `'ask'`)
4. Add `tools` field if the prompt requires specific capabilities
5. Consider adding `tested_with` for model-specific optimizations

## Related Resources

- [Agents](../agents/) - Custom GitHub Copilot agent definitions
- [Instructions](../instructions/) - Coding standards applied to file patterns
- [Skills](../skills/) - Agent Skills with bundled resources
- [Collections](../collections/) - Curated resource collections

## Examples

### Example: Using conventional-commit

```bash
# In GitHub Copilot Chat
#file:conventional-commit.prompt.md

# Copilot will:
# 1. Run git status
# 2. Run git diff
# 3. Analyze changes
# 4. Generate conventional commit message
# 5. Execute git commit automatically
```

### Example: SQL Optimization

```bash
# Select SQL code in editor
# In GitHub Copilot Chat
#file:sql-optimization.prompt.md

# Copilot will analyze and optimize:
# - Query performance
# - Index strategies
# - Execution plans
# - Pagination patterns
```

### Example: Generate README

```bash
# In GitHub Copilot Chat
#file:create-readme.prompt.md

# Copilot will:
# 1. Review project structure
# 2. Analyze code and documentation
# 3. Generate comprehensive README
# 4. Follow GFM and best practices
```

---

**Total Prompts**: 110+ | **Last Updated**: January 2026
