# General Enhancement Template

Use this template when the request is broad, mixed, or does not clearly belong to a single specialized category.

## Purpose

Turn a rough request into an internal prompt that is clearer, more actionable, and easier for the model to answer well.

## Internal Prompt Shape

Structure the rewritten prompt around these fields when useful:

- Objective: what the user wants done
- Context: relevant background or situation
- Constraints: limits, preferences, forbidden directions, or format needs
- Expected Output: the shape of the answer or deliverable
- Tone/Style: voice, depth, or audience fit if inferable

## Guidance

Keep the rewritten prompt concise.

Do not pad the prompt with generic instructions unless they improve the answer.

Preserve the user's actual task. Upgrade wording, structure, and clarity rather than changing the request.

## Example

Raw request:

`Help me write a product introduction.`

Possible internal rewrite:

`Objective: write a product introduction. Context: the user did not provide product details, so begin with a general product-introduction structure. Constraints: keep the language concise, suitable for public-facing use, and avoid empty marketing clichés. Expected Output: one ready-to-use product introduction, with optional placeholders where product-specific details can be inserted later. Tone/Style: professional, clear, and persuasive.`
