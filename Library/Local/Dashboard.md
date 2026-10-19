---
tags: meta
---

# Dashboard

## Recent Notes

${query[[
  from index.tag "page"
  order by lastModified desc
  limit 10
]]}

## Tasks

${query[[
  from index.tag "task"
  where not done
  limit 20
]]}
