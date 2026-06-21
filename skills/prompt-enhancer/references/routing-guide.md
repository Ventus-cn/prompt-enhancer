# Routing Guide

Use this guide to classify the user's request before rewriting it.

## Categories

### 1. Writing and Expression

Choose this when the user wants copy, rewriting, polishing, messaging, narrative, speech, post, caption, or explanation-quality improvements.

Focus the rewritten prompt on:

- audience
- purpose of the writing
- length
- tone
- required structure

Example:

- Raw request: `Help me polish this self-introduction.`
- Route: writing and expression

### 2. Analysis and Summarization

Choose this when the user wants explanation, comparison, breakdown, summary, synthesis, extraction of key points, or reasoning over content.

Focus the rewritten prompt on:

- source material or subject
- analytical lens
- depth
- output structure
- whether conclusions or recommendations are needed

Example:

- Raw request: `Help me analyze the key points in these meeting notes.`
- Route: analysis and summarization

### 3. Planning and Strategy

Choose this when the user wants a plan, roadmap, solution path, proposal, campaign idea, execution checklist, or decision support.

Focus the rewritten prompt on:

- target outcome
- time horizon
- priorities
- constraints
- deliverable format

Example:

- Raw request: `Help me create a launch plan for a new product.`
- Route: planning and strategy

### 4. Coding Help

Choose this when the user wants code, debugging, architecture help, refactoring, API usage, or technical implementation support.

Focus the rewritten prompt on:

- language or stack
- current problem
- constraints or environment
- desired result
- whether explanation, code, or both are needed

Example:

- Raw request: `Help me fix this Python error.`
- Route: coding help

## Fallback Rule

If the request spans multiple categories or is too vague to classify confidently, use the general template first and keep the answer flexible.

## Visibility Rule

Do not show the routed category or the rewritten internal prompt unless the user explicitly asks for that information.
