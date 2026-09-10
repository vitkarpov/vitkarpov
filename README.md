# Hi, I'm Viktor 👋

I'm a software engineer who's fond of designing programs and providing convincing evidence that they compute their function correctly. I care about structure, predictability, and systems you can reason about — not just code that happens to work.

## 🧭 What I'm building

**[Relational Formula Engine](https://github.com/vitkarpov/relational-formula-engine)** — an open-source formula engine for applications where users define their own objects, attributes, and relations at runtime. The machinery underneath a CRM's formula fields, a relational spreadsheet, or a no-code database — as a library you can embed. Inspired by [Attio's write-up on formula attributes](https://attio.com/engineering/blog/how-we-built-formula-attributes), but it's an engine, not a clone.

### Why I built it

Every product with user-defined data eventually grows formulas, and the hard part is never `Amount * 0.2`. It's that `Deal.Weighted = Amount * Company.Discount` reaches *across a relation*. Change one company's discount and you have to recompute exactly the deals pointing at that company — not every deal in the table, and not nothing. That's a compiler problem and a dependency-graph problem wearing a spreadsheet costume.

Most implementations hard-code it: the schema lives in TypeScript, the checker is a pile of per-function `if`s, the parser dies on the first syntax error, and invalidation is "re-evaluate the object." I wanted the version where none of that is left to interpretation.

So: **schema is data**, loaded from a repository as an immutable snapshot rather than compiled into the app. **References resolve to stable IDs**, so renaming an attribute can't silently change what a saved formula means. **Diagnostics are data** — the lexer, parser, and checker all return span-aware structured errors instead of throwing, which is what makes editors, APIs, and LLM-generated formulas possible. And null handling, coercion, and division by zero have written-down semantics that produce typed values, not exceptions.

### How it's built

- **Language**: hand-written lexer + recursive-descent parser → AST, with a printer and round-trip tests
- **Types**: functions declare their parameters, generics, coercions, and return type in a registry; the checker consumes declarations instead of scattering per-function validation
- **Dependencies**: an edge isn't just an attribute ID — it carries the relation path needed to map a changed source record back to the formula records it affects
- **Recompute**: one frontier-based engine walking the graph in topological order, shared by value writes, formula edits, and bulk evaluation
- **Storage**: SQLite reference adapter behind `SchemaRepository` / `ValueStore` interfaces, plus a pure in-memory adapter — the compiler knows nothing about SQL
- **Surfaces**: TypeScript library (Node + a browser-safe export with no native deps), a reference CLI with `--json` for agents, a CodeMirror playground, and an example MCP server

The design philosophy in one line: **schema is data, diagnostics are data, and invalidation follows relations.**

## 🛠️ Also built

**[System Design Interview Simulator](https://systemdesigntrainer.com)** — practice real system design interviews under pressure, before the real one. Engineers fail these interviews not because they lack the knowledge, but because they can't perform it under the format.

Built on the same instinct: interview state lives in the backend, rules track signals, and a Bull-queue scheduler enforces the clock — phases advance whether you're ready or not. NestJS + React/Vite + PostgreSQL/Drizzle, with a stateless LLM as the interviewer persona and all context supplied server-side. **A rigid interview flow with simple heuristics beats a smart AI with no structure.**

## 💼 Currently

Engineering at **HubSpot**, and building on the side.

## 🧠 I like

Designing programs I can prove correct · compilers, type systems, and incremental computation · interviews & competitive programming · turning fuzzy problems into systems with clear, enforceable rules.
