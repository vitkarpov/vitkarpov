# Hi, I'm Viktor 👋

I'm a software engineer who's fond of designing programs and providing convincing evidence that they compute their function correctly. I care about structure, predictability, and systems you can reason about — not just code that happens to work.

## 🧭 What I'm building

I built **[System Design Interview Simulator](https://systemdesigntrainer.com)** — a tool that lets engineers practice real system design interviews under pressure, *before* the real one.

### Why I built it

I kept noticing the same thing in myself and in people around me: engineers fail system design interviews not because they lack the knowledge, but because they can't perform it under the format. You panic. You don't know what to say at minute 30. You skip requirements and jump straight to drawing boxes. And mock interviews often provide warm, unhelpful feedback.

I wanted something that behaves like the real thing — and that's hard. So I designed it the way I design everything: **flow over intelligence**. Instead of trusting an LLM to "be a good interviewer," the interview state lives in the backend, rules track signals, and a background scheduler enforces the clock. Phases advance whether you're ready or not. No manual advancing. No second chances. Just like the real room.

The result is a system that's predictable and debuggable — I can tell you *exactly* why you lost points and which phase you ran out of time in, because none of that is left to interpretation.

## 🏗️ How it's built

- **Backend**: NestJS — interview orchestrator, phase-transition scheduler (Bull queue that ticks every minute), prompt engine, rule-based signal tracking
- **Frontend**: React + Vite — chat-based interview UI, whiteboard, live timers
- **AI layer**: stateless LLM as the interviewer persona; all context comes from the backend
- **Data**: PostgreSQL + Drizzle ORM

The design philosophy in one line: **a rigid interview flow with simple heuristics beats a smart AI with no structure.**

## 💼 Currently

Engineering at **HubSpot**, and building on the side.

## 🧠 I like

Designing programs I can prove correct · interviews & competitive programming · turning fuzzy problems into systems with clear, enforceable rules.

## 📫 Find me

- 🌐 [systemdesigntrainer.com](https://systemdesigntrainer.com)
- 🐙 [github.com/vitkarpov](https://github.com/vitkarpov)
