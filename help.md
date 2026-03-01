# Help — Q05: GitHub Actions Workflow with Status Badge

> **1.0 mark** · Use this file as a learning companion while solving the question.

---

## Quick Approach

1. Read `question.md` carefully — note the **exact output format** required.
2. Identify the key tool or concept (bash pipeline, LLM prompt, Python script, etc.).
3. Build and test your solution **locally** before submitting.
4. Paste the answer into the exam UI, click **Check**, verify the score, then **Save**.
5. Record your working in `answer.md` for revision.

---

## Bash Pipelines

```bash
# Fetch remote data
curl -s 'https://wttr.in/London?format=j1'        # JSON weather
curl -s 'https://wttr.in/London'                   # text weather

# Parse JSON with jq
curl -s URL | jq '.current_condition[0].temp_C'
curl -s URL | jq -r '.key'   # -r = raw string (no quotes)

# Parse with grep / sed / awk
echo 'temp_C: 12' | grep -oP '\d+'               # extract digits
echo 'key: value' | awk -F': ' '{print $2}'        # split on ': '
echo 'hello world' | sed 's/world/earth/'           # replace

# Debug a pipeline interactively
set -x    # print each command before running
set +x    # turn off debug trace

# Chain commands
curl -s URL | grep pattern | awk '{print $1}' | sort -u
```

### Handy one-liners
```bash
wc -l file.txt                    # count lines
sort -u file.txt                  # sort & deduplicate
cut -d',' -f2 data.csv            # get 2nd CSV column
awk -F',' '{print $2}' data.csv   # same with awk
head -5 file.txt                  # first 5 lines
tail -5 file.txt                  # last 5 lines
```

## API / HTTP Requests

```bash
# GET request
curl -s 'https://api.example.com/endpoint'

# GET with auth header
curl -s -H 'Authorization: Bearer YOUR_TOKEN' 'https://api.example.com/'

# POST JSON body
curl -s -X POST \
  -H 'Content-Type: application/json' \
  -d '{"key": "value"}' \
  'https://api.example.com/endpoint'

# Pretty-print JSON response
curl -s URL | python3 -m json.tool
curl -s URL | jq .

# Check HTTP status code
curl -o /dev/null -s -w '%{http_code}' URL
```

### AI Pipe
- Website: <https://aipipe.org/>
- AI Pipe is an OpenAI-compatible proxy — use it like the OpenAI API.
- Works with `llm keys set aipipe` or as a direct `Authorization: Bearer` header.

## SQL / SQLite

```bash
# Open a database interactively
sqlite3 data.db

# Run a query from the shell
sqlite3 data.db 'SELECT * FROM my_table LIMIT 5;'

# Output as CSV
sqlite3 -csv data.db 'SELECT * FROM my_table;'
```

```sql
-- Common patterns
SELECT col, COUNT(*) AS n FROM t GROUP BY col ORDER BY n DESC;
SELECT * FROM t WHERE col LIKE '%pattern%';
SELECT a.*, b.name FROM a JOIN b ON a.id = b.a_id;
```

## Git

```bash
git log --oneline -10              # last 10 commits
git diff HEAD~1 HEAD               # changes in last commit
git show HEAD:path/to/file         # file at a specific commit
git blame path/to/file             # who changed each line
```

---

## How to Verify Your Answer

1. Run your command / script locally and inspect the output.
2. Compare output format precisely to what the question specifies.
3. Submit in the exam UI and click **Check** — the score updates live.
4. If correct, click **Save** immediately and don't modify the answer.

---

## Common Pitfalls

- **Case sensitivity** — `Yes` ≠ `yes`; match exactly what the question asks for.
- **Trailing whitespace / newlines** — trim output before comparing.
- **JSON key names** — must match the schema exactly.
- **Changing a saved correct answer** — you may not get the same result again!
- **Timeouts** — if the exam page is slow, wait and retry rather than refreshing.

---

## My Notes

_Add your own observations, gotchas, and insights here as you work._

---

## Resources

- [TDS Public Discussions](https://github.com/sanand0/tools-in-data-science-public/discussions/)
- [AI Pipe](https://aipipe.org/) — LLM API proxy for the exam
- [llm CLI docs](https://llm.datasette.io/)
- [wttr.in API](https://wttr.in/:help) — weather API used in some questions
- [jq Manual](https://jqlang.github.io/jq/manual/)
- [uv docs](https://docs.astral.sh/uv/)
