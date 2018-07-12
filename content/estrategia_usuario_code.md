---
title: Service workers | Estrategias para guardar
next: estrategia_sync.md
prev: estrategia_usuario.md
---
## Interacción del usuario

```js
document.querySelector('.cache-article').addEventListener('click', function(event) {
  event.preventDefault()

  var id = this.dataset.articleId
  caches.open('mysite-article-' + id).then(function (cache) {
    fetch('/get-article-urls?id=' + id).then(function (response) {
      // /get-article-urls returns a JSON-encoded array of
      // resource URLs that a given article depends on
      return response.json()
    }).then(function (urls) {
      cache.addAll(urls)
    })
  })
})
```

