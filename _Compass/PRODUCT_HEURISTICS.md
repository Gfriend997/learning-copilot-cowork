# Product Heuristics

Gary's product intuition and rules of thumb, especially for agentic AI.

## Agentic AI Rules

- An agent is only as good as its source of truth. If the data layer is messy, the agent outputs garbage
- Skills should do one thing well. Multi-purpose skills become unpredictable
- "Work IQ" reasoning improves when context is structured, not when more context is added
- The Graph is the brain. SharePoint and OneDrive structure IS the product architecture

## Context Fencing

- Every business entity needs its own SharePoint site or document library
- Cowork should never pull context from Business A when working on Business B
- Naming conventions are the cheapest, most effective form of context fencing
- Prefix folders and files with the business entity name when ambiguity is possible

## Building for Others

- If Gary cannot explain the setup in under 5 minutes, it is too complex
- Every workflow should have a "cold start" guide: what someone needs to do from zero
- Configuration should be documented alongside the thing being configured, not in a separate wiki
- Screenshots and examples beat explanations every time

## Anti-Patterns

- Do not build workflows that depend on Gary being in the loop for every step
- Do not create skills that require tribal knowledge to use
- Do not optimize for edge cases before the happy path works
- Do not assume the user has read other documentation. Each guide should stand alone
