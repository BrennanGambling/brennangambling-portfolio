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

## [Wayback][wayback_main]

## [PotholeReporter][pothole_reporter_main]
<div style="text-align: center">
    <table>
        <tr>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/email_page.png?raw=true" width="200"/>
            </td>            
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/main_page.png?raw=true" width="200"/>
            </td>
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/map_page.png?raw=true" width="200"/>
            </td>     
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/report_page.png?raw=true" width="200"/>
            </td>     
            <td style="text-align: center">
                <img src="https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/assets/screenshots/settings_page.png?raw=true" width="200"/>
            </td>  
        </tr>
    </table>
</div>



[pothole_reporter_main]: https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/pothole-reporter/README.md
[wayback_main]: https://github.com/BrennanGambling/brennangambling-portfolio/blob/master/wayback/README.md
[bloc_flux_main]: https://github.com/BrennanGambling/bloc_flux

[general_architecture_img]: https://github.com/BrennanGambling/bloc_flux/blob/master/bloc_flux/doc/images/main/bloc_flux_architecture.png?raw=true