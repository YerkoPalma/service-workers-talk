---
title: Service workers | Estrategias para guardar
next: estrategias_para_mostrar.md
prev: estrategia_sync.md
---
## BackgroundSync

```js
self.addEventListener('sync', function (event) {
  if (event.id == 'update-leaderboard') {
    event.waitUntil(
      caches.open('mygame-dynamic').then(function (cache) {
        return cache.add('/leaderboard.json')
      })
    )
  }
})
```
