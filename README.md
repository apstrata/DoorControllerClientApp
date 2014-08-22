DoorControllerClientApp
=======================

Sample kinoma application that interacts with the DoorControllerApp (automatically opens the door, etc.).

**Note: you need to use this application in combination with [DoorControllerApp](https://github.com/apstrata/DoorControllerApp), [DoorControllerApp-backend](https://github.com/apstrata/DoorControllerApp-backend) and [kinoma-sdk](https://github.com/apstrata/kinoma-sdk)**

How to use 
==========

* Import the project to Kinoma studio
* Import the [kinoma-sdk](https://github.com/apstrata/kinoma-sdk) to Kinoma studio and link it to your project (or just copy the "apstrataClientModule.js" file 
to the "src" folder)
* Make sure that you have specified adequate values for your test in the main.xml file (DoorControllerClientApp/src/main.xml)
  * Set the value of the AUTH_KEY variable to your Apstrata auth key
  * Set the value of the ID variable to the username of one of your Apstrata users
  * Set the value of the PWD variable to the password of the aforementioned user
  * Make sure that the value of the URL variable points to your Apstrata cluster endpoint
* Click on "application.xml" then right-click "Run as" > "Kinoma simulator". This launches a virtual Kinoma player device
* A button is displayed in the middle of the screen. 
* You can also export the application as an Android app. Double-click on "application xml" send click on "Android Export Wizard"
When a DoorControllerApp instance is found and if it authenticates the current client, the button displays "close". 
* Tapping/clicking on the button instructs the DoorControllerApp instance (if any) to respectively close/open the lock

How it works
============

* When the DoorControllerClientApp (hereafter referred to as "client") is launched, it starts discovering instances of 
DoorControllerApp (hereafter referred to as "controller"). For this sample app we consider that there is only a single 
DoorControllerApp.
* Once a DoorControllerApp is discovered, the client invokes Apstrata's VerifyCredential API, signing the request 
with the end user username and password, in order to obtain an authentication token  (valid for 5 minutes only)
* Once an authentication token is obtained from Apstrata, the client sends it along a message to the controller, instructing
it to open the lock
* If the response to the message received from the controller is successful, the button switches from open to close or vice
-versa depending on the instruction that was sent (close/open)
* Pressing on the "close" respectively "open" button will triggers again step 2 and 3 above (in step 3, the instruction
will vary from open to close depending on the button that was pressed)
