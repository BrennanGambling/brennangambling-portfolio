# WayBack
<div style="text-align: center">
    <table>
        <tr>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/assets/screenshots/map_base.png?raw=true" width="150"/>
            </td>            
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/assets/screenshots/map_center_location.png?raw=true" width="150"/>
            </td>  
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/assets/screenshots/notification.png?raw=true" width="150"/>
            </td>   
        </tr>
        <tr>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/assets/screenshots/map_center_car.png?raw=true" width="150"/>
            </td>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/assets/screenshots/on_maps.png?raw=true" width="150"/>
            </td>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/assets/screenshots/directions.png?raw=true" width="150"/>
            </td>
        </tr>
    </table>
</div>

## Overview
Using seven different sensors, WayBack determines when you have parked your car.
This location is saved so if you forget where you parked you will have no problem finding your WayBack.

## Tour
The first time the application is opened, a background service is started that using multiple phone sensors determined when you have parked your car.
When the phone detects the user was in a moving car and then they no longer are, that means they must have parked their car.


To find the location of your car you can either click the "Find Car" button in the notification, or click on the car icon on the map.
This will open Google Maps with walking directions to your car.


By default WayBack will only display the last parking location on the map.
Older parking locations can be accessed from the Places page avaliable through the action menu.

## How It Works
WayBack's background service registers "Fences" with callbacks that will be called when the user's current "activity" changes.
There are several activities all related to movement that callbacks are avaliable.
They include activites like walking, biking, still, and driving.
A callback is registered for an activity changes and the last activity is compared to the new activity.
If the last activity was driving and now the activity is anything other than driving, the user must have parked their car.
When parking is detected the current location is saved in a SQL database along with the last 9 car locations.
To reduce battery usage location services are only used when parking has been detected.


The users current location and the location of the last parking spot are both displayed on the main page's map.
The current location is displayed as the default blue dot and the car location is displayed as a car icon.


To get the last parking location the user can go either to the map and find the car icon, or if out of the displayed range of the map the user can also click the "Find Car" button on the notification.
The nine previous parking location are also avaliable on the Places page which is avaliable by open the "3 dots" menu.
When the user clicks the "Find Car" button on the notification an Intent for Google Maps is dispatched asking for walking directions to the latitude and longitude of the parking location.
When the car location is acessed from the main page the user also has the option to just open the car location in Google Maps instead of getting directions to the location.


The map and location are displayed using a Google Maps fragment.
A custom map "pin" with a car icon is added to the map with the last known location.