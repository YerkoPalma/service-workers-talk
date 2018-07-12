---
title: Service workers | Estrategias para mostrar
next: estrategia_cache_red.md
prev: estrategia_cache.md
---
## Sólo cache

```js
self.addEventListener('fetch', function (event) {
  // If a match isn't found in the cache, the response
  // will look like a connection error
  event.respondWith(caches.match(event.request))
})
```
