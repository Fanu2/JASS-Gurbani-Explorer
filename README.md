# JASS Gurbani Explorer

## Latest Release: v1.1

**Application:** `JASS_Gurbani_Explorer_v1.1.py`\
**Database:** `JASS_Gurbani.db`

> **v1.1 is the current Explorer release.**

JASS Gurbani Explorer is the user-facing application for searching,
reading, saving, and presenting Gurbani from the canonical JASS
database.

------------------------------------------------------------------------

# 1. Purpose

The Explorer consumes the normalized database created by JASS Gurbani
Corpus Builder:

``` text
JASS_Gurbani_Corpus_Builder v4.6
              │
              ▼
       JASS_Gurbani.db
              │
              ▼
    JASS Gurbani Explorer v1.1
```

It is designed as an offline-first Gurbani workspace rather than a
database editor.

------------------------------------------------------------------------

# 2. Canonical Database

The Explorer uses the current normalized JASS structure:

``` text
corpus
sources
authors
ragas
sections
shabads
lines
line_content
passages
passage_lines
provenance
import_manifest
```

It does **not** depend on the old:

``` text
gurbani_lines
```

schema and does not expect:

``` text
lines.passage_id
```

The canonical Gurmukhi text is read from:

``` text
line_content.gurmukhi
```

Passage resolution uses:

``` text
passages
passage_lines
```

------------------------------------------------------------------------

# 3. v1.1 Features

## 🔎 Powerful Gurmukhi Search

Search directly against the canonical Gurmukhi text.

Supported modes include:

-   All words
-   Any word
-   Full-word matching
-   Substring matching
-   First-letter search

This makes the Explorer useful for both exact lookup and exploratory
discovery.

------------------------------------------------------------------------

## 👤 Author Filter

Search results can be narrowed by author.

This allows exploration of Gurbani associated with specific contributors
represented in the canonical database.

------------------------------------------------------------------------

## 🎵 Raag Filter

The Explorer supports filtering by Raag.

This provides a structured way to explore the corpus through its musical
classification.

------------------------------------------------------------------------

## 📖 Section Filter

Results can also be filtered by section.

This connects search directly to the corpus organization represented in
the canonical database.

------------------------------------------------------------------------

# 4. Cohesive Passage Results

Search results are passage-aware.

Instead of displaying only the individual matching line, the Explorer
resolves the result through:

``` text
line
  ↓
passage_lines
  ↓
passage
```

This allows the user to read the surrounding cohesive passage.

The goal is:

``` text
Search match
     ↓
Meaningful context
     ↓
Complete passage
```

rather than an isolated fragment.

------------------------------------------------------------------------

# 5. Passage Reader

The dedicated **Passage Reader** provides a larger reading view for the
selected Gurbani.

Features include:

-   Large Gurmukhi rendering
-   Passage title/context
-   Favorite
-   Card Studio
-   Copy Passage
-   Export TXT

The Reader is optimized for comfortable reading rather than database
inspection.

------------------------------------------------------------------------

# 6. Search Result Navigation

The Explorer provides:

-   Previous result
-   Next result
-   Direct result selection
-   Complete passage display

This makes sequential exploration quick and simple.

------------------------------------------------------------------------

# 7. ❤️ Favorites

Passages can be saved as local Favorites.

Favorites are maintained separately from the canonical database.

The Explorer therefore does not need to modify:

``` text
JASS_Gurbani.db
```

to maintain personal selections.

------------------------------------------------------------------------

# 8. 🎲 Random Gurbani

The Explorer includes a Random feature for discovering passages without
entering a search query.

This supports casual reading and daily exploration.

------------------------------------------------------------------------

# 9. ✦ Card Studio

Card Studio turns selected Gurbani passages into visual quote cards.

The current version provides:

-   Live Gurmukhi preview
-   Multiple card designs
-   Adjustable presentation
-   Portrait and square formats
-   Social-media-friendly layouts
-   PNG export

Supported aspect ratios include:

``` text
4:5
1:1
9:16
```

These correspond well to:

``` text
Portrait social posts
Square posts
Vertical stories / shorts
```

------------------------------------------------------------------------

# 10. Card Studio v1.1 Margin Refinement

v1.1 includes a visual refinement to the card layout:

### Increased left text margin

The Gurbani text now has additional breathing room from the left
edge/decorative boundary.

The current left margin was increased from approximately:

``` text
55 px
```

to:

``` text
90 px
```

The change is intentionally limited to presentation so that the working
Card Studio functionality remains stable.

------------------------------------------------------------------------

# 11. Copy and Export

Selected passages can be:

-   Copied to the clipboard
-   Exported as TXT

This makes it easy to reuse a passage outside the Explorer.

------------------------------------------------------------------------

# 12. Database Information

The Explorer can inspect the database and display information about:

-   Corpus
-   Tables
-   Record counts
-   Sources
-   Authors
-   Raags
-   Sections
-   Shabads
-   Lines
-   Passages
-   Import information

This provides confidence that the application is working with the
expected canonical database.

------------------------------------------------------------------------

# 13. Database Validation

The Explorer checks the database before relying on its canonical
structure.

Validation includes:

-   SQLite integrity
-   Required table presence
-   Expected schema
-   Compatible database structure

This is especially useful when opening a database manually.

------------------------------------------------------------------------

# 14. Open Database

The Explorer can open compatible database files through the **Open
Database** action.

Supported extensions include:

``` text
.db
.sqlite
.sqlite3
```

For normal JASS use, the recommended database is:

``` text
JASS_Gurbani.db
```

------------------------------------------------------------------------

# 15. Read-Only Corpus Principle

The Explorer treats the canonical corpus database as a data source.

It does not use the corpus database as a place to store personal UI
state.

Personal Explorer state is kept separately, such as:

``` text
jass_explorer_state.json
```

This separation protects the canonical corpus.

------------------------------------------------------------------------

# 16. User Interface

The Explorer is organized around a compact local workspace containing:

-   Search
-   Passage Reader
-   Card Studio
-   Random
-   Favorites
-   Database information
-   Database validation
-   Theme controls

The design emphasizes large, readable Gurmukhi text and quick
navigation.

------------------------------------------------------------------------

# 17. Typical Workflow

### Search

Enter a Gurmukhi word or phrase.

### Filter

Optionally select:

``` text
Author
Raag
Section
```

### Read

Select a result and view the complete passage.

### Save

Use:

``` text
♥ Favorite
```

### Create

Send the passage to:

``` text
✦ Card Studio
```

### Export

Use:

``` text
Copy
Export TXT
PNG
```

------------------------------------------------------------------------

# 18. Installation

Requirements:

-   Python
-   PySide6

Install PySide6 if necessary:

``` powershell
py -m pip install PySide6
```

Place the Explorer and database together for automatic opening:

``` text
JASS_Gurbani_Explorer_v1.1.py
JASS_Gurbani.db
```

Alternatively, use **Open Database**.

------------------------------------------------------------------------

# 19. Run

From PowerShell:

``` powershell
py .\JASS_Gurbani_Explorer_v1.1.py
```

Optional syntax check:

``` powershell
py -m py_compile .\JASS_Gurbani_Explorer_v1.1.py
```

------------------------------------------------------------------------

# 20. Technology

The Explorer is a local desktop application built with:

-   Python
-   PySide6
-   SQLite

It is designed to work locally without requiring a cloud backend.

------------------------------------------------------------------------

# 21. Data Architecture

The Explorer sits above the canonical corpus:

``` text
                    JASS_Gurbani.db
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
      Lines             Shabads           Metadata
        │                  │                  │
        └──────────────┬───┴──────────────────┘
                       ▼
                   Passages
                       │
                       ▼
                    Search
                       │
             ┌─────────┼─────────┐
             ▼         ▼         ▼
           Reader   Favorites   Cards
```

The Explorer is therefore a presentation and discovery layer, not the
authoritative corpus builder.

------------------------------------------------------------------------

# 22. Current Database

The current validated JASS database used during development contains:

``` text
Corpus:          1
Shabads:         5,549
Lines:           60,555
Line content:    60,555
Passages:        5,549
Passage lines:   60,555
Provenance:      66,104
Tables:          13
SQLite integrity: OK
```

The Explorer is designed around this canonical database structure.

------------------------------------------------------------------------

# 23. Version History

## v1.1 --- Current

Presentation refinement:

-   Increased left card text margin
-   Preserved working search and Card Studio behavior
-   Maintains canonical `JASS_Gurbani.db` compatibility

## v1.0

Canonical database edition:

-   Migrated from old `gurbani_lines` structure
-   Added canonical `JASS_Gurbani.db` support
-   Passage-aware search
-   Author/Raag/Section filters
-   Passage Reader
-   Favorites
-   Random discovery
-   Card Studio
-   PNG export
-   Database inspection
-   Validation
-   Copy/TXT export

------------------------------------------------------------------------

# 24. Design Philosophy

The Explorer follows these principles:

1.  **Read the canonical corpus; do not corrupt it.**
2.  **Show meaningful passages rather than isolated lines.**
3.  **Make Gurmukhi the primary reading experience.**
4.  **Keep personal state separate from corpus data.**
5.  **Prefer simple, local, reliable tools.**
6.  **Build useful presentation features without unnecessarily changing
    the database.**
7.  **Keep future semantic search/RAG layers downstream of the canonical
    corpus.**

------------------------------------------------------------------------

# 25. Relationship to the Builder

The two applications intentionally have different jobs.

  -----------------------------------------------------------------------
  Application                         Responsibility
  ----------------------------------- -----------------------------------
  **Corpus Builder v4.6**             Investigate, verify, normalize,
                                      build, validate

  **Explorer v1.1**                   Search, read, save, create cards,
                                      export
  -----------------------------------------------------------------------

The relationship is:

``` text
master.sqlite
     │
     ▼
JASS Gurbani Corpus Builder v4.6
     │
     ▼
JASS_Gurbani.db
     │
     ▼
JASS Gurbani Explorer v1.1
```

This separation keeps the corpus foundation stable while allowing the
Explorer to evolve independently.

------------------------------------------------------------------------

# 26. Current Status

**Latest version: v1.1**

**Status: Working / stable presentation release**

The Explorer is currently suitable for:

-   Gurbani search
-   Passage reading
-   Personal favorites
-   Random discovery
-   Card creation
-   PNG export
-   TXT export
-   Database inspection
-   Canonical database validation

------------------------------------------------------------------------

## Vision

> **Search naturally. Read deeply. Preserve faithfully. Create
> beautifully.**

JASS Gurbani Explorer is the user-facing workspace built on the verified
JASS Gurbani corpus.
