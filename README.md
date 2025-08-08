```javascript
(async () => {
  const result = await Promise
  .all([1,2,3]
    .map(e => new Promise(res => setTimeout(() => res(e), 2000)))
  )
  .then((values) => (
    values.reduce((p, c) => p + c, 0)
  ));

  console.log(result);
})();
```
