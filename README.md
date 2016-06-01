﻿Barcode Bakery 1D
===========

Generates 1D barcode used for tracking.

## Supported 1D symbologies

* [Codabar](http://www.barcodebakery.com/en/resources/api/nodejs/codabar)
* [Code 11](http://www.barcodebakery.com/en/resources/api/nodejs/code11)
* [Code 128](http://www.barcodebakery.com/en/resources/api/nodejs/code128)
* [Code 39](http://www.barcodebakery.com/en/resources/api/nodejs/code39)
* [Code 39 Extended](http://www.barcodebakery.com/en/resources/api/nodejs/code39extended)
* [Code 93](http://www.barcodebakery.com/en/resources/api/nodejs/code93)
* [EAN-13](http://www.barcodebakery.com/en/resources/api/nodejs/ean13)
* [EAN-8](http://www.barcodebakery.com/en/resources/api/nodejs/ean8)
* [Interleaved 2 of 5](http://www.barcodebakery.com/en/resources/api/nodejs/i25)
* [ISBN](http://www.barcodebakery.com/en/resources/api/nodejs/isbn)
* [MSI](http://www.barcodebakery.com/en/resources/api/nodejs/msi)
* [Standard 2 of 5](http://www.barcodebakery.com/en/resources/api/nodejs/s25)
* [UPC-A](http://www.barcodebakery.com/en/resources/api/nodejs/upca)
* [UPC-E](http://www.barcodebakery.com/en/resources/api/nodejs/upce)
* [UPC Extension 2](http://www.barcodebakery.com/en/resources/api/nodejs/upcext2)
* [UPC Extension 5](http://www.barcodebakery.com/en/resources/api/nodejs/upcext5)
* [Custom barcode](http://www.barcodebakery.com/en/resources/api/nodejs/othercode)

## Requirements

- [node-canvas](https://github.com/Automattic/node-canvas).
- node >= 4.2.6

## Installation

```bash
$ npm install barcode-bakery-1d
```

Don't forget to follow the installation instructions for node-canvas if the installation fails.

## Example

Each barcode can be created from the `barcode-bakery-1d` package.
Each barcode has different methods that can be used to change its size, color, etc. Check the manual to get more information.

```javascript
var barcodeBakeryCommon = require('barcode-bakery-common');
var barcodeBakery1D = require('barcode-bakery-1d');
var Color = barcodeBakeryCommon.Color;
var Drawing = barcodeBakeryCommon.Drawing;
var Font = barcodeBakeryCommon.Font;

// The arguments are R, G, B for color.
var colorFront = new Color(0, 0, 0);
var colorBack = new Color(255, 255, 255);

var code = new barcodeBakery1D.Code39();
code.setScale(2); // Resolution
code.setThickness(30); // Thickness
code.setBackgroundColor(colorBack); // Color of spaces
code.setForegroundColor(colorFront); // Color of bars
code.setFont(font); // Font (or 0)
code.parse("HELLO"); // Text
```

### Save to disk
```javascript
var drawing = new Drawing(code, colorBack);
drawing.save("image.png", Drawing.IMG_FORMAT_PNG, function() {
    console.log("Done.");
});
```

### Get buffer
```javascript
var drawing = new Drawing(code, colorBack);
drawing.toBuffer(Drawing.IMG_FORMAT_PNG, function (err, buffer) {
    response.writeHead(200, { "Content-Type": "image/png" });
    response.end(buffer);
});
```

### Sync methods
Both `save` and `toBuffer` have counterparts acting synchronously: `saveSync` and `toBufferSync`.

## Complete manual
See a complete manual for each barcode on our website http://www.barcodebakery.com.

## Tests
Simply type `mocha` to run the tests.

## License

Barcode Bakery 1D for NodeJS has two possible licenses.

- Commercial License
  (a paid license, meant for commercial use)
  http://www.barcodebakery.com/en/license/2

- Creative Commons Non-Commercial No-Derivatives
  (meant for trial and non-commercial use)
  https://creativecommons.org/licenses/by-nc-nd/4.0/