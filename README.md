# nuernberg-messwerte-api# Nürnberg messwerte API

``POST`` Requests only
no API - Token needed

Get Stations
> List of the different Stations
``` JavaScript
const  station_list = await fetch(
	"https://microservices.nuernberg.de/umweltdaten/api/umweltdaten/get_stations/",
	{
		method: 'POST',
		headers: {
			'Accept': 'application/json',
			'Content-Type': 'application/json'
		},
		body: JSON.stringify({all: 1})
	}
).then(res  =>  res.json());
```
Get Measure Editorial
> List of the different Measurement types

``` JavaScript
const  measure_editorial  =  await  fetch(
		"https://microservices.nuernberg.de/umweltdaten/api/umweltdaten/get_measure_editorial/",
		{
			method: 'POST',
			headers: {
			'Accept': 'application/json',
			'Content-Type': 'application/json'
		},
		body: JSON.stringify({all: 1})
	}
).then(res  =>  res.json());
```
