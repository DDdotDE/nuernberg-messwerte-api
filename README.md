# Nürnberg messwerte API

``POST`` Requests only
no API - Token needed

### Get Stations
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
returns the following type
```
{
	id_station: number; 
	name: string;
	station_code: string;
	measure_list: string[];
}[]
```
`id_station` is the most important value here, you need it to get the data 
`measure_list` is the second most important value, with it you can filter the categories


### Get Measure Editorial
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
returns the following type
```
{
	id_measure_editorial: number; 
	name: string;
	pdf_path: string;
}[]
```
`pdf_path` relative path to a pdf or a empty string
