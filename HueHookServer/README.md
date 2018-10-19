# HueHookServer
Control your Philips Hue system with simple HTTP GET requests. POST parameters are not needed!

This server run as a *Windows Console Application*. Good for testing and playing :grin:. For continuous usage see [HueHookService](https://github.com/rmmlr/HueHook/blob/master/HueHookService), also contains in this repository.

## How to use

### Start the program

Before the first program start, a settings file must be created. You can modify the example file, found in [ExampleData/HueHookSettings.xml](https://github.com/rmmlr/HueHook/blob/master/ExampleData/HueHookSettings.xml).
The file must be in the same directory as the program and named `HueHookSettings.xml`. See next point [Settings](#Settings) for detailed informations.

After successfully initialization the programm prints the server address (ip and port).

### Settings
The program settings are stored in a xml-formated file, named `HueHookSettings.xml`.
This file have one root node `<HueHookSettings>`, which have several child nodes.

|Node               |         |Description                                                                         |
|-------------------|:-------:|------------------------------------------------------------------------------------|
|`<BridgeIp>`       |:warning:|IP address of the Philips Hue Bridge                                                |
|`<BridgeUsername>` |:warning:|authorized user on the Philips Hue Bridge*                                          |
|`<LocalServerIp>`  |         |                                                                                    |
|`<LocalServerPort>`|         |port of the HueHookServer                                                           |
|`<WhiteList>`      |:warning:|                                                                                    |
|  `<IpAddress>`    |:warning:|this node contains child nodes (`<IpAddress>`) for each IP address of allowed client|
|  `<Disable>`      |:warning:|`true` or `false` to disable the whitelist                                          |
|`<LogPath>`        |:warning:|path to the logfile                                                                 |

:warning: required setting

An example you can find under [ExampleData/HueHookSettings.xml](https://github.com/rmmlr/HueHook/blob/master/ExampleData/HueHookSettings.xml).

\* to get an new username see the [Getting Started](https://www.developers.meethue.com/documentation/getting-started) article on the *hue developer program*.


### Use the program

Call the urls described below, each url starts with the address (ip and port) and have some optional parameters:

|Description       |Name|Value      |Light             |Group             |Scene             |
|------------------|----|-----------|:----------------:|:----------------:|:----------------:|
|:warning: URL     |    |`/*.hue`   |`/light.hue`      |`/group.hue`      |`/scene.hue`      |
|:warning: ID      |id  |0 - 254    |:heavy_check_mark:|:heavy_check_mark:|:heavy_check_mark:|
|On state          |on  |0, 1       |:heavy_check_mark:|:heavy_check_mark:|:x:               |
|Hue               |hue |0 - 65535  |:heavy_check_mark:|:heavy_check_mark:|:x:               |
|Saturation        |sat |0 - 254    |:heavy_check_mark:|:heavy_check_mark:|:x:               |
|Brightness        |bri |0 - 254    |:heavy_check_mark:|:heavy_check_mark:|:x:               |
|Color Temperature |ct  |153 - 500  |:heavy_check_mark:|:heavy_check_mark:|:x:               |

:warning: required parameter &nbsp; :heavy_check_mark: parameter allowed &nbsp; :x: parameter not allowed

The URL must at least be made up of the required parameters (:warning:). In addition, further allowed parameters (:heavy_check_mark:) can be appended. The parameters are appended to the URL as a query string (name/value pairs), see the example below.

#### Example
The url `http://192.168.0.1/light.hue?id=1&on=1&bri=127` means, switch on the light with id 1 and setup the brightness to a value of 127.

#### Security
Access is managed by a whitlist contains in [Settings](#Settings).

## Releases
This project build on the continuous integration (CI) platform [AppVeyor](https://www.appveyor.com/) and released in the [Release-Feed](https://github.com/rmmlr/HueHook/releases).

[![AppVeyor Build](https://img.shields.io/appveyor/ci/rmmlr/huehook.svg)](https://ci.appveyor.com/project/rmmlr/huehook)  
[![AppVeyor Tests](https://img.shields.io/appveyor/tests/rmmlr/HueHook/master.svg)](https://ci.appveyor.com/project/rmmlr/HueHook/build/tests)

[![GitHub Release](https://img.shields.io/github/release/rmmlr/huehook.svg)](https://github.com/rmmlr/huehook/releases/latest)  
[![GitHub (Pre-)Release](https://img.shields.io/github/release/rmmlr/huehook/all.svg)](https://github.com/rmmlr/huehook/releases) (Pre-)Release



## Credits

* **Elias Ruemmler** - *Initial work* - [rmmlr](https://github.com/rmmlr)

Under [Contributors](https://github.com/rmmlr/HueHook/contributors) you can see more project supporter.

### Open Source Project Credits

* [Q42.HueApi](https://github.com/Q42/Q42.HueApi) Bedienung der Hue-API

## License

This project (HueHook) is licensed under  [MIT License](http://www.opensource.org/licenses/mit-license.php "Read more about the MIT license form").  
Refer to [LICENSE](https://github.com/rmmlr/HueHook/blob/master/LICENSE.txt) for more information.

[![license](https://img.shields.io/github/license/rmmlr/HueHook.svg)](https://github.com/rmmlr/HueHook/blob/master/LICENSE.txt) 