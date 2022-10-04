# JS

## Element
### [Element.classList](https://developer.mozilla.org/ko/docs/Web/API/Element/classList)
```html
// replace class "foo" with class "bar"
div.classList.replace("foo", "bar");

// find out class name "foo"
div.classList.contains("foo");
```

## URL
### [URL.searchParams](https://developer.mozilla.org/ko/docs/Web/API/URL/searchParams)
```html
const urlParams = new URL(location.href).searchParams;
const name = urlParams.get('name');
```