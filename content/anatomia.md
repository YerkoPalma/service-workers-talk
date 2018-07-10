---
title: Service workers | Anatomia
next: registro.md
prev: caracteristicas.md
---

```js
/* eslint-env serviceworker */                                            // Linters

var VERSION = require('./package.json').version
var URLS = process.env.FILE_LIST

self.addEventListener('install', function (e) {                           // `self` -> ServiceWorkerGlobalScope
  e.waitUntil(self.caches.open(VERSION).then(function (cache) {           // también puede ser `onfetch`
    return cache.addAll(URLS)
  }))
})

self.addEventListener('fetch', function (e) {                             // _intercepta_ un request antes de que llegue al servidor
  e.respondWith(self.caches.match(e.request).then(function (request) {
    if (request) return request
    else return self.fetch(e.request)
  }))
})

```
