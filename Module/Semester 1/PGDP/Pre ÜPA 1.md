1.
```java
Car c = CarFactory.getInstance().getAssembledCar()
double i = c.getEngine().getConsumption()
c.getFueltank().consume(10d);
AssertGreaterThan(i,c.getEngine().getConsumption(),0.0001f);

```

Fueltank Konstruktor testen
attribute werden gesetzt
level>capacity, müsste problem geben?

fill() ändert nichts wenn amount negativ

fill() tankt, alles geht rein

fill() tankt, überschuss

consume() öndert fuel

consume() ändert nichts wenn amount negativ

Auto mit factory erstellen, prüfen dass alles != null

Räder müssen alle den gleichen durchmesser und breite haben

jedes rad nur einmal

getrange testen

getmaxrange testen
![[Pre ÜPA 2025-12-05 12.30.11.excalidraw]]