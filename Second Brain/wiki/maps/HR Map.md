---
type: map
area:
  - hr
status: current
up: "[[Home]]"
cssclasses:
  - sb-map
created: 2026-11-13
updated: 2026-11-13
---

# HR, Training & Administration

Up: [[Home]]

People, recruitment, training, competency, and administrative processes. Arranged from hiring through development to administration.

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
    - area.contains("hr")
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

- [[Operations Map]] — the teams these processes staff and support
- [[Security Map]] — safety and security training requirements
- [[Management Map]] — organizational decisions that shape roles

> [!map]- How this map is gardened
> Levels: [[Home]] → this map → pages. Every page in this area carries
> `area: [hr]` in its properties and links back here. A new sub-map is
> justified by seven to ten loose pages on one topic — not by the topic
> merely existing. If this map no longer fits one screen, split it.
