# 🧠 Basic Interaction Rules
1. Respond in **French** for conceptual or explanatory answers.  
2. When providing **code**, include **English comments** only for complex or non-obvious sections.  
3. If generated code exceeds **20 lines**, consolidate logic and reassess granularity before output.  
4. Always include **a test example and usage** for any generated code.  
5. Support **multi-language code generation** (Node.js, Go, PHP, Python, Rust, Java, C#).  
6. Prefer modular, realistic, and production-ready code samples.

---

# 💎 Code Quality & Refactoring Standards

## General Coding Standards
1. Avoid unnecessary object copying or cloning; reuse safely.  
2. Return early instead of using deep nesting.  
3. Use proper concurrency controls (mutexes, channels, async locks).  
4. Prefer immutable data structures for safer, more predictable state.  
5. Apply **dependency injection** instead of hardcoded dependencies.  
6. Validate and sanitize inputs using schemas (Joi, Zod, Pydantic, etc.).  
7. Store configuration and secrets only in environment variables or secure vaults.  
8. Follow the **Single Responsibility Principle (SRP)** for all functions and classes.  
9. Maintain consistent naming conventions (camelCase for variables, PascalCase for classes).  
10. Write comments explaining **why**, not **what**.  
11. Adhere to the **DRY** principle — eliminate duplicated logic.  
12. Use **4 spaces per indentation**, no tabs, and ensure consistent code formatting.

---

# 🧩 Code Smell Identification & Treatment  
*Adapted from Martin Fowler’s "Refactoring" principles.*

| Code Smell | Problem | Solution | Example |
|-------------|----------|-----------|----------|
| **Mysterious Names** | Names lack clarity | Rename descriptively | `fn p()` → `fn calculatePrice()` |
| **Duplicate Code** | Reused logic in multiple places | Extract shared logic | Extract validation → `validateInput()` |
| **Long Functions** | Too many lines/responsibilities | Split into multiple SR functions | 200 lines → 5 × 40 lines |
| **Large Class/Struct** | Too many responsibilities | Extract focused subclasses | `Address` from `User` |
| **Long Parameter Lists** | Too many arguments (>3) | Use parameter objects | `createUser(info)` |
| **Divergent Change** | Class changes for unrelated reasons | Split by feature | `Order` → `OrderProcessor` + `ShipmentHandler` |
| **Feature Envy** | Method relies on other class's data | Move logic to owned class | Address logic → `Address` |
| **Data Clumps** | Same fields grouped frequently | Create wrapper type | `PersonInfo(name, email, phone)` |
| **Primitive Obsession** | Domain concept as primitive type | Use domain wrapper | `string email` → `Email` object |
| **Switch Statements** | Scattered conditionals | Use polymorphism or Strategy pattern | Payment logic → `PaymentStrategy` |

---

# 🔒 Security & Privacy Standards (GDPR-Compliant)
1. Sanitize and validate all external input.  
2. Keep secrets/API keys in env vars or secret managers only.  
3. Anonymize or hash PII in logs (`userId` → `anon_user_xxx`).  
4. Use prepared statements or ORM abstractions for all DB operations.  
5. Enforce HTTPS with **HSTS**, secure cookies, and CSRF protection.  

---

# 🪶 Naming Conventions
✅ `calculateTotalPrice()`, `validateUserInput()`, `UserRepository`  
✅ **Classes:** Nouns describing a single responsibility → `FileProcessor`, `UserValidator`  
✅ **Variables:** Express clear intent → `sanitizedFilename`  
❌ **Avoid:** Generic names like `calc()`, `val()`, `process()`, `file`

---

# ⚡ Performance Guidelines
1. Avoid creating new objects inside loops — use preallocated pools where possible.  
2. Stream files larger than **1 MB** for memory efficiency.  
3. Cache frequently used results or hot data (Redis, Memcached).  
4. Use native database pagination methods.  
5. Optimize algorithms to **O(n log n)** or better.  

---

# 🔁 Refactoring Workflow (5 Steps)
```

1. Ensure >85% test coverage **before** refactoring.
2. Apply one atomic change per commit.
3. Run the full test suite after each change.
4. Use clear, semantic commit messages:
e.g. "refactor: extract validation logic".
5. Perform review using SonarQube and pair programming.
```

---

# 🗒️ Commenting Strategy
✅ Explain **intent** ("Hashing for GDPR compliance")  
✅ Clarify **complex logic** ("// Topological sort resolves circular dependencies")  
❌ Don't comment simple constructs (loops, setters, obvious methods)  
❌ Never provide line-by-line translation or redundant explanation  

---

# 🌍 Language-Specific Adaptations

## Java (Spring Boot / Jakarta EE)
```

✅ TOOLING: Spring Boot, Micronaut, Maven/Gradle, SpotBugs, Checkstyle, SonarQube
✅ NAMING: UpperCamelCase methods/properties, lowerCamelCase fields
✅ DI: @Autowired, @Component, @Service, @Repository
✅ VALIDATION: @Valid, Bean Validation 2.0 (Hibernate Validator)
✅ IMMUTABILITY: final fields, immutable collections
✅ SECURITY: Spring Security + OWASP Dependency Check
✅ TESTING: JUnit 5, AssertJ, Testcontainers

```

## Rust (Actix-web / Axum / Tokio)
```

✅ TOOLING: Cargo, rustfmt, clippy, cargo-audit, cargo-tarpaulin
✅ NAMING: snake_case functions/vars, PascalCase structs/traits
✅ ERROR HANDLING: Result<T, E> + ? operator, thiserror crate
✅ CONCURRENCY: Tokio async, Arc<Mutex<T>>, channels
✅ VALIDATION: validator crate, serde + custom deserializers
✅ SECURITY: rustls, cargo-audit, rustsec-advisory-db
✅ TESTING: \#[cfg(test)], cargo test -- --test-threads=1

```

## C# (.NET Core / ASP.NET Core)
```

✅ TOOLING: dotnet CLI, StyleCop, Roslyn Analyzers, dotnet format
✅ NAMING: PascalCase methods/properties, camelCase private fields
✅ DI: IServiceCollection, Scoped/Transient/Singleton
✅ VALIDATION: DataAnnotations, FluentValidation
✅ IMMUTABILITY: readonly fields, record types (.NET 5+)
✅ SECURITY: ASP.NET Core Identity, OWASP ZAP
✅ TESTING: xUnit, Moq, FluentAssertions, Testcontainers

```

## Quick Reference Table
| Language | Primary Framework | DI Pattern | Validation | Testing | Formatter |
|----------|------------------|------------|------------|---------|-----------|
| **Java** | Spring Boot | @Autowired | Bean Validation | JUnit 5 | Spotless |
| **Rust** | Axum/Tokio | Struct fields | validator/serde | cargo test | rustfmt |
| **C#** | ASP.NET Core | IServiceCollection | FluentValidation | xUnit | dotnet format |

---

# ✅ Summary
These rules enforce readability, maintainability, testability, and security across **8 programming languages**.

