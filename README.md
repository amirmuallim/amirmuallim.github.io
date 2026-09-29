# Portfolio + Interview Prep

Preview locally: `pip install -r requirements.txt` then `mkdocs serve` (http://127.0.0.1:8000).

## Add a question
1. Copy TEMPLATE.md into the right folder under docs/interview/, e.g. docs/interview/07-uvm/factory-override.md
2. Fill it in and save.
3. `git add . && git commit -m "add UVM factory question" && git push`
The site rebuilds in about a minute.

## Add a section
Create a new folder under docs/interview/ (for example 12-physical-design) with an index.md containing a heading. The number prefix controls sidebar order.

## Import from Word
`pandoc yourfile.docx -t gfm --extract-media=docs/assets -o draft.md`, then split draft.md into one file per question.
