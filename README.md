# cordova-plugin-idfa

Cordova plugin to get Advertising ID (IDFA or AAID)

## Installation

    ```cordova plugin add lycwed-cordova-plugin-idfa2 --save```

Plugin depends on [cordova-support-google-services](https://github.com/chemerisuk/cordova-support-google-services) for setting up google services properly. Please read the [README](https://github.com/chemerisuk/cordova-support-google-services/blob/master/README.md) carefully in order to avoid common issues with a project configuration.

## Supported Platforms

- iOS
- Android

## Methods

Every method returns a promise that fulfills when a call was successful.

### getInfo()

Returns advertising id with `limitAdTracking` flag. On iOS use `idfa` property, on Android use `aaid`.

```js

cordova.plugins.idfa.getInfo().then(function(info) {
    if (!info.limitAdTracking) {
        console.log(info.idfa || info.aaid);
    }
});

```

Example of usage with Ionic 3:

```ts

import { Injectable } from "@angular/core";

declare var Idfa;

@Injectable()
export class YourClassName {
    public getIdfa(): Promise<> {
        return new Promise((resolve, reject) => {
            Idfa.getInfo().then((info) => {
                if (!info.limitAdTracking) {
                    console.log(info.idfa || info.aaid);
                    resolve(info.idfa || info.aaid);
                } else {
                    reject();
                }
            });
        });
    }
}

```
