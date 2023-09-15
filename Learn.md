# How it works?
You can create the hover effect by writing the following JavaScript code:
```js
// script.js

const container = document.querySelector('.container');
const fixedObject = document.querySelector('.fixed-object');

container.addEventListener('mousemove', (e) => {
    const { clientX, clientY } = e;
    const { top, left, width, height } = container.getBoundingClientRect();

    const centerX = left + width / 2;
    const centerY = top + height / 2;

    const distanceX = clientX - centerX;
    const distanceY = clientY - centerY;

    const maxDistance = Math.max(width, height) / 2;

    const proximity = Math.min(1, Math.sqrt((distanceX ** 2 + distanceY ** 2) / (maxDistance ** 2)));

    // Adjust the object's behavior based on proximity
    const scale = 1 + proximity * 0.5;
    const backgroundColor = `rgb(52, 152, 219, ${proximity})`;

    fixedObject.style.transform = `translate(-50%, -50%) scale(${scale})`;
    fixedObject.style.backgroundColor = backgroundColor;
});
```
