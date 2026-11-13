---
type: map
area: []
status: current
up: "[[Home]]"
cssclasses:
  - sb-map
created: {{date:YYYY-MM-DD}}
updated: {{date:YYYY-MM-DD}}
---

# {{title}}

Up: [[Home]]

One or two sentences: what this map covers and how it is arranged.
Arrangement is the work — sequence, grouping and a phrase of commentary per
link are what make this a map instead of a search result.

## Curated trails

> [!map] Not yet grown
> The agent adds grouped links with commentary here as pages accumulate in
> this area. Three to five links per section reads best; past that, split a
> subsection.

## Everything in this area (live)

```base
filters:
  and:
    - file.inFolder("wiki")
    - file.hasProperty("area")
    - area.contains("CHANGE-ME")
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

- 

> [!map]- How this map is gardened
> Levels: [[Home]] → this map → pages. Every page under this map carries an
> `up` property and a `Map:` line pointing back here. A new sub-map is
> justified by seven to ten loose pages on one topic — not by the topic
> merely existing. If this map no longer fits one screen, split it.
