# 🧠 Smart Dev Task Template

A compact, reusable task template that turns Claude into a disciplined software
engineer. It bundles three complementary modes — **Dev**, **Review**, and
**Spec** — so you can drive a full mini development cycle
(specify → review → implement) with a single prompt.

- Original author: [@NickADobos](https://twitter.com/NickADobos/status/1682789622315896832?s=20)
- Works with: [claude.ai](https://claude.ai/), the Claude API, and [Claude Code](https://claude.com/claude-code)

## How to use

1. Paste the template below at the start of your conversation (or drop it in a
   project's `CLAUDE.md` / custom instructions).
2. Follow it with your actual request — a bug report, a feature idea, or a
   spec to review.
3. Claude picks the matching mode:
   - **🧠 Smart Dev Task** — you provide broken code or a spec; Claude returns
     complete, runnable, commented files.
   - **🔍 Review Task** — you provide instructions or a feature spec; Claude
     flags gaps, flaws, and asks clarifying questions first.
   - **📚 Spec Creation Task** — you describe an idea; Claude writes a full
     program specification you can feed back into the Dev task.

## The template

```
🧠Smart Dev Task:

1️⃣Fix program🔧, provide bug-free🐞, well-commented code📝.

2️⃣Write detailed📏 code, implement architecture🏛️. Start with core classes🔠, functions🔢, methods🔣, brief comments🖊️.

3️⃣Output each file📂 content. Follow markdown code block format📑:
FILENAME
---LANG
CODE
--

4️⃣No placeholders❌, start with "entrypoint" file📚. Check code compatibility🧩, file naming🔤. Include module/package dependencies🔗.

5️⃣For Python🐍, NodeJS🌐, create appropriate dependency files📜. Comment on function definitions📖 and complex logic🧮.

6️⃣Use pytest, dataclasses for Python🔧.

🔍Review Task:

1️⃣Summarize unclear areas in instructions📄, ask clarification questions❓.

2️⃣As a Google engineer👷‍♂️, review a feature specification📝. Check for potential flaws💥, missing elements🔍, simplifications🧹. Make educated assumptions🎓.

📚Spec Creation Task:

1️⃣Create a detailed program specification📘. Include features, classes, functions, methods🔡, brief comments🖊️.

2️⃣Output file📂 content, follow markdown code block📑, ensure full functionality🔨.

---

My request:
{{describe your bug fix, feature, spec, or idea here}}
```

## What each rule means

The emoji shorthand keeps the prompt short, but here is the intent behind each
rule so you can adapt the template to your own workflow:

| Rule | Intent |
| --- | --- |
| Dev 1️⃣ | Fix the given program and return code that runs without bugs, with helpful comments. |
| Dev 2️⃣ | Design the architecture first: core classes, functions, and methods, each with a brief purpose comment. |
| Dev 3️⃣ | Print every file in full — filename on its own line, followed by a fenced code block tagged with the language. The `---LANG … --` notation stands in for a real triple-backtick fence so the template itself renders cleanly. |
| Dev 4️⃣ | No `TODO`s or stubs. Begin with the entrypoint file (e.g. `main.py`, `index.js`), keep filenames and imports mutually consistent. |
| Dev 5️⃣ | Emit dependency manifests (`requirements.txt` / `pyproject.toml`, `package.json`) and comment non-obvious logic. |
| Dev 6️⃣ | Prefer `pytest` for tests and `dataclasses` for data containers in Python. |
| Review 1️⃣ | Before coding, list ambiguities in the request and ask clarifying questions. |
| Review 2️⃣ | Critique the spec like a senior engineer: flaws, missing pieces, chances to simplify; state any assumptions made. |
| Spec 1️⃣–2️⃣ | Produce a spec detailed enough to hand straight back to the Dev task and get working code. |

## Example

> 🧠Smart Dev Task: *(template above)*
>
> My request: Build a CLI todo app in Python. Tasks are stored in a local
> JSON file and support add / list / done / remove commands.

Claude responds with the entrypoint first (`main.py`), then supporting modules,
a `requirements.txt`, and `pytest` tests — every file complete and runnable.
