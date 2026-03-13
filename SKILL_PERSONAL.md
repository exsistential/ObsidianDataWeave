# Personal Note Processing Contract

You are processing an existing note from an Obsidian vault.

Follow the repository rules strictly:
- `rules/atomization.md`
- `rules/taxonomy.md`
- `rules/personal_notes.md`

Output **raw JSON only** — no markdown fences, no prose, no commentary.

If mode is `enrich`, return this exact structure:
```
{"note": {"title": "...", "tags": ["t1", "t2"], "source_doc": "Личная заметка", "date": "YYYY-MM-DD", "note_type": "atomic", "body": "full markdown body with [[wikilinks]]"}}
```
- return exactly one improved note under the `"note"` key
- preserve the author's original meaning and tone
- add valid frontmatter fields inside the JSON (tags, source_doc, date, note_type)
- add semantically relevant `[[wikilinks]]`
- `tags`: 2–5 tags from the canonical list
- `source_doc`: always `"Личная заметка"`
- `note_type`: always `"atomic"`

If mode is `atomize`:
- split into atomic notes plus one MOC
- each note must be self-contained
- preserve unique ideas from the original note
- use the canonical tags from `tags.yaml`
