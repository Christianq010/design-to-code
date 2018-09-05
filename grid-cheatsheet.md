# CSS Grid cheatsheet

## Layouts with normal fractions
_Notes: -1 spans full width of all columns_

```html
<div class="container">
    <div class="header">HEADER</div>
    <div class="menu">MENU</div>
    <div class="content">CONTENT</div>
    <div class="footer">FOOTER</div>
</div>
```

```css
.container {
    grid-gap: 3px;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: 150px auto 150px;
}
.header {
    grid-row: 1/2;
    grid-column: 4/-1; 
}
 .menu {
    grid-row: 1/3;
    grid-column: 1/4;
}
 .content {
    grid-row: 2/3;
    grid-column: 4/-1;
}
 .footer {
    grid-row: 3/3;
    grid-column: 1/-1;
} 
```
## Layouts with grid area

```html
<div class="container">
    <div class="header">HEADER</div>
    <div class="menu">MENU</div>
    <div class="content">CONTENT</div>
    <div class="footer">FOOTER</div>
</div>
```

```css
.container {
    height: 100%;
    display: grid;
    grid-gap: 3px;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: 150px auto 150px;
    grid-template-areas: 
        "m m m h h h h h h h h h"
        "m m m c c c c c c c c c"
        ". f f f f f f f f f f .";
}
.header {
    grid-area: h; 
}
.menu {
    grid-area: m;
}
.content {
    grid-area: c;
}
.footer {
    grid-area: f;
}
```

## Responsive layouts with minmax
_Note:Each column will always be a minimum of 250px, if >250px each `div` will increase in size and it will distribute the remaining space eqally._
* Each `div` without explicit defined width will always be `250px`.

```html
<div class="container">
    <div class="1">1</div>
    <div class="2">2</div>
    <div class="3">3</div>
    <div class="4">4</div>
    <div class="5">5</div>
    <div class="6">6</div>
    <div class="7">7</div>
    <div class="8">8</div>
    <div class="9">9</div>
</div>
```

```css
.container {
    display: grid;
    grid-gap: 5px;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-template-rows: repeat(3, 250px);
    grid-auto-rows: 250px;
}
```