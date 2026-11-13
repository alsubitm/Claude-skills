---
type: map
area:
  - security
status: current
up: "[[Home]]"
cssclasses:
  - sb-map
created: 2026-11-13
updated: 2026-11-13
---

# Security & Emergency

Up: [[Home]]

Security operations, incident and emergency response, and HSSE. Arranged from prevention through response to lessons learned.

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
    - area.contains("security")
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

- [[Operations Map]] — the service delivery these controls protect
- [[HR Map]] — training and competency that make procedures real
- [[Management Map]] — governance and reporting lines for incidents

> [!map]- How this map is gardened
> Levels: [[Home]] → this map → pages. Every page in this area carries
> `area: [security]` in its properties and links back here. A new sub-map is
> justified by seven to ten loose pages on one topic — not by the topic
> merely existing. If this map no longer fits one screen, split it.
