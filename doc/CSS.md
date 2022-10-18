# CSS

## CSSPageRule
### [@page](https://developer.mozilla.org/en-US/docs/Web/CSS/@page)
```html
<style>
@page a4sheet { size: 21.0cm 29.7cm }
.a4 { page: a4sheet; page-break-after: always }
</style>
```
+ You can only change the margins, orphans, widows, and page breaks of the document. Attempts to change any other CSS properties will be ignored.
+ pseudo-code
  + :blank, :first, :left, :right
+ <span style="color:red">Safari, Firefox doesn't work</span>
+ 
