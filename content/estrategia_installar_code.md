---
title: Service workers | Estrategias para guardar
next: estrategia_usuario.md
prev: estrategia_installar.md
---

## Al instalar, como dependencia

```js
self.addEventListener('install', function (event) {
  event.waitUntil(
    caches.open('mysite-static-v3').then(function (cache) {
      return cache.addAll([
        '/css/whatever-v3.css',
        '/css/imgs/sprites-v6.png',
        '/css/fonts/whatever-v8.woff',
        '/js/all-min-v4.js'
        // etc
      ])
    })
  )
})
```