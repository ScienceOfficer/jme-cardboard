# jme-cardboard
Google Cardboard integration for jMonkeyEngine 3.1. Tested with cardboard.jar 0.5.8

Take any jMonkeyEngine 3 application and run it in mobile VR.

How do I use this thing!?

This has only been developed for jMonkeyEngine 3.1 (trunk).

Before using it, you need to add Android support to your project through the SDK:

http://wiki.jmonkeyengine.org/doku.php/jme3:android?s[]=android

You also need to follow the instructions for how to develop for Google Cardboard:

https://developers.google.com/cardboard/android/download

Then, the project specific things:
New way using CardboardHarnessFragment:
1. Add jme-cardboard.jar to your project.
2. Turn on Android deployment for your project (Properties/Application/Android)
3. Follow these instructions to run jme in a fragment: http://www.softwarepioneering.com/2015/07/running-jmonkeyengine-3-on-android.html
But instead of extending AndroidHarnessFragment, extend CardboardHarnessFragment instead. MainActivity should extend CardboardActivity

For an example, look at test/CardboardStarTravel

If you need to set your own CardboardDeviceParams you can do so by a setter in CardboardContext. It has to be done before createView() is called.
You can access it via CardboardHarnessFragment:

((CardboardContext) getJmeApplication().getContext()).setCardboardDeviceParams(params);


If you wish to build the sources yourself, it needs access to an android.jar file.

Troubleshooting:
It seems to be important that the starting orientation is "forward" according to the cardboard. If you find that the screen is black when starting, try looking in the opposite direction, or rotate the spatial.
