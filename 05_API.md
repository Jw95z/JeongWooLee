---
layout: base
title: API
permalink: /api/overview
type: pbl
week: 7
---
<!-- HTML table fragment for page -->
## APIs in this Sub Menu
> HTML, CSS, and JavaScript are the front-end of the API.  Python and API resource definitions are used for RESTful API definitions. Abstraction of Frontend and Backend code, the exchange of standard data format (JSON), and guidelines for exchange (REST) is a technique that saves a lot of time between developers.  Learning APIs is a highly recommended step for every developer trying to break into the world of tech.<html>

<script>

    function testButtonClick(city) {
        
        if (!city.trim()) {
            alert("Enter a city.");
            return;
        }  

//alert("yo momma!:  " + city);

        // prepare HTML result container for new output
        const resultContainer = document.getElementById("astronomy");

        //clear contents of astronomy table
        resultContainer.innerHTML = "";

//alert("1: " + resultContainer);

        // prepare fetch options
        const url = "https://weatherapi-com.p.rapidapi.com/astronomy.json?q=" + city; 
                        
//alert("2: " + url);
            
        const headers = {
            method: 'GET', // *GET, POST, PUT, DELETE, etc.
            mode: 'cors', // no-cors, *cors, same-origin
            cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
            credentials: 'omit', // include, *same-origin, omit
            headers: {
                'Content-Type': 'application/json',
                'X-RapidAPI-Key': '0b6ef107f7msh5606de624633ceap17521ejsn27566d20ff5b',
                'X-RapidAPI-Host': 'weatherapi-com.p.rapidapi.com'
            },
        };

//alert("3: " + headers)

//alert("3a: pre-fetch" + headers);

        // fetch the API
        fetch(url, headers)
        // response is a RESTful "promise" on any successful fetch
        .then(response => {
            // check for response errors
            if (response.status !== 200) {

                const errorMsg = 'Database response error: ' + response.status;
                console.log(errorMsg);
                const tr = document.createElement("tr");
                const td = document.createElement("td");
                td.innerHTML = errorMsg;
                tr.appendChild(td);
                resultContainer.appendChild(tr);

                return;
            }
            // valid response will have json data
            response.json().then(data => {
                console.log(data);
                console.log(data.location)

                // World Data
                document.getElementById("name").innerHTML = data.location.name;
                document.getElementById("region").innerHTML = data.location.region;
                document.getElementById("country").innerHTML = data.location.country;
                document.getElementById("lat").innerHTML = data.location.lat;
                document.getElementById("lon").innerHTML = data.location.lon;
                document.getElementById("tz_id").innerHTML = data.location.tz_id;
                document.getElementById("localtime_epoch").innerHTML = data.location.localtime_epoch;
                document.getElementById("localtime").innerHTML = data.location.localtime;

                //alert("data.astronomy" + data.astronomy.astro.sunrise);
                // tr for each row
                const tr = document.createElement("tr");

                // td for each column
                const sunrise = document.createElement("td");
                const sunset = document.createElement("td");
                const moonrise = document.createElement("td");
                const moonset = document.createElement("td");
                const moon_phase = document.createElement("td");
                const moon_illumination = document.createElement("td");

                // data is specific to the API
                sunrise.innerHTML = data.astronomy.astro.sunrise;
                sunset.innerHTML = data.astronomy.astro.sunset; 
                moonrise.innerHTML = data.astronomy.astro.moonrise; 
                moonset.innerHTML = data.astronomy.astro.moonset; 
                moon_phase.innerHTML = data.astronomy.astro.moon_phase; 
                moon_illumination.innerHTML = data.astronomy.astro.moon_illumination; 

                // this builds td's into tr
                tr.appendChild(sunrise);
                tr.appendChild(sunset);
                tr.appendChild(moonrise);
                tr.appendChild(moonset);
                tr.appendChild(moon_phase);
                tr.appendChild(moon_illumination);

                // add HTML to container
                resultContainer.appendChild(tr);
            })
        })

//alert("4: post fetch");

    }


</script>

<body>

<h1>API Information and Example</h1>

<a href="#astronomybutton"><button> Astronomy API </button></a>

    
<!-- HTML table fragment for page -->


If you choose a city, it will list out the location and astronomy details.

<div id="astronomybutton">


<label for="city">Enter city name:</label>
<input type="text" id="city" name="city">&nbsp;&nbsp;<input type="button" value="Get Location & Astronomy" onclick="testButtonClick(document.getElementById('city').value)">
<br><br>

<table>
  <thead>Location Details
  <tr>
    <th>City</th>
    <th>Region</th>
    <th>Country</th>
    <th>Latitude</th>
    <th>Longitude</th>
    <th>Time Zone</th>
    <th>Local Time Epoch</th>
    <th>Local Date and Time</th>
  </tr>
  </thead>
  <tbody>
    <td id="name"></td>
    <td id="region"></td>
    <td id="country"></td>
    <td id="lat"></td>
    <td id="lon"></td>
    <td id="tz_id"></td>
    <td id="localtime_epoch"></td>
    <td id="localtime"></td>
  </tbody>
</table>






<table>
    <thead>Astronomy Details
    <tr>
        <th>Sunrise</th>
        <th>Sunset</th>
        <th>Moonrise</th>
        <th>Moonset</th>
        <th>Moon Phase</th>
        <th>Moon Illumination</th>
    </tr>
    </thead>
    <tbody id="astronomy">
        <!-- generated rows -->
    </tbody>
</table>    


<script>


/*
import requests

url = "https://weatherapi-com.p.rapidapi.com/astronomy.json"

city = input("Choose a city")
querystring = {"q":city}

headers = {
	"X-RapidAPI-Key": "0b6ef107f7msh5606de624633ceap17521ejsn27566d20ff5b",
	"X-RapidAPI-Host": "weatherapi-com.p.rapidapi.com"
}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.json)

print("Location details")
loc = response.json().get('location')  // turn response to json() so we can extract "world_total"
for key, value in loc.items():  // this finds key, value pairs in country
    print(key, ":", value)

print()

// This code looks for USA in "countries_stats"
print("Astronomy details")
astro = response.json().get('astronomy') // countries is the key, countries_stat is the value
// print(astro.items())
for key, value in astro.items():
	for x in value.keys() :
		print(x, ":", value[x])

//astro in astronomy:  # countries is a list
    //print(astro)
*/

<script>
