---
week: <% tp.date.now("YYYY-[W]W", 0, tp.file.title, "YYYY-[W]W") %>
year: <% tp.date.now("YYYY", 0, tp.file.title, "YYYY-[W]W") %>
---

## Notes
- 🚂

## History

<%*
Array.from(Array(7).keys()).map((i) => {
  date = tp.date.weekday("YYYY/MM-MMMM/YYYY-MM-DD-dddd", i, tp.file.title, "YYYY-[W]W");
  tR += `### ${date}\n`;
  tR += `![[Timestamps/Daily/${date}#Outcomes]]\n\n`;
});
%>
## Outcomes
1. 🪂
