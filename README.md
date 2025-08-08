```javascript
Promise.all([
  new Promise(res => setTimeout(() => res(1), 2000)), 
  new Promise(res => setTimeout(() => res(2), 2000)), 
  new Promise(res => setTimeout(() => res(3), 2000))
])
.then((values) => {
  console.log(values.reduce((p, c) => p + c, 0));
});
```
