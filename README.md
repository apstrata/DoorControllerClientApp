DoorControllerClientApp
=======================

Sample kinoma application that interacts with the DoorControllerApp (aiutomatically opens the door, etc.)
** Note: you need to use this application in combination with DoorControllerApp and DoorControllerApp-backend **

How to use 
==========

# Import the project to Kinoma studio
# Click on "application.xml" then right-click "Run as" > "Kinoma simulator". This launches a virtual Kinoma player device
# A button is displayed in the middle of the screen. 
# You can also export the application as an Android app. Double-click on "application xml" send click on "Android Export Wizard"
When a DoorControllerApp instance is found and if it authenticates the current client, the button displays "close". 
# Tapping/clicking on the button instructs the DoorControllerApp instance (if any) to respectively close/open the lock

How it works
============

# When the DoorControllerClientApp (hereafter referred to as "client") is launched, it starts discovering instances of 
DoorControllerApp (hereafter referred to as "controller"). For this sample app we consider that there is only a single 
DoorControllerApp.
# Once a DoorControllerApp is discovered, the client invokes Apstrata's VerifyCredential API, signing the request 
with the end user username and password, in order to obtain an authentication token  (valid for 5 minutes only)
# Once an authentication token is obtained from Apstrata, the client sends it along a message to the controller, instructing
it to open the lock
# If the response to the message received from the controller is successful, the button switches from open to close or vice
-versa depending on the instruction that was sent (close/open)
# Pressing on the "close" respectively "open" button will triggers again step 2 and 3 above (in step 3, the instruction
will vary from open to close depending on the button that was pressed)
