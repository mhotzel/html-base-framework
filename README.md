# html-base-framework
HTML-Basisframework mit einfachem CSS für meine eigenen Zwecke

## 1. Die Anatomie der Seite (HTML-Struktur)

Die Seite ist in vier Hauptebenen unterteilt. Achte beim Hinzufügen von neuem Code darauf, dass die div-Container sauber geschlossen werden.

- `header`: Für das Logo und den großen Titel.
- `.action-bar`: Die graue Leiste für schnelle Aktionen (Login/Logout) und Status-Badges.

- `#content-wrapper`: Das Herzstück. Es enthält:
- `nav`: Die Sidebar links (auf Desktop feststehend).
- `main`: Hier fließen deine Daten hinein. Nur dieser Bereich scrollt!
- `footer`: Für rechtliche Hinweise oder den Systemstatus.

## 2. Die wichtigsten Komponenten (CSS-Klassen)

Nutze diese Klassen im main-Bereich, um Inhalte einheitlich zu gestalten.

- **A. Die Inhalts-Karten (.card)**

Um Informationen sauber zu gruppieren (wie in Pico.css), nutzt du dieses Muster:

```html
<div class="card">
    <header class="card-header">Überschrift</header>
    <div class="card-content">Dein Inhalt hier...</div>
    <footer class="card-footer">Optionale Fußzeile</footer>
</div>
```

Die Klasse `section` funktioniert analog zu `card`, aber ohne Rahmen.
Die Klasse `section-content` rückt den Inhalt ein wie in `card`.

<div class="section">
    <header class="card-header">Überschrift</header>
    <div class="card-content">Dein Inhalt hier...</div>
    <footer class="card-footer">Optionale Fußzeile</footer>
</div>

Mittels `card-grid` können `card`-Elemente in eine Flexbox gepackt werden, um sie horizontal nebeneinander zu platzieren.
Wird die Breite zu schmal, werden sie untereinander platziert.

Die Klasse `card-small` macht eine schmale Card, derzeit ca. 400px breit. Karten innerhalb in `card-grid` sind von sich aus schon schmaler, das mach das Grid.
Die Klasse `card-center` macht ebenfalls eine schmale Card, zentriert sie aber zusätzlich.

Mit `section` gestylte Elemente können ebenso schmal gemacht oder zentriert werden, wenn sie als zweite Klasse `card-small` oder entsprechend `card-center` bekommen.

- **B. Das Button-System**

Wir unterscheiden zwischen dem großen Formular-Button und Aktions-Buttons:

- Speichern: `<button class="btn-submit">` (nutzt 100% Breite).

- Funktionen: Nutze `class="btn"` kombiniert mit:

- `.btn-primary` (Dunkelblau)
- `.btn-secondary` (Grau)
- `.btn-outline` (Weiß mit grünem Rand)

- Sollen mehrere Buttons nebeneinander in einer Zeile sein und die gleiche Breite haben: `.button-row`

- **C. Status-Meldungen (.status-box)**

Für Rückmeldungen an den Nutzer:

- `.info` (Blau)
- `.warning` (Gelb)
- `.error` (Rot)

## 3. Daten und Tabellen

**Die "perfekte" Zahlenausrichtung**

Damit Kommas in Tabellen exakt untereinander stehen, haben wir einen speziellen Mechanismus gebaut. Nutze in der Tabelle für Mengen oder Preise immer diese Struktur:

```html
<td class="col-number"><span>123,45</span> kg</td>
```

Das CSS sorgt durch `font-variant-numeric: tabular-nums` dafür, dass jede Ziffer die gleiche Breite hat (wie bei einer Schreibmaschine).

## 4. Menü

- Einfach in der nav ein neues `<li><a href="#">...</a></li>` hinzufügen.

## 5. Formulare - Zusatz-Features

Um Formulare mehrspaltig zu machen, müssen die Felder, die in einer Reihe sind, in ein Element mit der Klasse `form-row` eingebettet werden:

```html
<div class="form-row">
	<div class="form-group">
	    <label for="produkt">Produktname</label>
        <input type="text" id="produkt" placeholder="z. B. Äpfel Schlichten">
    </div>
	<div class="form-group">
	    <label for="menge">Menge (kg)</label>
	    <input type="number" id="menge" placeholder="0.00">
    </div>
</div>
```

Um einen Button direkt neben einem Eingabefeld zu platzieren, kann folgendes genutzt werden:

```
<div class="form-group">
    <label for="pw">Passwort</label>
    <div class="input-group">
        <input type="password" id="pw" placeholder="Passwort eingeben...">
        <button type="button" class="btn btn-outline">Anzeigen</button>
    </div>
</div>

<div class="form-group">
    <label for="user">Benutzername</label>
    <div class="input-group">
        <input type="text" id="user" placeholder="z.B. Max Mustermann">
        <button type="button" class="btn btn-primary">Prüfen</button>
    </div>
</div>
```


Die Standardbreite von Elementen ist 450px. Um die volle Breite nutzen zu können, kann die CSS-Klasse `full-width` beim Element gesetzt werden.

## 6. Mobile Ansicht

Das System ist "Responsive". Das bedeutet:

- auf dem *Desktop* ist die Sidebar links und der Content rechts.
- Auf dem *Smartphone* wandert die Navigation nach oben und die Buttons werden automatisch auf 100% Breite gestreckt, damit man sie mit dem Daumen besser trifft.

In der style.css unter `@media (max-width: 768px)` sind folgende Regeln aktiv:

- Die Sidebar rutscht über den Content.
- Das Logo im Header wird ausgeblendet (Platzsparend).
- Buttons werden auf 100% Breite gestreckt (Touch-optimiert).
- Der globale Scroll-Stopp wird aufgehoben.
