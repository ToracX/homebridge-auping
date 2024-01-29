![alt text](https://hotelsummit.nl/wp-content/uploads/Auping-logo.png)
# Homebridge-auping

A homebridge plugin to control Auping Smart Base with Auping Connect.

## How to use this plugin
This plugin creates a window accessories for each entry in the config.json. Now you can adjust the Smart Base between 0-100%. Where 0% is down flat and 100% is fully up. 

## Things to know when using this plugin
The auping connect is actually pretty dumb. It has no idea what the current position of the motors is. Thus the app can get out of sync when using both the app and the remote. Therefor it is recommended to only use the app. 

## How to install this plugin?
The prefered method is via homebridge web ui.
Other methods are, using NPM.
npm install homebridge-auping.
Or navigate to youre node_modules folder and use git clone. 


## How to setup this plugin?
I will assume you have the Auping Connect setup, and the app is working.

#### Obtaining IP-adress
First we will need the IP-adress of the Auping Connect. This can be found in the app. On the upper right of the screen click the cogwheel for the settings menu. Now scroll down and at the bottom you will see the IP-adress. 

#### Obtaining key
Second we will need the key. This can be found when clicking on share in the settings menu. This will open a sub menu with a 8 character code, underneath the QR code. This is the key.

#### CBU 
stands for controlbox unit. When you have only one Smart Base. This will always be 0. If you have 2 Smart Bases and want to control both of them in sync, also choose 0. 

Or this can be either 1 or 2 to control only one side of the bed. For example the left side is 1, the right side is 2. 

#### Motor 
Is the part of the bed you want to control. This can be: 
motor: 1 for head
motor: 2 for back
motor: 3 for legs

This is depending on what Smart Base you have. For 3M it is suggested to make multiple accessories, three for one motor each.

#### Duration up and down 
This plugin works by calculating how long a button should be pressed to reach the desired position in %. You need to count how long it takes the motor to go from the bottom position to the most upper position. For me 10 seconds, or 10000ms is perfect.

## Example config.json
    {
        "accessory": "AupingConnect",   
        "ipadress": "192.168.178.xxx",  
        "key": "xxxxxxxx",              
        "name": "Auping Smart Base",    
        "cbu": 0,                       //both sides
        "motor": 3,                     //legs
        "durationUp": 10000,          
        "durationDown": 10000,          
    },

Above config will control the leg side of both bases. 
