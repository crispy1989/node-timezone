node-timezone
=============
[![build status](https://secure.travis-ci.org/justin-john/node-timezone.png)](http://travis-ci.org/justin-john/node-timezone)


Node.js client library for accessing [Google Time Zone API](https://developers.google.com/maps/documentation/timezone).
It provides time offset data for locations on the surface of the earth.
Requesting the time zone information for a specific Latitude/Longitude pair will return the name of that time zone, the time offset from UTC, and the Daylight Savings offset.

## Installation

```bash
$ npm install timezoner 
```

## Usage

```js
    var timezoner = require('timezoner');
	/* Request timezone with location coordinates */
	timezoner.getTimeZone(
		39.6034810, // Latitude coordinate
		-119.6822510, // Longitude coordinate
		function (err, data) {
			if (err) {
				console.log(err);
			} else {
				console.log(data);
			}
		}
	);
```
#####Response data:  
	{
	   "dstOffset" : 0.0,
	   "rawOffset" : -28800.0,
	   "status" : "OK",
	   "timeZoneId" : "America/Los_Angeles",
	   "timeZoneName" : "Pacific Standard Time"
	}

You can pass in an optional options as a last argument, it can be useful for override [sensor](https://developers.google.com/maps/documentation/timezone/#RequiredParam) of Google Timezone API. The `sensor` defaults to `false`. 
```js
	timezoner.getTimeZone(
		39.6034810,
		-119.6822510,
		function (err, data) {
			if (err) {
				console.log(err);
			} else {
				console.log(data);
			}
		},
		{ sensor: true }
	);
```
The `sensor` specifies whether the application requesting data is using a sensor (such as a GPS device) to determine the user's location. It accepts true or false.

You can find more details about response and different status of response from [Time Zone Responses](https://developers.google.com/maps/documentation/timezone/#Responses).

## License

The MIT License (MIT)

Copyright (c) 2013 Justin John Mathews <justinjohnmathews@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
