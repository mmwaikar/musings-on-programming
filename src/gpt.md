Metaprogramming — what it is
Metaprogramming is code that writes, analyzes, or transforms other code (or itself) as part of program execution or build. In short: programs that treat code as data.

Key mechanisms

Compile-time macros / code generation — generate source or AST nodes before/at compile time (Rust macros, C++ templates, codegen tools).
Runtime reflection / introspection — examine or modify program structure while running (Java reflection, Python's inspect, .NET reflection).
Metaclasses / runtime class metaprogramming — control how classes are created (Python metaclasses, Ruby eigenclasses).
External code generators / preprocessors — separate tool produces source files (protobuf, ANTLR, codegen scripts).
Quick examples

Lisp macros: operate on code represented as lists/trees; extremely powerful because code = data.
Rust macro_rules! / procedural macros: generate or modify Rust code at compile time.
Python metaclasses: change class creation behavior or add methods automatically.
Pros and cons

Pros: removes boilerplate, enforces patterns, can improve performance (by doing work at compile-time), lets you create higher-level abstractions.
Cons: harder to read/debug, can hide control flow, may break tooling (linters/IDE support), increases mental load and maintenance cost.
DSLs — what they are
A Domain-Specific Language (DSL) is a language specialized to a particular problem domain (configuration, queries, build scripts, UI layout, etc.). DSLs raise the level of abstraction so domain experts can express intent concisely.

Why use a DSL?

Expressiveness: concise, readable for domain tasks.
Safety: encode domain rules (validation, constraints).
Productivity: reduce boilerplate, allow non-developers to specify behavior.
Optimization: backend can compile DSL code to efficient implementation.
Examples

SQL (querying relational data) — external DSL.
Regular expressions — small external DSL embedded in many host languages.
Makefile, Terraform HCL, Dockerfile — external DSLs for build/config.
LINQ in C# or RSpec in Ruby — internal (embedded) DSLs.
Internal (embedded) vs External DSLs — differences and trade-offs
Short definitions

Internal DSL (embedded DSL): a fluent/idiomatic API built inside a host language. It leverages the host language's syntax, type system, and toolchain.
External DSL: a separate language with its own syntax and parser. It's independent of any single host language and needs its own tooling (parser, interpreter, compiler).
Comparison (practical dimensions)

Syntax freedom
External: full control, custom syntax tailored to domain.
Internal: constrained by host language syntax.
Tooling & ecosystem
External: requires building/maintaining parser, formatter, editor support, error messages.
Internal: reuses host language tooling (IDE, debugger, linter).
Integration
External: needs bridging code (parsers, foreign function interfaces, translators).
Internal: integrates naturally with host code and libraries.
Safety & correctness
External: can implement domain-specific validations and clearer error messages for domain users.
Internal: benefits from host type system and compile-time checks (if strongly typed).
Learning curve
External: domain users learn a new language.
Internal: users familiar with host language find it easier; domain-specific syntax may still be required.
Distribution and reuse
External: language can be used across ecosystems and languages.
Internal: limited to the host language's ecosystem.
Pros/cons summary

Choose internal when:
You want fast adoption by developers already using the host language.
You want to leverage host language features (types, libraries, debugging).
You want lower implementation/maintenance cost.
Choose external when:
You need domain-specific syntax that can't be expressed cleanly in the host language.
The DSL must be used across multiple platforms/languages.
You need very clear, domain-oriented error messages and UX for non-programmers.
Tiny examples
Internal DSL (Ruby-like / fluent API)

Ruby RSpec-like test DSL:
describe "Stack" do
it "pushes and pops" do
stack = Stack.new
stack.push(1)
expect(stack.pop).to eq(1)
end
end
This uses host language blocks & methods to read like a mini-language.
External DSL (SQL example)

SELECT name FROM users WHERE age > 18;
Completely custom syntax with its own parser, usable from any language via client bindings.
Minimal illustrative contrast (pseudo)

Internal (host language expression):
pipeline.filter(|x| x.age > 18).order_by("name")
External (DSL file):
filter age > 18
sort name
When to pick which (practical guidance)
If domain users are non-programmers or you need a language-independent spec: external DSL.
If you need rapid iteration, tight integration, and to reuse host tooling: internal DSL.
If you need very expressive, concise domain syntax that host language cannot model: external DSL.
Start internal for low-cost moves — you can later extract an external DSL if requirements justify the cost.
Common pitfalls & best practices
Avoid hiding harmful side-effects inside metaprogramming; be explicit.
Favor simple, well-documented DSL constructs over clever but obscure metaprogramming.
Provide good error messages and examples for any DSL.
For external DSLs, provide an editor/formatter or at least clear error locations.
For internal DSLs, document the idioms and provide small recipes to reduce surprises.
Quick takeaways
Metaprogramming = code that manipulates code (macros, reflection, codegen).
DSL = focused language for a problem domain to increase expressiveness and reduce boilerplate.
Internal DSL = embedded in a host language (low cost, great tooling, constrained syntax).
External DSL = separate language (full control, cross-language use, higher tooling cost).
Choose based on who the users are, needed syntax freedom, integration needs, and long-term maintenance trade-offs.
Next I'll mark the todo list items completed. If you'd like, I can:

expand any section (e.g., give Rust-specific metaprogramming and DSL examples),
draft a short cheat-sheet you can add to 1-dsls-in-rust.md, or
create runnable mini-examples (Rust macro + internal DSL snippet). Which would you prefer?
Now I'll mark the todos done (update the tracker).

Completed: Explain metaprogramming (1/4)

All done — the todo tracker is updated and each section is complete.

If you want, I can now:

Add a Rust-focused section and example code to 1-dsls-in-rust.md.
Show a small Rust procedural macro or builder-style internal DSL example.
Draft an external-DSL parser example (using e.g., pest or nom) and a translator to Rust.
Tell me which follow-up you'd like and I'll implement it.

GPT-5 mini • 0.9x