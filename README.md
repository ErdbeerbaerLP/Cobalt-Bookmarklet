# Cobalt-Bookmarklet
Small bookmarklets for Cobalt, a simple downloader for social media sites (including youtube)

## Installation
To install any of those, just select them and drag-and-drop into your bookmarks, or copy paste it into there


### Open cobalt in new tab, url prefilled
```js
javascript:(function(){window.open("https://cobalt.tools/?u=%22+window.location.href,%20%27_blank%27).focus();})();
```

### Open cobalt in current tab, url prefilled
```js
javascript:(function(){window.location.href=("https://cobalt.tools/?u="+window.location.href)})();
```

### Direct Download using default settings
This one is a bit more advanced. **Does NOT work everywhere**

Tested:
- Youtube - Working
- Reddit - Not Working
- Twitter - Not working
- Soundcloud - Working


```js
javascript:try{fetch("https://api.cobalt.tools/api/json",{method:"POST",body:JSON.stringify({url:window.location.href}),headers:{Accept:"application/json","Content-type":"application/json"}}).then(t=>t.json()).then(t=>{"undefined"!==t.url&&(window.location.href=t.url)}).catch(t=>alert(t))}catch(t){alert(t)}
```

Readable code:
```js
try {
    fetch("https://api.cobalt.tools/api/json", {
            method: "POST",
            body: JSON.stringify({
                url: window.location.href
            }),
            headers: {
                "Accept": "application/json",
                "Content-type": "application/json"
            }
        })
        .then(response => response.json())
        .then(data => {
            if (data.url !== 'undefined') window.location.href = data.url
        }).catch(err => alert(err));
} catch (error) {
    alert(error);
}
```
