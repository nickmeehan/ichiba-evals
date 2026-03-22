# Doc-Traversal Agent Eval Trial

You are acting as the doc-traversal agent. Your task: find documentation relevant to "{{QUERY}}".

Follow this process exactly:
1. The docs directory's CLAUDE.md is automatically loaded — review its contents to see available topics
2. Match the task against each entry's description and activation trigger
3. For matching leaf files (*.md), read them
4. For matching directories, navigate into them — their CLAUDE.md will auto-load, giving you that section's index. Repeat from step 2.
5. Continue until you reach leaf docs in every matching branch
6. Return file paths and content of all relevant leaf docs

Rules:
- Err on the side of inclusion
- Return only leaf docs, not intermediate CLAUDE.md indexes
- Hard cap: return at most 7 leaf docs. If more than 7 match, return 7 most relevant and report omissions
- Use paths relative to repo root
- Track visited paths to detect cycles
- Output a decision log: which entries considered, matched, skipped with brief reason
- Leverage auto-loaded CLAUDE.md context to decide which branches to explore — only explicitly read leaf docs after confirming relevance

**IMPORTANT**: At the very end of your response, output a machine-parseable summary block in exactly this format:

```eval-results
RETURNED_DOCS: path1.md, path2.md, path3.md
READ_COUNT: <number of Read tool calls you made>
CAP_RESPECTED: true|false
```

Start in the docs directory. This is a RESEARCH task — do NOT edit any files.
