# Copilot Instructions — Java Projects

These instructions apply to all AI-generated code, refactors, and suggestions in this repository.

The goals are:

- Maintainability and readability
- SOLID design principles
- Testability
- Production-grade Java practices
- Clear documentation and naming
- Minimal technical debt

---

## 1. General Coding Standards

- Target **Java 17+** unless otherwise specified.
- Follow standard Java conventions:
  - `UpperCamelCase` for classes
  - `lowerCamelCase` for methods and variables
  - `UPPER_SNAKE_CASE` for constants
- Keep methods small and focused (generally < 30 lines).
- Prefer immutability where possible.
- Avoid premature optimization.
- Avoid static state unless truly necessary.
- Prefer composition over inheritance.
- Do not introduce unused code or imports.

---

## 2. SOLID Principles

### Single Responsibility Principle (SRP)
- Each class should have **one reason to change**.
- Separate business logic, persistence, infrastructure, and API layers.
- Avoid “god classes.”

### Open / Closed Principle (OCP)
- Extend behavior through interfaces or abstract classes.
- Avoid modifying existing logic when adding features.
- Use polymorphism instead of `if/else` chains where appropriate.

### Liskov Substitution Principle (LSP)
- Subtypes must be usable wherever their base type is expected.
- Do not weaken preconditions or strengthen postconditions.
- Avoid throwing new unchecked exceptions in subclasses.

### Interface Segregation Principle (ISP)
- Prefer multiple small, focused interfaces over large ones.
- Clients should not depend on methods they don’t use.

### Dependency Inversion Principle (DIP)
- Depend on abstractions, not implementations.
- Inject dependencies through constructors.
- Avoid creating concrete dependencies inside business classes.

---

## 3. Architecture & Layering

Prefer clean layered architecture:

- `controller` / `api` — HTTP or UI interfaces
- `service` — business logic
- `domain` — core models and rules
- `repository` — persistence
- `infrastructure` — integrations, frameworks, adapters

Rules:

- Controllers depend on services.
- Services depend on domain + interfaces.
- Repositories implement interfaces defined in the domain or service layer.
- No circular dependencies.

---

## 4. Dependency Injection

- Prefer constructor injection.
- Avoid field injection.
- Avoid static service locators.
- In Spring projects:
  - Use `@Service`, `@Repository`, `@Component` appropriately.
  - Avoid placing logic in controllers.
  - Keep configuration in `@Configuration` classes.

---

## 5. Error Handling

- Use exceptions for exceptional cases, not flow control.
- Prefer custom domain exceptions.
- Do not swallow exceptions.
- Log at appropriate levels.
- Wrap low-level exceptions only when adding context.

---

## 6. Logging

- Use SLF4J.
- Do not use `System.out.println`.
- Log meaningful messages.
- Do not log sensitive data.
- Prefer structured logging when possible.

---

## 7. Testing Standards

- Use **JUnit 5**.
- Use Mockito or similar for mocking.
- Follow Arrange-Act-Assert.
- Test behavior, not implementation details.
- Prefer constructor injection to simplify testing.
- Name tests clearly:
  - `methodName_condition_expectedResult`.

---

## 8. Documentation

- Public classes and methods should have Javadoc.
- Explain *why*, not just *what*.
- Add comments only where the code is not self-explanatory.
- Keep README updated for architecture decisions.

---

## 9. Streams, Optional & Modern Java

- Prefer streams for transformations, not complex logic.
- Avoid deeply nested streams.
- Do not abuse `Optional` for fields.
- Use records for immutable data carriers where appropriate.
- Prefer `var` only when the type is obvious.

---

## 10. Concurrency

- Prefer high-level concurrency utilities from `java.util.concurrent`.
- Avoid manual thread management unless required.
- Document thread-safety guarantees.
- Use immutable objects for shared state.

---

## 11. Security & Robustness

- Validate all inputs.
- Avoid exposing internal models directly through APIs.
- Never hardcode secrets.
- Follow least-privilege principles.
- Use DTOs at boundaries.

---

## 12. Performance & Resources

- Close resources using try-with-resources.
- Avoid blocking calls on async threads.
- Cache only with justification.
- Avoid unnecessary object creation in hot paths.

---

## 13. Code Review Expectations for AI Output

Copilot should:

- Explain non-obvious design choices in comments.
- Prefer simple solutions over clever ones.
- Avoid framework lock-in unless requested.
- Not introduce new libraries without justification.
- Match existing project patterns.
- Ask for clarification when requirements are ambiguous.

---

## 14. Formatting & Style

- Follow the project’s formatter (Spotless/Checkstyle if present).
- Limit line length to ~120 characters.
- Keep imports organized.
- One top-level class per file.

---

## 15. What NOT to Do

- Do not generate overly complex abstractions.
- Do not mix layers.
- Do not bypass validation.
- Do not use reflection unless required.
- Do not introduce breaking API changes without warning.

---

**Primary Objective:**  
Generate clean, maintainable, testable Java code that strictly follows SOLID principles and production-quality best practices.

