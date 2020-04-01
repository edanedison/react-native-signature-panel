# react-native-signature-panel

[![npm version](https://badge.fury.io/js/react-native-signature-panel.svg)](https://badge.fury.io/js/react-native-signature-panel)
[![styled with prettier](https://img.shields.io/badge/styled_with-prettier-ff69b4.svg)](https://github.com/prettier/prettier)

A React Native signature panel that captures and exports signatures to PNG, JPG or SVG. Works with Expo or Vanilla RN.

## Features

-   Works with Expo or Vanilla RN
-   Export signature as SVG, PNG or JPG
-   Customizable width, height, theming etc.

## Setup

This library is available on npm, install it with: `npm i react-native-signature-panel` or `yarn add react-native-signature-panel`.

## Dependencies

You will need to install `'react-native-svg'` and `'react-native-view-shot'`. If you are working with Expo, you should use the `'expo install'` method. If vanilla RN, then follow the usual instructions to add and link these libs.

## Usage

1.  Import react-native-signature-panel:

```javascript
import Signature from 'react-native-signature-panel';
```

2.  Use the component with its defaults

```javascript
render () {
    return (
	<Signature onFingerUp={signature => console.log(signature)}/>
    )
  }
```

## Notes

The onFingerUp method is triggered each time the user takes their finger off the pad. The 'signature' image data is then updated after a delay as defined by `onFingerUpTimeout` (default: 1000). This allows for multiple strokes to be made without it creating a load of junk images. Note that when using an image format other than SVG, there will be temp image files building up on the device. Be sure to put a process in place to remove these once you have done whatever is it you need to do with the final image. You could push the responses into an array, take the last one and process it, then use RN file system to clear the lot.

You may want to set a slight offset to the touch-point using the x or y offset props. Through personal use, I have found that a yOffset of -60 is often reqired.

## Available props

| Name              | Type             | Default   | Description                                          |
| ----------------- | ---------------- | --------- | ---------------------------------------------------- |
| height            | string or number | 300       | Height of the signature panel                        |
| width             | string or number | '100%'    | Width of the signature panel                         |
| offsetX           | number           | 0         | X offset of the finger touch point                   |
| offsetY           | number           | 0         | Y offset of the finger touch point                   |
| strokeColor       | string           | '#000'    | Stroke color                                         |
| strokeWidth       | number           | 3         | Stroke width                                         |
| imageOutputSize   | number           | 480       | Size of image output (non SVG)                       |
| imageQuality      | number           | 1         | Image output quality, 0.1 to 1                       |
| imageFormat       | string           | 'png'     | Image output type ['png', 'jpg', 'svg]               |
| outputType        | string           | 'tmpfile' | Output ['tmpFile', 'base64', 'data-uri']             |
| onFingerUp        | function         | () => {}  | Callback with the image value                        |
| onFingerUpTimeout | number           | 1000      | Timeout in ms after which the signature is processed |
| containerStyle    | object           | {}        | Style the signature container                        |

## That's it :)

Pull requests, feedbacks and suggestions are welcome! Any issues, please let me know.
