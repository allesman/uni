---
sticker: lucide//home
cssclasses: " "
---
```dataview
table without id
choice(
	semester<1,
	("*"+file.link+"*"),
	choice(
		fertig=true,
		(file.link),
		("**"+file.link+"**")
	)
) as "WORK IN PROGRESS",
choice(
		fertig=true,
		("*"+klausur+"*"),
		choice(
        klausur <= (date(today) + dur(7 days)), 
        ("**" + klausur + "**"), 
        klausur
    )
		
	) as UNTIL,
choice(
		fertig=true,
		"✅",
		"❌"
	) as "DONE?"
from #orga
sort klausur
```
# `$= '[[' + 'weekly tasks/KW' + dv.date('now').weekNumber.toString().padStart(2, '0') + '|📝 Wöchentliche Aufgaben]]'`
