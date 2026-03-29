# Development Document Writing Guide

Read this guide when the user explicitly asks to update a development document and the feature is complex enough that the template alone may be too thin.

## Purpose

The development document should explain the current implementation clearly enough that another engineer can:

- find the entry point quickly
- follow the main call path
- understand module responsibilities
- identify important contracts and states
- know where to debug when something breaks

The document should describe what the code currently does, not what someone once planned for it to do.

## What Good Documentation Looks Like

A strong development document is:

- implementation-first rather than design-theory-first
- specific about files, classes, methods, and responsibilities
- honest about limitations and unfinished branches
- readable from high-level flow down to concrete call chains

It should help someone continue the work without reading the entire repository from scratch.

## Recommended Writing Order

When writing or updating the document, use this order:

1. Functional goal
2. Document purpose
3. Code layers and responsibilities
4. Core classes and key methods
5. Key objects, fields, and states
6. Full process flow
7. Method call chain when the document is feature-specific
8. Current progress when the document needs to show implementation status
9. Maintenance, risks, and follow-up
10. Summary

## Core Required Headings

Treat these headings as the default backbone:

- Functional goal
- Document purpose
- Code layers and responsibilities
- Core classes and responsibilities
- Key method notes
- Key objects, fields, and states
- Full process flow
- Current characteristics and limitations
- Edge cases and special notes
- Maintenance, risks, and follow-up
- Summary

For the maintenance section, keep these subsections:

- Maintenance and extension suggestions
- Current issues and optimization directions
- Exception and error handling
- Follow-up work
- Risks and notes

## Conditionally Required Headings

These headings are not required for every document, but they become required under the right conditions:

- Method call chain
  Required for feature-specific development documents; usually optional for whole-project overview documents.
- Current progress
  Add when the document must explicitly state completed scope, partially completed scope, unfinished scope, or existing validation status.

## Minimum Detail Level

For a non-trivial feature, the document should not stop at naming files.

It should explain:

- why that file matters
- how it participates in the flow
- what data it consumes and produces
- what assumptions it makes

## When To Be More Detailed

Increase detail when the feature includes any of these:

- multiple entry points
- async processing
- queues or jobs
- scheduled execution
- state transitions
- retries or fallbacks
- external integrations
- feature flags
- non-obvious branching logic
- partial completion or known technical debt

## What Must Usually Be Covered

A solid implementation document should usually answer:

- Where does the flow start?
- What is the happy path?
- If this is a feature document, what does the method or call chain look like?
- Which modules own orchestration, validation, persistence, transport, and side effects?
- Which data structures or states drive branch decisions?
- Which config or external dependencies materially affect behavior?
- Where are failures caught, retried, logged, surfaced, or degraded?
- What has been completed, and what is still missing?

## Common Documentation Failures

Avoid these patterns:

- listing files without responsibilities
- describing future architecture instead of current implementation
- copying method names without saying what they do
- hiding known problems
- omitting configuration and external dependencies
- omitting test gaps
- using vague phrases like "handles logic" or "processes data" without concrete detail

## Practical Writing Advice

- Start from the execution path, not the folder tree.
- Prefer concrete file names and method names over abstract labels.
- Separate confirmed behavior from assumptions.
- Be honest about temporary workarounds and fragile branches.
- Keep terminology consistent with the codebase and task documents.
- Keep maintenance guidance, current issues, error handling, unfinished work, and risks under one combined top-level section, but make each subsection concrete enough that another engineer can continue the work without guessing.

## Final Check

Before finishing the document, make sure a reader can answer:

- Where does the flow start?
- What is the happy path?
- If this is a feature document, is the method call chain clear enough to follow?
- What are the key side effects?
- What data or state drives decisions?
- What fails most often?
- What still needs to be built or improved?

If those answers are not visible from the document, add detail before treating it as complete.
