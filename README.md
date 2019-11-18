### 前言

```
纯前端实现的浏览器指纹采集器，通过获取浏览器中所有能获取到的信息(部分通过base64转成String)，最后生成出md5，用于该用户在该设备上的唯一标识码，官方宣称准确度高达99.5%
```

### 用法

```js
Fingerprint2.get(function (components) {
  //异步采集回调--
  var murmur = Fingerprint2.x64hash128(components.map(function (pair) {
    return pair.value
  }).join(), 31)
  //murmur 就是我们想要的生成设备的唯一标识ID.
})
```

### 采集依据
--大概是利用navatior里的参数,canvas绘制拿base64,设备的系统语言,字体,一些device的参数,结合hash的md5算法,......  
这里不一一解释了,在fingerprint2.js里面 你会发现这些关键参数
```js
var components = [
  { key: "userAgent", getData: UserAgent },
  { key: "webdriver", getData: webdriver },
  { key: "language", getData: languageKey },
  { key: "colorDepth", getData: colorDepthKey },
  { key: "deviceMemory", getData: deviceMemoryKey },
  { key: "pixelRatio", getData: pixelRatioKey },
  { key: "hardwareConcurrency", getData: hardwareConcurrencyKey },
  { key: "screenResolution", getData: screenResolutionKey },
  { key: "availableScreenResolution", getData: availableScreenResolutionKey },
  { key: "timezoneOffset", getData: timezoneOffset },
  { key: "timezone", getData: timezone },
  { key: "sessionStorage", getData: sessionStorageKey },
  { key: "localStorage", getData: localStorageKey },
  { key: "indexedDb", getData: indexedDbKey },
  { key: "addBehavior", getData: addBehaviorKey },
  { key: "openDatabase", getData: openDatabaseKey },
  { key: "cpuClass", getData: cpuClassKey },
  { key: "platform", getData: platformKey },
  { key: "doNotTrack", getData: doNotTrackKey },
  { key: "plugins", getData: pluginsComponent },
  { key: "canvas", getData: canvasKey },
  { key: "webgl", getData: webglKey },
  { key: "webglVendorAndRenderer", getData: webglVendorAndRendererKey },
  { key: "adBlock", getData: adBlockKey },
  { key: "hasLiedLanguages", getData: hasLiedLanguagesKey },
  { key: "hasLiedResolution", getData: hasLiedResolutionKey },
  { key: "hasLiedOs", getData: hasLiedOsKey },
  { key: "hasLiedBrowser", getData: hasLiedBrowserKey },
  { key: "touchSupport", getData: touchSupportKey },
  { key: "fonts", getData: jsFontsKey, pauseBefore: true },
  { key: "fontsFlash", getData: flashFontsKey, pauseBefore: true },
  { key: "audio", getData: audioKey },
  { key: "enumerateDevices", getData: enumerateDevicesKey }
];
```


### 最后
```
有待测试……
```
(引自fingerprint2.js官方)[https://github.com/Valve/fingerprintjs2]
