# Einführung in p5

## Links

- [p5js.org](https://p5js.org)
- [p5 Editor](https://editor.p5js.org/)
- [p5 Reference](https://p5js.org/reference/)
- [openprocessing.org](https://openprocessing.org/) (Beispiele)

## Auf deinem Computer mit p5 arbeiten

Wenn deine Programme etwas länger werden, ist es besser, auf deinem eigenen Rechner zu coden als auf der p5-Website.

### Texteditor Software

Zur Programmierung deiner Scripts brauchst du einen Texteditor. Das ist eine Software, die speziell zum Schreiben in Programmiersprachen gemacht ist. Sie zeichnet z.B. Text farbig aus (‘Syntax Highlighting’) und macht ihn einfacher lesbar. Dazu kommen meist noch eine ganze Palette weiterer Werkzeuge.

Wir empfehlen [Visual Studio Code](https://code.visualstudio.com/), weil es darin u.a. ein eingebautes Terminal und eine Anbindung an *GitHub* gibt. Bei Bedarf gibt es viele weitere [Plugins](https://marketplace.visualstudio.com/), die du installieren kannst.

### Dateien

Folgende Dateien brauchst du, um mit p5 zu coden.

- `index.html` Eine HTML-Datei
- `sketch.js` Dein Programm, im Processing-Jargon ‘sketch’
- `p5.min.js` Die p5-Bibliothek (Alternativ: [Link auf CDN](https://cdn.jsdelivr.net/npm/p5@1.4.0/lib/p5.min.js))

#### Die p5 Library

Eine Library ist eine JavaScript-Datei, in der Funktionen und Variablen definiert werden, die komplexe Programmier-Tasks vereinfachen.

Damit du die Funktionen und Variablen von p5 nutzen kannst, musst du in der Datei `index.html` einen Link zur p5-Library herstellen.

Als Ziel des Links gibt es zwei Möglichkeiten: Die heruntergeladene Library oder ein CDN (‘content delivery network’), d.h. eine Online-Kopie der Library.

Link auf die heruntergeladene Library, im gleichen Ordner wie `index.html` und `sketch.js`: `<script src="p5.min.js"></script>`

Link auf CDN: `<script src="https://cdn.jsdelivr.net/npm/p5@1.4.0/lib/p5.min.js"></script>`

#### sketch.js

In p5 wird dein Programm ‘Sketch’ (Skizze) genannt. Die wichtigsten Bestandteile sind die Funktionen `setup()` und `draw()`.

```
function setup() {
  createCanvas(300, 400)
}

function draw() {
  background(100)
}
```

#### Die HTML-Datei

Die Datei sollte immer `index.html` heissen. Dadurch wird sie von einem Web-Server automatisch angezeigt, wenn es im gleichen Ordner mehrere HTML-Dateien gibt. Den Inhalt kannst du hier copy-pasten:

```
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <link rel="shortcut icon" href="#">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Titel</title>
</head>
<body>
  
  <script src="p5/p5.min.js"></script>
  <script src="sketch.js"></script>
</body>
</html>
```

## Nützliche Bausteine

Hier findest du die wichtigsten Code-Bausteine zum copy-pasten.

### Variablen

```
let foo = 0
```

### In die Konsole schreiben

```
console.log("Hello World")

console.log("3 + 4")

console.log(3 + 4)
```

### if / else

```
if (foo < 0.5) {
  console.log("salut")
} else {
  console.log("ciao")
}
```

### Loops

```
for (let i = 0; i < 10; i += 1) {
  console.log(i)
}
```

#### Verschachtelter Loop zur Positionierung im Raster

```
let cols = 10
let rows = 10

for (let row = 0; row < rows; row += 1) {
  for (let col = 0; col < cols; col += 1) {

    push()
    translate(col * cellSize, row * cellSize)

    // ab hier bist du «in der Rasterzelle»
    rect(0, 0, cellSize, cellSize)

    pop()
  }
}
```

Die Funktion [`pull()`](https://p5js.org/reference/#/p5/push) speichert Einstellungen wie Transformationen (Nullpunkt, Rotation), Farben und Schriftgrössen, die Funktion [`pop()`](https://p5js.org/reference/#/p5/pop) stellt sie wieder her. Auf diese Weise kannst du den Nullpunkt jeweils an die untere linke Ecke jeder Rasterzelle setzen ohne dass die Verschiebung unkontrolliert wird.

### Funktionen

Funktionen sind wie Werkzeuge: Mit ihnen kannst du Code-Abschnitte bei Bedarf aufrufen.

Um eine eigene Funktion zu definieren schreibst du das Schlüsselwort `function` und den Namen, der die Funktion kriegen soll:

```
function greet(name) {
  console.log("Hello " + name)
}
```

Danach kannst du die Funktion überall in deinem Code nutzen.

```
greet("Anna") // Hello Anna
greet("Pesche") // Hello Pesche
greet("World") // Hello World
```

Du kannst eine Funktion nutzen, um z.B. eine etwas komplexere Zeichnung zu machen.

```
function complexStuff(x, y, size) {
  line(x, y, x + size, y + size)
  line(x, y+size, x + size, y)
  line(x, y+size/2, x + size, y + size/2)
  line(x + size/2, y, x + size/2, y+size)
}

function setup() {
  createCanvas(400, 400);
  for (let i = 0; i < 30; i++) {
    complexStuff(random(width), random(height), random(50))
  }
}
```

Mit dem Schlüsselwort `return` kann dir eine Funktion einen Wert zurückgeben.

```
function pythagoras(a, b) {
  return Math.sqrt(a * a + b * b)
}

console.log(pythagoras(3, 4)) // 5
```

## Dinge, die in p5 anders heissen als in DrawBot

DrawBot: `width()` und `height()`

p5: `width` und `height`

---

DrawBot: `oval(x, y, w, h)`

p5: `ellipse(x, y, w, [h])` oder `circle(x, y, d)`

---

DrawBot: `fill(None)` und `stroke(None)`

p5: `noFill()` und `noStroke`

---

DrawBot: `with savedState():`

p5: `push()` und `pop()`

---

