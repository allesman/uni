---
sticker: lucide//home
cssclasses: " "
---
```dataview
table without id file.link as MODUL
from #orga
where fertig=false
```
# `$= '[[' + 'weekly tasks/KW' + dv.date('now').weekNumber.toString().padStart(2, '0') + '|📝 Wöchentliche Aufgaben]]'`
