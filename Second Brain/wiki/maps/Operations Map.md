---
type: map
area:
  - operations
status: current
up: "[[Home]]"
cssclasses:
  - sb-map
created: 2026-11-13
updated: 2026-11-13
---

# Operations & Service Delivery

Up: [[Home]]

Core operational processes, service delivery, facilities, and logistics. Arranged from daily delivery outward to what supports it.

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
    - area.contains("operations")
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

- [[Security Map]] — controls and emergency response wrapped around delivery
- [[Management Map]] — plans and KPIs that steer operations
- [[Finance Map]] — procurement and vendors operations depend on

> [!map]- How this map is gardened
> Levels: [[Home]] → this map → pages. Every page in this area carries
> `area: [operations]` in its properties and links back here. A new sub-map is
> justified by seven to ten loose pages on one topic — not by the topic
> merely existing. If this map no longer fits one screen, split it.
