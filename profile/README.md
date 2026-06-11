<p align="center">
  <img src="logo.svg" alt="cronn" width="250"/>
</p>

<p align="center">
  <strong>wir entwickeln software_</strong>
</p>

<p align="center">
  <a href="https://www.cronn.de">Website</a> ·
  <a href="https://blog.cronn.de">Tech Blog</a> ·
  <a href="https://www.linkedin.com/company/cronn-gmbh">LinkedIn</a>
</p>

---

We're a software development company based in Bonn, Hamburg, and Białystok (Poland), with 150+ people working on custom software for clients across the public sector, telecommunications, media, healthcare, and beyond.

## How we work

### 🔄 Agile

We develop iteratively. Short cycles, continuous feedback, and honest communication with our clients keep us aligned with what actually matters. We don't disappear for months and surface with a finished product. We build incrementally and adapt.

### 🧪 Test-driven

Tests are not an afterthought. Writing tests before or alongside code shapes better design, documents intent, and gives us the confidence to refactor, upgrade, and ship. We invest in tests that catch real problems, not just tests that satisfy a coverage metric.

### 🚀 Continuous

CI/CD is the default. Code that isn't integrated is code that's accumulating risk. We run pipelines on every commit, catch issues early, and deploy frequently. Continuous delivery isn't just a pipeline configuration. It's a discipline that keeps integration costs low and feedback loops short.

### ✨ Clean Code

Code is read far more often than it is written. We take naming, structure, and simplicity seriously. Not as an aesthetic preference, but because messy code has real costs: slower onboarding, harder debugging, higher risk when changing things. We invest in quality from the start so we don't pay for it later.

---

## How we build software

### ☕ Backend

Our backend work is Java-first. We build on Spring Boot and lean heavily on the ecosystem around it: Hibernate/JPA, Liquibase, Spring Security, and Gradle. We like the language's stability and the maturity of its tooling, and we invest in keeping our Java up to date rather than staying on old LTS versions.

### 🌐 Frontend

On the frontend we work with React and TypeScript. We care about accessible, well-tested UIs and use Figma for design handoff. The frontend is a first-class citizen, not an afterthought.

### 🧪 Testing

We're test-driven and integration-heavy. We don't just write unit tests for the sake of coverage. We invest in tests that actually catch real problems. That means testing at the right level: integrative tests that verify real behavior across layers, not mocks all the way down.

Our testing toolset:

- **JUnit 5** for unit and integration tests
- **Playwright** for end-to-end tests
- **Cucumber** for BDD-style acceptance tests

#### Validation Files / File Snapshots

One pattern we use consistently is asserting test output against files checked into the repository. The expected output lives next to the test code, so when the output changes, the diff is immediately visible in version control. Depending on the context this technique goes by different names: *golden files*, *snapshot testing*, *approval testing*, or *contract testing*. We've open-sourced our implementations for both the JVM and JavaScript ecosystems:

- **[validation-file-assertions](https://github.com/cronn/validation-file-assertions)**: file-based assertions for Java/JUnit 5
- **[file-snapshots](https://github.com/cronn/file-snapshots)**: snapshot testing for Playwright and Vitest

#### Determinism

For validation files to work reliably, test output has to be deterministic. Same input, same output, every time, in the same order. This sounds obvious, but in practice it requires deliberate choices.

A common counterargument is: *"the order doesn't matter for correctness, so a `HashSet` is fine."* We disagree with the premise. Order-agnostic data structures behave differently between runs, between JVM versions, or between environments: not just in their output, but in iteration order, serialization, and anything downstream of that. That makes test assertions brittle, diffs noisy, and bugs harder to reproduce.

Our position is that deterministic behavior is valuable in production too, not just in tests. Predictable behavior is easier to debug, easier to audit, and easier to reason about. If you know what the software will do given a certain input, you can build on top of it with confidence. So unless there's a specific reason not to, we default to ordered collections. We use `LinkedHashSet` instead of `HashSet`, `LinkedHashMap` instead of `HashMap`, and so on. Our [commons-lang](https://github.com/cronn/commons-lang) library includes utilities like `StreamUtil.toLinkedHashSet()` to make this the path of least resistance.

---

## 📦 Open Source

We publish libraries and utilities we've built and found useful.

**Backend (Java)**

| Project                                                                                         | Description                                         |
|-------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| [commons-lang](https://github.com/cronn/commons-lang)                                           | Java utilities filling gaps in the standard library |
| [reflection-util](https://github.com/cronn/reflection-util)                                     | Utilities for type-safe Java reflection             |
| [liquibase-postgres-enum-extension](https://github.com/cronn/liquibase-postgres-enum-extension) | Liquibase support for native PostgreSQL enums       |

**Backend / Testing (JUnit)**

| Project                                                                                 | Description                                |
|-----------------------------------------------------------------------------------------|--------------------------------------------|
| [validation-file-assertions](https://github.com/cronn/validation-file-assertions)       | File-based assertions for Java/JUnit 5     |
| [test-utils](https://github.com/cronn/test-utils)                                       | JUnit 5 utilities for common test patterns |
| [liquibase-changelog-generator](https://github.com/cronn/liquibase-changelog-generator) | Liquibase changelog generator              |
| [postgres-snapshot-util](https://github.com/cronn/postgres-snapshot-util)               | PostgreSQL snapshot utilities for testing  |

**Frontend**

| Project                                                   | Description                                |
|-----------------------------------------------------------|--------------------------------------------|
| [file-snapshots](https://github.com/cronn/file-snapshots) | Snapshot testing for Playwright and Vitest |

---

## ✍️ Tech Blog

We write about what we're learning and building: [blog.cronn.de](https://blog.cronn.de)

Topics span the Java ecosystem, frontend development, testing, infrastructure & DevOps, databases, and AI/ML.

---

## 💼 Work with us

We're always looking for developers who care about their craft.
→ [cronn.de/jobs/](https://www.cronn.de/jobs/)
