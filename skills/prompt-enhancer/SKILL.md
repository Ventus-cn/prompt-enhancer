---
name: prompt-enhancer
description: Transform rough user input into a clearer, more structured prompt before answering. Use only when the user explicitly invokes $prompt-enhancer and wants their draft request upgraded into a higher-quality AI-ready prompt for general chat, writing, analysis, planning, or coding help, with the optimized prompt shown first and the execution or answer following after it. When the current session already has a more relevant skill for the user's real task, route to that skill automatically so the user does not need to invoke it manually.
---

# Prompt Enhancer

## Overview

Rewrite the user's raw request into a stronger prompt, show that optimized prompt to the user, and then continue from that rewritten prompt.

When another currently available skill is a clearer fit for the real task, use prompt enhancement as the front layer and then hand off execution to that skill.

Improve clarity, structure, constraints, and output shape without forcing the user to write a polished prompt themselves.

## Core Rules

Treat this as an explicit-invocation skill. Do not apply this workflow unless the user intentionally calls `$prompt-enhancer`.

Do not claim that the input box or send action was technically intercepted or modified. Perform the prompt upgrade inside the model workflow after the skill is invoked.

Default to showing the rewritten prompt first. Treat prompt display as part of the normal workflow, not a debug-only path.

Follow the user's language. If the user writes in Chinese, keep the rewritten prompt and response strategy in Chinese. If the user writes in English, keep them in English unless the user asks otherwise.

Preserve the user's intent. Improve the request without changing the real task, audience, or desired outcome.

Only route to skills that are explicitly available in the current session. Do not assume a skill can be used just because it exists on disk.

## Workflow

1. Read the user's raw request and identify:
   - goal
   - context
   - constraints
   - desired output
   - tone or style, if inferable
2. Classify the request into the closest task family:
   - writing and expression
   - analysis and summarization
   - planning and strategy
   - coding help
3. If no class is clearly dominant, fall back to the general enhancement template in `references/general-template.md`.
4. Rewrite the request into a structured prompt using the chosen template.
5. Check the current session's available skill list and decide whether another skill is a clearly better fit for the user's actual task.
6. Show the rewritten prompt to the user under a short label such as `Optimized Prompt` or `Optimized Request`.
7. If a better-matched skill is available, invoke it immediately and pass the rewritten prompt or its intent into that skill's workflow.
8. If no better-matched skill is available, answer the user's request from the rewritten prompt immediately after showing it.

## Skill Routing

Route to another skill only when all of these are true:

- the skill is currently available in the session
- the skill description clearly matches the user's actual task
- using that skill is more appropriate than general prompt enhancement alone

Prefer routing in cases such as:

- frontend or web UI creation -> frontend design skill
- document creation or editing -> documents skill
- spreadsheet tasks -> spreadsheets skill
- slide deck tasks -> presentations skill
- browser navigation or web testing -> browser skill

When routing:

- keep `prompt-enhancer` as the normalization layer
- do not ask the user to manually invoke the second skill if it is already available
- briefly state which skill is taking over after prompt enhancement
- keep the rewritten prompt concise and directly usable by the downstream skill

When not routing:

- continue normally inside `prompt-enhancer`
- do not mention irrelevant skills

## Rewrite Standard

Include these slots when they are useful and can be inferred safely:

- objective
- background or context
- constraints
- expected output
- tone or style

Prefer compact structure over verbosity. Add only information that increases answer quality.

## Handling Missing Information

Auto-complete reasonable missing details when the missing pieces are low-risk and strongly implied by the user's request.

Examples of reasonable completion:

- infer that a summary should be concise when the user asks for a quick summary
- infer that a plan should be step-by-step when the user asks how to do something
- infer that code help should include explanation when the user seems to be learning

Ask brief clarifying questions only when a missing detail would materially change the output or risks producing the wrong kind of answer.

Do not fabricate hard facts, external context, or user preferences that are not inferable.

## Output Behavior

By default, show the rewritten prompt before returning the improved final answer.

Use this order unless the user explicitly asks for a different format:

1. show the rewritten prompt
2. provide the answer, execution, or next action generated from it

Keep the rewritten prompt concise and practical. Do not dump chain-of-thought or hidden reasoning. Show only the usable optimized prompt text.

When routing to another skill, still show the optimized prompt first and then continue with the downstream skill's workflow.

## References

Use `references/general-template.md` for the general rewrite frame.
Use `references/routing-guide.md` for task routing rules and examples.
