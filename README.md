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
Using seven seven different sensor WayBack determines when you have parked your car.
This location is saved so if you forget where you parked you will have no problem finding your WayBack.

### Tour
On first start of the application a background service is started that using multiple phone sensors determined when you have parked your car.
When the phone detects the user was in a moving car and they no longer are that means they must have parked their car.


To find the location of your car you can either click the "Find Car" button in the notification, or click on the car icon on the map.
This will open Google Maps with walking directions to your car.


By default WayBack will only display the last parking location on the map.
Older parking locations can be access from the Places page avaliable through the action menu.

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
Pothole Reporter allows you to quickly report potholes to the appropriate city officials. 
All you have to do is take a picture of the pothole in the application and then hit the “Send Email” button. 
The location of the pothole is taken from your phones GPS and based off of the latitude and longitude the app determines what city you are in. 
You can also report potholes using a Google Maps pin Drop. 
Based off of this information the address component of the email is auto filled based on the received location. 
The Subject line and body of the email is also auto filled. 
The body of the email consists of the latitude and longitude of the location at which the photo was taken and a picture of the pothole.



[pothole_reporter_main]: https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/README.md
[wayback_main]: https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/README.md
[bloc_flux_main]: https://github.com/BrennanGambling/bloc_flux

[general_architecture_img]: https://github.com/BrennanGambling/bloc_flux/blob/master/bloc_flux/doc/images/main/bloc_flux_architecture.png?raw=true