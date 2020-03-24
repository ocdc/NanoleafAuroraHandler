# Nanolea fAurora Handler
Smartthings device handler for the Nanoleaf Aurora and Canvas Devices

## Introduction

Updated March 2020 by Melinda Little

January 2019 by Melinda Little

This is a fork of Steve the Geek's and Logan Fraser's original code for the Nanoleaf devices.  It updates the code to fix broken commands, add regular device refresh, calculate and display the HEX IP:PORT value for the device network id, and retrieve the API key within the device.  See instllation instructions below for details.

This code should not require a device recreation for those using existing code. After updating your code, please resave device by resaving device preferences in settings to set the timer and information tiles.

I do not have Hubitat or use IFTTT so those device handlers are unchanged by me, so I have removed them from this repository.  This repository is set up for GitHub integration with Smartthings.

## March 2020 Changes

Changes made to attempt to improve new app support, especially since official device support is not working well or at all.

New function - Set individual panel colors.  This new command will allow webcore and smartapps to set individual panel colors are needed, such as for notification purposes.  This should work well with the new Nanoleaf layers in scenes.  Command details are

   setPanelColor(panelId, Color, blink)
   
panelId is the Nanoleaf assigned panelId.  The new managment smartapp can assist with determining this

Color is the color to set the panel.  Standard color names of black, white, red, blue, green, yellow, pink, orange, purple are predefined.  Any other color can be set using the #xxxxxx hex color definition.  The # must be the first character and the remaining characters must be a vaild hex color with a length of 6.

Blink is true or false, false is the default if omitted.  This will determine if your panel will blink between your desired color and black.
   
For example setPanelColor("123", "red", blink=true) will set panel 123 to red and blinking 
   
   One important note, for this to work correctly with your existing scene, the Scene Transistion setting for the device must be Off. This is found in the Nanoleaf app, under device settings, found in the top right corner of the Dashboard.


## Installation Instructions

1.  Install device handler in Smartthings IDE either manually or through GitHub integration.  There is lots of help on how to do this on the Smartthings Community Forums.  Owner is Mellit7, Name is NanoleafAuroraHandler, and branch is master.

2.  Once the device handler is installed, under the device tab in the IDE create a new device using this handler.

3.  Find the IP address for your Nanoleaf.  I have taken the simple route of hard coding the port information, so you do not need to figure that out.  If you are reassigning ports then you should have no trouble changing the code, lines 153, 512, and 537.

4.  You can now continue to manually calculate the HEX values of IP:PORT as described in the forum entry, or you can enter the IP address value in the device settings preferences.  Once you save the settings the device will display the HEX information that you need.

5.  Once you have your HEX value, enter it in the ide under the devices tab for your lights as the device network id.  You cannot skip this step or the device communication will not work.

6.  Get an API key.  You may still continue to manually retieve and enter an API through methods like Postman and do not need to do anything additional if you have already used this method.  If you are doing a new install, you may find it easier to have the device set the key itself.  You will still need to go to the Nanoleaf you are setting up, take your mobile devide with you, and press the power key until the lights blink to indicate it is ready for a key to be retrieved.  Once the lights are blinking, press Get API Key on the device screen in Smartthings.  If successful, you will see the message "API Key Retrieved" displayed in a device tile.

You should now be ready to use your device to control your Nanoleaf.

## Additional Information

The device will refresh the status information from the device every 5 minutes.  For faster or slower rates, change line 231.

There are now two additional information tiles for the device.  

One is for the IP address information.  it will display ""No IP Address provided" unless you enter an IP address in preferences.  If you have correctly set the device network id (step 5 above), the device will still function properly.

The second indicates the API Key status.  If you retrieve an API key through the device and enter on in the preferences, the Device will use the retrieved API key and the status will reflect it.  This field will display one of the following messages.
- API Key Retrieved
- API Key Was Entered
- No API Key Found   (device will not work if this is displayed)

There is a Clear API Key button on the device if for some reason you need to remove the retrieved API key from the device.  If you only need to get a new API key, step 6 above can simply be repeated and a new API key will be retrieved and replace the existing API key.  The Clear API Key wil set the stored value to an empty value.



