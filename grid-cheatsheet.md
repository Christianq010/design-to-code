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

## Responsive layouts - image gallery
* We fix blank spaces with `grid-auto-flow: dense;` at any width.

```html
    <div class="container">
        <div><img src="img/normal1.jpg"/></div>
        <div class="vertical"><img src="img/vertical1.jpg"/></div>
        <div class="horizontal"><img src="img/horizontal1.jpg"/></div>
        <div><img src="img/normal2.jpg"/></div>
        <div><img src="img/normal3.jpg"/></div>
        <div class="big"><img src="img/big1.jpg"/></div>
        <div><img src="img/normal4.jpg"/></div>
        <div class="vertical"><img src="img/vertical2.jpg"/></div>
        <div><img src="img/normal5.jpg"/></div>
        <div class="horizontal"><img src="img/horizontal2.jpg"/></div>
        <div><img src="img/normal6.jpg"/></div>
        <div class="big"><img src="img/big2.jpg"/></div>
        <div><img src="img/normal7.jpg"/></div>
        <div class="horizontal"><img src="img/horizontal3.jpg"/></div>
        <div><img src="img/normal8.jpg"/></div>
        <div class="big"><img src="img/big3.jpg"/></div>
        <div><img src="img/normal9.jpg"/></div>
        <div class="vertical"><img src="img/vertical3.jpg"/></div>
    </div>
```

```css
.container {
    display: grid;
    grid-gap: 5px;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    grid-auto-rows: 75px;
    grid-auto-flow: dense;
}
.horizontal {
    grid-column: span 2;
}
.vertical {
    grid-row: span 2;
}
.big {
    grid-column: span 2;
    grid-row: span 2;
}
```