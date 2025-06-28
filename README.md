# Nürnberg messwerte API

``POST`` Requests only
no API - Token needed

### Get All Stations
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

### Get Stations by Category
> List of all Stations in category

|Category| cat_id |
|--|--|
|Außenluft| 0 |
|Wetterdaten| 1|
|Fließgewässer| 2|

``` JavaScript
const  station_list = await fetch(
	"https://microservices.nuernberg.de/umweltdaten/api/umweltdaten/get_stations/",
	{
		method: 'POST',
		headers: {
			'Accept': 'application/json',
			'Content-Type': 'application/json'
		},
		body: JSON.stringify({cat_id: 0 || 1 || 2 })
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

### Get Stations by "Type"
> List of all Stations in category  and measure id?

|Category| cat_id |
|--|--|
|Außenluft| 0 |
|Wetterdaten| 1|
|Fließgewässer| 2|

``` JavaScript
const  station_list = await fetch(
	"https://microservices.nuernberg.de/umweltdaten/api/umweltdaten/get_stations/",
	{
		method: 'POST',
		headers: {
			'Accept': 'application/json',
			'Content-Type': 'application/json'
		},
		body: JSON.stringify({type: cat_id, id:  })
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


### Get Weather data
> this is at least the options for category 2


``` JavaScript
const  station_list = await fetch(
	"https://microservices.nuernberg.de/umweltdaten/api/umweltdaten/get_stations/",
	{
		method: 'POST',
		headers: {
			'Accept': 'application/json',
			'Content-Type': 'application/json'
		},
		body: JSON.stringify(
			// by yesterday
			{ cat: cat_id,type: station_code, measure: string, date_yesterday: date}
			// or by count of days ( 1, 7, 30 )
			{ cat: cat_id,type: station_code, measure: string, days: 1 || 7 || 30 }
			// or by timespan ( increment page every 5000 results )
			{ cat: cat_id,type: station_code, measure: string, date1: "yyyy-mm-dd",
			 date2: "yyyy-mm-dd", page: number }
		)
	}
).then(res  =>  res.json());
```
returns the following type
```
{
	// if success == 1; request was successfull
	success: number,
	// if result paginates, count of pages, else 0
	pages: number
	message: {
		// temperature in °C
		temperature: "AB.BC"; 
		date_entry: "DD.MM.YYYY HH:mm"
	}[]
}

```

