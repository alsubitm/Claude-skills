---
type: map
area:
  - finance
status: current
up: "[[Home]]"
cssclasses:
  - sb-map
created: 2026-11-13
updated: 2026-11-13
---

# Finance, Procurement & Contracts

Up: [[Home]]

Budgets, purchasing, vendors, contracts, RFPs and bids. Arranged from money in, through commitments, to money out.

## Curated trails

> [!map] Not yet grown
> As pages accumulate in this area, the agent plants grouped links here, each
> with a phrase of commentary — three to five links per section before a
> subsection is split off.

## Everything in this area (live)

```base
filters:
  and:
    - file.inFolder("wiki")
    - '!file.inFolder("wiki/maps")'
    - file.hasProperty("area")
    - area.contains("finance")
views:
  - type: table
    name: Area pages
    groupBy:
      property: note.type
      direction: ASC
    sort:
      - property: file.mtime
        direction: DESC
    order:
      - file.name
      - type
      - status
      - file.mtime
```

## Threads into other maps

- [[Startup Map]] — the ventures the budgets serve
- [[Operations Map]] — procurement that keeps delivery running
- [[Management Map]] — financial governance and KPI reporting

> [!map]- How this map is gardened
> Levels: [[Home]] → this map → pages. Every page in this area carries
> `area: [finance]` in its properties and links back here. A new sub-map is
> justified by seven to ten loose pages on one topic — not by the topic
> merely existing. If this map no longer fits one screen, split it.
