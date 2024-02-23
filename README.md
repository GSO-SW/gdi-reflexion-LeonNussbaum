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

```csharp
private void tmrGameTick_Tick(object sender, EventArgs e)
{
    //Position verändern mit Refresh wird neu "Gezeichnet" und die neue position wurde eingenommen
    this.Refresh();
}
```


### Objekte mit Tasten steuern

```csharp
        private void FrmFrogger_KeyDown(object sender, KeyEventArgs e)
        {
            if (e.KeyCode == Keys.Up)
            {
                    spieler.Y = spieler.Y - hoeheJeBereich;
            }

            if(e.KeyCode == Keys.Down)
            {
                spieler.Y = spieler.Y + hoeheJeBereich;
            }

            if(e.KeyCode == Keys.Left)
            {
                spieler.X = spieler.X - 60;
            }

            if(e.KeyCode == Keys.Right)
            {
                spieler.X = spieler.X + 60;
            }
            this.Refresh();
        }

```


### Verhindern, dass ein Spieler aus dem Bild läuft

```csharp

// Überprüfen mit ClientSize.Width oder ClientSize.Height
if(e.KeyCode == Keys.Right)
{
    if (spieler.X + 60 > this.ClientSize.Width)
        return;
    spieler.X = spieler.X + 60;
}

```
### Spiel pausieren

```csharp

// Stoppen des timers um das Spiel zu Pausieren
tmrGameTick.Stop();
// Um den Timer zu starten
tmrGameTick.Start();

```

### Bilder als Grafik zu verwenden
```csharp

Bitmap image = new Bitmap("../../Download.jpg");
e.Graphics.DrawImage(image, new Rectangle(aktuellesHindernis.X, aktuellesHindernis.Y, 

```


### Bilder rund machen 

```csharp
Bitmap playerImage = new Bitmap("../../marceleris.jpg");
Bitmap roundedImage = new Bitmap(playerImage.Width, playerImage.Height);
using (Graphics g = Graphics.FromImage(roundedImage))
{
// Grafikobjekt erstellen und als Kreis konfigurieren
GraphicsPath path = new GraphicsPath();
path.AddEllipse(0, 0, roundedImage.Width, roundedImage.Height);
// Die Zeichenfläche des Grafikobjekts auf den Kreis beschränken
g.SetClip(path);
// Das Originalbild im Kreis zeichnen
g.DrawImage(playerImage, 0, 0, playerImage.Width, playerImage.Height);
}

e.Graphics.DrawImage(roundedImage, spieler);
```