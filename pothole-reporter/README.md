# PotholeReporter
<div style="text-align: center">
    <table>
        <tr>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/map_page.png?raw=true" width="150"/>
            </td>            
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/report_page.png?raw=true" width="150"/>
            </td>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/email_page.png?raw=true" width="150"/>
            </td>     
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/main_page.png?raw=true" width="150"/>
            </td>     
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/settings_page.png?raw=true" width="150"/>
            </td>  
        </tr>
    </table>
</div>

## Overview
Pothole Reporter allows you to quickly report potholes to the appropriate city officials based on their location.
All the user has to do is take a picture of the pothole and hit the "Send" button.
An email application will be opened with a preformatted email including the location and picture of the pothole addressed to the approriate city email address.
Currently support is limited to 50 large Ontario cities.

## Tour
#### Creating A Report
On the main page there are two buttons, one to take a picture of the pothole and one to drop a pin on a map.

When the "Take Picture" button is pressed an Intent for a camera application is launched and the user takes a picture of the pothole.
After the picture is taken, a report page will be shown with the location of the pothole and picture, as well as the city email address.

When the "Drop Pin" button is pressed a map screen is opened where the user can drop a pin on the location of the pothole.
The pin will initially be placed on the users current location.
After the user hits the "Done" button the report page is launched with the location of the pothole and a Google Street View image of the location, as well as the city email address.

#### Sending A Report
When the email Intent is launched the email will already be populated with the location (in the form of latitude and longitude pair) as well as the picture of the pothole/location.
The email will automatically be addressed to a city email address depending on the city the pothole is in.
At this point the user can send additional information or just hit the send button.

## How It Works
#### Take Picture Mode
When the user clicks the "Take Picture" button on the main screen an Intent for a camera application is launched.
The picture taken with the camera app is the picture used in the report.
After the picture is taken, the GPS is queried for the users current location.
This location is used for the report.

#### Pin Drop Mode
When the user clicks the "Pin Drop" button on the main screen an Activity containing a Google Maps fragment is launched.
The fragment has a pin centered on the screen and user can choose the location by panning and zooming.
By default the pin is placed on the users current location.
The location of the pin on the map is the location used for the report.
An HTTP request is sent to the Google Street View API containing the location of the pin on the map.
The API returns a link to a Google Street View image that will be used as the picture in the report.

#### Determining Location
If the "Take Picture" mode is used, the location will be determined by querying the GPS.
For the "Drop Pin" mode the location is the location of the pin dropped on the map.

#### Determining Email Address
1. **Get Location**: The location is obtained either from the current location for the "Take Picture" mode or the location of the dropped pin for the "Drop Pin" mode.
The location is in the form of a latitude longitude pair.
2. **Get City Name**: The city name is determined using the Google Reverse Geocoding API.
An HTTP request is sent to the Google Reverse Geocoding API containing the latitude longitude pair.
The API server returns a JSON object which is parsed before obtaining the city name from it.
3. **Get Email Address**: Using the city name an email address is looked up from a map of city names to email addresses.
Currently this map only contains 50 large Ontario cities.

#### Sending Email
When the user clicks the "Send" button, an Intent for an email application is sent.
The Intent includes the recipient email address (cities email address), the location and the picture either taken by the user or obtained from the Google Street View API.
The user can include additional information if needed and then send the email.
