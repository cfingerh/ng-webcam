# ng-webcam

ngWebcam is an AngularJS directive for capturing images from your computer's camera, and delivering then to you as JPEG 
 or PNG [Data URIs](https://en.wikipedia.org/wiki/Data_URI_scheme). The images can then be displayed in your web page, render 
 into a canvas or submited to your server. ngWebcam uses [WebcamJS](https://github.com/jhuckaby/webcamjs) to provide the 
 core functionality.
 
## Browser suport
 
ngWebcam suports the same browsers supported by WebcamJS. 


## Live exemple

To see live exemple, go to the [sample page](http://www.google.com)

## Instalation

#### Using [Bower](http://bower.io)

```bash
bower install ng-webcam
```

## Usage

### Import files scripts

ngWebcam uses WebcamJS to work properly so you need to add the script in your main file, don't forget to load the directive file:

```html
<script src"/path/to/webcam.js"></script>
<script src"/path/to/ng-webcam.js"></script>
```

### Add the module as dependency

Simply add the module as dependency to your main application module likes this:
```javascript
angular.module("app", ["ngWebcam"]);
```

### The directive

```html
<ng-webcam 
    config="vm.config"
    on-error="vm.onError(err)"
    on-load="vm.onLoad()"
    on-live="vm.onLive()"
    on-capturing="vm.onCapturing(src, progress)"
    on-complete="vm.onComplete(src, progress)">
</ng-webcam>
```

### Options

ng-webcam comes with lots of options to simplify tour development:

* `on-error` _function_ Callback function for error. Fires when the WebcamJS library erro occurs 
(your callback function is passed an error string)
* `on-capture-complete` _function_ Callback function for capture complete action. Fires when the capture completes
(your callback function is passed an array string (_data_uri) in `src` parameter and an number (_progress) in `progress` 
parameter)
* `on-load` _function_ Callback function for load action camera. Fires when the WebcamJS library finisheds loading
* `on-live` _function_ Callback function for live action camera. Fires when the user's camera goes live - this will only
happen after the user allows access to their camera
* `on-capture-progress` _function_ Callback function for each capturing image with progress. Fires repeatedly while an capturing
progress (your callback function is passed an string (_data_uri) in `src` parameter and an number (_progress) in `progress`
parameter)
* `config` _object_ Config options for init params in WebcamJS e directive | _optional
    - `viewerWidth` _number_ Width of live camera viewer in pixels| _default to actual size of the DOM element `auto`
    - `viewerHeight` _number_ Height of live camera viewer in pixels| _default to actual size of the DOM element `auto`
    - `outputWidth` _number_ Width of captured snapshot image in pixels | _default 320
    - `outputHeight` _number_ Height of captured snapshot image in pixels | _default 240
    - `delay` _number_ Number of seconds to wait and display before getting snapshot | _default 0
    - `shots` _number_ Number of shots captured images | _default 1
    - `shutterUrl` _string_ Shutter sound's url to play when taking snapshot | _optional
    - `flahFallbackUrl` _string_ Url of the Adobe Flash player to enable the fallback and crossbrowser modes, _default based on `navigator.getUserMedia`

### Working example

A working example is available in the `test` folder. Make sure to install bower and node dependencies:

```bash
npm install && bower install
```

Then start the node server, it will ne accessible on `http://0.0.0.0:3000`

```bash
node server.js
```

## License

The MIT License (MIT)

Copyright (c) 2015 Weber Amaral

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARR