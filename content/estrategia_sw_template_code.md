---
title: Service workers | Estrategias para mostrar
next: librerias.md
prev: estrategia_sw_template.md
---
## ServiceWorker como template

```js
importScripts('templating-engine.js')

self.addEventListener('fetch', function (event) {
  var requestURL = new URL(event.request)

  event.respondWith(
    Promise.all([
      caches.match('/article-template.html').then(function (response) {
        return response.text()
      }),
      caches.match(requestURL.path + '.json').then(function (response) {
        return response.json()
      })
    ]).then(function (responses) {
      var template = responses[0]
      var data = responses[1]

      return new Response(renderTemplate(template, data), {
        headers: {
          'Content-Type': 'text/html'
        }
      })
    })
  )
})
```
