---
title: Service workers | Estrategias para mostrar
next: estrategia_sw_template.md
prev: estrategia_cache_red.md
---
## Cache primero, sino red

```js
self.addEventListener('fetch', function (event) {
  event.respondWith(
    caches.match(event.request).then(function (response) {
      return response || fetch(event.request)
    })
  )
})
```
