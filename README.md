Please refer original [readme.md](https://github.com/electron-userland/electron-spellchecker/blob/master/README.md) for base documentation.

---

**Changes done in this fork**

1. Modified <code>attachToInput</code> api, so that you can manually initialize spellcheck event listening over a target parent dom element. This was done so that a embedded iframe's document body can also be spellchecked (some richtext-editors still use iframe).

Code sample:

```javascript
// ...
let iframeDocumentBody = null;

try {
  iframeDocumentBody = document.body.querySelectorAll("iframe")[0].contentWindow.document.body;
} catch (err) {}

if (iframeDocumentBody) {
  spellcheckHandler.attachToInput(null, {
    targetElement: iframeDocumentBody
  });
}
// ...
```
