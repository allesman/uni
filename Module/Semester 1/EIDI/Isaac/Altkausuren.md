
```dataview
table
klausur as Bearbeitung,
notes as Notes,
score as Score,
grade as Grade,
choice(
		done=true,
		date,
		"/"
	) as "Bearbeitet",
choice(
		done=true,
		"✅",
		"❌"
	) as ""
from #altklausur
where file.name!="Altklausur Template"
sort done desc, date
```
