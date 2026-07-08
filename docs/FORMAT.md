# Question JSON format

The viewer loads a single **JSON array** of question objects. Questions are
sorted by their `order` field before display. Below is every field the
viewer understands.

## Question object

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| `id` | number | ✅ | Unique id for the question. |
| `order` | number | ✅ | Sort position within the set (ascending). |
| `passage_id` | number \| null | — | Groups questions that share a passage. Use the same value for every question under one passage. `null`/omitted = discrete question. |
| `passageHtml` | string \| null | — | HTML for the left passage pane. If `null`/omitted, the question is treated as discrete: the two-pane layout is kept and the left pane shows a note that the item is independent of a passage. |
| `question_content` | string | ✅ | HTML for the question stem. |
| `answer_choices` | array | ✅ | List of choice objects (see below). MCAT items use 4. |
| `correct_answer` | string | — | Letter of the answer (e.g. `"C"`). Reference only — correctness is taken from the `correct` flags, not this field. |
| `answer_content` | string | — | HTML explanation, shown when the answer is revealed. |

## Choice object

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| `id` | number | ✅ | Unique within the question. |
| `sort_order` | number | ✅ | 0-based. Maps to a letter: `0 → A`, `1 → B`, `2 → C`, `3 → D`. |
| `choice_content` | string | ✅ | HTML for the choice text. |
| `correct` | boolean | ✅ | Exactly **one** choice per question must be `true`. |

## Behaviours worth knowing

- **Passage grouping.** Questions sharing a `passage_id` are treated as one
  passage; the viewer numbers passages in the order they first appear.
- **Passage titles.** If `passageHtml` already contains a header like
  `Passage 1 (3 questions)`, the viewer hides its own generated title to
  avoid a duplicate. If it doesn't, the viewer generates one.
- **Images.** Reference local files with a relative path, e.g.
  `<img src="./images/diagram.png">`. Remote `http(s)`/`//` URLs render only
  while online; localise them for a fully offline set.
- **HTML is rendered as-is** in the passage, stem, choices, and explanation,
  so keep it to trusted content (it is injected via `innerHTML`).

## Minimal example

```json
[
  {
    "id": 1,
    "order": 1,
    "passage_id": 100,
    "passageHtml": "<p><strong>Passage 1 (1 question)</strong></p><p>Some passage text…</p>",
    "question_content": "<p>The passage suggests that…</p>",
    "answer_choices": [
      { "id": 11, "sort_order": 0, "choice_content": "<p>Option A</p>", "correct": false },
      { "id": 12, "sort_order": 1, "choice_content": "<p>Option B</p>", "correct": true },
      { "id": 13, "sort_order": 2, "choice_content": "<p>Option C</p>", "correct": false },
      { "id": 14, "sort_order": 3, "choice_content": "<p>Option D</p>", "correct": false }
    ],
    "correct_answer": "B",
    "answer_content": "<p><strong>The solution is B.</strong> Because…</p>"
  }
]
```

A discrete (non-passage) question simply sets `"passageHtml": null` (or omits
it) and `"passage_id": null`; the viewer keeps the two-pane layout and shows an
"independent of a passage" note in the left pane. See
[`../sample.json`](../sample.json) for a complete, working four-question example.
