# Chrome dev tools

## Log DOM element as object

```javascript
console.dir(document);
```

## Log duration

```javascript
console.time('My time');
console.log('Do something here');
console.timeEnd('My time');
```

## Log events

```javascript
monitorEvents(document.querySelector('#myDomElement'), 'mouse');
```

Event types:

- `mouse`
- `key`
- `touch`
- `control`

## Access dom element in console

1. inspect element
2. type `$0` in the console
