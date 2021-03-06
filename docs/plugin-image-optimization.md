---
id: plugin-image-optimization
title: Image Optimization
sidebar_label: Image Optimization
---

Optimize output images in this boilerplate using this plugin.

This plugin basically adds image-webpack-loader to current configuration.

## Installation

```bash
$ npm i @pawjs/image-optimizer --save-dev
```

## webpack.js

Edit/Create `/src/webpack.js`

```javascript
import ImageOptimizer from "@pawjs/image-optmizer/webpack";

// ... other imports if any


export default class ProjectWebpack {
  constructor({addPlugin}) {

    // Production is default supported env
    const optimizerOptions = {
      supportedEnv: [
        "production"
      ],
      // You can add direct options of image-webpack-loader if you need to   
      // config: {
      //  mozjpeg: {
      //    progressive: true,
      //    quality: 65
      //  },
      //  // optipng.enabled: false will disable optipng
      //  optipng: {
      //    enabled: false,
      //  },
      //  pngquant: {
      //    quality: '65-90',
      //    speed: 4
      //  },
      //  gifsicle: {
      //    interlaced: false,
      //  },
      //  // the webp option will enable WEBP
      //  webp: {
      //    quality: 75
      //  }
      //},
      // Default config used
      configLabel: "MEDIUM_QUALITY"
    };
    addPlugin(new ImageOptimizer(optimizerOptions));
    // ...
  }
}
```

## Config Labels

We have predefined configurations labels for your usage.

#### MAX_QUALITY

This configuration gives max quality output but does no lossy compression.  
The equivalent configuration for this is as below:

```json
{
  "mozjpeg": {
    "progressive": true,
    "quality": 100
  },
  "optipng": {
    "enabled": true
  },
  "pngquant": {
    "quality": "95-100",
    "speed": 2
  },
  "gifsicle": {
    "interlaced": false
  },
  "webp": {
    "quality": 100
  }
}
```

#### MEDIUM_QUALITY

The equivalent configuration for this is as below:

```json
{
  "mozjpeg": {
    "progressive": true,
    "quality": 70
  },
  "optipng": {
    "enabled": true
  },
  "pngquant": {
    "quality": "65-90",
    "speed": 4
  },
  "gifsicle": {
    "interlaced": false
  },
  "webp": {
    "quality": 80
  }
}
```

#### MIN_QUALITY

The equivalent configuration for this is as below:

```json
{
  "mozjpeg": {
    "progressive": true,
    "quality": 55
  },
  "optipng": {
    "enabled": false
  },
  "pngquant": {
    "quality": "45-65",
    "speed": 10
  },
  "gifsicle": {
    "interlaced": false
  },
  "webp": {
    "quality": 65
  }
}
```


if `config` option is provided, `configLabel` is ignored

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-7586505628408924"
     data-ad-slot="5652642939"
     data-ad-format="auto"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>