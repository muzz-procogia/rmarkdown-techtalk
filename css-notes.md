# rmarkdown talk
## css class names 

### hover over for tile overview:
```{css}
.remark__tile-view__tile:hover {
    /* background: #993d70; */
    background: #44bc96;
    opacity: 1;
}
```
### current selected for tile overview
```{css}
.remark__tile-view__tile--current {
    background: #ffd863;
    border: 5px solid #ffd863;
    margin: calc(0.5em - 5px);
    border-radius: 0;
}
```

### creating a black slide (default is white with black text)
```{css}
.inverse {
  background-color: #272822;
  color: #d6d6d6;
  text-shadow: 0 0 20px #333;
}
.inverse h1, .inverse h2, .inverse h3 {
  color: #f3f3f3;
}
```

### recoloring and resizing hr
```{css}
hr {
    margin-top: 20px;
    margin-bottom: 20px;
    border: 0;
    border-top: 12px solid #D6D3F0;
}
```

### the hover-over for code snippets

```{css}
.remark-code-line:hover:before {
    content: "\25B6";
    color: red;
    position: absolute;
    transform: translateX(-1.2em);
    animation: hover 0.66s alternate 8 cubic-bezier(0.445, 0.05, 0.55, 0.95);
}
```

### change the line width between code chunks, not needed for presentation 

```{css}
pre {
    display: block;
    font-family: monospace;
    white-space: pre;
    margin: 1em 0px;
    margin-top: 1em;
    margin-right: 0px;
    margin-bottom: 1em;
    margin-left: 0px;
}
```


#### note you can also create your own classes