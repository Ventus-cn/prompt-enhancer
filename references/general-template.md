# General Enhancement Template

Use this template when the request is broad, mixed, or does not clearly belong to a single specialized category.

## Purpose

Turn a rough request into an internal prompt that is clearer, more actionable, and easier for the model to answer well.

## Internal Prompt Shape

Structure the rewritten prompt around these fields when useful:

- Objective: What the user wants done
- Context: Relevant background or situation
- Constraints: Limits, preferences, forbidden directions, format needs
- Expected Output: The shape of the answer or deliverable
- Tone/Style: Voice, depth, or audience fit if inferable

## Guidance

Keep the rewritten prompt concise.

Do not pad the prompt with generic instructions unless they improve the answer.

Preserve the user's actual task. Upgrade wording, structure, and clarity rather than changing the request.

## Example

Raw request:

`帮我写一个产品介绍`

Possible internal rewrite:

`目标：撰写一段产品介绍文案。上下文：用户未提供产品细节，因此先采用通用产品介绍结构。约束：语言简洁、适合对外展示、避免空泛套话。期望输出：一版可直接使用的中文产品介绍，并在必要时补充可替换占位项。语气：专业、清晰、有说服力。`
