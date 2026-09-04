# Partly Cloudy

## Description:
WeatherNow just launched — a clean, simple weather lookup for any city.

Word around the dev team is that an old internal monitoring integration was supposed to be ripped out before this went live. Nobody's totally sure if it actually was.

Find out what's still running behind the scenes — and use it to figure out something the interface was never meant to show you.

## Flag:
BTWCTF{G00D_G01NG_F74G_F0UND}

## Solution:
1. Open Network tab and search for a city (chennai or mumbai or delhi)

2. Open the network request `weather?city=chennai`

3. Get the SyncToken from it - MAIN

4. Combine it with the region code CHN

5. Navigate to the endpoint `/api/station-info?station=CHN_MAIN