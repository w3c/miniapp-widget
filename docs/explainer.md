# MiniApp Widget Requirements explainer

> Note: This document serves as a supplementary explanation of the [MiniApp Widget Requirements](https://w3c.github.io/miniapp-widget/req/) note. If there is any inconsistency with the note, you should consider the note to be authoritative.

## Authors
Chen Canfeng (Xiaomi)  
Zhou Bingqing (Xiaomi)  
Chen Yinli (Xiaomi)

## What is this?
The MiniApp Widget is a special form of MiniApp Page. Same as a page, a widget runs in a host environment that is called the User Agent. Unlike a page, a widget can occupy a certain area instead of the entire screen. The Widget Requirements document describes the initial design considerations for developing a MiniApp Widget. The detailed Widget specification will be described in another document called Widget Spec.

## Why should we care?
As the MiniApp Widget is an integral part of MiniApp, the other relevant parts are described in other related MiniApp specification or note documents. This document mainly describes the specific requirements that need to be considered when defining the MiniApp Widget Specification as well as other dependencies.

## Key requirements
The following parts are covered in the MiniApp Widget Requirements document:
- Main use cases of widget: some widget example scenarios are described
- User Agent: some potential dependencies of the widget running environment are described
- Changes of MiniApp basic features in widget scenarios: potential changes and new requirement  brought by widget, including Addressing, Package, Manifest, Lifecycle, API, UI Components, etc
- New features of widget: requirement of communication between MiniApp and MiniApp Widget is described

## Sample code
### Addressing (URL)
```
miniapp://foo;version=1.0.1-trial@example.com:8080/widgets/index?k=v#bar
```

### Packaging
```
|___manifest.json
|___app.js
|___app.css
|___pages/
|       |___page1.js
|       |___page1.html
|       |___page1.css
|___widgets/
|       |___widget1.js
|       |___widget1.html
|       |___widget1.css
|___common/
|       |___componentA.js
|       |___componentA.html
|       |___componentA.css
|       |___example.png
|___i18n/
        |___zh-Hans.json
        |___en-US.json
```

### Miniapp widget manifest config
```json
{
    "widgets": [
        {
            "name": "widget",
            "path": "widgets/index/index",
            "min_platform_version": "1.0.0",
            "size": {
                "width": 100,
                "height": 100
            }
        }
    ]
}
```

### MiniApp widget lifecycle
```js
Widget({
  onLoad(query) {
    // MiniApp widget loading is completed
  },
  onShow() {
    // MiniApp widget switches to be running in foreground from background
  },
  onReady() {
    // MiniApp widget first rendering is completed
  },
  onHide() {
    // MiniApp widget switches to be running from foreground to background
  },
  onUnload() {
    // MiniApp widget is destroyed
  },
});
```
