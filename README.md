﻿![Logo](admin/daswettercom.png)
ioBroker.DasWetter.
===========================

[![NPM version](https://img.shields.io/npm/v/iobroker.daswetter.svg)](https://www.npmjs.com/package/iobroker.daswetter)
[![Downloads](https://img.shields.io/npm/dm/iobroker.daswetter.svg)](https://www.npmjs.com/package/iobroker.daswetter)
[![Tests](https://travis-ci.org/rg-engineering/ioBroker.daswetter.svg?branch=master)](https://travis-ci.org/rg-engineering/ioBroker.daswetter)

[![NPM](https://nodei.co/npm/iobroker.daswetter.png?downloads=true)](https://nodei.co/npm/iobroker.daswetter/)


This adapter reads weather forecast data from DasWetter.com.

You need an account on DasWetter.com. Register at https://www.daswetter.com/api/#/login
The account is for free under certain conditions.

In your account you will find three URL for four different data models:
* Forecast for the next 7 days and general information of the day: high and low, wind (symbol and description), Day symbol and weather conditions
* detailed information for 5 days and every 3 hours: The general daily information is the following: peak, lows, wind, gusts, Precipitation, relative humidity, 
sea level air pressure, snow line, Sunrise and sunset, dates related to the moon, local time
* Preview with detailed data every hour (only for the first 2 days, then every 3 hours)
* Prediction for 5 days and every 3 hours (in JSON format)

All four models are implemented and one should be used at least.
In settings URL like http://api.daswetter.com/index.php?api_lang=de&localidad=xxxx  must be used. Just copy the complete URL from your account.

## Hints

### icons used in vis
* Access icons like `http://ip:8082/adapter/daswetter/icons/tiempo-weather/galeria1/1.png`.
* in galerie5 and 6 original icons are in svg format. Vis app might have problems to visualize it. So convrted png are available. Just use option "use png"

### "current" in NextHours_Day1:
* DasWetter.com does not deliver real current weather values
* but sometimes it's helpfull to have the forecast of current hour available
* so we added "current" which is just a copy of related forecast hour values
* please make sure you call the adapter at least one time per hour to make sure "current" is updated well
* see also github feature request [issue24](https://github.com/rg-engineering/ioBroker.daswetter/issues/24)

## known issues
* at the moment DasWetter.com sends data which are different to their own specification. This is the reason why those data can not be parsed right now
As soon as we know how the json path will look like we will (re)implement it
* sometimes when deleting old data structure an out-of-memory exception is thrown

## Changelog

### 2.5.0 (2018-11-30)
* (René) since app has problems with svg we can use png instead. svg's are converted to png. In admin a new option is available to use original svg's or converted png's 
* (René) max. 500 datapoints are deleted per call to reduce work load, so it might take a few calls until all old data points are removed

### 2.4.0 (2018-11-26)
* (René) sunshine duration added
* (René) current in NextHours_Day1 and NextHours2_Day1 added

### 2.3.1 (2018-11-04)
* (René) clean up code

### 2.3.0 (2018-08-23)
* (René) support of 4. path (json)

### 2.2.0 (2018-08-20)
* (René) delete unused data structure

### 2.1.3 (2018-08-17)
* (René) typo fixed
* (René) missing Icon-URL's added

### 2.1.2 (2018-08-14)
* (bluefox) Configuration dialog was fixed

### 2.1.1 (2018-08-04)
* (René) parse timeout added
* (René) missing roles and states added
* (René) using of units from data structure

### 2.1.0 (2018-07-30)
* (bluefox) Added URLs to icons
* (bluefox) Added the roles and the names to states
* (bluefox) Icons moved to admin directory



### 2.0.0
* (René) new datastructure !not compatible to version 1.x!
now parsing all data from xml and store them in datapoints
for compatibility: in configuration old data structure can be enabled 
needs also 2.x of vis-weather-widget

### 1.0.3
* (René) bug fix for admin V3

### 1.0.2
* (René) bug fix for admin V3

### 1.0.1
* (René) Support of admin3

### 1.0.0
* (René) first stable version
* (René) symbol and symbolid: both values parsed	

### 0.1.6
* (René) bug fixing: wind-gust and wind-idb

### 0.1.5
* (René) testing changed

### 0.1.4
* (René) license changed

### 0.1.3
* (René) external png's corrected

### 0.1.2
* (René) dependencies added

### 0.1.1
* (René) UTF8 coding

### 0.1.0
* (René) first release

### 0.0.1
* (René) initial release

## License
Copyright (C) <2017, 2018>  <info@rg-engineering.eu>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.




