# LabVIEWSplashScreen
Creating a Splash Screen in LabVIEW for a more professional start up experience with your users on your programs.

How it works:
The splash screen should be the first VI called from your application. It is a simple sequence structure where the first stage is to change the classis string indicator to match the background colour of your splash image.

To modify the splash image, simply delete it and replace it with one you like. For me, I then opened paint and got the RGB colouring for the background, I then changed the constants in the first sequence to match that colouring and voila, it looks like just a label like in C#! Note: You may want to resize for your particular image. The VI has many disabled features from File -> VI Properties -> Window Appearance which give it the splash screen look and feel.

In the subsequent structure I then have a random "Starting Engines" and finally I load a .NET module in the next. The purpose of this third structure is where you should load things up, like ini files, .NET containers, C DLL's, anything which will take time and is part of your initialisation. If these result in indicators/controls, just hide them outside of the view of the front panel.

In our final sequence, we then "call and forget" (that's the purpose of the 80 input and the asynchronous calling convention) our actual main VI that the user will ultimately use or our first real VI we want them to use. I have set inputs on it's front panel (hidden out of view) of things we will pass it, like the .NET constructor reference and any errors which occurred in startup. It would be better to probably have this as a cluster of all the data you wish to be gathered in start up as well as references. For C DLL's, you may not have a reference to it, but it's good to start these up anyway so they're loaded into memory. Please note: LabVIEW only holds one DLL in memory at a time (unless that's changed) so try to keep any C DLL's to one if you can.

Finally, we close the splash screen now that our main application is up and running. For me, I've just created a dummy VI to quickly show this.
