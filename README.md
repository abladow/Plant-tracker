# Plant-tracker

## Executive summary
For optimum growth speed and output Hydroponics, aeroponic, and other forms of urban agriculture requireconstant maintance and obseravation of various environmental factors such as humidity, tempurate, light levels, and water level among variables. These challenges add increased diffuculty to those that are trying to grow their own produce locally, enficently, and economically.

Project goals
- create an app that can view a predefined webpage at a click on a local network
- develop a IoT application the runs on a raspiberry Pi that has a forward facing webpage
- have the IoT app be able to measure, and potentially react to environmental changes
- have App be able ot display the current statistics of the planter boxes sensors

This project once fully developed would lighten the load of both commercial and recreational urban farmers, by having all the information be corrilated and displayed in a single place. This could assist those that would not have started due to time constraints be able too, and lessen the need for centrallized produce manufactoring, decrease food prices, and improve food security for many people.


## Requirements

As a urban farmer that commonly sells at a market, I want to be able to view the statistics of my planter boxes from anywhere on my operation, so the I can save time and be able to keep my plants in their optimal ranges for growth without have to physically examine each box.

**Accepetance criteria**
- Must be able to be accessed from anywhere on my local network
- Must be able to be accessed from any device via web browser or mobile app
- Must be able to interface with a number of tempurature, humidity, light, and water sensors for data
- Must measure and display the current planter box statistics in a user readable fashion
- Must be able to react to changes in the environment

As a recreational gardener that keeps a single box of plants, I want to be able to quickly see how the plants are doing and have it automatically adjust parameters, so that I do not have to consistently work on it.

**Accepetance criteria**
* Must be to easily accessible and quick to use so that I can glance at it any time im on the network
* Must be able to automatically measure and adjust parameters in the box
* Must be accessible on any Android phone or tablet

As a rival urban farmer that sells at the same market I want to be able disrupt or damage my rivals grow operation so that I can increase my prices and have a larger market share at the market

**mitigations**
* Implement logging on the actions completed by a given device
* Implement some form of accounts or user permission attached to actions
* Implement a form of whitelist for allowed users or devices
* control the distribution of the given version of the app or instance of it

As a rival urban farmer that sells at the same market I want to steal growth information and box setting parameters so that I can use them to increase my own crop yield.

**mitigations**
* Implement user accounts to control access
* Have the application only visible via designated apps on the local network 
* Have any on or off device data storage encrypted and/or password protected 

## High Level Design

[Plant-tracker high level](abladow.github.com/repository/Plant-tracker/planttracker.png)

## Component List
### Humidity/Tempurature sensor
This sensor measures the current percent humidity and tempurature in Celcius, sends it through the GPiO pins. Node-red has a specific module that can be installed to read the data.
### Light Sensor
This sensor uses a photoreactive sensor to detect whether or not there is a configurable amount of light shining on it. it only work in binary output on whether there is light or not over the GPiO pins of the raspberri PI.
### Water sensor
The water sensor is a repurposed rain sensor that is able to tell whether or not there is a sufficent configurable amount of water on the sensor board. It only provide output in binary reagarding whether there is water on it or not over the GPiO pins of the raspberri PI.
### LED array
this array can display information regarding parameters dispalyed on the plater-tracker operation be it location in temputure range or whether there is enough light or water. It runs off of the GPiO pins for power and data
### Raspberri PI
The Raspberri Pi is a self contained mini computer that has bluetooth, wifi, ethernet, and GPiO connections on it. This device is the primary hardware that acts as the server for the server-side of the application, and interprets the input.
### Node-red
Node red is web base development platform that is used to run the server-side of the application on the PI, it has number of modules that can be used to interpret data and display it through the Pi's output. It could be considered the heart and brain of the application
### Planter-tracker client app
This is an app designed and deployed using apache cordova and it has a button the when pressed opens up the trackers page on the PI server. this app acts as a dummy terminal to access all of the data on the server.

## Security analysis
Text describing high level diagram with red or other callouts identifying problem points or attacks.
[Plant tracker threats](abladow.github.com/repository/Plant-tracker/planttrackersec.png)

| Component name | Category of vulnerability | Issue Description | Mitigation |
|----------------|---------------------------|-------------------|------------|
| Raspberri PI | Device misuse | This component has the possibility of having the default webpage on the given port beign changed to a malicious site | Increasing the user permission requirements, and remove any unneccesary software or install software on light weight as possible hardware|
| Raspberri PI | DoS | There exist various forms of malware that effect the connection between the raspiberri pi hardware, kernal, and the node red software | Could be migated by properlly set up permission, and usage of anti-virus |
| Node-Red program | Unauthorized access | A malicous user on the network with the Ip address can access the device and its dashboard | could be migated via the creation of a whitelist, passphrase, or account system |
|Plant tracker client app| DoS | it is possible that the connection between the client and server can be compromised | Alternate forms of communication and various forms of DoS protection and mitgation software |
| Plant tracker client app | URL redirection | It is possible that the address the app uses to route to the server can changed to a different site or IP | possible mitigations could displaying the IP address along with being able to edit it and or having a form of ping that makes sure that it is the server on the other end of the connection |

##implementation
see file Plant-trackerclient-master.zip, and Planttrackerserver.json

## Testing plan
due to the simplistic and straight forward nature of teh application, The testing plan will be ass follows
* check if app connects to server on Rasberri PI
* Check if server registers the existance and data of each sensor
* Check if the tempurature sensor is able to change the tempurate meter on the app
* Check if the humidity sensor is able to change the humidity meter on the app
* check if light sensor changes state of light marker
* check if water sensor changes state of water marker

## Demonstration
[Demo](https://app.vidgrid.com/view/Sd3YyOHQlvrZ)
