# qrcode-with-logos 

## FORKED
Original package: https://github.com/zxpsuper/qrcode-with-logos
Forked changed:
- no rollup, build with just typescript
- updated dependencies and dev deps
- updated configs
- removed redundant code and files

## Introduction

QRcode-with-logos is a tool for creating a QRcode with a logo in your object.

It depend on `qrcode` dependence and be more powerful than `qrcode`.

It can create a canvas or a image for the QRcode and even you can use the method to download the file you want.

## Usage

Install
```
npm i qrcode-with-logos
```

Import
```
import QrCodeWithLogo from 'qrcode-with-logos';
```

Write the output to a canvas on page:
```
  const canvas = document.getElementById('canvas') as HTMLCanvasElement;

  new QrCodeWithLogo({
    canvas: canvas,
    content: props.qrValue,
    width: 380,
    logo: {
      src: 'https://avatars1.githubusercontent.com/u/28730619?s=460&v=4',
    },
  });
```

Output to an image:
```
  const qrcode = new QrCodeWithLogo({
    content: 'some value, for example, a URL goes here',
    width: 380,
    logo: {
      src: 'https://avatars1.githubusercontent.com/u/28730619?s=460&v=4',
    },
  });

  qrcode
    .getImage()
    .then(() => {
      qrcode.downloadImage('myqrcode');
    });
```

## Options

### `content`(required)

Type: `String`

QR Code content.

### `width`

Type: `Number`

Default: `0`

QR Code width.

### `canvas`

Type: `DomElement`

Default: a new canvas tag

A canvas tag to show the QR code.

### `image`

Type: `DomElement`

Default: a new img tag

A img tag to show the QR code.

### `download`

Type: `Boolean`

Default: `false`

You can set the value to be true to download the file immediately.

### `downloadName`

Type: `String`

Default: `qr-code.png`

Set the download file name, should be used with the `download` property.

### `nodeQrCodeOptions`

Type: `Object`

`nodeQrCodeOptions.margin`:

Type `Number` -- qrcode margin

`nodeQrCodeOptions.errorCorrectionLevel`:

Type `String`-- qrcode errorCorrectionLevel, such as "M", "Q", "H"

`nodeQrCodeOptions.scale`:

Type `Number`-- qrcode scale

`nodeQrCodeOptions.color`:

Type `Object`-- qrcode color

`nodeQrCodeOptions.color.dark`:

Type `String`-- qrcode color value of dark

`nodeQrCodeOptions.color.light`:

Type `String`-- qrcode color value of light

### `text`

Type: `Object` (optional)

`text.text` (required)

Type `String` -- The text to add to the QR code

`text.font` (optional)

Type `String` -- The font to use, defaults to '16px Arial'

`text.colorHexCode` (optional)

Type `String` -- The font colour to use, defaults to '#000000'

`text.positionOffset` (optional)

Type `Number` -- The offset position relative to the bottom, defaults to 10

### `logo`

Type: `Object`

`logo.src`(required):

Type `String`-- logo url or logo module

`logo.logoRadius`:

Type `Number` -- Default: `0`

`logo.logoSize`:

Type `Number` -- Default: `0.15`, is the scale to qrcode

`logo.borderRadius`:

Type `Number` -- Default: `8`

`logo.borderColor`:

Type `String` -- Default: `"#ffffff"`

`logo.borderSize`:

Type `Number` -- Default: `0.05` , is the scale to qrcode

`logo.bgColor`:

Type `String` -- Default: `"#ffffff"`, the logo background color

`logo.crossOrigin`:

Type `String` -- Default: `"Anonymous"`

## Methods

`downloadImage(name: string)` ———— Return `Promise`, set the filename and download the image.

```js
let qrcode = new QrCodeWithLogo({
  canvas: document.getElementById("canvas"),
  content: "https://github.com/zxpsuper",
  width: 380,
  //   download: true,
  image: document.getElementById("image"),
  logo: {
    src: "https://avatars1.githubusercontent.com/u/28730619?s=460&v=4"
  }
});

qrcode.downloadImage("hello-world.png").then(() => {
  // do what you want to do
})
```
`getCanvas()` ———— Return `Promise<HTMLCanvasElement>`, you can use the HTMLCanvasElement to do more things with canvas.

```js
let qrcode = new QrCodeWithLogo({
  canvas: document.getElementById("canvas"),
  content: "https://github.com/zxpsuper",
  width: 380,
  //   download: true,
  image: document.getElementById("image"),
  logo: {
    src: "https://avatars1.githubusercontent.com/u/28730619?s=460&v=4"
  }
});

qrcode.getCanvas().then(canvas => {
  canvas.toDataURL()
  // or do other things with canvas
});

```

`getImage()` ———— Return `Promise<HTMLImageElement>`, you can use the HTMLImageElement to do more things with image.

```js
let qrcode = new QrCodeWithLogo({
  canvas: document.getElementById("canvas"),
  content: "https://github.com/zxpsuper",
  width: 380,
  //   download: true,
  image: document.getElementById("image"),
  logo: {
    src: "https://avatars1.githubusercontent.com/u/28730619?s=460&v=4"
  }
});

qrcode.getImage().then(image => {
  // or do other things with image
});

```

## Example

```html
<canvas id="canvas"></canvas> <img src="" alt="" id="image" />
<img id="image" alt="">
```

```js
import QrCodeWithLogo from "qrcode-with-logos";
let qrcode = new QrCodeWithLogo({
  canvas: document.getElementById("canvas"),
  content: "https://github.com/zxpsuper",
  width: 380,
  //   download: true,
  image: document.getElementById("image"),
  logo: {
    src: "https://avatars1.githubusercontent.com/u/28730619?s=460&v=4"
  }
});

qrcode.downloadImage("qrcode.png");
```

## Ecosystem

| Project  | Status                             | Description                   |
| -------- | ---------------------------------- | ----------------------------- |
| [qrcode] | [![qrcode-status]][qrcode-package] | QR code/2d barcode generator. |

[qrcode]: https://github.com/soldair/node-qrcode
[qrcode-status]: https://img.shields.io/npm/v/qrcode.svg
[qrcode-package]: https://npmjs.com/package/qrcode

## Questions or advise

If you have some question or advise, you can send me a E-mail(zxpscau@163.com) or open an [issue](https://github.com/zxpsuper/qrcode-with-logos/issues/new).
