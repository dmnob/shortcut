# Shortcut

Turns any https:// address into an Android home screen app that opens it in its own window, without a Chrome tab. Nothing is predefined: target, name and icon all come from the link.

## Link format

```
https://dmnob.github.io/shortcut/<slug>/?to=<url>&name=<label>&icon=<icon>
```

- `<slug>`: any path segment. Each shortcut needs its own, because Chrome treats each path as a separate app.
- `to`: the address the app opens. Only https:// is accepted.
- `name`: the label under the icon. Defaults to the target's domain.
- `icon`: an emoji (rendered as Google's Noto emoji) or the https:// address of a square image of at least 144 px. Defaults to the site's favicon.

[dmnob.github.io/shortcut](https://dmnob.github.io/shortcut/) builds the link from a form.

## Install

1. Open the link in Chrome on Android.
2. ⋮ → Add to Home screen → **Install**.

The installed app redirects straight to the target. In a normal tab, the page shows a preview and the install steps instead.

## How it works

- `index.html` is the form that builds links.
- `404.html` is the shortcut page. GitHub Pages serves it for every path that is not a file, which gives each shortcut its own path and scope.
- The web app manifest is generated in the browser from the link's parameters and attached as a `data:` URL.
- After installation the name and icon are fixed. To change them, remove the app and install it again.
