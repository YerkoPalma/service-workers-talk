---
title: Registrando un service worker
---

```js
if ('serviceWorker' in navigator) {                                                         // verificación de compatibilidad
  window.addEventListener('load', function () {
    navigator.serviceWorker.register('/sw.js').then(function (registration) {               // registro mediante promesas
      console.log('ServiceWorker registration successful with scope: ', registration.scope)
    }).catch(function (err) {      
      console.log('ServiceWorker registration failed: ', err)
    })
  })
}
```
