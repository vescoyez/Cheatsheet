# CSS Cheatsheet

## Counter

```css
body {
  counter-reset: counter-name;
}

h3::before {
  counter-increment: counter-name;
  content: counter(counter-name);
}
```
