# GDI+
Eine Sammlung von Tipps und Tricks zum Thema Grafikprogrammierung mit GDI+.

## Klassen / Ereignisse
### Timer
Ein Timer führt in regelmäßigen Abständen ein `Tick`-Event aus. Der [`System.Windows.Forms`.`Timer`](https://learn.microsoft.com/de-de/dotnet/api/system.windows.forms.timer?view=windowsdesktop-8.0&viewFallbackFrom=net-6.0) kann über die Toolbox auf die GUI gezogen werden. 

Anschließend können wir 
- die Zeit zwischen jedem `Tick`-Event einstellen (`+ Interval { get; set; }: int`) und
- den Timer starten (`+ Start():void`) oder
- stoppen (`+ Stop():void`) oder
- den Zustand abfragen. (`+ Enabled{ get; set; }: bool`) (Standard ist ausgeschaltet: `enabled = false`)



## Tipps und Tricks
Ergänzen Sie hier die notwendigen Code-Ausschnitte, um zu zeigen, wie man es macht. 
- Sie können [CodeBlöcke mit Syntax-Highlighting](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#syntax-highlighting) einsetzen
- Wird es zu unübersichtlich? Sie können auch Unterordner mit Beispiel-Code anlegen und auf die entsprechenden Dateien verlinken. [Inspiration](https://github.com/gsoTH/flaskShowcase/tree/master/datenbanken).
- Die folgende Liste kann gerne ergänzt werden :)

### Bewegung animieren

### Objekte mit Tasten steuern

### Verhindern, dass ein Spieler aus dem Bild läuft

### Spiel pausieren

### Ihr schönstes Ergebnis





