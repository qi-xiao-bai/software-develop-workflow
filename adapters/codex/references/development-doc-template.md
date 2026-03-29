# Development Document Template

Use this template only when the user explicitly asks to maintain the project development document.

This is a public template for explaining how the current implementation actually works.

## Mandatory Core Headings

These headings are the fixed backbone of the document and must remain:

```md
# XXX - Current Implementation Notes

## Functional Goal

## Current Progress

## Document Purpose

## Code Layers and Responsibilities

## Core Classes and Responsibilities

## Key Method Notes

## Key Objects, Fields, and States

## Full Process Flow

## Method Call Chain

## Current Characteristics and Limitations

## Edge Cases and Special Notes

## Maintenance and Extension Guidance

## Known Issues and Improvement Ideas

## Current Error Handling

## Pending Work

## Known Risks and Notes

## Summary
```

## What Each Core Heading Should Contain

### Functional Goal

Explain what problem the feature solves and what result it is expected to produce.

Keep this section focused on purpose rather than implementation detail.

### Current Progress

Describe the real current state.

This should make clear:

- what is already complete
- what is only partially complete
- what is still missing
- how much validation already exists

### Document Purpose

Explain what this document covers and what the reader should understand after reading it.

### Code Layers and Responsibilities

Describe the overall structure first.

If the implementation has recognizable layers such as entry, service, repository, domain, utility, or async layers, explain what each layer is responsible for and what it should not own.

### Core Classes and Responsibilities

List only the classes that truly matter for understanding the main implementation path.

For each one, explain:

- class name
- main responsibility
- main dependencies
- where it fits in the overall flow

### Key Method Notes

Document the important methods rather than every helper.

For each important method, try to include:

- input parameters
- return value
- purpose
- when it is called
- important side effects

### Key Objects, Fields, and States

Document the objects and state that drive behavior, such as:

- request objects
- response objects
- domain entities
- tables
- state fields
- enum values
- messages

Do not just name them. Explain why they matter.

### Full Process Flow

Describe the whole flow in plain language before dropping into method-level detail.

This section should help the reader understand the big picture first.

### Method Call Chain

This section is mandatory and should be detailed.

Each key step should ideally include:

- input parameters
- return value
- purpose

If the chain is long, start with a short overall summary first.

### Current Characteristics and Limitations

Be honest about the implementation as it exists today, for example:

- synchronous instead of asynchronous
- optimized for readability instead of throughput
- hard-coded assumptions
- temporary compatibility logic
- high coupling in certain areas

### Edge Cases and Special Notes

Document special branches, business exceptions, non-default paths, and any behavior that a future maintainer could easily miss.

### Maintenance and Extension Guidance

Explain:

- where new logic should go
- what should not be changed casually
- which constraints must remain true
- where future maintainers are most likely to break things

### Known Issues and Improvement Ideas

Document the weaknesses already known today and the improvements worth making next.

Be concrete whenever possible.

### Current Error Handling

Explain:

- where exceptions are caught
- which errors are surfaced directly
- which errors are transformed into business responses
- which failures retry, degrade, or stop execution
- whether current logging is sufficient

### Pending Work

Use this section for work that is explicitly known to be unfinished.

This is different from known issues:

- known issues are current weaknesses
- pending work is unfinished implementation

### Known Risks and Notes

Document the main risks for future maintenance, such as:

- performance risks
- concurrency risks
- state transition risks
- unstable integrations
- strong configuration coupling
- temporary compatibility logic that is easy to remove incorrectly

### Summary

Close the document by restating:

- the current implementation state
- the main execution path
- the main risks
- the main maintenance cautions

## Extension Headings

The following headings are optional and should only be added when the feature actually needs them:

- Repository Entry Points
- Dependencies, Configuration, and External Integrations
- Validation and Test Status
- Troubleshooting Notes
- API or Message Contract Notes
- Additional State Transition Notes

These extension headings add clarity for complex features, but they do not replace the mandatory core structure.

## Method Call Chain Example

```md
## Method Call Chain

Overall chain summary:
The request enters through the entry layer, moves into the main service for orchestration, persists intermediate state, runs follow-up work, and finally returns the result.

Request enters the system
-> `ApiHandler.handle(request)`
   - Input: `request`
   - Output: `Response`
   - Purpose: Accept the incoming request and trigger the main flow
-> `TaskService.execute(command)`
   - Input: `command`
   - Output: `TaskResult`
   - Purpose: Execute the core process and aggregate results
-> `TaskService.buildContext(command)`
   - Input: `command`
   - Output: `Context`
   - Purpose: Build execution context and prerequisite data
-> `Repository.save(context.state)`
   - Input: `context.state`
   - Output: persisted result or no direct return
   - Purpose: Persist the current state
-> `Notifier.publish(context)`
   - Input: `context`
   - Output: no return or side-effect result
   - Purpose: Run notifications, async work, or post-processing
-> Return `Response`
   - Purpose: Return the final result to the caller
```
