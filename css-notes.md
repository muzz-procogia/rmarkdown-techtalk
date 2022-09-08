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
```
.inverse {
  background-color: #272822;
  color: #d6d6d6;
  text-shadow: 0 0 20px #333;
}
.inverse h1, .inverse h2, .inverse h3 {
  color: #f3f3f3;
}
```
#### note you can also create your own classes