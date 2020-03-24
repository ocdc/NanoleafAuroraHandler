# Nanoleaf Management SmartApp

This smartapp is designed primariy to make using the custom DTH easier in the new Smartthings app.  The hope is eventually to be able to eliminate this and incorporate its functions into the DTH once the new app has stabilized.  But that hasn't happened yet, here is my experiment.

## Objectives

Expose missing tile funcions to the new Smartthings app, so the app can be installed and used in the new app.  The app will also work in the classic app.

## Details

This smartapp does not show the the presets or the next and previous buttons, but allows you to select from a list of all available scenes stored on your Nanoleaf which scene to activate.

The other new feature is the ability to find the Nanoleaf panelId through color tagging.  There is a new command in the DTH to set individual panel colors (see Readme for details), but it requres the panelId to work.  This tool helps in finding the panelId.  Nine different colors are used to identify panels, if you have more than nine, the colors will repeat, but will still leave you with a short list of panelIds to try.

The smartapp installs from the github in the standard manner.  It is not a perfect solution.  Navigation is not great and you may find bugs.  Feedback is welcome and I will see if I can fix issues.