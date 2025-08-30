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
- https://ithelp.ithome.com.tw/m/articles/10194296
- https://mdn.github.io/dom-examples/web-workers/simple-shared-worker/
- [GoogleChromeLabs/comlink: Comlink makes WebWorkers enjoyable.](https://github.com/GoogleChromeLabs/comlink)
- https://mdn.github.io/dom-examples/web-workers/simple-web-worker/main.js
  - ```javascript
    const first = document.querySelector("#number1");
    const second = document.querySelector("#number2");
    
    const result = document.querySelector(".result");
    
    if (window.Worker) {
      const myWorker = new Worker("worker.js");
    
      [first, second].forEach((input) => {
        input.onchange = () => {
          myWorker.postMessage([first.value, second.value]);
          console.log("Message posted to worker");
        };
      });
    
      myWorker.onmessage = (e) => {
        result.textContent = e.data;
        console.log("Message received from worker");
      };
    } else {
      console.log("Your browser doesn't support web workers.");
    }
    ```
