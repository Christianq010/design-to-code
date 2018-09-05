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