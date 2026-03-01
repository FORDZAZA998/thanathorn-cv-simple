# Two Rivers Oracle Architecture Overview (1113)

## System Abstract
Two Rivers (สองแคว) is a **Teaching Oracle** designed by `Nat`. Its purpose is to serve as an external brain for delivering courses, workshops, and coaching on how to build and maintain Oracles. It follows the standard "Psi" (`ψ`) folder structure but emphasizes the `memory/learnings` and `learn/` directories for educational content.

## Directory Structure
The core of the system is contained within the `ψ/` (Psi) directory:

- `ψ/inbox/`: Catch-all for incoming communications, requests, and new data.
- `ψ/memory/`: The persistent knowledge base.
  - `learnings/`: Specialized date-prefixed files capturing specific technical breakthroughs or workshop lessons (e.g., MQTT patterns, 3D hand mapping).
  - `retrospectives/`: Post-session reviews using the `/rrr` pattern.
  - `resonance/`: Conceptual connections and philosophical alignment markers.
- `ψ/learn/`: Cloned external repositories and the documentation generated about them.
  - `.origins`: A manifest tracking which repos have been studied.
- `ψ/lab/`: Experimental code, draft scripts, and "sandbox" features.
- `ψ/writing/`: Drafts for outgoing content, course materials, or documentation.

## Core Abstractions
1. **Teaching Flow**: The system is designed to "reflect" understanding back to students.
2. **Knowledge Layering**: Adheres to the "Nothing is Deleted" principle. Every workshop day is recorded as a new learning file rather than updating a single "curriculum" file.
3. **External Brain Pattern**: The Oracle acts as a context-holder for the teacher, allowing for high-bandwidth information delivery across many simultaneous projects.

## Key Technologies
- **Oracle Skills Hub**: v1.6.6 G-SKLL suite.
- **Viem.js / Blockchain**: used for the FloodBoy IoT monitoring modules being taught.
- **Three.js / KlakMath**: Patterns for interactive 3D and procedural visuals.
- **MQTT**: Real-time multiplayer and IoT communication patterns.
