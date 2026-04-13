---
name: imp
description: |
  Improve and enhance any prompt or request before executing it. Use this skill whenever the user's message starts with "/imp" or when the user asks to "improve my prompt", "enhance this request", "optimize this prompt", or wants Claude to apply prompt engineering techniques before executing a task. The skill rewrites the user's raw request using best practices (clarity, XML structure, examples, context, role-setting), then executes the improved prompt and shows both the improved version and the result.
---

# Prompt Improver (imp)

Triggered when the user prefixes their request with `/imp` or asks to improve/enhance a prompt before execution.

## What This Skill Does

1. **Improve** the user's raw prompt using prompt engineering best practices
2. **Execute** the improved prompt
3. **Show** both the improved prompt and the result

---

## Step-by-Step Process

### Step 1: Extract the Raw Prompt

The user's actual request comes after `/imp`. For example:
- `/imp اكتب مقال عن الذكاء الاصطناعي` → raw prompt: `اكتب مقال عن الذكاء الاصطناعي`
- `/imp write a python function to sort a list` → raw prompt: `write a python function to sort a list`

### Step 2: Improve the Prompt

Apply the following techniques as appropriate:

**Clarity & Directness**
- Be explicit about desired output format, length, and tone
- Add specific constraints and success criteria
- Replace vague instructions with concrete ones
- Use numbered steps when order matters

**Context & Role**
- Add a relevant role/persona when beneficial (e.g., "You are an expert Python developer...")
- Include motivation or purpose behind the request
- Specify the intended audience

**Structure**
- Use XML tags to separate instructions, context, examples, and input
- Use `<instructions>`, `<context>`, `<format>`, `<examples>` tags where helpful
- Break complex tasks into explicit sub-steps

**Examples (Few-Shot)**
- Add 1–3 concrete examples if the task involves a specific pattern or format
- Wrap examples in `<example>` tags

**Output Control**
- Specify the desired format (prose, JSON, code, markdown, etc.)
- Set length expectations (brief, detailed, X paragraphs, etc.)
- Mention what to avoid if relevant

**Scope Calibration**
- If the original prompt is vague, expand it to request a complete, high-quality output
- Add "Go beyond the basics" or "Include edge cases" when thoroughness matters

### Step 3: Execute the Improved Prompt

After improving, actually carry out the task described in the improved prompt. Produce a real, complete response.

### Step 4: Present the Output

Show the result in this exact structure:

```
## ✨ البرومت بعد التحسين

[The improved prompt, clearly formatted]

---

## 📋 النتيجة

[The actual output from executing the improved prompt]
```

If the user wrote in Arabic, show the section headers in Arabic as above.
If the user wrote in English, use English headers:
```
## ✨ Improved Prompt
## 📋 Result
```

---

## Important Notes

- **Always execute**: Don't just show the improved prompt — actually complete the task.
- **Respect the original intent**: Improve the *how*, not the *what*. Don't change what the user is asking for.
- **Proportional improvement**: A simple request needs minor refinement. A complex task may need full XML structuring, role-setting, and examples.
- **Language consistency**: Keep the improved prompt in the same language as the original request.
- **Don't over-engineer**: Apply only the techniques that genuinely improve the prompt. Not every prompt needs every technique.

---

## Example

**User input:** `/imp اعمل لي قصيدة عن القمر`

**Improved Prompt:**
```
أنت شاعر عربي متمكن يكتب بأسلوب راقٍ وعاطفي.

اكتب قصيدة عربية أصيلة عن القمر تلتزم بالمعايير التالية:
- الطول: 8 إلى 12 بيتاً
- الأسلوب: شعر عمودي فصيح مع اهتمام بالموسيقى والإيقاع
- المحتوى: ابدأ بوصف جمال القمر، ثم انتقل إلى مشاعر الشوق أو التأمل التي يُثيرها
- اختر تفعيلة شعرية واحدة والتزم بها طوال القصيدة
- اختم بصورة شعرية لا تُنسى
```

**النتيجة:** [القصيدة كاملة]
