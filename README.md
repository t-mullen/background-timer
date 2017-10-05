# background-timer
Allows timeouts, intervals and animations to continue in background tabs.

Chrome and Firefox throttle timers in background tabs, but they do NOT throttle WebWorkers. This is a hack to allow timers to continue more or less normally.

Timers will use the regular methods when the tab is in focus, and switch to WebWorker timers when out of focus (with no delay).

## Install

NPM:
```shell
npm install --save background-timer
```
```javascript
const BackgroundTimer = require('background-timer')
```

Script:
```html
<script src="dist/background-timer.js">
```
```javascript
window.BackgroundTimer
```

## Examples

```javascript
  BackgroundTimer({global: true}) // override globals with this option

  window.requestAnimationFrame(function () {}, 50)
  window.setInterval(function () {}, 50)
  window.setTimeout(function () {}, 50)
  
  window.cancelAnimationFrame(id)
  window.clearInterval(id)
  window.clearTimeout(id) 
```

```javascript
  var backgroundTimer = new BackgroundTimer({global: false}) // it's cleaner to avoid globals

  backgroundTimer.requestAnimationFrame(function () {}, 50)
  backgroundTimer.setInterval(function () {}, 50)
  backgroundTimer.setTimeout(function () {}, 50)
  
  backgroundTimer.cancelAnimationFrame(id)
  backgroundTimer.clearInterval(id)
  backgroundTimer.clearTimeout(id) 
```