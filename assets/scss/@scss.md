# @scss folder

Durch SCSS wird die Schreibweise von CSS vereinfacht und Variablen fest definiert. Hierdurch ist eine übersichtlichere Darstellung, weniger Schreibarbeit und eine einfachere Überarbeitung durch die Verwendung von Variablen gewährleistet.

**CSS:**
```css
#header {
  margin: 0;
  border: 1px solid red;
}
#header p {
  font-size: 12px;
  font-weight: bold;
  color: red;
}
#header a {
  text-decoration: none;
 | Column 2 |
```

**SCSS:** 
```css
$colorRed: red;
#header {
  margin: 0;
  border: 1px solid $colorRed;

  p {
    color: $colorRed;
    font: {
      size: 12px;
      weight: bold;
    }
  }

  a {
    text-decoration: none;
  }
}
```

