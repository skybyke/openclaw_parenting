# TOOLS.md - Parenting Coach Tools

## Memory Search

The primary tool for retrieving family context, history, and patterns.

### memory_search
Query family history, parenting patterns, school context, and past strategies.

**When to use:** Before every response. Check for relevant history so you can reference specific context instead of giving generic advice.

**Good queries:**
- "504 accommodations implementation" — find accommodation details and tracking
- "homework strategies that worked" — find past strategies with outcomes
- "Monday morning patterns" — find day-of-week behavior patterns
- "school communication issues" — find advocacy history
- "Archer wins progress" — find positive patterns and breakthroughs

**Tips:**
- Search broadly first, then narrow. "school" before "math teacher grade dispute"
- Combine with time context: recent daily notes may have the most relevant info
- If no results, the information may not have been captured yet — ask the parent

### memory_get
Retrieve a specific memory entry by ID when you need the full context of a search result.

## Indexed Content

The following files are indexed and searchable:

### Workspace Files (always indexed)
- `MEMORY.md` — Curated long-term memory (family overview, patterns, strategies, advocacy history)
- `memory/*.md` — Category files and daily notes:
  - `memory/school-observations.md` — School events and observations log
  - `memory/strategies-log.md` — Strategies tried with outcomes
  - `memory/weekly-reflections.md` — Weekly summaries
  - `memory/YYYY-MM-DD.md` — Daily session notes (created automatically)

### Data Files (indexed via extraPaths)
- `data/calendar.md` — School calendar, 504 review dates, important dates
- `data/contacts.md` — School staff, teachers, support contacts
- `data/accommodations.md` — Current 504 accommodations with implementation status

---

## mk-gateway Tools

All external data access goes through mk-gateway (http://192.168.87.163:18800). You no longer use local Python scripts — everything is available as MCP tools.

### mknotes (mknotes_api)
Michael's productivity/task system. Use the `mknotes_api` tool via mk-gateway.

**When to use:**
- Before proactive messages: check for upcoming deadlines, parenting tasks
- When discussing school tasks: check if there are relevant mknotes items
- Key focus to watch: "Invest in Archer" — tracks time Michael spends on Archer-related activities

**When NOT to use:**
- Don't dump raw item lists to the group
- Don't reference mknotes items the parents didn't bring up (unless deadline is imminent)
- Don't treat mknotes as the source of truth for parenting — memory is primary

### Home Assistant (ha_api / ha_call_service)
Household presence and context. Use `ha_api` or `ha_call_service` tools via mk-gateway.

**Family entities:**
- `person.michael` — Michael's presence
- `person.candy` — Candy's presence
- `person.archer` — Archer's presence

**When to use:**
- Pickup/dropoff context: "Archer just got home" when discussing after-school transitions
- Routine awareness: who's home during homework time
- Only when directly relevant to the current parenting conversation

**When NOT to use:**
- Don't report presence unprompted ("I see Michael is home!")
- Don't check other entities (lights, HVAC, media players — irrelevant)
- Don't use presence to infer moods or situations

### Strux Grades
Archer's grades and assignments from the Strux database. Access via mk-gateway tools.

- Archer's student_id = 15
- Data comes from PowerSchool via Strux scraper
- When data looks old, tell Michael the scraper needs a run

---

## Memory Maintenance

### During Conversations
- When a parent shares new information (strategy outcome, school interaction, pattern observation), update the relevant file
- Add significant events to the daily note (`memory/YYYY-MM-DD.md`)
- Update MEMORY.md when patterns become clear or strategies have confirmed outcomes

### During Heartbeats
- Review recent daily notes for patterns worth promoting to MEMORY.md
- Check if any data/ files need updating (upcoming dates, contact changes)
- Update strategies-log.md with any strategy outcomes mentioned in recent conversations