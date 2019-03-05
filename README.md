# Brennan Gambling's Projects

## [bloc_flux][bloc_flux_main]
The goal of the bloc_flux package is to take the best parts of the Flux and BLoC state management patterns.

![General Architecture][general_architecture_img]

The general architecture of a bloc_flux application is similar to that of a Flux application. 
A bloc_flux application consists of a single **Dispatcher** that dispatches **Actions** to all registered **Blocs**. 
All data flows from component to component in Observables.
**Observables** (from RxDart) are like streams with more built in features for stream transformations and are by default **synchronous** whereas most stream implementations are **asynchronous**.
The only input and output to the Dispatcher occur in the form of Actions. 
The Blocs then receive any dispatched Actions from the Dispatchers actionObservable. 
The Blocs do not receive input from anywhere else. 
Blocs then update their state in response to the Action. 
Any changed values will be added to an output Observable. 
Views listen to the output observables on the Blocs and rebuild whenever a new value is available. 
The output observable also emits the last emitted value to every new listener so default init values do not have to be specified.

## [WayBack][wayback_main]
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

### Overview
Using seven different sensors, WayBack determines when you have parked your car.
This location is saved so if you forget where you parked you will have no problem finding your WayBack.

### Tour
The first time the application, a background service is started that using multiple phone sensors determined when you have parked your car.
When the phone detects the user was in a moving car and then they no longer are, that means they must have parked their car.


To find the location of your car you can either click the "Find Car" button in the notification, or click on the car icon on the map.
This will open Google Maps with walking directions to your car.


By default WayBack will only display the last parking location on the map.
Older parking locations can be accessed from the Places page avaliable through the action menu.

## [PotholeReporter][pothole_reporter_main]
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

### Overview
Pothole Reporter allows you to quickly report potholes to the appropriate city officials based on their location.
All the user has to do is take a picture of the pothole and hit the "Send" button.
An email application will be opened with a preformatted email including the location and picture of the pothole addressed to the approriate city email address.
Currently support is limited to 50 large Ontario cities.

### Tour
#### Creating A Report
On the main page there are two buttons one to take a picture of the pothole and one to drop a pin on a map.

When the "Take Picture" button is pressed an Intent for a camera application is launched and the user takes a picture of the pothole.
After the picture is taken a report page will be shown with the location of the pothole and picture as well as the city email address.

When the "Drop Pin" button is pressed a map screen is opened where the user pans can drop a pin on the location of the pothole.
The pin will initially be placed on the users current location.
After the user hits the "Done" button the report page is launch with the location of the pothole and a Google Street View image of the location as well as the city email address.

[pothole_reporter_main]: https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/README.md
[wayback_main]: https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/README.md
[bloc_flux_main]: https://github.com/BrennanGambling/bloc_flux

[general_architecture_img]: https://github.com/BrennanGambling/bloc_flux/blob/master/bloc_flux/doc/images/main/bloc_flux_architecture.png?raw=true